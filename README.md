# InkTime - Smartwatch cu nRF52840

Proiect de smartwatch ultra-low power bazat pe microcontrolerul nRF52840 și display E-Ink de 1.54 inch.

---

## 1. Diagramă Bloc
![Diagrama Bloc](Images/diagrama.png)
*Diagrama de interconectare a modulelor: nRF52840, Display E-Ink, RTC, Accelerometru și sistemul de alimentare.*

---

## 2. Bill of Materials (BOM)

| Componentă | Producător / Cod JLC | Link Achiziție | Datasheet |
| :--- | :--- | :--- | :--- |
| **MCU** | nRF52840 | [Link JLC](https://jlcpcb.com/partdetail/Nordic_Semiconductor-NRF52840QIAA_R/C190768) | [Datasheet](https://infocenter.nordicsemi.com/pdf/nRF52840_PS_v1.0.pdf) |
| **Display** | E-Ink 1.54" | [Link JLC](https://jlcpcb.com/) | [Datasheet](https://jlcpcb.com/) |
| **RTC** | PCF8563 | [Link JLC](https://jlcpcb.com/) | [Datasheet](https://jlcpcb.com/) |
| **Accel.** | LIS3DH | [Link JLC](https://jlcpcb.com/) | [Datasheet](https://jlcpcb.com/) |
| **LDO** | AP2112K-3.3 | [Link JLC](https://jlcpcb.com/) | [Datasheet](https://jlcpcb.com/) |
| **Charger** | TP4056 | [Link JLC](https://jlcpcb.com/) | [Datasheet](https://jlcpcb.com/) |

Tabelul detaliat poate fi găsit în directorul "Manufacturing"

---

## 3. Funcționalitate Hardware
Dispozitivul este construit în jurul SoC-ului **nRF52840** (arhitectură ARM Cortex-M4F), optimizat pentru consum redus și conectivitate BLE.

* **Module și Senzori:**
    * **Display E-Ink:** Tehnologie bi-stabilă care consumă energie doar la refresh. Comunică prin **SPI** (8MHz).
    * **RTC (Real Time Clock):** Menține timpul precis chiar și când MCU-ul este în Deep Sleep. Conectat prin **I2C** (400kHz).
    * **Accelerometru:** Permite detectarea mișcării (gestul de ridicare a mâinii) pentru activarea display-ului. Conectat prin **I2C**.
* **Alimentare:**
    * Baterie LiPo încărcată prin USB-C (controler TP4056).
    * Regulator LDO de 3.3V cu zgomot redus pentru stabilitatea senzorilor.
* **Calcule Consum:**
    * **Deep Sleep:** ~20-30 µA.
    * **Refresh activ:** ~3-4 mA pe durata tranziției imaginii.

---


## 4. Detalii Design

* **PCB Design:** Placa a fost realizată pe **4 straturi** pentru a asigura un plan de masă (GND) solid și o distribuție eficientă a alimentării (3V3), reducând interferențele pe liniile de mare viteză (SPI).
* **Stackup:**
    1. Layer 1 (Top): Semnale și componente.
    2. Layer 2: Plan de masă (GND).
    3. Layer 63: Plan de alimentare (3V3).
    4. Layer 64 (Bottom): Semnale secundare.
* **Review:** Componentele au fost grupate logic (zona de radio, zona de power, zona de senzori) pentru a minimiza lungimea traseelor critice..

## 5. Structura Repository
Hardware/
  - schematic (.sch)
  - board (.brd)

Manufacturing/
  - gerbers.zip
  - Bill of Materials (.bom / .csv)
  - Pick and Place (.cpl)

Mechanical/
  - ansamblu complet (.step)
  - fisierul Fusion360 al ansamblului complet

Images/
  - randari PCB
  - randari assembly
  - capturi schematic / board

LICENSE
README.md

