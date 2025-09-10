Exp-No: 02 - Write and simulate seven segment display using Verilog HDL and verify with testbench
Aim:

  To design and simulate a Seven Segment using Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.
Apparatus Required:

  Vivado 2023.1

Procedure:


Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu.
Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). Project Location: Select the folder where the project will be saved. Click Next. Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). Make sure to check the box "Copy sources into project" to avoid any external file dependencies. Click Next. Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). Default Part Selection: You can choose a part based on the FPGA board you are using (if any). If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). Click Next, then Finish.
Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier. Add the Verilog files (mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.) and the testbench (mux4_to_1_tb.v).
Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. Under "Synthesis", click "Run Synthesis". Vivado will check your design for syntax errors. If any errors or warnings appear, correct them in the respective Verilog files and re-run the synthesis.
Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench.
View and Analyze Simulation Results 
Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).
Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results". Save the report for reference in your lab records.
Save and Document Results Save your project by clicking File → Save Project. Take screenshots of the waveform window and include them in your lab report to document your results. You can include the timing diagram from the simulation window showing the correct functionality of the Seven Segment across different select inputs and data inputs.
Close the Simulation Once done, by going to Simulation → "Close Simulation

Input/Output Signal Diagram:

RTL Code:
```
  module seven_segment(bcd,seg);
    input  [3:0] bcd;       
    output reg [6:0] seg ;     
  always @(bcd)
  begin
  case(bcd)
          4'b0000: seg = 7'b0111111; 
          4'b0001: seg = 7'b0000110; 
          4'b0010: seg = 7'b1011011; 
          4'b0011: seg = 7'b1001111; 
          4'b0100: seg = 7'b1100110; 
          4'b0101: seg = 7'b1101101; 
          4'b0110: seg = 7'b1111101; 
          4'b0111: seg = 7'b0000111; 
          4'b1000: seg = 7'b1111111; 
          4'b1001: seg = 7'b1100111; 
          default: seg = 7'b0000000; 
  endcase
  end
  endmodule
```
TestBench:
```
  module segg7_tb;
  reg [3:0]bcd_t;
  wire [6:0]seg_t;
  seven_segment dut(.bcd(bcd_t), .seg(seg_t));
  initial
  begin
  bcd_t=4'b0000;
  #100
  bcd_t=4'b1000;
  #100
  bcd_t=4'b0011;
  end
  endmodule
```
Output waveform:
  <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/b457c11f-d2ad-4bb8-b1bf-f3e72e097a9c" />


Conclusion:
Thus, To design and simulate a Seven Segment using Verilog HDL and verified its functionality through a testbench using the Vivado 2023.1 simulation environment.
