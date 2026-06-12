---
title: "Problems running binary files"
date: 2011-07-08
forum: General Help
---

### Post by rangleink on 2011-07-08
Dear All

I'm a relative novice on Ubuntu and am more of an end user than a programmer. I'm trying to install a binary file but I can't get it to run. I've been through the forums already and it's not a simple issue of using the right command to run the file (well I don't think it is). 

The file is executable, I have superuser privileges, and I have tried running it using:
./jinstall.bin
sudo ./jinstall.bin
sudo bash ./jinstall.bin

And I get an error message saying "No such file or directory"

This is a new VMware set up (Ubuntu 10.10). The IT department where I  work have set up the platform but don't haev any experience with linux systems (scary, I know).  

I'm concerned that i am missing a basic step or a basic programme (I installed a cshell onto ubuntu myself), but I don't really know where to start. 

The programme requires java, but I have that downloaded. I'd really appreciate any advice. Thanks.

---

### Post by haqking on 2011-07-08
> **rangleink said:**
> Dear All

I'm a relative novice on Ubuntu and am more of an end user than a programmer. I'm trying to install a binary file but I can't get it to run. I've been through the forums already and it's not a simple issue of using the right command to run the file (well I don't think it is). 

The file is executable, I have superuser privileges, and I have tried running it using:
./jinstall.bin
sudo ./jinstall.bin
sudo bash ./jinstall.bin

And I get an error message saying "No such file or directory"

This is a new VMware set up (Ubuntu 10.10). The IT department where I  work have set up the platform but don't haev any experience with linux systems (scary, I know).  

I'm concerned that i am missing a basic step or a basic programme (I installed a cshell onto ubuntu myself), but I don't really know where to start. 

The programme requires java, but I have that downloaded. I'd really appreciate any advice. Thanks.

have you made the file executable ?

changemod 755 jinstall.bin

or right click on it in a GUI and make it executabl

edit: sorry i just saw you said it was executable

I take it you are in the correct location for the file ?

You have changed directory to the location of the jinstall.bin file yes ?

---

### Post by jerome1232 on 2011-07-08
My bet is that your missing a library for it, was there any documentation that came with this binary that indicates the required libraries.

Failing that perhaps the script getlibs can help you automatically get the required libraries.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Erik1984 on 2011-07-08
You need to navigate to the folder where the executable file resides. By default when you open the terminal the active directory is /home/yourusername (shorthand ~). So cd /path/to/file and then ./jinstall.bin.

---

### Post by rangleink on 2011-07-12
Thanks of that suggestion. You were spot on.  I was missing a library. A friend suggested a specific library, which I've installed and now it launches without  hitch. 

I knew the set up would be missing something simple. 
Many thanks.

---

