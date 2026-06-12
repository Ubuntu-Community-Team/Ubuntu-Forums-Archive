---
title: "Need help with Bios"
date: 2010-10-13
forum: General Help
---

### Post by MaxTesla on 2010-10-13
Hello


Ubuntu will not install on or work as run live cd on my computer


I am quite certain it is the BIOS that are somehow messing it up


I have a fujitsu siemens ESPRIMO P1500


If I go to the fujitsu siemens home page click help and support, then click download drivers, then enter the name of my computer, choose windows 7 64 bit and then click bios I get a list of Bios and on of them the top one is called Linux Bios 6 – 1.05
 
[http://www.fujitsu.com/global/](http://www.fujitsu.com/global/)


Now IF I were to install this bios would unbutu work and would I still be able to use my windows


OR


will the windows bios be replaced?


And how exactly in the most exact way do I install these Bios?


I know very little about computers

---

### Post by sendblink23 on 2010-10-13
> **MaxTesla said:**
> Hello


Ubuntu will not install on or work as run live cd on my computer


I am quite certain it is the BIOS that are somehow messing it up


I have a fujitsu siemens ESPRIMO P1500


If I go to the fujitsu siemens home page click help and support, then click download drivers, then enter the name of my computer, choose windows 7 64 bit and then click bios I get a list of Bios and on of them the top one is called Linux Bios 6 &#8211; 1.05
 
[http://www.fujitsu.com/global/](http://www.fujitsu.com/global/)


Now IF I were to install this bios would unbutu work and would I still be able to use my windows


OR


will the windows bios be replaced?


And how exactly in the most exact way do I install these Bios?


I know very little about computers

I'm assuming here ... but I think the different OS thing about the Bios... its so that you can install the updated Bios through linux or installing it through Windows.

Ofcourse I'm just assuming here, I've seen the same thing on another laptops


Eitehrway can you tell me how to search your computer on the "http://www.fmworld.net/globalpc/download/index.html" page I couldn't find it(I'm probably selecting the wrong things)... I just want to check those files to see what is the difference

---

### Post by MaxTesla on 2010-10-13
What??

I dont have a laptop

And most of what you wrote makes no sense to me

---

### Post by sendblink23 on 2010-10-13
> **MaxTesla said:**
> What??

I dont have a laptop

And most of what you wrote makes no sense to me

I meant - As in giving you the options of installing the updated Bios from within Linux or through within Windows

I mentioned laptop because, I've seen it before for a laptop(I'm not saying you have a laptop) - My bad *actually just reading what I wrote, it does sound like I wrote you had a laptop, sorry

Like i asked before, help me out on searching your computer on that website.. I want to see the bios updates they offer you - so that i can check the files and see if there is any difference between the Linux Bios & the Windows bios files.

---

### Post by PaulReaver on 2010-10-13
Yeah but fujitsu's don't come with ubuntu

fujitsu only sell openSuse and SLED computers. 
I wouldn't update the bios on ubuntu if I had the option of doing it on windows,  

there are quite big underlying differences between buntu and suse

---

### Post by WeAreLinux on 2010-10-13
> **MaxTesla said:**
> Hello


Ubuntu will not install on or work as run live cd on my computer


I am quite certain it is the BIOS that are somehow messing it up


What exactly happens? Error messages? Are you able to boot from the CD?

---

### Post by MaxTesla on 2010-10-13
First of all I do not have any linux installed on my computer
 

 Secondly there is no linux installed on my computer
 

 Thirdly I only have windows installed on my computer
 

 What happens when I try to &#8220;try ubuntu without installation&#8221; is that I get a blinking white line in the upper left corner and then the screen goes black and then the screen shuts itself off
 

 I have searched the net and many others with the same computer have the same problems


[sendblink23]("http://ubuntuforums.org/member.php?u=639398") -----------------> [http://www.fmworld.net/globalpc/download/index.html](http://www.fmworld.net/globalpc/download/index.html) ----------------> Europe----------------> Enter name or serial----------> ESPRIMO P1500------------> windows 7 64 bit---------------Bios
 

 NOW
 

 what I want answered is, IF I install the bios that I mentioned above will they overwrite my bios and make it not possible for me to use my windows or will it just be an extra allowing me to use both windows and linux OR should I not do it at all because the preinstalled version was windows 7
 

 And how exactly do you update bios in the most exact way

---

### Post by sendblink23 on 2010-10-13
well since you are ignoring the simple question I asked I won't help you out(I haven't talked about anything you having windows or you having linux - but you are surely asking in a forum about linux)

I just simply want to verify both of the Bios files (the one for Windows & the one for Linux) to see if the actual "bios file" if they are any different or exactly the same.

Usually updating the bios works for everything, it won't kill the usage of another operating system.. only issue that can happen is kill/render your motherboard - in which only happens if you flash the wrong bios(A Bios that isn't for your motherboard)

