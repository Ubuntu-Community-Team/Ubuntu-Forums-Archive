---
title: "I'm getting really frustrated here!!!"
date: 2011-06-01
forum: General Help
---

### Post by KidneyBean on 2011-06-01
I need some serious assistance yet nobody seems to be offering any. My laptop keeps shutting down out of nowhere- now more so than ever since installing Ubuntu.

After starting a thread in the hardware and laptop section asking anyone if they had a solution to a well known fan problem with the Acer Aspire 5315 (my laptop), the only responses I received were rubbish in nature. Simply put, the Acer Aspire 5315 has a faulty fan which runs only when it wants to- not when the computer NEEDS it to. 

I found THIS solution to my problem: [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521). As suspected, this isn't a BIOS thing as some have told me that it was. But here's the REAL crappy part- the solution posted in this thread works up until you're about to install the fix via the terminal. The commands spit back at me that "No such file or directory exists". THUS, I'm unable to get this thing working.

I need someone to explain to me why the terminal is spitting out the garbage that it is- that no such file or directory exists when attempting to install and launch the fix for this fan issue. Please be as detailed as possible. What? Should I move the script to some sub-directory? If so, how does this input into the terminal? Please explain. 

This is my only machine. Like most of America, I'm broke and I can't afford a new laptop. Will somebody PLEASE, FINALLY help me? 

I sort of feel like I'm standing in Time Square shouting at the top of my lungs as everyone walks on by ignoring.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Honestly, I understand your frustration. The most important thing though is to make sure your system doesn't overheat for now.  Go into BIOS and switch the fan to "always" be running.  That way you don't fry your system, until we can provide you with a solution.  Don't leave it up to Ubuntu to decide when the fan should be on until the problem is resolved. :) 

In the meantime, since I have no knowledge of Acer's and Ubuntu 11.04. 

Have you tried burning a stick of an early version of Ubuntu, and booting from that to see the issue is resolved by rolling back to an early version with the live USB stick of Ubuntu?  I don't know if it is a 11.04 bug or what at this point. But it is worth a try.

---

### Post by cgroza on 2011-06-01
Ok, I think I know the reason of your "No file or directory".
The tutorial never tells you to cd to the extracted folder.
Use these updated commands:
```

1) Download the script
2) Unpack the script
tar xvfz acer_fancontrol.tar.gz 
###Cd to the extracted folder

cd acer_fancontrol

3) Pick the memory size which matches your memory size(it doesn't matter if the model isn't the same). 
vim acer_fancontrol   
You can use other text editors too.
4) Install the script
  sudo cp acer_fancontrol /usr/bin 
  sudo cp mempat /usr/bin
5) Make it run automatically
  sudo gedit /etc/rc.local
  Insert "acer_fancontrol" before the final "exit 0"
```

---

### Post by KidneyBean on 2011-06-01
Alright, so the problem really is that I'm a noob with the ubuntu terminal (which I'm catching on to). 

I need you, if you could, to provide me with the exact code to punch in. The file is i:n home/grant/Downloads/acer_fancontrol/

Could you tell me possibly what I should punch in to the terminal exactly?

---

### Post by KidneyBean on 2011-06-01
There's a little typo.. the directory where the file is: home/grant/Downloads/acer_fancontrol/

---

### Post by doas777 on 2011-06-01
> **KidneyBean said:**
> I need some serious assistance yet nobody  seems to be offering any. My laptop keeps shutting down out of nowhere-  now more so than ever since installing Ubuntu.

After starting a thread in the hardware and laptop section asking anyone  if they had a solution to a well known fan problem with the Acer Aspire  5315 (my laptop), the only responses I received were rubbish in nature.  Simply put, the Acer Aspire 5315 has a faulty fan which runs only when  it wants to- not when the computer NEEDS it to. 

I found THIS solution to my problem: [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521).  As suspected, this isn't a BIOS thing as some have told me that it was.  But here's the REAL crappy part- the solution posted in this thread  works up until you're about to install the fix via the terminal. The  commands spit back at me that "No such file or directory exists". THUS,  I'm unable to get this thing working.

I need someone to explain to me why the terminal is spitting out the  garbage that it is- that no such file or directory exists when  attempting to install and launch the fix for this fan issue. Please be  as detailed as possible. What? Should I move the script to some  sub-directory? If so, how does this input into the terminal? Please  explain. 

This is my only machine. Like most of America, I'm broke and I can't  afford a new laptop. Will somebody PLEASE, FINALLY help me? 

I sort of feel like I'm standing in Time Square shouting at the top of my lungs as everyone walks on by ignoring.


1) hardware problems, especially those that deal with power management  are some of the hardest things to troubleshoot in linux. I have years of  experience, and I likely would NOT have tried that fix. it is very very  likely that no one, alive or dead, knows why your fan is acting up, or  what to do about it. My HP won't kick up the fan until after its above  70C. HP tells me that there will never be anything I can do about it, as  they will not ever give me an unlocked bios.

2) your problem IS your bios, as is clearly evident from looking at the script you tried to run
> 
# ***************************************************************************
# Principle of Operation
# ***************************************************************************
# On the Acer 5720, the ACPI Embedded Controller controls the CPU fan.
#
# Communication between the Operating System and the ACPI Embedded Controller is
# documented in the the Differentiated System Description Table (DSDT).
#
# The DSDT is provided as part of of the BIOS. It is written in ACPI Source
# Language (ASL) and compiled to ACPI Machine language (AML), intructions for a
# bytecode interpreter that is part of the Operating System.
#
# The DSDT is accessible on Linux as /proc/acpi/dsdt; 'cat' it somewhere to
# look at it.
#
# The Intel ASL compiler (iasl) compiles ASL to AML, and decompiles AML (eg. as
# saved from /proc/acpi/dsdt) back to ASL.
#DSDT is part of the BIOS. linux just allows you to manipulate it in a way windows tries to hide from you.

3) a friend of mine once told me that I should never argue with a Crazy  person, because to somone passing by, we'd both look crazy. you seem to  be arguing with a crazy person, but the other party isn't even here. 

4) to run your script, download the tar.gz file to Downloads.
then open a terminal, and enter these commands:
```
cd Downloads
tar -xvf acer_fancontrol.tar.gz
cd acer_fancontrol
gedit acer_fancontrol

<EDIT the file to set your max mem size as Dushmi94 instructed, save the file and exit gedit>

sudo chmod +x ./acer_fancontrol
sudo cp ./* /usr/bin

gksu gedit /etc/rc.local

<Edit the file to add 'acer_fancontrol' (without quotes) above teh line that says 'Exit 0'. Save and close>

sudo reboot

```thats as easy as anyone can make somthing as complicated as updating your bios image at boot.

---

### Post by KidneyBean on 2011-06-01
Forget that.. Figured it out. My noobish skills, me hopes, are fading.

---

### Post by cgroza on 2011-06-01
Is it fixed?

---

