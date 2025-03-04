# RTL_Design_RISCV32
Verilog Design For RISC V 32bit Processor

Overview
This project implements a 32-bit RISC-V processor using SystemVerilog. The processor supports arithmetic, logical, memory, and branch operations, as well as a halt instruction. It follows a simple instruction fetch-decode-execute cycle with condition flag updates.

Features

Instruction Set:
Arithmetic operations: MOVSGPR, MOV, ADD, SUB, MUL
Logical operations: AND, OR, XOR, XNOR, NAND, NOR, NOT
Memory operations: STOREREG, STOREDIN, SENDDOUT, SENDREG
Branch and jump instructions: JUMP, JCARRY, JZERO, JSIGN, JOVERFLOW, and their negated variants
HALT instruction to stop execution

Components:
Instruction Memory (Program Memory): Stores instructions
Data Memory: Stores data used during execution
General Purpose Registers (GPRs): 32 registers for computation
Special Register (SGPR): Stores the upper bits of multiplication results
Condition Flags: Sign, Zero, Carry, Overflow
Instruction Fetch-Decode-Execute FSM

Instruction Format
The instruction register (IR) is structured as follows:

[31:27] - Operation Type
[26:22] - Destination Register
[21:17] - Source Register 1
[16]    - Immediate Mode Select
[15:11] - Source Register 2 / Immediate Data High Bits
[10:0]  - Immediate Data Low Bits (if applicable)

Finite State Machine (FSM)
The processor operates in several states:
Idle - Waits for reset
Fetch - Loads instruction from program memory
Decode & Execute - Decodes and executes instruction, updates condition flags
Next Instruction - Advances the program counter (PC)
Sense Halt - Determines whether execution should stop or continue
Running the Processor

Prerequisites
Verilog simulator (e.g., ModelSim, Questa, Vivado, or Verilator)
Compiling and Running
Compile the top module and tb files.
Load the instruction memory with inst_data.mem using $readmemb.
Simulate the design to observe execution behavior.

Files in Repository

top.v: Main processor module
inst_data.mem: Instruction memory file
tb.v : Testbench Module