Since you said you are using windows, then simply update the Bios using the *Windows file/method they offer to update the bios (maybe that can probably make Ubuntu work or maybe it won't change anything)

Also by any chance have you tried any other Linux Distros... or older Ubuntu versions?

************UPDATE
Sorry I just noticed you included what I asked... hold on a bit

Okay checked it, and yes they are both the same - do the USB Flash Drive method of updating the Bios through Windows
According to teh instructions, the .exe they provide it will automatically install the necessary files to make it bootable to install the bios update... so run it... then just reboot the computer & boot from usb and follow the on screen instructions

> Downloaded image contains a self-extracting USB stick image file (*.exe). 
To create a bootable USB memory stick please:
- connect a spare USB stick (backup all data on your USB stick now, since the memory stick data will be overwritten)
- execute the downloaded *.exe file
- select connected USB stick (if not already pre-selected) and start "Copy Image File To USB Device"
- safely dismount and disconnect the USB stick
To start update of your target system, please:
- power on the system and enter the boot menu with F12 key
- select the USB device that contains the BIOS files
- press `Enter` to boot from the stick
- follow the displayed instructions

---

### Post by MaxTesla on 2010-10-13
I wrote above

[sendblink23]("http://ubuntuforums.org/member.php?u=639398") -----------------> [http://www.fmworld.net/globalpc/download/index.html](http://www.fmworld.net/globalpc/download/index.html)  ----------------> Europe----------------> Enter name or  serial----------> ESPRIMO P1500------------> windows 7 64  bit---------------Bios

What is " USB Flash Drive method"

By USB do you mean a USB stick, and i dont have one

Can you be more specific like where to click exactly which option and how to click in what order

---

### Post by AggravatedGestalt on 2010-10-13
Have you entered the BIOS and set it to boot from CD? And if you have a SATA hard drive, you might need to enable compatibility-mode on the hard drive settings for installation (if you choose to install), but maybe not.

I just installed Ubuntu on my friend's 10year old HP computer (and HP really su*ks!), and everything worked fine with a little BIOS tweaking. And I first booted the live CD before installing.

---

### Post by MaxTesla on 2010-10-13
I have not entered Bios to boot from CD I have no idea how to do that

And as mentioned above live cd will not work on my computer, all I get is a white line blinking in the top left corner, then the screen goes black, then the monitor shuts off and it has been the same with older version of ubuntu as well, 10.04 and 9.10

---

### Post by cascade9 on 2010-10-13
Hmmm...bit of a misunderstanding here I guess. 

BIOS = "basic input/output system". There isnt a windows BIOS and a linux BIOS, they both use the same BIOS. 

"Linux Bios 6 &#8211; 1.05" doesnt mean its a BIOS for linux, if you click on that link then you get this information- 

> Installation description:                                                                                                                                           The BIOS Update File is a .sh file (Shell Script), which enables you to create
a bootable disk to update the BIOS.[http://support.ts.fujitsu.com/Download/ShowDescription.asp?SoftwareGUID=2EEEF5FD-1375-4B25-B86C-B92768617FFE&OSID=B3514DE7-EBF1-45C7-9D91-9C491FE892B7&Status=False&Component=Flash%20Bios%20for%20D2950-A1x]("http://support.ts.fujitsu.com/Download/ShowDescription.asp?SoftwareGUID=2EEEF5FD-1375-4B25-B86C-B92768617FFE&OSID=B3514DE7-EBF1-45C7-9D91-9C491FE892B7&Status=False&Component=Flash%20Bios%20for%20D2950-A1x")

The different BIOS versions are for different ways of updating the BIOS (eg from a floppy boot disc, a USB stick, from inside windows, etc.). The actual BIOS version is the same, no matter which method you use to update the BIOS (1.05, 02.10.2009, 1.04, 11.09.2009, 1.03, 20.08.2009). 

BTW, I dont think its your BIOS that is causing problems. You can update it if you want, but I think that this is more likely the cause- 

> Machine: Fujitsu Esprimo P1500 

The installer requires the 'noapic' option, otherwise it freezes at the 
'Select a language' step. Booting also requires 'noapic'. [http://help.lockergnome.com/linux/Bug-586854-Installation-Fujitsu-Esprimo-P1500-requires-noapi--ftopict522117.html](http://help.lockergnome.com/linux/Bug-586854-Installation-Fujitsu-Esprimo-P1500-requires-noapi--ftopict522117.html)

I'd try the 'noacpi' and 'acpi=off' options. More information on how to do that here- 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by MaxTesla on 2010-10-13
I checked the Bios with a program called cpuz and apparently I have the newest ones
 

 I tried doing the live cd and select “noapic” and it worked with live cd, I have not installed anything 

 

 So what does apic do, what is it purpose?

---

### Post by cascade9 on 2010-10-13
ACPI = Advanced Configuration and Power Interface. 

Its meant to replace Advanced Power Mangement, Play and play BIOS and a few other bits and pieces.

---

### Post by MaxTesla on 2010-10-13
What will happen if I install Ubuntu with "noapic" what am I not installing and will Ubuntu work normally and what exactly will happen?

---

### Post by cascade9 on 2010-10-13
All the 'noacpi' option does is make ubuntu not pay any attention to acpi. Ubuntu should work normally. ;)

*edit- Right, thats what I get for confusing acronyms. Damned dsylexia :( 

ACPI = Advanced Configuration and Power Interface

APIC = Advanced Programmable Interrupt Controllers

Its "noapic", not "noacpi". 

APIC is a more advanced form of PIC (Programmable Interrupt Controllers), and basicly its about IRQs (Interrupt Request). 

Still ubuntu should run normally with the "noapic" option.

---

### Post by MaxTesla on 2010-10-13
I installed Ubuntu 10.10 with the noapic options, but now when I select Ubuntu to start it, I believe does not choose "noapic"

It goes back to its old way of blinking a white line in the upper left corner

So How do I make an installed 64bit version of Ubuntu 10.10 start up with "noapic"

---

### Post by MaxTesla on 2010-10-13
I found it

When the computer starts you use the arrow keys to select ubuntu then  you press E and use the arrow keys again to go behind the words quiet  splash and press space bar and then type in noapic and then press ctrlx

---

### Post by cascade9 on 2010-10-13
Heh, that saved me searching, I havent had to use noapic for a long time and then it was only once ;)

---

