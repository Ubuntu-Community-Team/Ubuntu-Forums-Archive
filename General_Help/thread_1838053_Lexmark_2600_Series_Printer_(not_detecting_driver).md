---
title: "Lexmark 2600 Series Printer (not detecting driver)"
date: 2011-09-02
forum: General Help
---

### Post by johnsmoke on 2011-09-02
I tried to set up my printer tonight and I was hoping it would automatically detect the driver, but it did not. I followed the info in the Ubuntu 11.4 wiki and clicked the top right panel, selected "system settings" went to printers and clicked "add" and on the left side under devices "Lexmark 2600 Series." I click "forward" to try and have it detect the driver for it, but it's not finding it. Where do I go from here??

---

### Post by johnsmoke on 2011-09-02
I see that I can possibly choose a generic driver... but I need to know if this printer is PCL 4, 5 0r 6... I have no idea how to find that out. Did some google searches to no avail. Also, this printer is a printer/scanner combo, even if I found a generic driver that would work, would my scanner also be functional with this driver?

---

### Post by switch10 on 2011-09-02
I had that exact same printer about 2 years ago.  I gave it to a friend and upgraded to a Linux friendly H.P. because I never got it working.

---

### Post by johnsmoke on 2011-09-04
So there is NO way to install this printer in Ubuntu??? :(

---

### Post by dave01945 on 2011-09-04
have you tried to install this driver it says it is for 8.04 but i installed one for a different printer and it works fine 

[Lexmark Drivers]("support.lexmark.com/index?productCode=LEXMARK_X2600&page=driversdownloads&linkSelected=node2^subnode2&locale=EN&userlocale=EN_UK")

---

### Post by johnsmoke on 2011-09-04
> **dave01945 said:**
> have you tried to install this driver it says it is for 8.04 but i installed one for a different printer and it works fine 

[Lexmark Drivers]("http://support.lexmark.com/index?productCode=LEXMARK_X2600&page=driversdownloads&linkSelected=node2%5Esubnode2&locale=EN&userlocale=EN_UK")

Haven't tried that one. I have the All in one Lexmark 2600 series, I don't think mine is the X2600. I can try and install this, but do I run a risk of messing up my OS if this driver doesn't work, or is there any way to delete it if it doesn't? And when I use the filter option on the link you provided, there are several different drivers that come up, is it this one?:

 				**Printer Driver for Debian Package Manager based distros**

 			
 		 		  			**File Name:** 			 lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip 		
 		 		 			**Released** 			 05/04/2011 		
 		 			**Version:** 		  	 1.0.1 		
 		 			**File Size** 			 29.91 MB 		
 		 			     	 		**Download Estimate**

 	
 	 		 			Dialup 		
 		 			01:12:55 		
 		 			DSL 		
 		 			00:03:59 		
 		 			Cable 		
 		 			00:00:47 		
 		 			LAN 		
 		 			00:00:23 		
 	
 		
 		 			 				**Release Notes**

   			
   			 				This Linux driver for Debian Package Manager based distros for basic  USB print and scan which contains Lexmark Printer Toolbox that allows  users to perform maintenance operations on the device and check ink  levels of the cartridges.
**Installation Information**
IMPORTANT:  Follow these steps only if your driver is listed on the Linux  Compatibility Page. You can also check the Home or Small Office/Home  Office compatibility list for more information.
**A. RUNNING THE GUI INSTALLER SCRIPT IN THE TERMINAL**

[LIST=1]
[*] Open up your favorite terminal (xterm, konsole, gnome-terminal, etc)
[*] Extract the zip file
[*] Use the following command to install the driver 
   #./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
[*] Follow the instruction in the installation screen.
[/LIST]
**B. RUNNING THE GUI INSTALLER SCRIPT **
[LIST=1]
[*] Do not attach the printer via USB to the Linux machine.
[*]Extract the zip file.
lexmark-inkjet-[xx]-driver-[x.x.x].i386.deb.sh
[*]  Run the installer script file by double-clicking on the file icon and  then click the "Run in Terminal" button or run the script file via  command-line.
[*] Follow the instructions in the installer screen.
[/LIST]
 			
 		
 		 		 			 			 				**Operating Systems:** 			  	 Debian GNU/Linux 4.0, Debian GNU/Linux 5.0, Ubuntu 8.04 LTS 			
 				 				**Data Stream:** 				 Lexmark Host Based Solution 			
 			 				**Languages:** 				 English 			
 			 				**Products:** 				 Lexmark X2670, Lexmark X2695, Lexmark Z2300, Lexmark Z2320, Lexmark Z2390, Lexmark X2600, Lexmark X2620, Lexmark X2630, Lexmark X2650, Lexmark X2690 			
 		
 		 			<< Less Details

---

### Post by dave01945 on 2011-09-04
no it shouldn't mess up your os if it doesn't work it just wont be used and you should be able to remove it using synaptic as it is a deb file

---

### Post by Darren Sparrow on 2011-09-04
I have the same problem with a Dell all in one printer. As far as I can recall they're made by lexmark as well. Now Lexmark do have some drivers, but they may be a little out of date. It's worth trying them and seeing what happens. Dell may also be worth a try just in case for some weird reason they have an all in one printer that looks very similar to yours.

---

### Post by johnsmoke on 2011-09-04
I'll go ahead and give this driver a try. If it doesn't work and worse comes to worse, I will just give away this Lexmark to a friend and find a relatively inexpensive Linux-friendly printer/scanner combo that will work.

---

### Post by walt.smith1960 on 2011-09-05
> **johnsmoke said:**
> I'll go ahead and give this driver a try. If it doesn't work and worse comes to worse, I will just give away this Lexmark to a friend and find a relatively inexpensive Linux-friendly printer/scanner combo that will work.

I hope you're able to get your Lexmark to work.  If not, HP & Brother are quite Linux friendly, with HP often/usually being plug & play.

---

### Post by DanAlvares on 2011-09-06
I had a HP printer/scanner working pretty fine under the latest Ubuntu version, then its scanner stopped to work and my mom gave me this printer, Lexmark X2695.. OMG.. what a headache to have it working.. I got the drivers, installed it via console and all went fine. But I can't scan documents.. XSane gives me an error message. I must make this printer/scanner combo work.. I can't buy another one.
I'll try to report the message error later.
I need halpz!!!

---

### Post by johnsmoke on 2011-09-09
Hey, I downloaded the driver from the site. But I click on it and select "run in terminal" it brings up the installation, but when it asks me for my root/administrator password... I don't know what it is! I'm entering the password I use to get into the OS when the system boots up or when it's idle for a bit then asks for it... but that's not working... where do I find this root/administrator password??

---

### Post by dave01945 on 2011-09-10
if your user is an administrator you should be able to use your login password you should try running it from a terminal with sudo


```
sudo ./nameofinstallfile.sh
```

if that doesnt work let us know what error it gives

---

### Post by johnsmoke on 2011-09-10
> **dave01945 said:**
> if your user is an administrator you should be able to use your login password you should try running it from a terminal with sudo


```
sudo ./nameofinstallfile.sh
```if that doesnt work let us know what error it gives


Just tried it, I typed: sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh      Then it asked me for my password, I typed it, then the response was sudo: ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh: command not found

---

### Post by dave01945 on 2011-09-10
you also need to be in the directory where the file is stored

```
cd path/to/directory/
```

forgot to mention that before so if it is in the downloads folder you would type

```
cd Downloads/
```

i always find it's best to use <TAB> to complete the words as you know they are typed correctly

---

### Post by johnsmoke on 2011-09-10
> **dave01945 said:**
> you also need to be in the directory where the file is stored

```
cd path/to/directory/
```forgot to mention that before so if it is in the downloads folder you would type

```
cd Downloads/
```i always find it's best to use <TAB> to complete the words as you know they are typed correctly

YES!!! Thanks so much! I installed this driver and the printer works! Just printed out a test page! :)   Now I'm going to see if I can use the scanner.

---

### Post by johnsmoke on 2011-09-10
Printer works like a charm, but it has a built in scanner that Ubuntu doesn't seem to be recognizing. I tried to use Simple Scan and it says "failed to scan unable to connect to scanner".... don't know how to go about troubleshooting this. I'd appreciate any info.

---

### Post by dave01945 on 2011-09-10
sorry but i haven't had any experience setting up a scanner i think you need to lookup about the config files for SANE or it may be worth starting a new thread about setting up the scanner

---

### Post by johnsmoke on 2011-09-10
> **dave01945 said:**
> sorry but i haven't had any experience setting up a scanner i think you need to lookup about the config files for SANE or it may be worth starting a new thread about setting up the scanner


Ok, thanks for all your help with this. I'm glad I got my printer working.

---

### Post by dave01945 on 2011-09-10
thats ok also if you mark this thread as solved other people can learn from it

---

