---
title: "Checking Hardware Configuration On Ubuntu"
date: 2011-06-24
forum: General Help
---

### Post by carmenat250 on 2011-06-24
I'm not sure what these programs are called at the moment, but on Windows, they are a dime a dozen.

These apps, when you run them will scan your computer and tell you everything that you need to know about the hardware...processor speed, how much ram, size of hard drive, etc.

Is there something similar for Ubuntu that I can use?

---

### Post by DunZH on 2011-06-25
In ubuntu usually these functions are done by commands in the terminal.  Graphical programs aren't all that common.

Pls check out some 'commonly used commands' and get familiar with the terminal.  Its useful!

I don't have any really good ones handy, (never remember them later) but here is one:

 df -h

Which will show you all your mounted drives.

---

### Post by oldfred on 2011-06-25
Some command line tools that create info:

sudo lshw | grep -m 1 -A 25 "*-memory"
For explanation, lshw stands for list hardware, and spits out page after page of information on all the hardware in your machine, this information is then sent to grep, which searches for a key word. I have set a few flags for it, -m 1 which limits the search results to one, saving some time finding additional results when there is only ever going to be one in the hardware output, and -A 25 which sets the number of lines of output after finding the search term to 25(default 0, which wouldn't help here). "*-memory" is there because this is our search term.

Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

HTML version of info
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by Ozymandias_117 on 2011-06-25
Useful command line tools include:

lshw       (Everything from Ram to Motherboard to Processor... etc)
lspci      (PCI devices)
lsusb      (USB devices)
fdisk -l   (Hard Drives)
dmidecode  (Like the previous poster said)


You can pipe all the output either into less so you can scroll, or into a file for easy viewing.

command | less  (Scrolling in the terminal)
command > ~/filename  (Output to a file, overwriting the file)
command >> ~/filename (Output to a file, appending to the end)

---

### Post by gandaran on 2011-06-25
> **carmenat250 said:**
> I'm not sure what these programs are called at the moment, but on Windows, they are a dime a dozen.

These apps, when you run them will scan your computer and tell you everything that you need to know about the hardware...processor speed, how much ram, size of hard drive, etc.

Is there something similar for Ubuntu that I can use?
install 'sysinfo' from software center.

---

### Post by jmszr on 2011-06-25
carmenat250,

There also is "hardinfo" . When installed it can be found under Applications > System Tools > System Profiler and Benchmark .

---

