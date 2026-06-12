---
title: "back to xp"
date: 2006-02-21
forum: General Help
---

### Post by gatorgrips on 2006-02-21
I had xp on a 30 gig drive. Then i resized and installed ubuntu onto 14 of those gigs. Then i installed a video card and ubuntu won't boot. So it's out the window with ubuntu.  

I have searched the forums and google and i can't see a solution to my problem. What I want to do is just give the whole hd back to ntfs and get rid of GRUB. I tried just resizing the whole partition, but then it wouldn't load xp. So I reinstalled ubuntu and grub, and it was able to boot xp again (but not ubuntu b/c of the vid card). It seems rather pointless to have ubuntu on here JUST to load xp, and while i loved ubuntu, it's incompatibility with my video card stops me from using it. 

Is there a way to remove ubuntu and grub WITHOUT reinstalling XP?

---

### Post by akiro.yamamoto on 2006-02-21
You can download a DOS boot disk and do a 
fdisk /mbr
That will remove grub, then use something like Partition Magic to resize the NTFS partition to 30GB and delete the EXT3 (Ubuntu) Partition.
Sorry to hear you had so many problems.

---

### Post by gatorgrips on 2006-02-21
so what does fdisk/ mbr do?
i saw that in a few forums i searched, and tried it from command prompt (in xp) but it didn't do anything. i'll do it from a dos disk. 
if i make a dos boot disk (floppy) from the floppy format list in xp, will that work?

---

### Post by shade11 on 2006-02-21
It should. Just work.

---

### Post by heimo on 2006-02-21
[quote=gatorgrips]so what does fdisk/ mbr do?
i saw that in a few forums i searched, and tried it from command prompt (in xp) but it didn't do anything. i'll do it from a dos disk. 
if i make a dos boot disk (floppy) from the floppy format list in xp, will that work?[/quote]

[http://support.microsoft.com/kb/q69013/](http://support.microsoft.com/kb/q69013/)

---

### Post by bmathis on 2006-02-21
fdisk /mbr will remove the master boot record which basically stores GRUB and other boot straps. Although it should work to remove GRUB, it should, but might now restore the windows MBR. You might have to boot to an XP disk and do a "repair" on windows, this will restore the MBR as well as other files, back to default.

There's other methods, but it requires running a debug script with a dos boot disk and clearing out all of your partition table information. I've only had to do this once about 2 years ago when i was messing with Fedora 1. If it comes down to it, let me know and i will tell you how to preform the debug.

---

### Post by gatorgrips on 2006-02-21
ok tight.
so if i resize the ntfs partitition to 30 gigs and then boote the dos floppy and type fdisk/ mbr i should be good to go?

---

### Post by gatorgrips on 2006-02-21
it SHOULD just work.
that's why i'm so frustrated.
I have ubuntu working fine with a few other computers. some have onboard video and some have cards. but it won't work with this video card. (ati powercolor 9250 pci 256mb)

i'm using this comp as my gaming rig. (it's ridiculous)
i had an emachines t2825 (dvd drive and cdr drive) that fried a mobo. so i put a cognac mobo in with  a733 celeron :P. I have 2 sticks of 256mb pc100! lol. i put a cool blue led fan on the cpu and speeded the fsb to 82 (giving me a clock speed of around 900mhz, which is just enough to play call of duty 2).
anyways, i can't play cod2 without the video card, and i can't have ubutu without onboard video. 

i think, in the end, cod2 is worth more to me than ubuntu. especially on this machine. it has a clear window, blue uv ata cables, and 2 cathodes. it looks freakin awesome for how shitty it is.

thanks for all the help i'll let you know how it goes.

---

### Post by bmathis on 2006-02-21
sounds like a kick a$s system for some aged hardware ;) post back after you try the boot disk and let us know... good luck!

---

### Post by akiro.yamamoto on 2006-02-21
What was your previous card?
Did you try using the ATI set-up guide to get the card working?
Post back with any errors.

---

### Post by patrickfromspain on 2006-02-21
When you say ubuntu doesn't boot, what do you mean? I goes into a command line UI? Or not even that? Have you tried booting in safe mode?

Another thing you could do is boot from the live cd and then edit xorg.conf to use the vesa driver instead the one you were using, and then reboot to see if it works.

See you

---

### Post by megamania on 2006-02-21
[QUOTE=gatorgrips]i resized and installed ubuntu onto 14 of those gigs. Then i installed a video card and ubuntu won't boot. So it's out the window with ubuntu.  

I have searched the forums and google and i can't see a solution to my problem. [/QUOTE]
Not trying to convince you to stay with Ubuntu (why should I?), but it seems strange to me that there's no solution for you to be able to *boot*. I understand that it may be difficult/impossible to configure the card to use it at its best, but I'm sure many people here (probably not me) can help you in order to have Ubuntu boot at least in plain vga mode.

Good luck anyway!

---

### Post by gatorgrips on 2006-02-21
previously i was using onboard video, which worked fine in ubuntu. you have to know that this is a cognac mobo from an hp pavilion. 
anyway, i need the card for gaming (even though i lose sound when the fsb is above 82). as soon as i put the card in, ubuntu stopped booting. it loads everything on the usplash and then won't load login screen. 
i'm just tired of trying to work on it, and when i intalled cod2, i only had like, 1gig left on the ntfs partition. dual booting on a 30 gig hard drive is just retarded. 

also, i tried to boot from the live cd, and the same thing happens. it freezes after loading usplash stuff. maybe there's drivers or something that must be installed. whatever, i don't care. i have ubuntu on other comps, like i said.


so here's what I did(after i removed my floppy drive b/c i realized it doesn't work anymore):

I booted from windows xp pro sp2 install cd, and went to recovery mode. i logged onto the windows and typed fdisk/ mbr which was an invalid command. the computer suggested i type "help" for a list of commands, which I did. 
FIXMBR and FIXBOOT both stood out so i contemplated for a while and decided on fixmbr.
then i almost did fixboot, decided not to, and restarted.
it loaded xp, did a disk check (something about integrity) restarted once more and was fine. 
 i downloaded partition magic, resized the ntfs to 30 and all is good. 
thanks for helping. I'm gonna go play cod2 with no sound and a barely tolerable framerate. :)

---

