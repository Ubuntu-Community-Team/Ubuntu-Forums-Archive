---
title: "The quick and dirty grub 2 list edit?"
date: 2010-07-26
forum: General Help
---

### Post by justinsn95 on 2010-07-26
I just want the quickest way to remove entries in the grub 2 boot menu. Right now I have about 6 versions of ubuntu that I could boot into, and I only want one. I have two memtest86's, 2 windows vistas, and I only want one of each. And I want windows 7 to be at the top of the list. What is the quickest and easiest way to accomplish that? I read that large guide on grub two that we have around here, but it wasn't nearly as clear as I would like it to be. Any help would be greatly appreciated.

---

### Post by worksofcraft on 2010-07-26
assuming you have obsolete versions of Linux there, you need to remove them and then run "update-grub"

I use System->Administration->Synaptic Package Manager

then I searched for 2.6.32 (the main version number of my Linux kernel) The latest I have are 2.6.32-23 so all the older ones like 2.6.32-21 that have green box (meaning they are installed) I mark them for complete removal.

Then I click on the "Apply" button, after making doubly sure I not remove any of the latest one!

Then open a command prompt window and run:

sudo update-grub

it will also find your legitimate copies of winblows and make menu entries for them and should remove anything it can't find.

---

### Post by worksofcraft on 2010-07-26
Right I assume that worked... next step is to get rid of your undesired recovery options?!

So again at command prompt:

cd /etc/default
gksudo gedit grub

find the bit that says:
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

um... and then take the # off that second line (# starts a comment)

do another
sudo update-grub

reboot and with a bit of luck you will see no recovery option in your boot menu :)

---

### Post by Segofam on 2010-07-26
I am used to editing /boot/grub/grub.cfg
i.e. changing which OS I want to boot into, and deleting all those unwanted choices.

When I do the update-grub, it brings back all those annoying earlier version choices.
Is there a way to update the grub! or should I not perform the update-grub once I have edited it?

Kind regards,

Scott

---

### Post by worksofcraft on 2010-07-26
^ z0mg, no you not want to edit that file at all!
In fact I think grub.cfg has a comment to tell you it is automatically generated from configuration data elsewhere... actually they mean /etc/grub.d folder to be precise!

you see "etc" stands for "Execution Target Configuration" and update-grub processes all teh files in numerical order that it finds in grub.d folder there. Thus if you get that right then your grub.cfg will be just the ticket :)

Like say you wanna get rid of those irksome memtest entries?

Well easy peasy... simply move the file /etc/grub.d/20_memtest86+ to /var/tmp (*) and run update-grub again.

(*) Note: well move it anywhere you want really, as long as it isn't in /etc/grub.d when you run update-grub... right ;)

---

### Post by Segofam on 2010-07-26
> **worksofcraft said:**
> ^ z0mg, no you not want to edit that file at all!

OHHHHHHHHHHHHHH...

I have become quite familiar with editing the /boot/grub/grub.cfg!!!
I also wondered what would happen if I stuffed it up, so far I would say I have been lucky then :)

What you have said now makes me understand why it changes or goes back to default.

Your input has been much appreciated.

---

### Post by Segofam on 2010-07-26
> **worksofcraft said:**
> Well easy peasy... simply move the file /etc/grub.d/20_memtest86+ to /var/tmp (*) and run update-grub again.

This particular file will not cut and past from /places/home folder etc

Can it be done from the command line, and if so how?

---

### Post by worksofcraft on 2010-07-26
Oops yeah you will have to run it with appropriate privileges

I mean like

sudo mv /etc/grub.d/20* /var/tmp

Another thing Justin wanted was for his Windows to be first in the menu... so looking in /etc/grub.d you see a file called 30_os-prober that evidently will come AFTER 10_linux. All we have to do is rename it to say 08_os-prober and then run that "update-grub" again and it will make a new grub.cfg for us where these "probed" os'es (i.e. Windows) come before our Linuxes.

again at the command prompt that needs super user privilege... You see all those system files are protected from viruses and accidental user corruptions:

