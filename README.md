AIM:

To implement 4 bit synchronous up counter and validate functionality.

SOFTWARE REQUIRED:

Quartus prime

THEORY

4 bit synchronous UP Counter

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

image
<img width="764" height="762" alt="Screenshot 2025-12-27 134255" src="https://github.com/user-attachments/assets/a32b3d50-1a62-4e28-9346-4a610564e59b" />

image

Each flip-flop in this circuit will be clocked at exactly the same time. The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.” Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse. Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time. The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed. However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

Procedure 1.Initialize the shift register to a known state (e.g., all zeros). 2.Input a bit serially into the shift register. 3.Shift the contents of the register one position to the right (or left). 4.Output the shifted bit from the last stage of the register. 5.Repeat steps 2-4 for each bit you want to input and shift.

PROGRAM

module exp11(out,clk,rstn);
input clk,rstn;
output reg [3:0]out;
always @ (posedge clk)
begin
	if(!rstn)
	out<=0;
	else
	out<=out+1;
end
endmodule
Developed by;J.SRI SARAN RegisterNumber:25015592

RTL LOGIC UP COUNTER image<img width="1039" height="578" alt="Screenshot 2025-12-27 134332" src="https://github.com/user-attachments/assets/825b2a31-f717-47d3-9a43-431d431364bf" />


TIMING DIAGRAM FOR IP COUNTER image
<img width="1040" height="159" alt="Screenshot 2025-12-27 134440" src="https://github.com/user-attachments/assets/d5385ccd-50b6-4da3-aba5-33aeae78b1a0" />


TRUTH TABLE image

<img width="1054" height="339" alt="Screenshot 2025-12-27 134507" src="https://github.com/user-attachments/assets/e41e8cc1-3aaa-403a-af6d-7e878c277005" />


RESULTS Hence a 4 bit synchronous up counter is implemented correctly.
