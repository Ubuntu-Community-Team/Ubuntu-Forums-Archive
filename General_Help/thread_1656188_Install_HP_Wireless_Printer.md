---
title: "Install HP Wireless Printer"
date: 2010-12-30
forum: General Help
---

### Post by leona on 2010-12-30
Hello, hope you can help me (again!)
I have just bought a new printer.
A HP Photosmart Pro (B210).
I want to connect this to my computer, 
I would like to use the wireless option if possible.
I have set the printer up and it connects to my router fine, it even did a software update! :)

But I am unable to get my Ubuntu 10.04 system to see it.

I have plugged it into my computer via the USB at the moment, and Ubuntu has located and installed it.  But Xsane will not find the scanner and I'd
like to use all the HP Features in the HP LIP Toolbox, ink levels, etc.

I have the HP LIP Toolbox installed.
I try both wireless options, but it is not found.
I tried this in terminal
```
hp-check
```
and get
```
error: 10 errors and/or warnings.
```
of them one was.
```
error: Unsupported model: Photosmart_Plus_B210_series
```

Does anyone know how to get this printer working with Linux?
I had a HP Photosmart previously, a C5180 which worked a treat, so I 'assumed' this one would too.  



Thank you.

---

### Post by leona on 2010-12-31
Found some answers [here]("http://www.linuxformat.com/forums/viewtopic.php?p=95865") so installing that, see how things get on.

Seems the version of HPLIP is out of date, so we need the new one, 3.10.9.

Step 1 Download  hplip-3.10.9.run, from ([http://sourceforge.net/projects/hplip/files/hplip/]("http://sourceforge.net/projects/hplip/files/hplip/"))
Step 2 navigate to saved location and resolve dependencies by 
```
apt-get build-dep hplip
```
Step 3 made the file executable 
```
chmod a+x hplip-3.10.9.run
```
Step 4 Run it 
```
./hplip-3.10.9.run
```
Follow the prompts, it should all install fine.
It doesn't however seem to place an icon in the Preferences menu, but you can do that yourself.
Edit the menu, go to preferences, make a new item, the command is 
```
/usr/bin/hp-toolbox
```
But I was unable to find the correct icon for it.
This all worked perfectly for me.
I have a HP Photosmart Plus B210 on a wireless network,  Works flawlessly now. 
Hope this helps others.

---

### Post by dacoolio on 2011-01-06
Hi,

Just wanted to thank you for posting the steps! I just purchased one of these and you saved me a lot of time :D

---

### Post by mefarmerdan on 2011-03-28
@leona

Thank you for posting your solution.  I used the directions today to configure an HP-Photosmart-d110 series printer.  The only modification I had to make to your "howto" was that I needed the current version of hplip which is now hplip-3.11.3.

[Observation]Ubuntu is way behind on hplip updates.[/Observation]

Thanks again.

Dan

---

### Post by leona on 2011-03-28
You are welcome, glad it was useful, yes the version I used was 'the latest at the time', as you quite rightly say, Ubuntu doesn't seem to includes these updates, I don't know why that is.

---

### Post by Nevparker on 2011-03-29
Hi, I hope  you all can help.  Leona, your how to looks like something I should do, but I managed to install the most recent HPLip and was able to follow the process to the following point.

add device...chose the wireless/W108g option.  connected USB as directed.  Clicked next, printer located clicked next (was hoping for the confirmation of wirless network etc) got a pop up saying there was an I/O error with the USB connection.

I know the USB printer cable works as it worked fine with another printer.

Any suggestions?

Thanks

---

### Post by leona on 2011-03-30
If you open a terminal then type > hp-check what is the output.
If its like mine, ie "Unsupported Device" you will need to download the latest HPLip.
If this doesn't solve it, then I don't think I can help, its either a device fault (can you try it on a Windoz box?) or a system config problem, which you would be better off starting a new thread on, as this one is marked Solved, so people will not view it.
If you start a new thread, remember to list out as much infomation as possible, your system, OS and version, installed version of HPLip, your printer make and model and what steps you have alread taken.
Good luck

---

### Post by griztown on 2011-04-09
I'm trying to follow these steps but I keep seeing this error message when running the hplip script:

CHECKING FOR NETWORK CONNECTION
-------------------------------
error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.


Any ideas?  The network is definitely up as I'm posting this now.

---

### Post by griztown on 2011-04-09
> **griztown said:**
> I'm trying to follow these steps but I keep seeing this error message when running the hplip script:

CHECKING FOR NETWORK CONNECTION
-------------------------------
error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.


Any ideas?  The network is definitely up as I'm posting this now.
I changed directory into the hplip directory and ran './install.py -n' and now it's running.  Weird

---

### Post by leona on 2011-04-10
Well I am glad its working,as you say most odd.  I had not come across that issue, the only thing I was going to suggest was checking your router to see if the device appeared in the 'attached devices' section to ensure everything was ok, ensuring you had a steady blue light (under the power button) which denotes a network connection.

---

### Post by sailorboy on 2011-04-27
This forum has been good 2 me so here is MY experience with the HP Photo-smart B210e on Ubuntu 10.04, the printer worked -but not the scanner.
 Somewhat 'noob' but found that 10.04 has the 'dated' hplip 3.10.2 package, the current (2 this date) is actually 3.11.3a- available here :
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

-the above instructions gave me trouble, knowing the terminal opens to the desktop folder, I copied the downloaded file from the (default) 'download' folder to the desktop folder. However, simply selecting 'open' didn't work (or terminal command- said 'unable to open'). Instead, I (right clicked)-selected 'open with other program', selected 'custom command') and typed:  sh , then <enter>.
 It will open in terminal- follow instructions! It asks you to 'disable' optic drive(s) B4 install, so I shut down and simply unplugged them. Rebooted (hit enter to bypass <no cd drive note> and repeated the above, then the 'magic' worked!
 After restart, go to terminal and type: hp-setup , then <enter> to finish it (I was using USB so didn't need wireless option).
 In retrospect, unsure if moving file was needed or if I did it properly- but scanner DOES work correctly- no apparent issues.
 Also, there's a utility (hp-dbg), one can install (from synaptic) and run in terminal to troubleshoot with- but rather 'cryptic' for the average PC user.
Google helps, it led me here- hope this helps someone else!

---

