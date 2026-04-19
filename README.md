# Havlicek_2019_Repo
Reproducing Havlíček et al.: Quantum-Enhanced Feature Spaces
_____________________________________________________________________
Overview

This repository studies the quantum kernel method introduced in Supervised Learning with Quantum-Enhanced Feature Spaces (Havlíček et al., 2019).

The goal is not only to reproduce the pipeline, but to understand:
How quantum feature maps define kernel;
How kernel geometry affects classification;
and how feature-map choice influences the geometry of the embedding and therefore the kernel.
_____________________________
Key idea

In kernel-based supervised learning (e.g., SVM), only the kernel function

K(x,x′)=∣⟨ψ(x)∣ψ(x′)⟩∣^2

is required for training and classification.

In the quantum setting, classical data is encoded into quantum states using a feature map. The kernel is then computed as the overlap between these states, effectively embedding the data into a high-dimensional Hilbert space.
_____________________________
Repository structure

Part 01: Kernel basics
General idea of quantum kernel method is investigated in this part. Main goal of this part  was to understand the quantum kernel idea through the minimal working example. A simple circuit consist of Hadamard gates, single and two qubit phase gates used to generate feature map. After successfully simulating and calculating kernel matrix, several other circuits, such as circuit without entangling part, deeper circuit and possible example of bad circuit has been generated in order to compare and analyze.

Part 02: Havlicek feature map
In this part feature map that is simple but similar to Havlíček work has been generated. First manually applied all gates then another feature map has been generated using qml.adjoint() function.

Part 03: Classification and boundaries
In this part classical and quantum kernel matrices calculated in the simple data set and fed into classical SVM to perform training also the classification. Then estimated decision boundaries on both methods for comparison. To examine these methods further two-moons data set has been classified and corresponding decision boundaries estimated.

Part 04: Feature map complexity study
The goal of this part was to study how circuit depth affects feature map expressivity in kernel matrix. More general Havlíček style feature map has been generated and tested on 2-qubit 1 layer, 3-qubit 1,3,5-layers.
_____________________________
Main observations

On simple data sets both quantum and classical kernel methods gave 100% classification success.
Quantum kernel matrix were more expressive showing gradual similarities than classical RBF kernel matrix.
Decision boundary of quantum kernel method had a band-like architecture from phase-encoded overlaps in Hilbert space, while classical decision boundary was way more simple almost linear diagonal line.
The quantum decision boundary takes significantly longer to compute than the classical one.
When two methods tried on the two-moon shaped data, the classical RBF kernel performed significantly better. Accuracy after classification was 0.65 on the quantum method and 0.95 on the classical method.
This result also followed on the decision boundaries. Decision boundary from classical method was way more cleaner than quantum induced kernel method.
The kernel structure becomes richer as the number of qubits increases.
Deeper circuits showed more expressive kernels however for deeper circuits (e.g., ≥4 layers), the kernel begins to flatten, indicating loss of useful structure.
_____________________________
Conclusion

This work demonstrates that quantum kernels define similarity through the geometry of a quantum feature space rather than Euclidean distance.
While quantum kernels can produce richer and more structured similarity patterns, they are not universally superior. Their effectiveness depends on how well the feature map aligns with the dataset structure.
Increasing the number of qubits enriches the feature space, while increasing circuit depth enhances expressivity only up to a point. Excessive depth may lead to flattened kernels and reduced performance.
_____________________________
Next steps

Possible next steps include exploring more complex datasets, testing alternative feature maps, and extending the approach to photonic quantum circuits.
_____________________________
What surprised me

Quantum kernel decision boundaries have band-like structures
Quantum kernels are not always superior
Deeper circuits do not necessarily lead to better performance
Expressive kernel doesn't mean automatically "good" kernel
Feature-map and data set compatibility matter more than I have expected.

This work serves as a conceptual bridge toward more physically grounded implementations, such as photonic quantum kernels.
