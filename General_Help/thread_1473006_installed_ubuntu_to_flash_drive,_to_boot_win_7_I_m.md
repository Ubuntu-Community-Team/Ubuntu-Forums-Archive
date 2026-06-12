---
title: "installed ubuntu to flash drive, to boot win 7 I must have drive plugged in. help!?"
date: 2010-05-04
forum: General Help
---

### Post by blaad on 2010-05-04
So I was following a tutorial on how to install ubuntu fully onto a flash stick so you can save things aswell. I have two flash sticks, so I installed the sort of "trial" on one with unetbootin. Then i booted to the flash stick, and plugged in my other flash stick.
 
Then I clicked to make a startup disk, and selected the unused USB drive. It all seemed to be working well, it installed. I restarted and booted from the now officially installed usb stick. However when I took it out and restarted to boot into windows 7, it gave me some sort of error and had a command line that said "grub rescue>" and I could enter a command. However I am unsure of what to do.
 
So I restarted with the flash stick in, and it gave me a bunch of boot options, windows 7 included.
 
Could someone please explain what I have done wrong or how I can fix it?

---

### Post by Bats72 on 2010-05-04
your boot loader is on your flash drive ..


i cant help you to  move it  aorry maybe someone knows how to  but in my case reinstall everything with the boot loader in your hdd on your pc and even there i dont know how grub will perform in these cases ....

---

### Post by wilee-nilee on 2010-05-04
Plug the booting full install thumb in then boot the live cd and post this boot script in code tags. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This will help since you have not given a full description but this script will. It will be helpful to know as well what is your final goal here.

---

### Post by blaad on 2010-05-04
I cant boot into ubuntu anymore.. I restart with the usb stick in, and I pick the option which says "ubuntu with linux 2.6.32-21-generic-pae"
 
then it starts to boot up, it shows the ubuntu startup screen, then flashes to a dos screen which states "ubuntu 10.04 LTS tty1" and it asks me to login.
 
I enter my username and password and then it gives me the ability to enter further commands with sudo or su.
 
my final goal is to be able to boot windows 7 on my hard drive without having to have the usb stick plugged in, atm I care not about what happens to ubuntu as it is only on a flash stick.

---

### Post by blaad on 2010-05-04
bump for further support

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> I cant boot into ubuntu anymore.. I restart with the usb stick in, and I pick the option which says "ubuntu with linux 2.6.32-21-generic-pae"
 
then it starts to boot up, it shows the ubuntu startup screen, then flashes to a dos screen which states "ubuntu 10.04 LTS tty1" and it asks me to login.
 
I enter my username and password and then it gives me the ability to enter further commands with sudo or su.
 
my final goal is to be able to boot windows 7 on my hard drive without having to have the usb stick plugged in, atm I care not about what happens to ubuntu as it is only on a flash stick.

W7 can have it's bootloader reinstalled it is not a hard process, you just need a recovery disc and some instructions. 1st are the instructions 2nd is a link to a recovery disc.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

So your saying that if you load a thumb with the Ubuntu ISO say with unetbootin you can't just go to a live session. If you can do this then you may want to post the bootscript just so we are sure we are on the same page.

If W7 hasn't been corrupted by any nasty-ware, and is still there, you are probably in good shape to get it going again.

