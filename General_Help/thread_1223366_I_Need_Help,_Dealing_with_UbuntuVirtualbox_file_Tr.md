---
title: "I Need Help, Dealing with Ubuntu/Virtualbox file Transfer"
date: 2009-07-26
forum: General Help
---

### Post by rcastoro on 2009-07-26
Hello all, I'm brand new to the Forum, I'm glad to be a part of the Open Source OEs world, where Windows is only a condiment for the main entrée; Linux (Ubuntu 9 with GNOME).

I'm not new to Linux, but I'm severely inexperienced. I just added Ubuntu to my Windows Vista computer; Dual Boot. I Installed VirtualBox and got Vista working inside Ubuntu without incident and now need to transfer files and folders from my Ubuntu OS  to the Virtualbox OSE Vista Emulation.

I've never used Share options in my 13 years of Computer Learning and Programming.

I go to Applications>Accessories>VirtualBox OSE and hit start, Vista Loads without Fault. I've done a bit of research with no avail. I read somewhere to select in the VirtualBox Devices>Install Guest Additions. I Did this, and that installed with no fault.

Now I have Ubuntu & Virtualbox Windows Vista, along with a giant GAP in my knoweldge of Sharing / Transfering Files.

To make a long story alittle shorter, I need to move an entire Directory including its files from Ubuntu to the Vista Emulation.

I Know nothing of sharing, I've searched for hours for an answer and cannot get a clear, precise answer. Obviouslym I tried to drag the folder from Llinux to the Virtualbox Vista, but no way.

I know this has to do with sharing but I've always feared the sharing buttons since Windows 2000 and have since avoided it. I know nothing of it.

If from the kindness of your heart -- Could somebody please Type up a Descritive set of steps I need to take to share/transfer/move(copy+paste) or whatever my Ubuntu main home folder(username folder and all inside) to any location on my Virtualbox Windows Vista Emulation Instance. Pretty.......PRETTU please, with $5 paypal donations on top...

Id be happy if you can contact me with the steps via my [FONT=Arial Black]_**[EMAIL="rcastoro@verizon.net"]email[/EMAIL]**_[/FONT] or reply here.

This will solve my major road-block. I'm am hoping to migrate from Windoze to Linux with a full copy of Vista still on Dual Boot with Ubuntu for my Photo and Video Editing Capabiltafiliries as an Intermediate Programmer/Developer with java, php, mysql knowledge and hopefulu  learning to become a IP Administartive Manager some day,

Rocco Castoro,
you can contact me with the steps via my [FONT=Arial Black]_**[EMAIL="rcastoro@verizon.net"]email[/EMAIL]**_[/FONT] or here is fine.
[FONT=Verdana][SIZE=1][I]
-- Karma is a figurative bumerange. When you throw it without care - it can put you down harder than take you out with your target --[/I][/SIZE][/FONT]

---

### Post by grayn0de on 2009-07-26
That's simple enough. :)

I've created a video tutorial for you (cause I was bored. ;) ), here: [http://www.grayn0de.com/videos/tut-shared_folders_vbox.ogv](http://www.grayn0de.com/videos/tut-shared_folders_vbox.ogv)

Enjoy! (You can play it with VLC or Movie Player after download.)

---

### Post by akudewan on 2009-07-26
> **rcastoro said:**
> 
To make a long story alittle shorter, I need to move an entire Directory including its files from Ubuntu to the Vista Emulation.


1) Start VirtualBox and load up Vista

2) In the VirtualBox window, (the one running Vista), go to Devices > Shared Folders. (Go out of fullscreen if you can't see it)

3) A window will come up. Select the "Add new shared folder" button from here
[[IMG]http://img198.imageshack.us/img198/461/sharedfolders.th.png[/IMG]](http://img198.imageshack.us/i/sharedfolders.png/)

4) Choose the Ubuntu folder that you want to share with the Vista emulation

5) Enter a folder name, ('shared', for example)

6) Tick the 'Make permanent' option if you don't want to repeat this every time.
If you tick Read-only, you will not be able to copy files from Vista to Ubuntu, but you can copy from Ubuntu to Vista. The choice is yours

7) Click OK to dismiss the dialog and you should see your share under 'Machine folders'. Click OK to dismiss that dialog.

8) In windows, you need to 'Map Network drive'. (In windows XP this is done from My Computer > Tools (from the menu) > Map network drive)

9) The 'Map Network Drive' option will ask you for a drive letter and a folder path. The folder path will be **\\vboxsvr\shared** (or whatever name you entered in point(5) )

10) Click OK or Finish to dismiss the dialog and you should be able to see your Ubuntu folder as a Network drive in Vista.

Hope this helps. If you come across any problem, let me know.

Btw, people on this forum will be glad to help even without $5 paypal incentives :)
I wouldn't encourage e-mailing, since this post may help other people with the same problem.

---

### Post by ericab on 2009-07-26
> **rcastoro said:**
> Pretty.......PRETTU please, with $5 paypal donations on top...

uh oh, someone is down and out $10

:o

---

