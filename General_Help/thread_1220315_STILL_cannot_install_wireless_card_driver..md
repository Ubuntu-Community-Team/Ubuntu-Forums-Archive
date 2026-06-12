---
title: "STILL cannot install wireless card driver."
date: 2009-07-22
forum: General Help
---

### Post by -spy on 2009-07-22
I posted a thread a year ago, followed the instructions, could not get it to work.

Today I reinstalled ubuntu, followed my old thread verbatim.... did not work.

The ndiswrapper 1.55 I downloaded doesn't show the driver I need in the file. (netMW14x.inf)

My laptop: [http://support.gateway.com/s/Mobile/2007/Tempest/1014770R/1014770Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/Tempest/1014770R/1014770Rsp2.shtml)

The card is a marvell topdog

edit: version 8.04.1

old threads:

[http://ubuntuforums.org/showthread.php?t=906552](http://ubuntuforums.org/showthread.php?t=906552)
[http://ubuntuforums.org/showthread.php?t=575785](http://ubuntuforums.org/showthread.php?t=575785)

---

### Post by -spy on 2009-07-22
This is what I get folowing those instructions

 sudo ndiswrapper -i NetMW14x.inf
couldn't open NetMW14x.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by dk06 on 2009-07-22
Try Ndisgtk, (it gives you a GUI)
[http://packages.ubuntu.com/search?keywords=ndisgtk](http://packages.ubuntu.com/search?keywords=ndisgtk)

After install, it will be in your Apps
Just open it, click "New" & browse to your .inf

Very Easy

---

### Post by -spy on 2009-07-22
> **dk06 said:**
> Try Ndisgtk, (it gives you a GUI)
[http://packages.ubuntu.com/search?keywords=ndisgtk](http://packages.ubuntu.com/search?keywords=ndisgtk)

After install, it will be in your Apps
Just open it, click "New" & browse to your .inf

Very Easy

dont know how to do that :(

---

### Post by -spy on 2009-07-22
bump

easy step by step on how to install that for a complete noob?

---

### Post by dk06 on 2009-07-23
> **-spy said:**
> dont know how to do that :(
__________________________________________________________________________


Open your terminal and type:
> 
sudo apt-get install ndisgtk
enter your password and follow the instructions
__________________________________________________
Then:
Go to your computer manufacturers website & download the wireless driver specific to your mahine
After you get it, unzip it on your desktop
&
In your programs list, you will see "Windows Wireless Drivers" -Click it

Click "New" and browse to the driver folder on your desktop
inside you might see an XP folder and inside of that you will have a **.inf** file.......click it & say "OK"

-DONE-

---

### Post by -spy on 2009-07-23
> **dk06 said:**
> __________________________________________________________________________


Open your terminal and type:
enter your password and follow the instructions
__________________________________________________
Then:
Go to your computer manufacturers website & download the wireless driver specific to your mahine
After you get it, unzip it on your desktop
&
In your programs list, you will see "Windows Wireless Drivers" -Click it

Click "New" and browse to the driver folder on your desktop
inside you might see an XP folder and inside of that you will have a **.inf** file.......click it & say "OK"

-DONE-

Thanks, but what exactly do I install from that link? It's like a continuous loop for me, once I get to the mirrors, none of them work.

---

### Post by dk06 on 2009-07-23
> **-spy said:**
> Thanks, but what exactly do I install from that link? It's like a continuous loop for me, once I get to the mirrors, none of them work.

Ignore the link from the 1st post unless you want to manually download & install

In the 2nd post another option that I think will be easier, but you need open the command line terminal.....
[B]_STEP 1:_
Open your terminal 
[U]
STEP 2:[/U]
[/B]  	**In the terminal, type the following in red** (or copy & paste it in with your mouse)

 	 	 		 			 				[COLOR=Red]sudo apt-get install ndisgtk 			 		[/COLOR] 	 	 
_**STEP 3:**_
Press the **[enter]  **key on your keyboard
[B]
_STEP 4:_
Type your password & press [enter][/B]
(and answer any questions additional questions it may ask with [enter] )
---{ndisgtk will be installed after doing steps 1-4}---
[U][B]
STEP 5:[/B][/U]
 Go to your computer manufacturers website &** download the wireless driver specific to your mahine**

 After you get it, **unzip it on your desktop**
---{now you should have the wifi driver}---  

_**STEP 6:**_
 In your programs list, you will see [B]"Windows Wireless Drivers" -Click it

[/B]_**STEP 7:**_
*(may not be exact, but I'm sure you can browse to the .inf file inside your driver folder)*
**Click "New" **and **browse to the driver folder** on your desktop
 inside you might see an XP folder and inside of that you will have a** .inf **file**.**......**select it **
&
 say **"OK"**
_______________DONE_______________

---

### Post by -spy on 2009-07-24
Thanks, Gateways driver downloads are .exe's will the .inf be in them? And it's only under Vista, not XP.

---

### Post by gradinaruvasile on 2009-07-24
Try opening them with archive manager. Usually they are self extracting archives.

---

### Post by -spy on 2009-07-24
Windows wirless drives in programs says Invalid driver..

also..

name-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
name-laptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
Driver 'netmw14x' is already used for '11AB:2A08'
name-laptop:~$ sudo ndiswrapper -l
netmw14x : invalid driver!
Name-laptop:~$ 

ugh

---

### Post by -spy on 2009-07-25
update: Still cant connect, but it says the driver is installed..? what

name-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
name-laptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
WARNING: Driver 'netmw14x' will be used for '11AB:2A08'
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08
name-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

name-laptop:~$ sudo depmod -a
name-laptop:~$ sudo modprobe ndiswrapper
name-laptop:~$ sudo ndiswrapper -l
netmw14x : driver installed
	device (11AB:2A08 ) present
name-laptop:~$



--
Also in "windows wireless network drivers" installed NetMW14x, but it says "Hardware present: No".

---

### Post by -spy on 2009-07-25
bump

---

### Post by -spy on 2009-07-27
:(

---

### Post by -spy on 2009-08-02
this is 8.04.1 if that makes any difference

---

### Post by dk06 on 2009-08-19
**[COLOR=Red]sudo apt-get install ndisgtk[/COLOR]**

it works through the GUI, you don't  need to mess with the command line, just make sure your wireless card is in then add the ***whatever***[COLOR=Red]**.inf **[/COLOR][COLOR=Black]from the driver .exe package you downloaded.

Make sure you downloaded the correct driver (you want the wifi driver, not bluetooth/etc...)

_**Ndisgtk** will be under your programs _and is called*[COLOR=Red] "Windows Wireless Drivers"[/COLOR]*

Ndiswrapper is the command line non-GUI driver tool
[/COLOR]

---

### Post by Commander_Keen on 2009-08-19
Thank you very much for these instruction.
It will help me out very much.

---