Here is a thread #4 post is the instructions just the same as the MS link so you can orientate yourself.
[http://ubuntuforums.org/showthread.php?t=1466021](http://ubuntuforums.org/showthread.php?t=1466021)

---

### Post by blaad on 2010-05-04
ok, brb i will boot into the unetbootin live session and post the boot script

---

### Post by wilee-nilee on 2010-05-04
A W7 install DVD will work or the recovery link to get to the command section to put the commands in, I think your in good shape here we just want to make sure.

So when you get the script paste it to the thread highlight it then click on the # in the upper bar this will put it in a scrolling display easier to read.

---

### Post by blaad on 2010-05-04
I cant get it to activate it. I moved the file to desktop for convenience. I then pasted in: 
 
sudo bash ~/Desktop/boot_info_script*.sh 
 
I tried all sorts of variations, nothing is working..
 
I will try the commands posted in that thread you linked. brb.

---

### Post by C.S.Cameron on 2010-05-04
When doing a Full Ubuntu install to flash disk I always recommend unplugging the internal drives first.
With XP and I assume Windows Seven you need to use your install disk then go to recovery console and type "fixmbr".

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

If you are duel booting Win 7 and Ubuntu you should only need to reinstall grub.
Alternately you could install Ubuntu for dual boot and this should fix things.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> I cant get it to activate it. I moved the file to desktop for convenience. I then pasted in: 
 
sudo bash ~/Desktop/boot_info_script*.sh 
 
I tried all sorts of variations, nothing is working..
 
I will try the commands posted in that thread you linked. brb.

I would look to see if in the multi attempts that it did appear in where ever the download was when you ran the bash script. Also you can just delete the download do it again put it on the desktop and run the script as you have it posted it looks correct.
sudo bash ~/Desktop/boot_info_script*.sh

It is not real tough and I have never had it not work for myself, but anything is possible. You could also in the live cd terminal run.
sudo fdisk -l and post that, l=a small case L

---

### Post by blaad on 2010-05-04
um using the method from the thread you posted worked. everything is working now. thank you so much for your help. It is extremely appreciated.

---

### Post by wilee-nilee on 2010-05-04
Actually there is one missing link here is what version of windows are you using if it is XP as Cameron suggests, will be different commands.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> um using the method from the thread you posted worked. everything is working now. thank you so much for your help. It is extremely appreciated.

Hey oldfred is the one we all thank and the others on the forum who know this stuff, I'm just the conduit. ;)

@Cameron, thanks for posting as I had not isolated the OS.

Also if you want a live running Ubuntu on a thumb just repost and I will give you the lowdown, or another will.

---

### Post by blaad on 2010-05-04
title of my thread is "** installed ubuntu to flash drive, to boot win 7 I must have drive plugged in. help**"
 
so I am using windows 7, and the commands from that thread worked like a charm

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> title of my thread is "** installed ubuntu to flash drive, to boot win 7 I must have drive plugged in. help**"
 
so I am using windows 7, and the commands from that thread worked like a charm

Oh yes I guess it is, Doh.

---

### Post by blaad on 2010-05-04
Just wondering, does anyone have a really good guide to properly installing ubuntu onto a flash stick, so that preferences and such can be saved? If you use unetbootin, every restart preferences are erased.
 
That is what I was attempting to do here.. but clearly failed

---

### Post by blaad on 2010-05-04
um can you guys tell me if my plan will work?
 
Im going to burn the iso onto a dvd and then unhook my hard drive and boot from the cd. then i will stick in the usb stick and install to the usb stick.
 
with this work as a full install? or will my preferences be lost every time I restart?

---

### Post by wilee-nilee on 2010-05-04
Hold on I will find you the information on a full install to the thumb or a persistent/saves information install. How big is the thumb? actually you don't have to remove any hard drives, it is just putting grub on the thumb, not the hard drive which is what happened the 1st time.

So a full install to the thumb will run the fastest, but I have heard that it will only run on the computer it is built on. A Iso loaded thumb like the unetbootin will run on any computer. Hopefully others can confirm the full install booting information.

---

### Post by blaad on 2010-05-04
its a 4gb usb stick. my goal is to have it perform on multiple systems rather than just my own, I assumed it would be possible.. i hope so too

---

### Post by wilee-nilee on 2010-05-04
So here is a link to how to have a persistent install.
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Personally I like the full install instead but I only use my thumbs for testing operating systems.

---

### Post by blaad on 2010-05-04
so is that pretty much ubuntu? or is it different in many ways?

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> its a 4gb usb stick. my goal is to have it perform on multiple systems rather than just my own, I assumed it would be possible.. i hope so too

If you don't have access to the Ubuntu ISO disc loader the link is for a windows friendly loader just click on the link to on the link page and enjoy. This is just like a unetbootin load except with the saving of what you have done.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> so is that pretty much ubuntu? or is it different in many ways?

I'm not sure what your question is.

---

### Post by blaad on 2010-05-04
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)
 
would this method allow the ubuntu on the flash stick to work on multiple systems or only my own?

---

### Post by blaad on 2010-05-04
> **wilee-nilee said:**
> I'm not sure what your question is.
 
I was just asking if the pendrive linux is pretty much the same OS as ubuntu, or if there are many differences, such as looks or features.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> I was just asking if the pendrive linux is pretty much the same OS as ubuntu, or if there are many differences, such as looks or features.

Yes the pendrivelinux method will boot on any computer. Also it is just the loader although there are all kinds of links to all the different operating systems that they have set up to run. If you want Lucid get the daily release ISO it will have everything updated until today, so you don't have to due a bunch of updating.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

