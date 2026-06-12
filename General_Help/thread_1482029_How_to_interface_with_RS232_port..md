---
title: "How to interface with RS232 port."
date: 2010-05-13
forum: General Help
---

### Post by Speedhawk on 2010-05-13
I am new to ubuntu forums. I don't know whether we can ask this type of question. I am trying to interface a machine (lock in amplifier) with Ubuntu using a RS 232(25pin) to USB cable. I wrote a program in c to interact with the machine. I think the machine is detected (after connecting the machine a file is created in folder /dev with name ttyusb1. I heard that ubuntu has all the header files required to interface with the port. with the help of a person i wrote this program (please see the attachment below.) but i don't know whether the commands are right or wrong. the program is compiled. but when i run the program it is getting stuck. i have to stop the program using Ctrl+z. if anyone knows these commands (how to write to or read from the port) please help me with this program.:confused:


Any help is appreciated. Thanks a lot!!!

---

### Post by ritchie-w on 2010-05-13
Hello Speedhawk,

here is a small program using the rs232 port with a usb converter.

Hope it will help you. The main trick is almost the opening of the port.
So see the function setupRS232() and the termio commands.

Mainly the was a small test program for my main c++ program, which i write now totally in english. This program is a little mix of german and english.

But I guess it will help you.

Feel free to use the code.

Best regards

Ritchie

---

### Post by Speedhawk on 2010-05-14
Thanks a lot for the program!!! you rock :guitar:
I am new to programming. I don't know German and i don't know many of the functions in rs 232 communication. I would be grateful to you if you can tell me what each of the functions do.
I have to give inputs in the form of strings (eg: fmod 1 <lf>) so where should i change the program.

Thanks again for the program.:KS

---

### Post by zaphod777 on 2010-05-14
You might be reinventing the wheel in the software center there is a program called microcom.

> microcom is a minimalistic terminal program for accessing devices (e.g. switches) via a serial connection. It features connection via RS232 serial interfaces (including setting of transferrates) as well as in "telnetmode" as specified in rfc2217.

---

### Post by Speedhawk on 2010-05-14
Ohh!!
Thank you Zaphod. :)
but i don't know what is a minimalistic terminal program. can you tell me how to install and use it.

---

### Post by zaphod777 on 2010-05-14
You can install it from the software center

[IMG]http://lh3.ggpht.com/_sjlVRfKJcmw/S-05ymcLWgI/AAAAAAAABEE/sTP7sNNuvsU/s400/Screenshot-Ubuntu%20Software%20Center.png[/IMG]

Here are the options

> *****@zaphod:~$ microcom --help
Usage: microcom [options]
 [options] include:
    -p devfile      use the specified serial port device (/dev/ttyS0);
    -s speed        use specified baudrate (115200)
    -t host: port    work in telnet (rfc2217) mode
microcom provides session logging in microcom.log file
Exitcode 1 -  

******@zaphod:~$ 


---

### Post by Speedhawk on 2010-05-14
Thanks a lot Zaphod.
That program is not available in our internal repositories](*,). It took me this much time to find it .
Anyway Have a great weekend.:KS

---

