---
title: "Black screen of death (help!)"
date: 2010-08-05
forum: General Help
---

### Post by ironferret on 2010-08-05
ok so I've been on windows for all my life, decided to take Linux for a run, my dad installed a easy loader on his computer and had no trouble, click click, done.

i installed it and when i choose ubuntu in the boot up menu it has a flickering "_" for a few seconds then it goes black, i don't hear any sound, i press alt ctrl f1 f2 i tried all the F's

after scanning a lot of forums and trying all the suggestions i decided i need direct help.

i'm on a sony vaio, windows 7 64 bit, intel core i3, Nvidia geoforce, 4gb ram, plenty of hard drive space (500gb) 

i read it might be the nvidia card....but im not sure how im suppose to fix that.

if you could, would you give step by step instruction, im not used to linux lingo yet

thank you very much.

---

### Post by Mr_VeRiTy on 2010-08-05
> **ironferret said:**
> ok so I've been on windows for all my life, decided to take Linux for a run, my dad installed a easy loader on his computer and had no trouble, click click, done.

i installed it and when i choose ubuntu in the boot up menu it has a flickering "_" for a few seconds then it goes black, i don't hear any sound, i press alt ctrl f1 f2 i tried all the F's

after scanning a lot of forums and trying all the suggestions i decided i need direct help.

i'm on a sony vaio, windows 7 64 bit, intel core i3, Nvidia geoforce, 4gb ram, plenty of hard drive space (500gb) 

i read it might be the nvidia card....but im not sure how im suppose to fix that.

if you could, would you give step by step instruction, im not used to linux lingo yet

thank you very much.
I had this Problem the first time I tried ubuntu, I had to reinstall without Wubi to get it to work (Wubi is where you install it inside of windows) I'd install it in another partition, even if you didn't use wubi, reinstall anyways.

---

### Post by ironferret on 2010-08-05
ok well i used wubi, so i have a 30 gb partition set aside, do i neet to make a / and a swap partition too?? or can i use the 30gb to do that? and what would be the best way to go about installing ubuntu (and uninstalling the wubi)

Edit: i found a file ubuntu in C Cleaner, would uninstalling that do the job?

---

### Post by Mr_VeRiTy on 2010-08-06
> **ironferret said:**
> ok well i used wubi, so i have a 30 gb partition set aside, do i neet to make a / and a swap partition too?? or can i use the 30gb to do that? and what would be the best way to go about installing ubuntu (and uninstalling the wubi)

Edit: i found a file ubuntu in C Cleaner, would uninstalling that do the job?
If I remember correctly, you can un-install the wubi ubuntu from the add/remove programs menu in control panel.
Also, the only partition you need is the / partition and some swap space (which is like pagefile in windows) you can make theese partitions during the ubuntu installation, also make sure you install the grub boot utility which the installer should do by default.

---

### Post by ironferret on 2010-08-06
so update time :P

got a 4gb sd card acting as usb device in a sd port for the trial for ubuntu as directed by the ubuntu website

i set the boot to external devices, and enabled the right things, and it just goes to windows, if i click the installer on the sd it just used wubi

im working with the netbook version 

is there something im missing....it won't boot to the sd card

edit: also when i click the wubi file in the sd card it says "there is no disk in the drive. please insert a disk into drive \device\dardisk1\DR1"

---

### Post by What Rights on 2010-08-06
> **ironferret said:**
> so update time :P

got a 4gb sd card acting as usb device in a sd port for the trial for ubuntu as directed by the ubuntu website

i set the boot to external devices, and enabled the right things, and it just goes to windows, if i click the installer on the sd it just used wubi

im working with the netbook version 

is there something im missing....it won't boot to the sd card


Press the Pause or Break key when the bios screen loads, then look at your options, you want to find the boot order select, or just go into your bios and change the usb boot options to above the cd and harddrive option.

---

### Post by ironferret on 2010-08-06
> **What Rights said:**
> Press the Pause or Break key when the bios screen loads, then look at your options, you want to find the boot order select, or just go into your bios and change the usb boot options to above the cd and harddrive option.

did that already

---

### Post by What Rights on 2010-08-06
> **ironferret said:**
> did that already


So you are sure that it is trying to boot from your USB. 

Did you create it correctly?

---

