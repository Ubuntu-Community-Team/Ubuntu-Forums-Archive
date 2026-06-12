---
title: "bash error when launching a file."
date: 2011-06-08
forum: General Help
---

### Post by pizzaia on 2011-06-08
This is my problem

bash: /usr/local/uvlayout-pro/bin/headus: No such file or directory

but the file exists. If I uncheck the Allow execute as a program the error is

bash: /usr/local/uvlayout-pro/bin/headus: permission denied

I used the sudo command. Any suggestions to fix this?

(I tried to change the folder permissions to read and write, cause if I didn't, then the file, when not in nautilus, had an x in the top right of the icon. Before this it didn't work anyway)

Everytime I copy a file that is excecutable that x appears. I'm new in ubuntu. I appreciate some help.

Thank you for your time.

---

### Post by gmargo on 2011-06-08
What sort of file is it?  Use the "file" command on the executable to find out. Also try the "ldd" command to see what libraries it wants.

You might see this error if it's a 32-bit program, but you're on a 64-bit system, without having the 32-bit compatibility libraries installed.

---

### Post by pizzaia on 2011-06-08
> **gmargo said:**
> What sort of file is it?  Use the "file" command on the executable to find out. Also try the "ldd" command to see what libraries it wants.

You might see this error if it's a 32-bit program, but you're on a 64-bit system, without having the 32-bit compatibility libraries installed.

root@Scarface-Linux:/usr/local/uvlayout-pro/bin# file headus
headus: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped
root@Scarface-Linux:/usr/local/uvlayout-pro/bin# ldd headus
    not a dynamic executable

this is what it says. any suggestions of why the x appears on the icon? what doews it means?

how can I install the 32 bit libs??
 
Thanks for your help!

---

### Post by matt_symes on 2011-06-08
Hi

Do you have a 64 bit version of Ubuntu and have you installed the 32 bit libraries ?

```
uname -a
```to check for 64 bit

```
sudo apt-get install ia32-libs
```

for 32 bit libs

Kind regards

---

### Post by pizzaia on 2011-06-08
> **matt_symes said:**
> Hi

Do you have a 64 bit version of Ubuntu and have you installed the 32 bit libraries ?

```
uname -a
```to check for 64 bit

```
sudo apt-get install ia32-libs
```for 32 bit libs

Kind regards


this is the message after the code uname -a

Linux Scarface-Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Thanks for the answer, I'll try the other command.

---

### Post by matt_symes on 2011-06-08
Hi

Install the 32 bit libraries using the second command i posted. 

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by pizzaia on 2011-06-08
> **matt_symes said:**
> Hi

Install the 32 bit libraries using the second command i posted. 

Enter your password. It will not be echoed to the screen.

Kind regards


Thank you so much!!! It seams that someway, the first time I installed Ubuntu and everything worked, somehow I installed this libs by mistake (such a noob). Now I know that this is the problem. It worked great!
Thanks for the help!!

---