### Post by rcastoro on 2009-07-26
Hey - ! If I Say I'll pay the man, I'm going to keep my word. (Offer only applicable to first user response, offer valid through July 25-July27 2009. Offer not available in Alaska, Hawaii, or Antarctica. Little people, and Panda Bears need not apply.

Thanks For your Help Gentlemen, Please send me your paypal accounts to my email and I'll give you a Donation for your time. 

**I've always appreciated the Online and Open Source Community.**

[rcas]toro[@]veri[zon].{net}

Wait, I have to test it first... Ill add another reply saying OK if it worked and then you can send me your paypal for a Donation, I INSIST.

---

### Post by rcastoro on 2009-07-26
Grayn0de, the Video you Created I'm sure will help 100's if not 1000's of people who come to this forum with the same question, It's a great resource and I Thank you for taking the time to create it:popcorn: 

It still will not mount the 'rcsatoro' or my actual ubuntu home folder to the VirualBox - My Theory is when you go to Start Menu and Run in Vista, you type: net use [SIZE=2]**x:**[/SIZE] \\vb-name\folder - is the X a Drive that I need to change to fit my computer, or is -x an argument or option, because It's not working still.

Other then that, everything seem's like it should work (Beuatiful video quality)

Thanks again grayn0de, I look forward to your response.

> **grayn0de said:**
> That's simple enough. :)

I've created a video tutorial for you (cause I was bored. ;) ), here: [http://www.grayn0de.com/videos/tut-shared_folders_vbox.ogv](http://www.grayn0de.com/videos/tut-shared_folders_vbox.ogv)

Enjoy! (You can play it with VLC or Movie Player after download.)

---

### Post by rcastoro on 2009-07-26
AKUDEWAN, I completed steps 1 - 7 without fault, however when I enter the name of the Virtual Box (I named it Virtual-Vista) into the folder field of the Map Network Drive Dialog Box and type in the Ubuntu Directory I Shared via Devices>Shared Folders (/home/rcastoro/Pictures/wallpapers) \\Virtual-Vista\Wallpaper and hit Finish it says Attempting to connect to \\Virtual-Vista\Wallpaper...\ then a Error box pops up saying "The Network Path \\Virtual-Vista\Wallpaper Could not be found... When I Hit Browse in the Folder: Field, it gives me a Dialog Box with Network, Ubuntu, and VIRTUALBOXVISTA, when I try to Expand Ubuntu, it displays Printers and that's all...

Also in the Network Map Folder in Vista I have VirtualBoxVista ---> Gateway ----> Internet. Then Below that it says "The Following discovered device(s) can not be placed in the map. (I have a feeling this has something to do with it? - Also The name of the Virtualbox Vista Instance I named it Virtual-Vista - But I Keep seeing VirtualBoxVista too. 

What am I Doing Wrong?

Here's a few ScreenShots:
[IMG]http://img36.imageshack.us/img36/7991/share1.png[/IMG]

[IMG]http://img36.imageshack.us/img36/4899/share2.png[/IMG]

[IMG]http://img36.imageshack.us/img36/6513/share3.png[/IMG]



> **akudewan said:**
> 1) Start VirtualBox and load up Vista

2) In the VirtualBox window, (the one running Vista), go to Devices > Shared Folders. (Go out of fullscreen if you can't see it)

3) A window will come up. Select the "Add new shared folder" button from here
[[IMG]http://img198.imageshack.us/img198/461/sharedfolders.th.png[/IMG]]("http://img198.imageshack.us/i/sharedfolders.png/")

4) Choose the Ubuntu folder that you want to share with the Vista emulation

5) Enter a folder name, ('shared', for example)

6) Tick the 'Make permanent' option if you don't want to repeat this every time.
If you tick Read-only, you will not be able to copy files from Vista to Ubuntu, but you can copy from Ubuntu to Vista. The choice is yours

7) Click OK to dismiss the dialog and you should see your share under 'Machine folders'. Click OK to dismiss that dialog.

8) In windows, you need to 'Map Network drive'. (In windows XP this is done from My Computer > Tools (from the menu) > Map network drive)

9) The 'Map Network Drive' option will ask you for a drive letter and a folder path. The folder path will be **\\vboxsvr\shared** (or whatever name you entered in point(5) )

10) Click OK or Finish to dismiss the dialog and you should be able to see your Ubuntu folder as a Network drive in Vista.

Hope this helps. If you come across any problem, let me know.

Btw, people on this forum will be glad to help even without $5 paypal incentives :)
I wouldn't encourage e-mailing, since this post may help other people with the same problem.

---

### Post by akudewan on 2009-07-26
Use **\\vboxsvr\Wallpaper** instead of \\Virtual-Vista\Wallpaper

---

### Post by howefield on 2009-07-26
> **rcastoro said:**
> As for Anybody else that comes across this - I'm not Advertising I'm returning the favor. For Anybody else interested, you wont get this deal, but you will get my generally Low Prices, just email me.

Good luck to you but it is still spam. 

Makes you wonder if the thread has been concocted for this very purpose....

---

### Post by jadhav333 on 2009-07-27
It works.. I have tested it.. WE need more people like rcastoro :)

---

### Post by therocco2k on 2009-07-27
Thanks god for this thread, I've been looking for an answer to do the same thing and this totally Helped.

---

### Post by howefield on 2009-07-29
> **therocco2k said:**
> Thanks god for this thread, I've been looking for an answer to do the same thing and this totally Helped.

Of course you have... you and rcastoro are the same person. 

:lolflag::lolflag:

---