### Post by ironferret on 2010-08-06
> **What Rights said:**
> So you are sure that it is trying to boot from your USB. 

Did you create it correctly?

i followed ubuntu website direction to the letter..... maybe because it's not in a usb slot it's in a sd card reader built in my computer?  either way this is just weird...i want to trial it before i install, cause the last time it black screened...meh this is bothersome, i need a magic fix it person

im going to call it a night. try again in the morning...

---

### Post by Mr_VeRiTy on 2010-08-06
I don't think it will boot from an sd card, try burning it to a disk, or if you want to try it before installing, try using virtual box, this allows you to install an operating system onto a virtual machine and run it in windows, for instructions go [here]("http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu") this will not install Ubuntu on your system, but will let you try it. But remember that the speed Ubuntu runs in virtual box will be nowhere near the speeds achieved by actually installing it. If you do decide to install, you will have to burn a disk, if you don't have a disk burner, use someone else's computer to burn it, or your work computer.

---

### Post by ironferret on 2010-08-06
ok so i got a usb drive that works, the boot menu reads it, it loads up, text flys over the screen, then it goes black again.....i can see the usb light flickering like it's being used, but the screen is dead black when i try to boot from the usb

is it my video card, cause the usb looks like it works fine

any suggestions? im open to anything that will get ubuntu working on my computer short of erasing windows (need that for work)

---

### Post by bcbc on 2010-08-06
> **Mr_VeRiTy said:**
> I had this Problem the first time I tried ubuntu, I had to reinstall without Wubi to get it to work (Wubi is where you install it inside of windows) I'd install it in another partition, even if you didn't use wubi, reinstall anyways.

It sounds like a graphics card issue, unrelated to wubi. Try booting a live CD - you'll probably have the same issue. 

