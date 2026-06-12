---
title: "How do I install an emulator for the TI-83 Plus calculator?"
date: 2009-09-27
forum: General Help
---

### Post by ZER01NE1NE on 2009-09-27
Hello,

I'm sure this will seem blasphemous to long-time Linux users, but I need to know.

Why is it so darn difficult to install software on Linux? In order to install one program I have to install all of their dependencies, and install THEIR dependencies, and I have to compile from source (never mind that all this has to be done from the command line.) And when I hit a roadblock that I can't figure out how to get around, I just try a substitute, but then I run into the same missing dependency.

What's the deal? Why do I have to go on a wild goose chase looking for this package and that dependency, following this broken FTP link and reading that forum thread, just to install a program? I switched from Windows to Ubuntu because Windows crashes. But Windows was never this hard to use.

I'm a Linux noob. Please explain this to me, I need to know.

---

### Post by Bölvaður on 2009-09-27
no no no no.
If you are a normal user you will never have to compile or even touch the terminal, you might be blindly going by some how-tos written 5 years ago that is well outdated (everything older than 1 year old is outdated in our world.. alteast my milk is) and... oh look below.

Look at your top panel
Applications &#8594; Add/Remove
(look at the top of this application and change the drop box to show)
Show: All Available Applications

Again Look at your top panel
Applications &#8594; Administration &#8594; Synaptic Package Manager

Now google: *Ubuntu install software*
to learn more about how to install software in ubuntu, you can even install software from your browser... [just click this link to install a simple tetris-like game]("apt:crack-attack")

The reason you are asked to use command line is because it is easier (you dont have to understand anything, just copy and paste) and because no matter what distro you are using this will work.
But. You can do it any way you like, and there are GUI options for almost anything, it's just easier not to use it and it takes less text to explain commands than clicking there and there.

And no you aren't downloading programs that are dependencies for your program necesserly, it's all just packages, which can be anything.

---

### Post by LewRockwell on 2009-09-27
all other topics aside...

you've got to admire Iceland schooling New York!

.

---

### Post by ZER01NE1NE on 2009-09-27
I've been trying to install an emulator for the TI-83 Plus calculator, but it depends on GTK+. Trying to install that was a nightmare. Before I resorted to command-line installation, I looked in the Synaptic package manager for "gtk." There are a bazillion choices and I don't know which one does what. So I just followed the installation instructions that came with GTK+, which said to use the terminal.

---

### Post by lovinglinux on 2009-09-27
I agree with Bölvaður. Most of the time, installing applications in Ubuntu is a lot easier than Windows. 

Check the [Adding, Removing and Updating Applications](https://help.ubuntu.com/9.04/add-applications/C/index.html) documentation, which explains the installation methods available.

---

### Post by aysiu on 2009-09-27
Installing obscure (and that's what this is) software is definitely difficult in Linux. The rest of the software is really easy to install (just [use the repositories](http://www.psychocats.net/ubuntu/installingsoftware)).

Since Tilem needs to be compiled from source, this may help you:
[https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt)

---

### Post by Bölvaður on 2009-09-27
> **ZER01NE1NE said:**
> I've been trying to install an emulator for the TI-83 Plus calculator

I thought gtk2.0 which is basically gtk+ as the plush indicates it is more than just gtk, if my [SIZE="1"][COLOR="silver"](rapidly worsening)[/COLOR][/SIZE] memory isn't failing me ([SIZE="1"][COLOR="Silver"]which slowly is happening to it)[/COLOR][/SIZE].


> **aysiu said:**
> Installing obscure (and that's what this is) software is definitely difficult in Linux.
lol try it on windows, it's hell to install from source on it!

---

### Post by FunkyRes on 2009-09-27
Back when I did this, I was using Fedora.
I was able to find pre-packed emulator, the only difficult thing was extracting the ROM from my calculator (ROM is not free software).

I suspect some PPA has the software prepacked, you probably still need to get the ROM for your calculator.

---

### Post by shark1997 on 2009-09-27
[SIZE="4"]Step 1: Get rom8x (search for it on ticalc.org), and follow the instructions

Step 2: Use a windows computer to get the *.rom file
Step 3: Download TilEm ([http://www.ticalc.org/archives/files/fileinfo/355/35552.html](http://www.ticalc.org/archives/files/fileinfo/355/35552.html))
Step 4: Extract the file into a directory called TilEm in your home folder then compile the source and install the application

```
cd TilEm
make
sudo checkinstall
```


Step 5: Open up nautilus
Step 6: Press Ctrl-H
Step 7: Go to the directory called .TilEm in your home directory
Step 8: Go to the directory that matches your calculator model
Step 9: Place the *.rom file here

To run the emulator, open up the Terminal (Applications, Accessories, Terminal), type in
```
tilem
```
and press Enter[/SIZE]
:guitar:

---

### Post by ZER01NE1NE on 2009-09-27
OK, I got the emulator working. Thank you guys so much for your help and patience. The transition from Windows has been difficult for me. :)

---

### Post by Bölvaður on 2009-09-27
> **ZER01NE1NE said:**
> OK, I got the emulator working. Thank you guys so much for your help and patience. The transition from Windows has been difficult for me. :)

bet it was difficult to learn how to ride a bike also ;) :lolflag:

---

