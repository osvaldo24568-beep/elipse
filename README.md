from abc import ABC, abstractmethod
import math

class Figura(ABC):
    @abstractmethod
    def calcular_perimetro(self) -> float:
        pass

    @abstractmethod
    def calcular_area(self) -> float:
        pass

    @abstractmethod
    def obtener_nombre(self) -> str:
        pass

class Elipse(Figura):
    def __init__(self, radio_mayor: float, radio_menor: float):
        self.radio_mayor = radio_mayor
        self.radio_menor = radio_menor

    def calcular_perimetro(self) -> float:
        a = self.radio_mayor
        b = self.radio_menor
        h = ((a - b) ** 2) / ((a + b) ** 2)
        return math.pi * (a + b) * (1 + (3 * h) / (10 + math.sqrt(4 - 3 * h)))

    def calcular_area(self) -> float:
        return math.pi * self.radio_mayor * self.radio_menor

    def obtener_nombre(self) -> str:
        return "Elipse"

if __name__ == "__main__":
    e = Elipse(5, 3)
    print(e.obtener_nombre())
    print(f"Perímetro (aprox): {e.calcular_perimetro():.2f}")
    print(f"Área: {e.calcular_area():.2f}")
