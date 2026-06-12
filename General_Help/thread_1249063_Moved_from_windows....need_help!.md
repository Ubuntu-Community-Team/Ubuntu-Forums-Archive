---
title: "Moved from windows....need help!"
date: 2009-08-24
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2009-08-24
Hi, I've just moved over to Linux Ubuntu (9.04 I think...Jumpy J something...). I've been using Windows since I started using computers, and Vista finally saw me search for an alternative. 

Just a few quick questions, if someone can help me that would be great :D.

1. I have this beep noise when I get to the end of a list or try to type when I'm not on the page, its annoying, it doesn't go off when the sound is off...please help!

2. I'm trying to install the fonts Times New Roman, and Arial, into openoffice (thats right, FREE office :O) but wiki says I need to open the directory and type something in....wtf is the directory and how do I access it?

3. I'vre downloaded a driver package for my HP printer (K5300) (.run file) but I don't know what program I use to open/install it. It opens in something called archive manager by default, but doesn't do anything. Please can you tell me what the install program is or how to install programs.

I'll probably have loads more questions soon, but I'm going to try playing around with stuff to learn it all. Sorry if these seem like idiotic questions, but I really don't want to use Windows anymore, so i want to try and learn linux asap.

---

### Post by oldos2er on 2009-08-24
Regarding your HP printer, check System, Administration, Printing to see if you can enable it from there.

 For fonts, easiest way is to install them with Synaptic Package Manager, or Add/Remove.

---

### Post by uylug on 2009-08-24
> **Dalek Draco ON LINUX said:**
> Hi, I've just moved over to Linux Ubuntu (9.04 I think...Jumpy J something...). I've been using Windows since I started using computers, and Vista finally saw me search for an alternative. 

Just a few quick questions, if someone can help me that would be great :D.

1. I have this beep noise when I get to the end of a list or try to type when I'm not on the page, its annoying, it doesn't go off when the sound is off...please help!

2. I'm trying to install the fonts Times New Roman, and Arial, into openoffice (thats right, FREE office :O) but wiki says I need to open the directory and type something in....wtf is the directory and how do I access it?

3. I'vre downloaded a driver package for my HP printer (K5300) (.run file) but I don't know what program I use to open/install it. It opens in something called archive manager by default, but doesn't do anything. Please can you tell me what the install program is or how to install programs.

I'll probably have loads more questions soon, but I'm going to try playing around with stuff to learn it all. Sorry if these seem like idiotic questions, but I really don't want to use Windows anymore, so i want to try and learn linux asap.

2. I can't remember exactly how to install fonts. I remember myself putting them under /usr/share and some subfolder.

3. I don't think you will need any drivers at all. Go into System -> Administration -> Printing and Click on New and add a new printer. If it does not work, then do this:

Copy the .run file you just downloaded to your home folder and then run
```
sudo bash *name_of_your_run_file.run*
```

---

### Post by tubasoldier on 2009-08-24
Fonts:
Applications --> utilities --> terminal

sudo apt-get install msttcorefonts ; sudo fc-cache -fv

it will ask for your password.



Your printer should be found and installed by default. It uses the hplip driver already available in Ubuntu. I'm not running ubuntu but there is a printer setup. I believe it is under the administration menu.

---

### Post by Dalek Draco ON LINUX on 2009-08-24
Thanks for the quick replies, I've got the printer up and runnning (I think), it just needed to be plugged in (don't blame me, I'm used to windows golden rule: don't plug it in until you've installed the drivers).  I found a folder called fonts under user>share I guess I'll try finding a times new roman font and pasting it in there?  Another question thats sprang to mind, we have a wireless network at uni, and connect through a VPN client. But when I go to add VPN under network connections, it doesnt allow me to add one...

---

### Post by tubasoldier on 2009-08-24
the easiest way to install the fonts is to open the terminal and type in the following:

```
sudo apt-get install msttcorefonts ; sudo fc-cache -fv
```

I understand this is much different than the windows world. From our perspective it is easy to give you something to copy/paste for a quick fix as opposed to saying click here, then here, then click here. now here. The command line seems to be very overwhelming for some but coming from an old OS/2 user I would think you have some sort of old DOS command line ability. Sometimes it is just easier for us to type in a few commands. YOu will need to have the Universe repository enabled, I think it is by default but i'm not using ubuntu currently so I can't tell you for sure.

---

### Post by uylug on 2009-08-24
> **Dalek Draco ON LINUX said:**
> Thanks for the quick replies, I've got the printer up and runnning (I think), it just needed to be plugged in (don't blame me, I'm used to windows golden rule: don't plug it in until you've installed the drivers).  I found a folder called fonts under user>share I guess I'll try finding a times new roman font and pasting it in there?  Another question thats sprang to mind, we have a wireless network at uni, and connect through a VPN client. But when I go to add VPN under network connections, it doesnt allow me to add one...

Oh lol, i used to paste fonts in here where i was a complete n00b, and it worked...

```
/usr/share/fonts/truetype/openoffice
```The right thing is to put them under truetype and running a certain command that configures fonts or something.

Edit: the command is (posted by the user above me) : 
 sudo fc-cache -fv 
I haven't myself configured a VPN, sorry, can't help.

---

### Post by Dalek Draco ON LINUX on 2009-08-24
I've got the fonts installed :D. Thank you all for your replies.  Its all a lot different from windows, but I'll get used to it lol.  I found the terminal as well, it was hiding in applications>accessories. I was looking under system assuming that it would be hidden like windows does. Go linux :D

---

### Post by cascade9 on 2009-08-24
> **Dalek Draco ON LINUX said:**
> 1. I have this beep noise when I get to the end of a list or try to type when I'm not on the page, its annoying, it doesn't go off when the sound is off...please help!


