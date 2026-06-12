---
title: "I can't import a file in a spreadsheet (Excel file)?!"
date: 2010-10-05
forum: General Help
---

### Post by jeremy28 on 2010-10-05
Hi all;

I have a file with ".tgff" format that a piece of it, is as below (this file is for describing a benchmark in hardware design):
```
# AMD ElanSC520-133 MHz
@PROC 0 {
# price buffered preempt_power commun_energy_bit io_energy_bit idle_power
  33    1        1.6           0                 0             0.16
#------------------------------------------------------------------------------
# type version valid task_time preempt_time code_bits task_power
# Angle to Time Conversion
0       0      1     9e-06     150E-6       6.9e+04   1.6

# Basic floating point
1       0      1     2.3e-05   150E-6       5.8e+04   1.6

# Bit Manipulation
2       0      1     0.00049   150E-6       2.9e+04   1.6

# Cache Buster
3       0      1     3.5e-06   150E-6       2e+04     1.6

# CAN Remote Data Request
4       0      1     1.8e-06   150E-6       1.4e+04   1.6

# Fast Fourier Transform (Auto/Indust. Version)
5       0      1     0.014     150E-6       7.1e+04   1.6

# Finite Impulse Response Filter (Auto/Indust. Vers)
6       0      1     6.9e-05   150E-6       1.7e+04   1.6

# Infinite Impulse Response Filter
7       0      1     8e-05     150E-6       8.7e+04   1.6

# Inverse discrete cosine transfom
8       0      1     0.00091   150E-6       7.5e+04   1.6

# Inverse Fast Fourier Transform (Auto/Indust. Vers)
9       0      1     0.013     150E-6       6.9e+04   1.6

# Matrix arithmetic
10      0      1     0.0067    150E-6       9.3e+04   1.6

# Pointer Chasing
11      0      1     0.00033   150E-6       9.6e+03   1.6

# Pulse Width Modulation
12      0      1     4.5e-06   150E-6       1.4e+04   1.6

# Road Speed Calculation
13      0      1     3.2e-06   150E-6       6.9e+03   1.6

# Table Lookup and Interpolation
14      0      1     3e-05     150E-6       6e+04     1.6

# Tooth To Spark
15      0      1     7.4e-05   150E-6       4.1e+04   1.6

# OSPF/Dijkstra
16      0      1     0.0012    150E-6       2.8e+05   1.6

# Route Lookup/Patricia
17      0      1     0.0032    150E-6       2.5e+05   1.6

# Packet Flow - 512 kbytes
18      0      1     0.00097   150E-6       2.6e+05   1.6

# Packet Flow - 1 Mbyte
19      0      1     0.002     150E-6       2.6e+05   1.6

# Packet Flow - 2 Mbytes
20      0      1     0.004     150E-6       2.6e+05   1.6

# Autocorrelation - Data1 (pulse)
21      0      1     3.1e-05   150E-6       4.4e+03   1.6

# Autocorrelation - Data2 (sine)
22      0      1     0.0051    150E-6       4.4e+03   1.6

# Auto-Correlation - Data3 (speech)
23      0      1     0.0048    150E-6       4.4e+03   1.6

# Convolutional Encoder - Data1 (xk5r2dt)
24      0      1     0.00068   150E-6       6.3e+03   1.6

# Convolutional Encoder - Data2 (xk4r2dt)
25      0      1     0.00081   150E-6       6.3e+03   1.6

# Convolutional Encoder - Data3 (xk3r2dt)
26      0      1     0.00092   150E-6       6.3e+03   1.6

# Fixed-point Bit Allocation - Data2 (typ)
27      0      1     0.0061    150E-6       5.4e+03   1.6

# Fixed-point Bit Allocation - Data3 (step)
28      0      1     0.00041   150E-6       5.4e+03   1.6

# Fixed Point Bit Allocation - Data6 (pent)
29      0      1     0.004     150E-6       5.4e+03   1.6

# Fixed Point Complex FFT - Data1 (pulse)
30      0      1     0.0013    150E-6       1.3e+05   1.6

# Fixed point Complex FFT - Data2 (spn)
31      0      1     0.0013    150E-6       1.3e+05   1.6

# Fixed Point Complex FFT - Data3 (sine)
32      0      1     0.0013    150E-6       1.3e+05   1.6

# Viterbi GSM Decoder - Data1 (get)
33      0      1     0.0031    150E-6       1.1e+04   1.6

# Viterbi GSM Decoder - Data2 (toggle)
34      0      1     0.0031    150E-6       1.1e+04   1.6

# Viterbi GSM Decoder - Data3 (ones)
35      0      1     0.0031    150E-6       1.1e+04   1.6

# Viterbi GSM Decoder - Data4 (zeros)
36      0      1     0.0031    150E-6       1.1e+04   1.6

# Compress JPEG
37      0      1     0.33      150E-6       2.4e+05   1.6

# Decompress JPEG
38      0      1     0.25      150E-6       2.9e+05   1.6

# High Pass Grey-scale filter
39      0      1     0.053     150E-6       7.6e+03   1.6

# RGB to CYMK Conversion
40      0      1     0.029     150E-6       5.8e+03   1.6

# RGB to YIQ Conversion
41      0      1     0.11      150E-6       7.2e+03   1.6

# Dithering
42      0      1     0.029     150E-6       3.6e+03   1.6

# Image Rotation
43      0      1     0.0061    150E-6       1.2e+04   1.6

# Text Processing
44      0      1     0.0091    150E-6       1.4e+04   1.6

# src-sink
45      0      1     1e-05     150E-6       80        1.6

}
```
 
I want to "Import" this file to a spreadsheet "openoffice spreadsheet" in linux or "Microsoft Excel" in windows so that:
Informations like this line:
```
# type version valid task_time preempt_time code_bits task_power
```

to be shown in columns, I mean each item (like type, version, ...) in one column and the values below them in the related column.
But I want that the first column to be intended for the "comment" lines like:
```
# Angle to Time Conversion

# Basic floating point

# Bit Manipulation
...

```
 
So that the related value of each one, to be shown in front of each comment: in 2th column, 3th column, ...

I can do this work with copy them and paste in a spreadsheet file one by one, but I want it to be done completely Automatic!

One solution is: saving this file (.tgff) in ".csv" format in linux and select the "space" character as a separator. 
but again, after opening it in the openoffice spreadsheet, we have to change some parts manually!

Anyway, is there a complete solution to do this?

Or is it required to have a program (some codes) to parse for example "#" items as "comment" in first column in linux and ...?

Or is there a Tool to do this in windows or specially in linux?

Or any Tip&Trick to do so?!

BTW, I've uploaded a sample ".xls" file in the following links to show the desired output in a spreadsheet together with ".tgff" file:
```
http://www.mediafire.com/?z2b6860ka40avdp
http://www.mediafire.com/?ts97g7529u2o9hx
```
 
I'll await your good suggestions please?!

TIA.

---

### Post by searchfgold6789 on 2010-10-05
Maybe you could try JEdit, it is possible that it has an extension for tgff files...
The [tgff website]("http://ziyang.eecs.umich.edu/%7Edickrp/tgff/index.html") has some good stuff.

---