cd /etc/grub.d
sudo mv 30_os-prober 08_os-prober

Note: I not am quite sure how you get win 7 to precede Vista, but suspect it may simply depend on your drive partition order. On some computers the BIOS lets you prioritize that order but I also suspect you will get problems if said sequence is not the same as what grub expects, so probably not worth the risk!


p.s. "sudo" runs a command with super-user privilege providing you enter the right password of course!

---

### Post by Malta paul on 2010-07-26
An easy way is to install Ubuntu Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Then go to 'Package Cleaner' & go to clean Kernel then >clean up<
After that go to Clean Config again >clean up<

;)

---

### Post by Segofam on 2010-07-26
> **worksofcraft said:**
> 
sudo mv /etc/grub.d/20* /var/tmp


scott@scott-laptop:~$ sudo mv /etc/grub.d/20* /var/tmp
[sudo] password for scott: 
mv: cannot stat `/etc/grub.d/20*': No such file or directory
scott@scott-laptop:~$ 

Hmm..didn't work!
What's wrong with my command?

I really want to, and like using the command line, but the Ubuntu-Tweak did the job to a T.
It showed the redundant kernals and cleaned them out in a flash.

Thanks guys.

---

### Post by worksofcraft on 2010-07-26
^ That is strange about your command line. On my computer I can see  following in the /etc/grub.d folder...

ls /etc/grub.d
00_header	 10_linux	30_os-prober  README
05_debian_theme  20_memtest86+	40_custom

However, I also am delighted to learn of new ubuntu-tweak tool. Makes it even easier :)

---

### Post by Cavsfan on 2010-07-26
> **Malta paul said:**
> An easy way is to install Ubuntu Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Then go to 'Package Cleaner' & go to clean Kernel then >clean up<
After that go to Clean Config again >clean up<

;)

There is a way to have just a 2 line (or a 3 if you are dual booting) on your Grub screen.
It is a maintenance free Grub. I used to watch my list get longer every time a new kernel came out.
**Ranch Hand** (smart guy) told me how to fix it up like that.
I will try to explain how if you are interested.

---

### Post by justinsn95 on 2010-07-26
> **worksofcraft said:**
> 

Then open a command prompt window and run:

sudo update-grub


Unfortunately, this command didn't work. It just said "unrecognized command" or "command not found" or something. I know I did it right because I just copied and pasted it in the terminal. I follow you on everything else, though.

---

### Post by worksofcraft on 2010-07-27
^  Very strange your commands are not working :(
I realize you probably not need those commands after using ubuntu-tweak. However, you may want to check output of following:

$> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

$> which sudo
/usr/bin/sudo

$> which update-grub
/usr/sbin/update-grub

Originally I used
System->Administration->Computer Janitor
to clear out obsolete kernels and things but it doesn't work as well as ubuntu-tweak. Also instead of removing unwanted configuration steps from /etc/grub.d you should be able to just remove execute permissions e.g:

sudo chmod -x /etc/grub.d/20_memtest86+

... and when you run update-grub you will have no more memory tests in the menu.

Thus is easier to put them back later, but first you will need to have sudo command working to give you necessary privileges ;)

---

### Post by justinsn95 on 2010-07-27
> **worksofcraft said:**
> ^  Very strange your commands are not working :(
I realize you probably not need those commands after using ubuntu-tweak. However, you may want to check output of following:

$> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

$> which sudo
/usr/bin/sudo

$> which update-grub
/usr/sbin/update-grub

Originally I used
System->Administration->Computer Janitor
to clear out obsolete kernels and things but it doesn't work as well as ubuntu-tweak. Also instead of removing unwanted configuration steps from /etc/grub.d you should be able to just remove execute permissions e.g:

sudo chmod -x /etc/grub.d/20_memtest86+

... and when you run update-grub you will have no more memory tests in the menu.

Thus is easier to put them back later, but first you will need to have sudo command working to give you necessary privileges ;)

Im sorry but I have no idea what you just said. I'm afraid that I may be a bigger noob than you realize. When I opened the terminal, and tried to run "update-grub" it said 

"justin@justin-desktop:~$ update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: sudo apt-get install <selected package>
justin@justin-desktop:~$"

I'm afraid that I have no idea what that means either. Man I really suck at linux.

---

### Post by Cavsfan on 2010-07-27
> **justinsn95 said:**
> Im sorry but I have no idea what you just said. I'm afraid that I may be a bigger noob than you realize. When I opened the terminal, and tried to run "update-grub" it said 

"justin@justin-desktop:~$ update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: sudo apt-get install <selected package>
justin@justin-desktop:~$"

I'm afraid that I have no idea what that means either. Man I really suck at linux.

Try entering this is a terminal "grub-install -v" This will tell what version of Grub you have. I take it you are using Lucid right? 
GRUB 2 should display a version number of 1.96 or later. Legacy GRUB is version 0.97. 
Mine displays this "grub-install (GNU GRUB 1.98-1ubuntu7)"

If you need to install it (which from looking at above you do), just enter "sudo apt-get install grub-pc". See what that produces.

You should always run it as root "sudo update-grub". But, judging from the output from the command above it is not even installed.

So, I am curios as to the output of "grub-install -v". Please post that here.

---

### Post by justinsn95 on 2010-07-27
I got this when I entered that:

justin@justin-desktop:~$ grub-install -v
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: sudo apt-get install <selected package>
justin@justin-desktop:~$

---

### Post by justinsn95 on 2010-07-27
So I ran the other command that you said, this one: "sudo apt-get install grub-pc" and it eventually came up with what I have in the pic. And, I didn't know what to do lol.

---

### Post by bodhi.zazen on 2010-07-27
> **worksofcraft said:**
> ^ That is strange about your command line. On my computer I can see  following in the /etc/grub.d folder...

ls /etc/grub.d
00_header     10_linux    30_os-prober  README
05_debian_theme  20_memtest86+    40_custom

However, I also am delighted to learn of new ubuntu-tweak tool. Makes it even easier :)

This thread got off track fast ...

The "proper" way to do this, rather then editing /boot/grub/grub.cfg , is to add the menu entery you want into 

/etc/grub.d/40_custom

The syntax for a menu entry is exactly the same in grub.cfg and 40_custom

The only downside is that you will need to manually update the kernel and initrd line (in 40_custom) with kernel upgrades.

See : [Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")

---

### Post by worksofcraft on 2010-07-28
> **justinsn95 said:**
> So I ran the other command that you said, this one: "sudo apt-get install grub-pc" and it eventually came up with what I have in the pic. And, I didn't know what to do lol.

it definitely looks like your grub installation somehow got muddled up. What I really don't understand is how you got Lucid Lynx Ubuntu without the latest grub2.

However I think your best bet is to install the latest from package maintainer. Those instructions I gave earlier should then produce the nice simple boot menu you want with your Windows as first entry.

Note: If you do have more inconsistencies, then check your computer bios setup. I just noticed on mine that I can pop different disks to the top of the boot order, but grub installation would not know about that. It means you could be booting from an older installation on the wrong drive o_O

---

### Post by Cavsfan on 2010-07-28
> **bodhi.zazen said:**
> This thread got off track fast ...

The "proper" way to do this, rather then editing /boot/grub/grub.cfg , is to add the menu entery you want into 

/etc/grub.d/40_custom

The syntax for a menu entry is exactly the same in grub.cfg and 40_custom

The only downside is that you will need to manually update the kernel and initrd line (in 40_custom) with kernel upgrades.

See : [Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")

I have _never_ had to modify anything since I made my grub2 custom even when new kernel updates come along. I had help from **Ranch Hand**. 
Mine is _absolutely maintenance free_. Have not had to touch except when the grub update a few days ago came along and then did a side by side 
comparison and ended up taking the new version. I only had to make one change after that and that was which line the default OS was on.
I am working on a tutorial for how to do this just as **Ranch Hand** showed me. He definitely gets all the credit.

---

### Post by bodhi.zazen on 2010-07-28
> **Cavsfan said:**
> I have _never_ had to modify anything since I made my grub2 custom even when new kernel updates come along. I had help from **Ranch Hand**. 
Mine is _absolutely maintenance free_. Have not had to touch except when the grub update a few days ago came along and then did a side by side 
comparison and ended up taking the new version. I only had to make one change after that and that was which line the default OS was on.
I am working on a tutorial for how to do this just as **Ranch Hand** showed me. He definitely gets all the credit.

It depends on how you set up your custom menu item and the OS you are booting.

grub2 does not recognize Fedora on my system no matter what I do. It will not chainload to the fedora boot partition. So I need to manually update the menu item when I update the fedora kernel.

YMMV depending on what OS you are booting, Windows for example may well be maintenance free.

---

### Post by Cavsfan on 2010-07-28
> **bodhi.zazen said:**
> It depends on how you set up your custom menu item and the OS you are booting.

grub2 does not recognize Fedora on my system no matter what I do. It will not chainload to the fedora boot partition. So I need to manually update the menu item when I update the fedora kernel.

YMMV depending on what OS you are booting, Windows for example may well be maintenance free.

Thanks for the reply! I believe you probably have forgotten more about all of this than I will ever know!
And yes I just meant Ubuntu (Lucid) and windows 7, but it should work for xp, etc.
Ever since Ranch Hand showed me how to do this I have been totally delighted and just wanted to share this valuable knowledge.
Where would I go about putting this Grub2 tutorial?
I found a thread where someone had submitted a topic on Tutorials and Topics where ever that is and was wondering why it disappeared. 
Forum Staff **cariboo907** came along and answered him. I asked where to put my Tut. there too and hope I am not causing any heartache!
Thanks and I had to google YMMV to see what it meant! LOL I do that a lot.

---

### Post by bodhi.zazen on 2010-07-28
[QUOTE=Cavsfan;9648849]Where would I go about putting this Grub2 tutorial?/QUOTE]

Honestly, I would suggest you look at the Wiki page and add to it.

---

### Post by Cavsfan on 2010-07-28
> **bodhi.zazen said:**
> [QUOTE=Cavsfan;9648849]Where would I go about putting this Grub2 tutorial?/QUOTE]

Honestly, I would suggest you look at the Wiki page and add to it.

Thanks! I don't want to appear brain damaged, but where is the Wiki page located?
Is the Tutorials & Tips section OK? (I just found it finally)
Thanks in advance!

---

### Post by bodhi.zazen on 2010-07-28
> **Cavsfan said:**
> Thanks! I don't want to appear brain damaged, but where is the Wiki page located?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by justinsn95 on 2010-07-28
Wow ok I give up lol. This is the main problem I have with ubuntu/linux. Everything is so dang complicated. I'll just have to live with a bunch of unnecessary entries I guess. I think the grub guys could have done a much better job, though. In my humble opinion, you ought to be able to make changes to it right there at the Grub menu before you boot into an OS.

---

### Post by Cavsfan on 2010-07-28
> **justinsn95 said:**
> So I ran the other command that you said, this one: "sudo apt-get install grub-pc" and it eventually came up with what I have in the pic. And, I didn't know what to do lol.

Did you go ahead and install it? The picture you posted came to me when the grub update came down the pipe a couple of days ago.
If not, go ahead and install it as that is the first step.
When you get it installed, you should see some of the stuff in my GRUB2 link in my signature when you boot up. It should be in black or blue.

---

### Post by Cavsfan on 2010-07-28
> **justinsn95 said:**
> Wow ok I give up lol. This is the main problem I have with ubuntu/linux. Everything is so dang complicated. I'll just have to live with a bunch of unnecessary entries I guess. I think the grub guys could have done a much better job, though. In my humble opinion, you ought to be able to make changes to it right there at the Grub menu before you boot into an OS.

I agree that it is not simple, but it is doable. Maybe the link in the post above yours will help.
Or the one in my signature. It might be the same one I am not sure.
I am coming up with a how to tutorial that will help you add a custom wallpaper background 
to GRUB and make it maintenance free whether you are strictly Ubuntu or you are dual 
booting Ubuntu and Windows, such as myself.
That should help if you have grub2 installed and everything else is fine.

---

### Post by bodhi.zazen on 2010-07-28
> **justinsn95 said:**
> Wow ok I give up lol. This is the main problem I have with ubuntu/linux. Everything is so dang complicated. 


Orly ?

If Windows is so easy, just use configure the Windows boot loader. I think if you try that you will find Windows is not so easy either.

Honestly, I suggest you read the grub2 page as, IMO, you did not get the best of advice in this thread.

---

### Post by Cavsfan on 2010-07-28
I have been working on the tutorial, but I am not as fast as I used to be. I may get it posted tomorrow and I think someone will have to review it before it gets posted.
But, it will (if you are using Lucid) be totally maintenance free. You can choose to have memtest display or not. Your display will never change if you don't want it to.
And no more changing grub every time a new kernel comes in.

I will let you know when it is up. But, keep posting to this thread.
And we will try helping you get there...

---

### Post by justinsn95 on 2010-07-28
Ok I will keep at it. I don't like to fail. And, I will be very glad to read your tutorial. When you do get it finished, can you please post it in this thread?

---

### Post by worksofcraft on 2010-07-28
> **bodhi.zazen said:**
> 
Honestly, I suggest you read the grub2 page as, IMO, you did not get the best of advice in this thread.

Well Justin was asking: "I just want the quickest way to remove entries in the grub 2 boot menu... "

That involves:

1. remove obsolete operating systems
2. prevent generating recovery boot options
3. remove memtest menu entry generation
4. move os-probe for Windows before Linux

I think my posts were the appropriate ones. However evidence suggests there is something else wrong with Justin's grub installation.

---

### Post by justinsn95 on 2010-07-28
> **worksofcraft said:**
> Well Justin was asking: "I just want the quickest way to remove entries in the grub 2 boot menu... "

That involves:

1. remove obsolete operating systems
2. prevent generating recovery boot options
3. remove memtest menu entry generation
4. move os-probe for Windows before Linux

I think my posts were the appropriate ones. However evidence suggests there is something else wrong with Justin's grub installation.

Yeah it says that I have grub 1.98. I thought that 10.04 was supposed to come with grub 2.0 or higher?

---

### Post by karmila on 2010-07-29
> **worksofcraft said:**
> Well Justin was asking: "I just want the quickest way to remove entries in the grub 2 boot menu... "

That involves:

1. remove obsolete operating systems
2. prevent generating recovery boot options
3. remove memtest menu entry generation
4. move os-probe for Windows before Linux

I think my posts were the appropriate ones. However evidence suggests there is something else wrong with Justin's grub installation.

hi all!

have you consider to install [burg]("https://help.ubuntu.com/community/Burg")?

1. remove obsolete operating systems
**i usually use ubuntu tweak for this job.**
2. prevent generating recovery boot options
**with burg you just need to press F at the boot menu and burg will hide it. Simply press F again to make the recovery option back.** 
3. remove memtest menu entry generation
**by default, burg don't show memtest entry.**
4. move os-probe for Windows before Linux
**I still figured out how to do this. Because i prefer ubuntu be my default OS.**

and last, burg is pretty :D

---

### Post by ironhoof on 2010-07-29
I edit grub2 all the time now that everyone around me uses Linux. Its very easy...

go in /etc/grub.d
You can turn off the executable bit on 20_memtest86+ to make its entries go away. Then type update-grub

I would be VERY careful though but...
once you understand it, its rather fun! You can do this:

if you need to make changes to names and such

/etc/grub.d
You need to add a 06_custom file then add this:
exec tail -n +3 $0

Then add ALL the menuentry { ... } items from /boot/grub/grub.cfg

turn off the executable bits from these files:

10_Linux
30_OS-prober
20_memtest86+

Then turn the bit execute bit on 06_custom ON

THEN update-grub

when you reboot you will see the exact menu you had because the custom file will have all your old entries from grub.cfg.

Removes the ones you don't want by clearing

menuentry -------some stuff ---------- {
all
the way down
to
} <- This.
Now this item will not show up.

You can change the names of items by testing each one on boot to find out what each one does. change the names between the "quotes".

If this doesn't work there is always a way to boot in and change all the execute bits back and turning 06_custom bit off if you make a mistake.

remember to update-grub after you make any changes. 

Here is an EXAMPLE of my grub 06_custom menu:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 508ea1e9-cc39-43b6-b21b-c74fbf7ef586
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=508ea1e9-cc39-43b6-b21b-c74fbf7ef586 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 509ea1e9-cc39-45b6-b21b-c74fbf7ef586
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=509ea1e9-cc39-45b6-b21b-c74fbf7ef586 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Kubuntu" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bc16387b-c380-421c-8e3c-989a073fc46d
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=bc16387b-c380-421c-8e3c-989a073fc46d ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Kubuntu (recovery mode)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bc16387b-c380-421c-8e3c-989a073fc46d
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=bc16387b-c380-421c-8e3c-989a073fc46d ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/30_os-prober ###

---

### Post by Cavsfan on 2010-07-29
> **justinsn95 said:**
> Yeah it says that I have grub 1.98. I thought that 10.04 was supposed to come with grub 2.0 or higher?

You have the latest 1.98 is GRUB2 The output of "grub-install -v" on my pc says this:
grub-install (GNU GRUB 1.98-1ubuntu7)

I will definitely post the tutorial on here when it's up.

---

### Post by Cavsfan on 2010-07-30
Well I submitted my tutorial for making a GRUB2 bootup screen that never needs modified when a new kernel is installed.
It will always default to the desired line. And it tells how to make a custom wallpaper type background for it too.

It should work with Ubuntu versions that use GRUB2 and dual booting with Windows like mine too.
It should work for all situations as long as one OS is Ubuntu as that is the first two lines on the menu-  Ubuntu and Ubuntu Recovery Mode.
I will let you know when it comes out as it has to be reviewed by a moderator.

**Ranch Hand** showed me all of this stuff and now I am sharing what I have learned. :D
It's taken me quite a while to do, but hopefully it will be a real benefit to most people.
But, it should not take all that long to make the changes in my tutorial. 
I have to struggle a bit, but most of you can probably do this in less than a half an hour.

---

### Post by justinsn95 on 2010-07-30
> **Malta paul said:**
> An easy way is to install Ubuntu Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Then go to 'Package Cleaner' & go to clean Kernel then >clean up<
After that go to Clean Config again >clean up<

;)

Thank you very much, I found this to be invaluable. I can now just purge any that I don't like without having to hunt them all down and enter some command that I don't understand. I'd recommend this to all noobs from now on. I think it helped me easily fix about 5 different problems I was having.



> **karmila said:**
> hi all!

have you consider to install [burg]("https://help.ubuntu.com/community/Burg")?

1. remove obsolete operating systems
**i usually use ubuntu tweak for this job.**
2. prevent generating recovery boot options
**with burg you just need to press F at the boot menu and burg will hide it. Simply press F again to make the recovery option back.** 
3. remove memtest menu entry generation
**by default, burg don't show memtest entry.**
4. move os-probe for Windows before Linux
**I still figured out how to do this. Because i prefer ubuntu be my default OS.**

and last, burg is pretty :D

I installed BURG using the instructions in the link you provided. But er.. where did it go? I can't seem to find BURG anywhere on my computer. I need to be able to open it so I can use it.

---

### Post by Cavsfan on 2010-08-02
If anyone is interested in having a maintenance free grub2 screen whether you dual boot windows or just use Ubuntu here it is

My tutorial:
[U][http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)
[/U]This will work as long as you have GRUB2 as your menu.

You won't have to mess with anything when a new kernel is installed like you do now.

---

### Post by balise on 2010-10-15
[QUOTE=ironhoof;9651375]I edit grub2 all the time now that everyone around me uses Linux. Its very easy...

Etc., etc.

Thanks very much Ironhoof.  This is what I wanted.  Darned if I know why these developers keep changing things that work Ok, but don't address new hardware, etc.  No one is thinking of Linux challenging Windows anymore.  Not seriously anyhow.

---

