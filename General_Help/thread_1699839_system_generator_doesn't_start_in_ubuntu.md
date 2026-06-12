---
title: "system generator doesn't start in ubuntu"
date: 2011-03-04
forum: General Help
---

### Post by pavankumarl73 on 2011-03-04
Hello,
         I'm new to the concept of sysgen. I installed ISE 12.2 DSP edition trail version and I have matlab 2009b edition.  After a brief search I found &#65279;[http://xlnx.lithium.com/t5/Installation-and-Licensing/System-Generator-Won-t-Start-in-Linux/m-p/4544](http://xlnx.lithium.com/t5/Installation-and-Licensing/System-Generator-Won-t-Start-in-Linux/m-p/4544)... this. But directory hierarchy is different in 12.2 than that of mentioned in that forum link. 
 
       I have installed matlab at /home/trans/Matlab and xilinx at /home/trans/Xilinx. Though I have sysgen_startup.m at &#65279;&#65279;/home/trans/Xilinx/ISE_DS/ISE/sysgen/util if I try to run sysgen by using command "./sysgen" I get error as &#65279;
 
ERROR: Could not find SysGen startup script at "/home/trans/Xilinx/ISE/sysgen/util/sysgen_startup.m".
 
As per the above mentioned link I found sg_config at /home/trans/Xilinx/ISE_DS/ISE/sysgen/bin/lin and used command &#65279;"./sg_config -install_to_matlab /home/trans/Matlab" I get message like this
 
 
[: 26: unexpected operator
[: 28: /home/trans/Xilinx/ISE_DS/ISE/sysgen/lib/lin:: unexpected operator
DSPTools successfully installed into MATLAB!
 
[: 26: unexpected operator[: 28: /home/trans/Xilinx/ISE_DS/ISE/sysgen/lib/lin:: unexpected operatorDSPTools successfully installed into MATLAB!
 
Then I ran matlab by giving command ./matlab and opened simulink. I found HDL libraries in simulink but when I tried to generate HDL code I got error like 
 
 
Warning: Failed to update device information. It is possible that the device
target information in a System Generator token is out of date with respect to
your ISE installation. Failed cast to Dictionary
 
 
 
ans =
 
Error using ==> xlgetpartinfo
The environment variable "XILINX" currently points to "/home/trans/Documents/MATLAB", which is not a valid ISE installation.
 
 
ans =
 
Error using ==> xlgetpartinfo
The environment variable "XILINX" currently points to "/home/trans/Documents/MATLAB", which is not a valid ISE installation.
 
 
I didn't understand the above error. I have chosen matlab workspace as /home/trans/Documents/MATLAB but I haven't pointed anything to that location. 
 
So finally how do I set environmental variables at /home/trans/Xilinx/ISE_DS/ISE and how do I get sysgen to work?
I installed ISE from the DVD which I got from xilinx
 
reply would be really appreciable

---

### Post by tommpogg on 2011-07-01
Hi,

You can set the environmental variables by running 
[INDENT]source settings32.sh
[/INDENT]This file is located in the ISE installation directory.
This should also fix your problems with system generator.

Nevertheless, last time I have installed xilinx ISE (+ system generator), I needed to run settings32.sh each time I open a shell.
Thus, I have modified the script .bashrc (in my home folder) by adding the following line at the end:
[INDENT]source /usr/local/xilinx/ISE_DS/settings64.sh > /dev/null
[/INDENT]I used the command "> /dev/null" in order to suppress the output of source

Hope it helps you

PS: Once you have managed to install xilinx system generator, I suggest to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1789063"). Just in case you find system generator to be too slow

---