You need to modify the boot options - add 'nomodeset' after quiet splash and it should display fine. Depending on the install medium the method of modifying the boot options changes. [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

generally, if someone advises to reinstall without a clear explanation of how it will fix your problem, i'd ignore that advice.

---

### Post by ironferret on 2010-08-07
> **bcbc said:**
> It sounds like a graphics card issue, unrelated to wubi. Try booting a live CD - you'll probably have the same issue. 

You need to modify the boot options - add 'nomodeset' after quiet splash and it should display fine. Depending on the install medium the method of modifying the boot options changes. [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

generally, if someone advises to reinstall without a clear explanation of how it will fix your problem, i'd ignore that advice.
  lol yah, i wasn't sure how helpfull reinstalling would be if i used the same official website
thanks for the info, i'll try it and get back to you on the results

---

### Post by ironferret on 2010-08-07
so pressing f6 or e while the text loads and scrolls by does nothing, f6 puts a [[16 in there but it skips over that quickly

im still not clear on where i can actually impute anything

im using a usb and it gives me the choice to run the usb or install on hard drive and some other option....

---

### Post by bcbc on 2010-08-07
> **ironferret said:**
> so pressing f6 or e while the text loads and scrolls by does nothing, f6 puts a [[16 in there but it skips over that quickly

im still not clear on where i can actually impute anything

im using a usb and it gives me the choice to run the usb or install on hard drive and some other option....

when you boot from the usb, the first thing you see on the bottom of the screen is a small icon of a keyboard and a person. Press any key e.g. the spacebar. Then select language and you arrive at a menu. On the bottom it will list some function keys and pressing F6 gives you a list of options. Choose nomodeset.

---

### Post by ironferret on 2010-08-07
it said press tab to enter menu so i pressed it and typed nomodeset and pressed enter, black screen :/

here's the thing, i can't even get to the install screen, i get to a dos looking screen that lest me choose from installing and running the usb and after that it black screens, it seems like you need to press f6 when you get into the installation option in ubuntu....but i have yet to see what screen

ugh.... ubuntu must hate me

---

### Post by Ozymandias_117 on 2010-08-07
> **ironferret said:**
> it said press tab to enter menu so i pressed it and typed nomodeset and pressed enter, black screen :/

here's the thing, i can't even get to the install screen, i get to a dos looking screen that lest me choose from installing and running the usb and after that it black screens, it seems like you need to press f6 when you get into the installation option in ubuntu....but i have yet to see what screen

ugh.... ubuntu must hate me

Press f6 at the dos looking screen with the Install, Try without installing, Check disk for errors, and Memtest options.

What graphics card are you using? And how is your monitor connected?

---

### Post by Nick_Jinn on 2010-08-07
I had the same problem but it wasnt just Wubi....it was also the live CD installer.

I had to install it on a different PC then swap the hard drive back after enabling the Nvida drivers....adjusted itself and works like a charm now.



You might also be able to use a USB install (made on a different PC from live disk) and then update the video drivers (use the proprietary ones) while still on that PC. Then use that USB stick to install.

Yet a third way is to use an older version of Ubuntu.....Say Jaunty....then set updates to LTSR only and upgrade to Lucid after enabling the video drivers. That should work.

---

### Post by Nick_Jinn on 2010-08-07
Trust me. I tried following all this other advice and it didnt work. I tried the above and it worked. I bet you have the same problem....this affects the live installer and not just wubi.

---

### Post by ironferret on 2010-08-07
ok so clarification is needed, im on a sony vaio laptop so the monitor is connected..well it's part of the machine :P

and i found a round about way to the f6 menu, i go to "help" then f6 is boot parameters for spesific machines, i tried nomodeset there but it didn't recognize that command, it said something about video display errors and vga=771 for display.... not sure if that helps

switching hard drives on my computer...it's kinda hard and expensive for a laptop

---

### Post by 23dornot23d on 2010-08-07
Two things ..... the SD card size what size in Gb are you using ?

Have you tried it in a separate card reader ..... rather than the slot in the front of the machine
sometimes these are not that clever as I found out on my machine ...... it only seems to read 2 Gig Max.

Just a thought ....... as I use a 8 Gig SD card in an external card reader ........ and it works.
[COLOR=Red]( I cannot use the same SD card in the built in slot in the computer it does not work  )
[/COLOR] 
Might be another issue ,,, but worth checking if you have a card reader handy and a good size SD card.

---

### Post by ironferret on 2010-08-07
> **23dornot23d said:**
> Two things ..... the SD card size what size in Gb are you using ?

Have you tried it in a separate card reader ..... rather than the slot in the front of the machine
sometimes these are not that clever as I found out on my machine ...... it only seems to read 2 Gig Max.

Just a thought ....... as I use a 8 Gig SD card in an external card reader ........ and it works.
[COLOR=Red]( I cannot use the same SD card in the built in slot in the computer it does not work  )
[/COLOR] 
Might be another issue ,,, but worth checking if you have a card reader handy and a good size SD card.

well i switched to a 1gb usb pendrive now

---

### Post by 23dornot23d on 2010-08-07
1 Gig is not big enough you need at least a 4 Gig ... as far as I know .... and 8 Gig is better if you can get one at a reasonable price.

I will check ..... but I am sure the page that says about Pen Drives states the minimum size somewhere on it.
This is for installing Ubuntu onto it ..... 

[B][COLOR=Red]Yours is a different issue I think you are only using the SD drive to install it .........
[/COLOR][/B]
[B][URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]Installing Ubuntu USB stick
[/URL]
directly on a USB Flash drive[/B]

 In order to install a fully working Ubuntu operating system on your USB Flash drive make sure that: 

[LIST]
[*]Your Flash Drive has more than 2GB of memory
[*]Your Flash Drive is bootable
[*]Your Flash Drive has a high read/write speed and is USB 2.0 enabled
[/LIST]
The process is described in detail in an [external source]("http://iwebdevel.com/2010/02/13/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox/").

__________________________________________________

Ok the [WUBI]("http://wubi-installer.org/") requirements are different ......

         **Requirements**

         [IMG]http://wubi-installer.org/images/memory.png[/IMG] 384 MB memory
         [IMG]http://wubi-installer.org/images/harddisk.png[/IMG] 5 GB harddisk space
         [IMG]http://wubi-installer.org/images/windows.png[/IMG] Windows 98, 2000, XP, Vista

---

### Post by ironferret on 2010-08-07
hmmm ok i'll try something bigger, the thing is i don't have any pen drives bigger than 1gb, but i have 2 4gb sd cards and a bunch of 4 and 8 gb microsd cards.... and a 8gb dou pro...bah.......those won't work will they

im sure i can borrow a pen drive 2gb from someone, but i have a feeling that won't solve the problem :/

---

### Post by 23dornot23d on 2010-08-07
Its worth trying other things if you are stuck .... to use a different method of installation .....

Is your graphics card this one ?
*NVIDIA GeForce* 310M
There do seem to be a few issues with this graphics card .... but they can be resolved from what I have read.

---

### Post by Nick_Jinn on 2010-08-07
If its a SATA drive, they are 100% compatible with desktop SATA, both power and connectors....the only thing different is the housing. My case is kind of cool in that it has housing for 1 laptop hdd and up to 3 regular sized ones.

If you find a desktop, just unscrew it and swap the SATA drives.


If its PATA then forget about it, unless you have an adapter of some kind. I have a universal docking station that turns any hard drive into an external hard drive. Anyway.

You MIGHT be able to get away with 2gb installation, but 4 is better.

You can also try installing 9.04 or even Karmic then upgrading.



I know it feels hopeless, but trust me. Once you have the full OS downloaded it will work better and correct itself. Remember to install the video drivers first.

---

### Post by ironferret on 2010-08-07
> **23dornot23d said:**
> Is your graphics card this one 

*NVIDIA GeForce* 310M

yup yup, that's the one

---

### Post by 23dornot23d on 2010-08-07
Ok the thread that I was reading is here ...... [Nvidia Graphics 310M]("http://ubuntuforums.org/showthread.php?t=1392766")

I will look and see if there is a way to get you up and running ......

I think its going to be the NOMODESET option .....

that someone mentioned earlier ,,, you need to get to the installation screen first

either from a CD USB or SD card ,,,, once we are there you can add this and hopefully
get a good installation.

_________________________________________

These are more related to once you get it to install and boot ...... but you are going to have
to do a little work to get the graphics going from what I am reading .... 

I just found this too [URL="http://ubuntuforums.org/showthread.php?t=1369420&page=3"]Full thread is here

[/URL]  [Link to a solution]("http://ubuntuforums.org/showpost.php?p=9518433&postcount=22")

---

### Post by ironferret on 2010-08-07
oh ok, that looks good, i'll try that in the morning when i have energy to read straight, other wise im likely to rename [I]sonycw.txt    sonycw.bacon

[/I] i'll get back on this in about 8 hours or so, thanks again

---

### Post by 23dornot23d on 2010-08-07
Ok your welcome ..... but you need to get it to install first ...... the steps in the
last links are to get the graphics working after you get it installed ..... ok all for now.

___________________________________________________________________

There was a link was given by BCBC ...... and this is where you need to begin to get things sorted
I just checked the graphics out to make sure you were not going to be wasting your time
and from what I found out - things look good ........

So in the morning ..... work through this ,,,, do it slowly and make sure that you understand what
they are doing ..... and then you will get your computer working and running UBUNTU.

If you get stuck with anything like editing the GRUB to boot it - just leave a message here.


[COLOR=Blue]This link was posted earlier and is the key to getting this working ..... you have to start here
[/COLOR]
NOMODESET
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


_____________________________________________________________________

Also check this out .....
This is a compatibility guide to running Linux with the Sony Vaio CW laptop. 
Read the first mention in the discussion at the [bottom of this page]("http://www.linlap.com/wiki/sony+vaio+cw") ......
[COLOR=Blue]Some of the other links may be useful too .... for later on once you are up and running.[/COLOR]
and its a recent report
( looking at the dates when the comments were started on it gives a good indication as to
how old the information is ..... the newer information is better usually the speed things change nowadays )

---

### Post by ironferret on 2010-08-08
well i tried renaming sonycw.txt to sonycw.bin, but that's just in name, it still reads like a text file.  i'm still not sure what they mean by "terminal" seems like alot of people have been unsucessfull on installing linux with this particular laptop.  

my main concern is that im not sure where i should type all the commands in

---

### Post by ironferret on 2010-08-12
never mind. i'l stick with windows :/

---

### Post by Nick_Jinn on 2010-08-12
Sorry you had such a bad experience. Did you try my suggestion though?

Try installing Karmic, installing the video drivers then upgrading. If Karmic works it should be a really easy fix...easier then some of the suggestions you have gotten from here. Its just the graphical live mode thats broken on some video cards only, but Karmic might not have that problem.


Give it one more shot before Windows.

---

