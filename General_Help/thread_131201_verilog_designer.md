---
title: "verilog designer"
date: 2006-02-15
forum: General Help
---

### Post by sublime on 2006-02-15
is there a verilog design program that could replace the windows MAX+PLUS II software?  i have a couple designs from a lab class that i would like to open in ubuntu.  trying to drift as far away from windows as possible.

---

### Post by frodon on 2006-02-16
I don't know if they are some freeware for verilog/vhdl compiling however there are many program for linux because linux is the most used OS for design development. For exemple you have : modelsim, cadence, synopsis, design compiler, ise (xilinx software).
But be careful that max+plus II is an altera software so if you use the altera libs in your design (i mean some and, nor, d-latch, ...) you will need to compile them to use it on ubuntu but it's not really complicated.

---

### Post by uno on 2006-02-17
Most linux design tools are setup for redhat linux. As of right now I'm trying to get xilinx's free tool to run on my ubuntu box, but there is some library dependecy I can't resolve. It says it need libXm.so.3 which I can't seem to find anywhere. The altera tool, which you mentioned, requires windows. 

There is an ubuntu package appropriately named verilog, that has the icarus verilog similator. That works good for simulations. And gtkwave is a decent waveform viewer. I don't know of a working synthesis tool for ubuntu.

---

