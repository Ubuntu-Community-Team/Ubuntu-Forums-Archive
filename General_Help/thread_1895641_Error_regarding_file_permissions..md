---
title: "Error regarding file permissions."
date: 2011-12-15
forum: General Help
---

### Post by UbuBegUsr on 2011-12-15
Hello, I downloaded Nvidia driver from its website and it was a **.run** file. I downloaded Java from its website and it was a **.bin** file. I know about the _PPA_ but installing the driver using it corrupted the system. I tried to install the 2 programs using this way which I used to install Savage 2:
```
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_32.bin
./Savage2Install-1.5.0-x86_32.bin
```When I installed the game, I didn't get any error but when I tried to install this files, I've got the same error:
```
bash: ./NVIDIA-Linux-x86-290.10.run: Permission denied
``` **Why?** What should I do?

---

### Post by lukeiamyourfather on 2011-12-15
Did you enable execution on the installer and are you running it as root (i.e. with sudo)? Also be sure to follow the directions from Nvidia like stop X before installing the driver.

---

### Post by UbuBegUsr on 2011-12-15
> **lukeiamyourfather said:**
> Did you enable execution on the installer and are you running it as root (i.e. with sudo)? Also be sure to follow the directions from Nvidia like stop X before installing the driver.
How to enable excution on the installer? It's all the steps which I used to install Java and the driver. If there's a step which I didn't use, write it. I'll search for the direction in Nvidia website.

---

### Post by lukeiamyourfather on 2011-12-15
> **UbuBegUsr said:**
> How to enable excution on the installer? It's all the steps which I used to install Java and the driver. If there's a step which I didn't use, write it. I'll search for the direction in Nvidia website.

An example command is below. Again, be sure to follow directions from Nvidia. If you don't, it won't work. Installing graphics drivers is more involved than installing other software.

```

chmod a+x NVIDIA-Linux-x86-290.10.run
sudo ./NVIDIA-Linux-x86-290.10.run

```

---

### Post by UbuBegUsr on 2011-12-15
> **lukeiamyourfather said:**
> An example command is below. Again, be sure to follow directions from Nvidia. If you don't, it won't work. Installing graphics drivers is more involved than installing other software.

```

chmod a+x NVIDIA-Linux-x86-290.10.run
sudo ./NVIDIA-Linux-x86-290.10.run

```
I'll. thanks. This the directions from Nvidia website**,** **"**Installation instructions: Once you have downloaded the driver, change  to the directory containing the driver package and install the driver by  running, as root, sh ./NVIDIA-Linux-x86-290.10.run**"** Can you explain the different between the 2 ways, please?

---

### Post by drmrgd on 2011-12-15
What Luke is suggesting is to first make sure the file is executable by changing the permissions on it (the "chmod a+x" part).  Then he is executing the file in the next line.  The instructions from Nvidia are basically saying the same thing, but ensuring that use the shell interpreter to run the file.  So, I would issue the command as:

```
sudo sh ./NVIDIA-Linux-x86-290.10.run
```

That will ensure that you execute the file as root and do essentially the same thing as luke suggested.

---

### Post by UbuBegUsr on 2011-12-15
Thanks all. So the code'll be like this:
```
cd /...
[FONT=monospace]chmod a+x Nvidia.run
[/FONT]sudo sh ./Nvidia.run

``` Right?

---

### Post by lukeiamyourfather on 2011-12-15
> **UbuBegUsr said:**
> Thanks all. So the code'll be like this:
```
cd /...
[FONT=monospace]chmod a+x Nvidia.run
[/FONT]sudo sh ./Nvidia.run

``` Right?

Yup. Plus the other Nvidia instructions like installing gcc and the kernel headers. :)

---

### Post by MartijnNL on 2011-12-15
Why cd /...?
And are you abbreviating the filename to save typing or did you rename the file?

If the file is on your Desktop the commands should be:

```
cd ~/Desktop
chmod a+x NVIDIA-Linux-x86-290.10.run
sudo sh ./NVIDIA-Linux-x86-290.10.run
```

The sudo bit executes the command as the root user, just like the instructions say.

---

### Post by mörgæs on 2011-12-15
Changed the thread title to a more descriptive one.

---

### Post by oldos2er on 2011-12-15
> **UbuBegUsr said:**
> Hello, I downloaded Nvidia driver from its website and it was a **.run** file. I downloaded Java from its website and it was a **.bin** file. I know about the _PPA_ but installing the driver using it corrupted the system. 

It would be worth starting a new thread to sort out whatever problems you're having with the PPA drivers. While there's nothing wrong with installing the driver from Nvidia, anytime there is a kernel upgrade you will have to reinstall it. If you use the PPA driver, this is taken care of automatically.

Please mention which model Nvidia card you have.

---

### Post by UbuBegUsr on 2011-12-19
Hello.
> Why cd /...?
And are you abbreviating the filename to save typing or did you rename the file?
If the file is on your Desktop...The file's not at the desktop. I didn't rename it. It's an example to save time.
> It would be worth starting a new thread to sort out whatever problems  you're having with the PPA drivers. While there's nothing wrong with  installing the driver from Nvidia, anytime there is a kernel upgrade you  will have to reinstall it. If you use the PPA driver, this is taken  care of automatically.

Please mention which model Nvidia card you have.     I've Nvidia 7300 GS. I installed updates for the system.
> Yup. Plus the other Nvidia instructions like installing gcc and the kernel headers. > **Installing the Kernel Interface**

    The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer.
 When the installer is run, it will check your system for the required kernel sources and compile the kernel interface. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required.
 After the correct kernel interface has been compiled, the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver.
How to do that?
> Changed the thread title to a more descriptive one. Thanks.

---

### Post by UbuBegUsr on 2011-12-22
Sorry for late reply, can you reply now? I'm here.

---

### Post by MartijnNL on 2011-12-22
Do you know how to navigate in a terminal to the directory containing the file? (using the 'cd' command)? If so, please do so. (If not, you might want to learn how to do so, for example [using this]("http://beginnerlinuxtutorial.com/help-tutorial/basic-linux-commands/change-directory-using-cd-linux-command/").)

If you don't know how to do so run:

```
sudo apt-get install nautilus-open-terminal
```

Open nautilus (the file manager) right click on the directory where your file is and choose "open in terminal".

Then once you have a terminal in the directory where the file is run the commands I gave earlier:

```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run
sudo sh ./NVIDIA-Linux-x86-290.10.run
```

I will be offline in about 45 minutes and probably won't be back on this forum (much) before January 2nd. So be quick if you need more help from me (or perhaps someone else can help you).

Edit: 45 minutes are about over. So I probably can't help you with this for a while.

---

### Post by UbuBegUsr on 2011-12-23
Hello, I know how to navigate but it's not my problem. My problem is following the instructions to install the diver. When I've my computer fixed, I'll try to install it. I hope I'll do it.

---

### Post by UbuBegUsr on 2012-02-05
I'm able to install it now. Thanks.
Problem: [COLOR=Lime]Solved[/COLOR].

---

