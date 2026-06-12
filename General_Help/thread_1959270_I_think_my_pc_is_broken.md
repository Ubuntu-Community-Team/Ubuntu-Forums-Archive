---
title: "I think my pc is broken"
date: 2012-04-15
forum: General Help
---

### Post by dictodude on 2012-04-15
So, I was installing Ubuntu on my (old 2005 xp) pc, because I now have a new win 7 laptop....
(I take risks with older pcs)

I ran wubi through xp media centre edition and allocated ubuntu 6gb of space... Sucesss.

Then it rebooted my pc... and I decided to choose to boot Ubuntu... But I went through advanced boot options and booted demo mode... (to try it out as my pc does not boot from cd). So to me.. Ubuntu was the best ;) .

Then I clicked ..install Ubuntu 11.10.. (from the desktop). I was going through the installation process... until I got to the partitioning process..... Here's where the trouble begins... :(

I clicked the install alongside windows option... And waited... It came up with an error and sent me to the advanced partitioner. I tryed to use that... But the same error came up... (I don't remember what it said)

And on third try... It froze... So I hard rebooted (holding power button) and it is now stuck on boot with a _
that keeps on flashing on a black screen. (so I can't access the bootloader). So here is my plan...

I'll put my hdd in my dads desktop xp pc... Use chkdsk to repair my hdd... Get rid of the Linux partition... But how to I get rid of ubuntus boot entry from another pc???... (as my hdd is in my dads pc)

---

### Post by dictodude on 2012-04-15
Oh and I can't boot from cd cos my pc isn't set to do that and I can't set it cos my boot menu needs a password for access and I don't know it. I've tryed resetting it before.. But it dosent work.

---

### Post by dictodude on 2012-04-15
Pc specs:

Acer Aspire T180-OA7Z
Amd Sempron 3000+
512mb ram (I think)
Win xp media centre edition

I have no windows disk....

---

### Post by dictodude on 2012-04-15
Help me people..... :(

---

### Post by overdrank on 2012-04-15
Hi and welcome, please do not bump your thread so quickly. Once a day (24hr) is polite.

---

### Post by dictodude on 2012-04-15
> **overdrank said:**
> Hi and welcome, please do not bump your thread so quickly. Once a day (24hr) is polite.

Ok .... I'll try not to keep posting...... But can some people answer within 24 hrs cos I really need an answer!!

---

### Post by jadtech on 2012-04-15
> **dictodude said:**
> 
I ran wubi through xp media centre edition and allocated ubuntu 6gb of space... Sucesss.

Then it rebooted my pc... and I decided to choose to boot Ubuntu... But I went through advanced boot options and booted demo mode... (to try it out as my pc does not boot from cd). So to me.. Ubuntu was the best ;) .

Then I clicked ..install Ubuntu 11.10.. (from the desktop). I was going through the installation process... until I got to the partitioning process..... Here's where the trouble begins... :(

I clicked the install alongside windows option... And waited... It came up with an error and sent me to the advanced partitioner. I tryed to use that... But the same error came up... (I don't remember what it said)

And on third try... It froze... So I hard rebooted (holding power button) and it is now stuck on boot with a _
that keeps on flashing on a black screen. (so I can't access the bootloader). So here is my plan...

I'll put my hdd in my dads desktop xp pc... Use chkdsk to repair my hdd... Get rid of the Linux partition... But how to I get rid of ubuntus boot entry from another pc???... (as my hdd is in my dads pc)

ok not sure why so much urgency if this is an old  computer , I have some confusion here for one thing because Wubi don't work as you are describing at all nothing is partitioned what so ever and when things reboot for the first time there is nothing to select at all it continues setting up ubuntu which when done with WUBI is a windows program linux running on windows..
you do get a menu to choose windows or ubuntu on your next restart after all the install is finished..

did you reboot your computer from USB memory stick you brunt  ubuntu ISO on ??? or down load wubi install from windows through your browser ??

---

### Post by jadtech on 2012-04-15
sounds to me like you have 2 different things going on at first  it sounds like a Wubi install allocating disk space size for wubi to use in window , the reboot  wubi install never offer to boot demo mode and never takes you some where change partition or format harddrive..

if that is what you have done you will need a CD for windows I believe if you removed the MBR..

a wubi install works from windows  it work like daul boot how ever  work  witha line in windows boot INI, wubi can be removed like any other windows program through the  add and remove program list in the control panel ..

---

### Post by callmemahavir on 2012-04-15
It seems that ubuntu does not managed to write the dual boot properly.
But anyway the data is still in your hard disk.
So to recover all the data use recovery disc.

Download the following recovery disc and boot from the disc and save all your data.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Eirreann on 2012-04-15
I had problems similar to this when I installed Ubuntu; Wubi worked great for a while, but it was really slow for me so I switched to the disc install and had the exact same error as you.  I found that my computer just couldn't handle dual-booting, so when creating the partition it would cancel the process for some reason.  It was quite annoying.  However, I found that when installing Ubuntu as the only OS (completely re-writing XP) everything worked great and now I am completely content using Ubuntu on my 2001 XP laptop!
But I digress.  So the BIOS splash screen doesn't appear at all?  Well if you are able to access the bootloader at all I'd recommend installing Ubuntu with a full installation; it is well worth it!

---

### Post by jadtech on 2012-04-15
that was the odd part I dont understand since they only installed wubi where any of the other stuff comes   they did use a CD to boot they down loaded wubi installer.. 

no mention of if down loaded for 32bit 64bit or nothing and no reason to get a message about partitioning ..

though if they want ubuntu on the older machine they most likly will have better like with a light version since they only have 512K ram..

---

### Post by Eirreann on 2012-04-15
> **jadtech said:**
> that was the odd part I dont understand since they only installed wubi where any of the other stuff comes   they did use a CD to boot they down loaded wubi installer.. 

no mention of if down loaded for 32bit 64bit or nothing and no reason to get a message about partitioning ..

though if they want ubuntu on the older machine they most likly will have better like with a light version since they only have 512K ram..
I think that his machine probably has more than 512MB of RAM... hopefully 1GB; if not, upgrade, or else your experience with Ubuntu won't be very satisfactory at all!
But yes, Xubuntu or Lubuntu are preferable alternatives to Ubuntu on older, low-speced machines; I personally love Xubuntu and use it occasionally when something is too much for my laptop to handle while running Ubuntu (which for me is pretty much just gaming, but anyway).

---

### Post by 3Miro on 2012-04-15
My guess here is that OP installed Ubuntu via Wubi and left the CD in the CD-Rom. On Reboot, the machine booted form the CD and OP chose "Install". Then things messed up on the partitioning stage, which means that the partition table may have been damaged.

dictodude: see if you can boot from the LiveCD with "Try Ubuntu" option. Then see if you can access your files.

---

### Post by bcbc on 2012-04-15
> **jadtech said:**
> sounds to me like you have 2 different things going on at first  it sounds like a Wubi install allocating disk space size for wubi to use in window , the reboot  wubi install never offer to boot demo mode and never takes you some where change partition or format harddrive..

if that is what you have done you will need a CD for windows I believe if you removed the MBR..

a wubi install works from windows  it work like daul boot how ever  work  witha line in windows boot INI, wubi can be removed like any other windows program through the  add and remove program list in the control panel ..

Actually Wubi does have an option to boot from CD. It's called 'Demo and full installation'. Within this there are two options - the obvious reboot with the CD in the tray - and the 'CD boot helper' - for computers that can't boot from CD using the BIOS.

As far as I know, the CD boot helper doesn't work in 11.10, so not really sure which option was used. But whichever option, it takes you to the live Desktop, where you can run the installer.

---

### Post by jadtech on 2012-04-15
> **dictodude said:**
> 

Then it rebooted my pc... and I decided to choose to boot Ubuntu... But I went through advanced boot options and booted demo mode... (to try it out **as my pc does not boot from cd**). So to me.. Ubuntu was the best ;) .

Then I clicked ..**install Ubuntu 11.10.. (from the desktop)**. I was going through the installation process... until I got to the partitioning process..... Here's where the trouble begins... :(



ok sorry maybe I miss under stand some how I just read cant boot from disk installed from desktop .. wouldnt you have to boot from disk to mes up partitions ???

---

### Post by bcbc on 2012-04-16
> **jadtech said:**
> ok sorry maybe I miss under stand some how I just read cant boot from disk installed from desktop .. wouldnt you have to boot from disk to mes up partitions ???
Wubi has two option to boot from the CD. One, you reboot and select to boot from CD. Two, it installs the grub4dos etc. bootloader into the windows boot manager, and it boots the CD. Both of these result in a live CD desktop which has the Install option on the desktop.

The other option with Wubi is to install inside Windows (most common).

Coming in 12.04, you won't be able to install within Windows using an Ubuntu CD. The only option will be to reboot and boot the CD. Maybe the CD boot helper will be there as well, but not the install inside windows option (this will only be available when running wubi.exe standalone).

---

### Post by critin on 2012-04-16
> Then it rebooted my pc... and I decided to choose to boot Ubuntu... But I  went through advanced boot options and booted demo mode... (to try it  out as my pc does not boot from cd). 

To be clear--you did not download ubuntu and burn to a CD to install?  You used the WUBI installer only?   That's the only way I've used it.

Here's some info that may help you.

> [COLOR=Red]Warning

Wubi uses a virtual disk that is sensitive to forced shutdowns.[/COLOR] If Ubuntu appears to be frozen please refer to: How to reboot cleanly even when the keyboard/mouse are frozen

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Doing a hard shutdown isn't good for the systems.

---

### Post by bcbc on 2012-04-16
If you install from CD, when you reboot (to complete the install), you can hit the Esc key and you get a menu. The last option is "Demo mode". I tested it a long time ago (a different release from 11.10) and it didn't work.

This might be what the OP selected.

---

### Post by critin on 2012-04-16
> **dictodude said:**
> Oh and I**[COLOR=Red] can't boot from cd cos my pc isn't set to do that[/COLOR]** and I can't set it cos my boot menu needs a password for access and I don't know it. I've tryed resetting it before.. But it dosent work.

OP must have used the Wubi installer, but something odd is happening here in order to have those choices.
Wubi downloaded a 64AMD version to my 32bit computer (it gave no choices) and it wouldn't work.  Perhaps something like this happened here.

---

### Post by bcbc on 2012-04-16
Anyway... how it happened isn't really material. The installer ran, the partitions are messed. I doubt whether it's the MBR bootloader as this is only installed later on during the installation.

It seems more likely that either the partition table was damaged, or Windows was damaged if the partition was resized, or maybe Ubuntu didn't recognize the partition table and a new one was written.

In all these cases, the best bet is to run a partitioning tool and see if it can recover the old partition table. From Ubuntu you can use testdisk for this.

If you can boot an Ubuntu CD as a live CD (select "try ubuntu" without installing), and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), that contains useful diagnostic information to repair.

---

### Post by dictodude on 2012-04-16
Ok.... Here we go guys.... I know I didn't explain enough so sorry.....

I downloaded wubi.... Burned it to cd, ran the cd through win xp...... Clicked install alongside windows.

Rebooted...... (note this is 64bit) booted into Ubuntu...... NOT THE INSTALLATION.... I ran demo mode..... 

To run demo mode... I booted Ubuntu... Clicked ESC.... Chose demo mode.

I didn't use the live cd on boot.... REMEMBER I CAN'T BOOT FROM CD.... MY PC ISN'T SET TO DO THAT AND TO SET IT I NEED ACCESS TO THE BOOT MENU.... BUT I CAN'T DO THAT COS ITS BLOCKED WITH A PASSWORD THAT I DON'T KNOW AND I CAN'T RESET IT.....

---

### Post by dictodude on 2012-04-16
> **3Miro said:**
> My guess here is that OP installed Ubuntu via Wubi and left the CD in the CD-Rom. On Reboot, the machine booted form the CD and OP chose "Install". Then things messed up on the partitioning stage, which means that the partition table may have been damaged.

dictodude: see if you can boot from the LiveCD with "Try Ubuntu" option. Then see if you can access your files.

Impossible. I CAN'T BOOT FROM CD!! And yes I do have 1gb of ram...

32-bit

---

### Post by dictodude on 2012-04-16
> **Eirreann said:**
> I had problems similar to this when I installed Ubuntu; Wubi worked great for a while, but it was really slow for me so I switched to the disc install and had the exact same error as you.  I found that my computer just couldn't handle dual-booting, so when creating the partition it would cancel the process for some reason.  It was quite annoying.  However, I found that when installing Ubuntu as the only OS (completely re-writing XP) everything worked great and now I am completely content using Ubuntu on my 2001 XP laptop!
But I digress.  So the BIOS splash screen doesn't appear at all?  Well if you are able to access the bootloader at all I'd recommend installing Ubuntu with a full installation; it is well worth it!

I'd rather not plz..... This is my htpc (home theatre pc) and I have xp media centre with a tv tuner. I don't want to get rid of it.

---

### Post by dictodude on 2012-04-16
What my problem is:

I can't boot up ANY os because UBUnTu messed up my partitions.

---

### Post by nothingspecial on 2012-04-16
Please stop bumping your thread to the top.

---

### Post by 3Miro on 2012-04-16
I can think of 3 options:

- Find who put the password on your machine and get the password. It is your machine, right?

- Find a way to reset the BIOS CMOS, note that on an older computer there may be multiple jumpers, you need to find the one for the CMOS (check the manual, on-line for the motherboard model or read the tiny letters there should be a CMOS label).

[http://www.youtube.com/watch?v=Pdp_L5IxaNI](http://www.youtube.com/watch?v=Pdp_L5IxaNI)

- Remove the HDD from the computer and put it on a machine that can boot from a CD.

---

### Post by Eirreann on 2012-04-16
I'm still confused as to how you got Wubi (the Windows Installer) on a disc, when it is in face an .exe file not an ISO file... it installs like a normal programme, not as a completely separate operating system.

---

### Post by jadtech on 2012-04-16
> **bcbc said:**
> Actually Wubi does have an option to boot from CD. It's called 'Demo and full installation'. Within this there are two options - the obvious reboot with the CD in the tray - and the 'CD boot helper' - for computers that can't boot from CD using the BIOS.

As far as I know, the CD boot helper doesn't work in 11.10, so not really sure which option was used. But whichever option, it takes you to the live Desktop, where you can run the installer.

hehe down load stuff on line for so long nearly forgot programs can  and will load and run just putting them in the drive while windows is running or going into my computer ..

---

### Post by ZekeGraal on 2012-04-16
> **Eirreann said:**
> I'm still confused as to how you got Wubi (the Windows Installer) on a disc, when it is in face an .exe file not an ISO file... it installs like a normal programme, not as a completely separate operating system.

Maybe he actually has the Ubuntu image on a disk, which also comes with the Wubi installer (the last time I checked.)

---

### Post by Eirreann on 2012-04-16
> **bcbc said:**
> Actually Wubi does have an option to boot from CD. It's called 'Demo and full installation'. Within this there are two options - the obvious reboot with the CD in the tray - and the 'CD boot helper' - for computers that can't boot from CD using the BIOS.

As far as I know, the CD boot helper doesn't work in 11.10, so not really sure which option was used. But whichever option, it takes you to the live Desktop, where you can run the installer.

Um... does it?  I used Wubi only a couple of weeks ago to get it onto my desktop and there was no such option that I could see...

---

### Post by dictodude on 2012-04-16
> **Eirreann said:**
> Um... does it? I used Wubi only a couple of weeks ago to get it onto my desktop and there was no such option that I could see...
 
 
well there is

---

### Post by dictodude on 2012-04-16
> **ZekeGraal said:**
> Maybe he actually has the Ubuntu image on a disk, which also comes with the Wubi installer (the last time I checked.)
 
Exactly right..... thats how i did it

---

### Post by Eirreann on 2012-04-16
> **dictodude said:**
> well there is

Huh... well, that's odd...  Either way, I personally don't trust Wubi any more, after all of the problems I've experienced with it (and, it seems, so have you).  Anyway, I hope you're able to sort everything out, mate!

---

### Post by bcbc on 2012-04-16
dictodude, you said you put your hard drive in another computer. Can you boot that computer using the Ubuntu CD? and then can you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")? That will help show what's going on.

Thanks

---

### Post by Eirreann on 2012-04-16
Okay, just a notif; I just downloaded Wubi from Ubuntu.com on my Windows 7 desktop and started up the setup and I am seeing no options to boot from a disc or anything like that... Did you download Wubi from Ubuntu.com, and could you post the link of wherever it is that you downloaded it?

---

### Post by bcbc on 2012-04-16
> **Eirreann said:**
> Okay, just a notif; I just downloaded Wubi from Ubuntu.com on my Windows 7 desktop and started up the setup and I am seeing no options to boot from a disc or anything like that... Did you download Wubi from Ubuntu.com, and could you post the link of wherever it is that you downloaded it?

Boot Windows.
Take ubuntu desktop CD. 
Insert CD.
Voila.

---

### Post by Eirreann on 2012-04-16
> **bcbc said:**
> Boot Windows.
Take ubuntu desktop CD. 
Insert CD.
Voila.
Erm.... this is Wubi, Windows Installer, we're talking about, right?  The .exe programme downloadable [here]("http://www.ubuntu.com/download/ubuntu/windows-installer")?  I mean, sure you could write the .exe file onto a disc and configure an Autorun.ini file to start it up, but it isn't an ISO, so I'm still confused how he managed to boot from it.  I feel like I'm missing something here...

---

### Post by jadtech on 2012-04-16
if you burn the CD you can boot with it, how ever , if you are running window just put the cd in the drive it will auto run and give a list of options including wubi install or install side by side with windows just as if you bought a game from the store on CD you would start windows pop the CD in and it would autp run and install the game  ...

---

### Post by bcbc on 2012-04-16
> **Eirreann said:**
> Erm.... this is Wubi, Windows Installer, we're talking about, right?  The .exe programme downloadable [here]("http://www.ubuntu.com/download/ubuntu/windows-installer")?  I mean, sure you could write the .exe file onto a disc and configure an Autorun.ini file to start it up, but it isn't an ISO, so I'm still confused how he managed to boot from it.  I feel like I'm missing something here...
You could do that I suppose, but since it's already done on the Ubuntu Desktop CD ISO, you don't have to do it.

So the part you are missing is that wubi.exe is on the desktop CD ISO and when you insert it (while running windows) it will run wubi.exe. That's about as clear as I can make it.

If you run wubi.exe standalone, it magically detects this and doesn't present the CD menu, just the install within windows screen.

Here's [the code]("http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/view/head:/src/wubi/application.py"):
```
    def run_cd_menu(self):
        '''
        If Wubi is run off a CD, run the CD menu (old umenu)
        '''
        log.info("Running the CD menu...")
        self.frontend = self.get_frontend()
```

---

### Post by Eirreann on 2012-04-16
> **bcbc said:**
> You could do that I suppose, but since it's already done on the Ubuntu Desktop CD ISO, you don't have to do it.

So the part you are missing is that wubi.exe is on the desktop CD ISO and when you insert it (while running windows) it will run wubi.exe. That's about as clear as I can make it.

If you run wubi.exe standalone, it magically detects this and doesn't present the CD menu, just the install within windows screen.

Here's [the code]("http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/view/head:/src/wubi/application.py"):
```
    def run_cd_menu(self):
        '''
        If Wubi is run off a CD, run the CD menu (old umenu)
        '''
        log.info("Running the CD menu...")
        self.frontend = self.get_frontend()
```

Ah, okay.  This desktop CD that you refer to, I'm assuming that is the ISO that you download from [here]("http://www.ubuntu.com/download/ubuntu/download"), right?  This is the first time I've heard of Wubi running off of a disc; I was under the impression that the whole point of Wubi was to avoid having to deal with discs and boot menus and all of that...
But thanks for clearing that up for me, mate!  Sometimes I can be such an obvious noob, haha!

---

### Post by Eirreann on 2012-04-16
> **jadtech said:**
> if you burn the CD you can boot with it, how ever , if you are running window just put the cd in the drive it will auto run and give a list of options including wubi install or install side by side with windows just as if you bought a game from the store on CD you would start windows pop the CD in and it would autp run and install the game  ...

Ooooh.... I did not know that, haha!  Wow, I feel like such an idiot now.

---

### Post by RJARRRPCGP on 2012-04-28
> **dictodude said:**
> 

And on third try... It froze... So I hard rebooted (holding power button) and it is now stuck on boot with a _
that keeps on flashing on a black screen. 

You're gonna have to clear the MBR. (wipe sector 0 at the least)

---