So I hope this makes sense.

---

### Post by wilee-nilee on 2010-05-04
I am on my W7 set up now checking out this loader as I know how to get a persistent set up without it. If you want to use a downloaded ISO just scroll down to the bottom of the list on the loader to try some other live Linux CD. Just used it seems okay.

---

### Post by blaad on 2010-05-04
ah im sorry for the confusion, I assumed pendrive linux was its own OS for a flash stick. I should of read a little further. Thus causing your confusion by asking stupid questions, as im sure you can tell, I am not at all experienced with linux.
 
when the usb installer says to select a persistance option, what is it asking me?
 
I have 
 
          no persistence
          1gb casper-RW
          2gb casper-RW
          3gb casper-RW
          4gb casper-RW
 
What do you recommend I set it to?

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> ah im sorry for the confusion, I assumed pendrive linux was its own OS for a flash stick. I should of read a little further. Thus causing your confusion by asking stupid questions, as im sure you can tell, I am not at all experienced with linux.
 
when the usb installer says to select a persistance option, what is it asking me?
 
I have 
 
          no persistence
          1gb casper-RW
          2gb casper-RW
          3gb casper-RW
          4gb casper-RW
 
What do you recommend I set it to?

Since it is a 4 gig thumb I would try the 4 gig 1st I think it is set up to recognize the thumb. The ISO is only 700mb so the rest is for the persistent basically. Hey there are no stupid questions, and today now you know how to reload W7's boot-loader and shortly how to load a thumb in this manner. ;)

---

### Post by blaad on 2010-05-04
4gb wont work and neither will 3... says i only have 3590mb of 3772mb..
 
when I try to format it it will only give me the option of 3.51gb not sure what the problem is, it is a 4gb stick, I dont remember ever only having 3.5gb to work with..

---

### Post by wilee-nilee on 2010-05-04
So I noticed that when I used my daily download that it doesn't show the persistent dropdown, but there are Lucid links on pendrivelinux and I suspect that will work. Also if you had a bigger thumb it can be modified to have a bigger then 4 gig persistent setup.

The daily ISO I have is a rsync ISO, this is a way of having the daily updates without downloading the whole ISO every time. This is not applicable on your thumb other then I suspect that the ISO I have has some extra stuff that is blocking the persistent part, so my experience may not be the same as a standard daily live cd.

---

### Post by blaad on 2010-05-04
I put it on my other 4gb usb stick.. which oddly enough has 3.72gb out of 4gb free. I understand some of it is system reserve, but I am unsure of why the other one is 3.51 out of 4gb free.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> I put it on my other 4gb usb stick.. which oddly enough has 3.72gb out of 4gb free. I understand some of it is system reserve, but I am unsure of why the other one is 3.51 out of 4gb free.

All thumbs come with some sort of firmware, I think that is what your seeing, and the way gigs are measured. I have a external hard drive that claims to be 320 gigs but shows less then that on the computer.

---

### Post by blaad on 2010-05-04
now this persistance, does this give me extra room when i boot into ubuntu? or what exactly is the purpose of setting the persistance to high as apposed to 1gb?
 
I will have to read your response in the morning, where I live its about 2 am now and I gotta get some sleep.
 
thank you for assisting me through my terribly naive and what i believe to be intolerantly stupid troubles. I appreciate every bit of assistance you have given me.

---

### Post by wilee-nilee on 2010-05-04
> **blaad said:**
> now this persistence, does this give me extra room when i boot into Ubuntu? or what exactly is the purpose of setting the persistence to high as apposed to 1gb?
 
I will have to read your response in the morning, where I live its about 2 am now and I gotta get some sleep.
 
thank you for assisting me through my terribly naive and what i believe to be intolerantly stupid troubles. I appreciate every bit of assistance you have given me.

The persistence is for having an area to save stuff to, like updates and upgrades, any downloads....etc. 

When a person wants more then the maximum of 4 gigs allowed a second partition is made=ext2 named casper-rw. Then you remove the casper-rw from the home file of the ISO loaded CD. You can't see the extra space as a partition in the side bar at home but if you go to the menu-accessories-disc usage analyzer it will show you the space you have. 

So only one gig of persistence could work it just depends what your use for it is. It would be difficult to add any media codecs and other tweaks to make it a bootable thumb that will play a DVD for example, 1 gig persistent is cutting it close, but okay for just having it save like the basic system like bookmarks in FF.

---

