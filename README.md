# # Experiment-01
## 1)	Title page
LT spice Simulation of Common source Amplifier

## 2)	Objective 
The goal of this simulation-based study is to evaluate the performance of a Common Source (NMOS) amplifier using the 180nm technology node. The analysis is divided into three critical stages
- DC Analysis: To establish the biasing conditions and fix the Quiescent (Q) point.
- Transient Analysis: To observe the time-domain signal inversion and peak-to-peak voltage response.
- AC Analysis: To characterize the small-signal voltage gain and determine the frequency-dependent phase shift.
## 3)	Circuit Description
•	Circuit Components
   - NMOS (180nm technology node)
   - Resistor- 3.75K
   - Voltage source (1.5V, 0.9V)
   - AC ground
   - Wries

## 4)	Circuit Schematic 

![Image](https://github.com/ullasnarahatti/experiment/blob/main/ckt.png?raw=true)
##### Fig 1: CS Amplifier with all the components

## 5)	Procedure 
1.	Build the common source amplifier circuit as the circuit diagram using LTspice.
2.	Set the Resistor value as 3.75K, DC voltage as 1.5V, Gate voltage as 0.9V.
3.	Download the library file tsmc018 (1).txt
4.	Create a folder. Save the library file and LTspice file to the folder.
5.	Import the library file to LTspice using spice directive(.op).
6.	Set the mosfet model name CMOSN as given in the library file, length as 180nm, width as 1.07uF.
7.	Find the current value for the given power rating.
8.	DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.
9.	Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.9V, Amplitude 10mV, frequency 1KHz. Keep stop time for 5ms and run to get the expected waveform.
10.	AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 10, start and stop frequency as 0.1Hz and 500GHz to get the expected ac waveform.

## 6)The design utilizes an NMOS transistor with the following parameters:
- Technology: 180nm CMOS (via tsmc018.txt).
- Drain Resistor ($R_D$): $3.75\text{ k}\Omega$.
- Supply Voltage ($V_{DD}$): $1.5\text{V}$.
- Gate Bias ($V_G$): $0.9\text{V}$.
- Vt : ($V_{Vt}$): $0.36\text{V}$.
- Device Dimensions: $L = 180\text{nm}$, $W$ is tuned to achieve the target current.
 - a) - VD=VDD/2.
    - 1.5/2= ($V_{VD}$): $0.75\text{V}$.
  - b) - RD=VDD-VD/ID.
     - (1.5-0.75)/200uA= ($R_D$): $3.75\text{ k}\Omega$.
  -  c)W=μCox​(VGS​−Vt​)22ID​L
  -  μ=273.89×10^(-4)
  -  Eox=𝜀𝑟ε0​.
  -  𝜀𝑟=3.9.  ε0​=8.854×10^(-12)
  -   Eox=𝜀𝑟ε0​=34.53×10^(-12)
  -   tox=4.1×10^(-9)
  -   μCOX=Eox/tox=230.5×10^(-6)​
  -   W=(2×200u×180n)/(230.5u×(0.9-0.36)=1.07u
    
## 7)	Theory And Simulation Setup
#### DC Analysis :
In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.The MOSFET operates in the saturation region when drain-source voltage(VDS) is greater than the overdrive voltage (VOV=VGS-VTH). the drain current is given by
ID= 1/2Kn(VOV)2
VDS and ID provides the operating point of the MOSFET.

### Tabular column
![Image](https://github.com/ullasnarahatti/Experiment-1/blob/8d83d831c6155402c3a6da77986d2a06172235b7/Screenshot%202026-02-21%20102240.png)
##### Fig 2 : output of DC Ananlysis and Circuit

#### Transient analysis :
Transient analysis examines how the amplifier responds to time varying signals, such as pulse inputs or sudden changes in voltage. The behaviour is influenced by the charging and discharging of capacitors including coupling capacitors and bypass capacitors.The response of the amplifier due to the sudden changes in the input is limited by its time constants which depends upon the capacitance and resistance in the circuit. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifier's suitability for fast signals.

![Image](https://github.com/user-attachments/assets/eaa14547-bd3c-4dd5-9cd0-f6df86f5e690)
##### Fig 3: Transient Analysis Parameters 

#### AC analysis:
In AC analysis MOSFET treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge
iD=gmvgs
where gm is transconductance. Therefore, The voltage gain of the amplifier is given by
Av= -gm(RD||RL)
The negative sign indicates the 180 degree phase shift between the input and output signals. The input impedance is primarily determined by the gate biasing resitors whereas output impedance is largely influenced by the resistor RD . At low frequency the gain is effected by coupling capacitors and bypass capacitors, while at high frequencies by paracitic capacitors.

![Image](https://github.com/ullasnarahatti/Experiment-1/blob/3ceae5d584af28656e2b7d75412f8d7c2016be7c/Screenshot%202026-02-22%20060346.png)
#### Fig 4: AC Analysis Parameters

## 8)	Results 
#### 1. DC Analysis

![Image](https://github.com/user-attachments/assets/8081cf6c-e742-46bf-b9c3-7e5f98817674)
##### Fig 5: DC Analysis Result

- ID = 200uA
- width = 1.07um
- Vout = 0.745V
- DC operating point as (0.745V, 200uA)

  #### 2. AC Analysis

  ![Image](https://github.com/user-attachments/assets/eb0725db-8f27-4adb-bbad-87b8fc9cc726)
##### Fig 6: AC Ananlysis Result

- At Frequency = 204.527 kHz
- Gain = 7.18 dB
- Phase shift = 177.53°
  
#### 3. Tansient Ananlysis 

![Image](https://github.com/user-attachments/assets/24d8bf03-48cb-4eea-878f-98e55c54f8a9)
##### Fig 7: Transient Analysis Result

- A common source amplifier typically provides a 180° phase shift between input (Vin) and output (Vout) at mid-frequency.
- From the ploted graph, the phase shift at 204.527 kHz (marked on the graph) is approximately 177.53°
- This phase shift deviates from ideal 180° due to the influence of parasitic capacitances, load resistance, and MOSFET characteristics.
- Vout= 0.745V for width of 1.07um

  ## Inference
 - From the DC analysis, we determine the DC operating point of the MOSFET, which helps verify whether the transistor is functioning in the saturation region. This confirmation is crucial, as operation in saturation ensures that the MOSFET acts as an amplifier with the desired characteristics. 

- From the Ac analysis, The gain drops at high frequencies due to the bandwidth limitation,As frequency increases, the phase shift gradually approaches negative values, indicating a typical low-pass filter behavior of the common source amplifier, the common source amplifier operates as a voltage amplifier with a limited high-frequency response due to intrinsic capacitances.

- From the Transient analysis, At low frequencies, the phase shift remains close to 180°, confirming the inverting nature of the amplifier,At higher frequencies, the phase shift decreases due to the effects of the parasitic capacitances
-# Experiment-1