I hate those beeps. Its from your onboard speaker, the one that goes 'beep' when you boot your computer. I normally just disconnect the speaker, but you may not want to do that (if its even possible, some of them are hardmounted to your motherboard). 

I have not tested this, so I'm not sure it works. But if you want to try, go to the terminal, and type 

setterm -blength 0

---

### Post by Dalek Draco ON LINUX on 2009-08-24
> **cascade9 said:**
> I hate those beeps. Its from your onboard speaker, the one that goes 'beep' when you boot your computer. I normally just disconnect the speaker, but you may not want to do that (if its even possible, some of them are hardmounted to your motherboard). 

I have not tested this, so I'm not sure it works. But if you want to try, go to the terminal, and type 

setterm -blength 0

 :( didn't work. Still beeps. Does it when you search for a word on a page, and the word isn't there too. Really annoying.

---

### Post by jesuisbenjamin on 2009-08-24
**Question 1.** Go to System > Preference > Sound
Chose the second tab entitled 'Sounds' and uncheck the 'Play alert sound' box. The very annoying bip should never come back again.

**Question 2.** You may want to bookmark this document [https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d](https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d)
You can install fonts manually or with command lines, it's up to you and how you like to work with computers.

---

### Post by tubasoldier on 2009-08-24
> **Dalek Draco ON LINUX said:**
> :( didn't work. Still beeps. Does it when you search for a word on a page, and the word isn't there too. Really annoying.

Here is a thread that may work for your system beep issue. I'm not sure why they just don't do this by default. The system beep is the most ridiculously old technology which should just be banned the world over.

[http://ubuntuforums.org/showthread.php?t=531781](http://ubuntuforums.org/showthread.php?t=531781)

---

### Post by Gen2ly on 2009-08-24
> **uylug said:**
> Oh lol, i used to paste fonts in here where i was a complete n00b, and it worked...

Yeah, done that too :)

Best to install with the package manager though as tubasoldier suggested. (btw I dont' think updated the font cache is necessary I think the package is already set up to do that).  Fonts that aren't available with a package manager can be put in ~/.fonts.  ~/.fonts means your home folder in a hidden directory call .fonts.

As for disabling the pcspkr, I've heard that:

```
setterm -blength 0
```

Can cause problems.  In Ubuntu you should be able to unload the pcspkr module:

```
sudo rmmod pcspkr
```

I don't know enough about Ubuntu to know how to do this at boot though.

---

### Post by Dalek Draco ON LINUX on 2009-08-24
> **jesuisbenjamin said:**
> **Question 1.** Go to System > Preference > Sound
Chose the second tab entitled 'Sounds' and uncheck the 'Play alert sound' box. The very annoying bip should never come back again.

**Question 2.** You may want to bookmark this document [https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d](https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d)
You can install fonts manually or with command lines, it's up to you and how you like to work with computers.
 
It worked :D!!! Thank you so much. The beeping seems to have ceased   Just to be a real pain in the ****, one last question, Ive got a logitech quickcam (Communicate STX) and I can't seem to get it working, haven't been able to find any installation drivers or anything online, and of course the disc is windows only.

---

### Post by tubasoldier on 2009-08-24
This may help with your webcam problem. I don't have one to work with so I have never used them.

[http://help.ubuntu.com/community/Webcam](http://help.ubuntu.com/community/Webcam)

---

### Post by Dalek Draco ON LINUX on 2009-08-24
> **tubasoldier said:**
> This may help with your webcam problem. I don't have one to work with so I have never used them.

[http://help.ubuntu.com/community/Webcam](http://help.ubuntu.com/community/Webcam)

 THANK YOU!!!  I installed a program called cheese (using the terminal no less :D) and it has opened up with my ugly mug :). Thank you all for your help, doubtless I'll be back when I get stuck.

---

### Post by tubasoldier on 2009-08-24
Great to hear. Enjoy Linux

---

### Post by garvinrick4 on 2009-08-24
Get your third party repositorys installed  Partners and Medibuntu.

Will give you bells and whistles. Fonts,flashplayer and such. Then
you can install from Synaptic package manager and learn command line
later when system is proper. 
 Third party is in Software Sources. Click on close will tell you to reload and they will be there. 
 Any problem with Medibuntu just google there are a thousand links to tell you how to install. Should be know problem though. 

You can update and upgrade from Graphic User Interface. Do not worry
about command line until you have time to study!
 Enjoy it do not make it to complicated.

---

### Post by dragos240 on 2009-08-25
> **Dalek Draco ON LINUX said:**
> Hi, I've just moved over to Linux Ubuntu (9.04 I think...Jumpy J something...). I've been using Windows since I started using computers, and Vista finally saw me search for an alternative. 

Just a few quick questions, if someone can help me that would be great :D.

1. I have this beep noise when I get to the end of a list or try to type when I'm not on the page, its annoying, it doesn't go off when the sound is off...please help!

2. I'm trying to install the fonts Times New Roman, and Arial, into openoffice (thats right, FREE office :O) but wiki says I need to open the directory and type something in....wtf is the directory and how do I access it?

3. I'vre downloaded a driver package for my HP printer (K5300) (.run file) but I don't know what program I use to open/install it. It opens in something called archive manager by default, but doesn't do anything. Please can you tell me what the install program is or how to install programs.

I'll probably have loads more questions soon, but I'm going to try playing around with stuff to learn it all. Sorry if these seem like idiotic questions, but I really don't want to use Windows anymore, so i want to try and learn linux asap.

1. When you're backspacing?

2. Create a folder in your home directory called '.fonts' and place the font inside.
Also, open does not mean free, open refers to sharing the source.

3. you may want to open a terminal and type './whateverfile.run"

---

