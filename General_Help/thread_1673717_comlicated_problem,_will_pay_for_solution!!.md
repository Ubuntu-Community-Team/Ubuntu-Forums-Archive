---
title: "comlicated problem, will pay for solution!!"
date: 2011-01-22
forum: General Help
---

### Post by adamjomha on 2011-01-22
long story short, i have had my setup since 10.10 came out so i have lots of data i cannot lose..

i was installing zero ballistics and it requires some libraries that come with the bz2 so i unpacked and LD_LIBRARY_PATH=myhomefolder/Downloads/zb_20/shared_libs so it could find the libraries.
that didnt work so i just cp'd the directory to /lib and made sure it wouldnt overwrite any existing files. the instant i ran the command my window manager crashed and i couldnt open terminal with ctrl alt t or anything.. i just had a screen with my dock and background image
so i did a reboot (bad idea) and surely now it hangs at boot saying 

```
/usr/sbin/winbindd: error while loading shared libraries: libz.so.1: wrong ELF class: ELFCLASS32
```

heres the image 
[IMG]http://img338.imageshack.us/img338/4757/screenod.jpg[/IMG]

if it helps, im on 10.10 with kernel 2.6.35-24-generic

and heres what happens when i try to boot a live disc:

```
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)on //filesystem.squashfs 
```

NOTE - this happened since i had the computer not just since the lib issue.

if anyone can find a solution to this without somehow backing up data and re installing, then i will reward you over paypal that is how desperate i am! 

-adam

---

### Post by djeikyb on 2011-01-22
(1) What computer is it? Built it yourself? Bought it from Dell? What are the specs?

(2) If I understand correctly, the 10.10 livecd has never worked for you. How then did you install Ubuntu?

(3) What happens when you try to boot into a safe mode? There should be several entries in your boot menu, at least one of them should be marked safe mode.

(4) The admins prolly frown on bounties (?), but if I can help you, donate to my choice of charity instead.

(5) Instant messaging might be helpful if you have time to work on it right now. PM me your username if you'd like to take this to AIM or Skype. We'll of course keep this thread updated for posterity.

---

### Post by tigerstripedcat on 2011-01-22
1) Why don't you have a backup!?
2) Why don't you have a backup!?
3) Your data is probably fine, but get yourself a external hard drive, usb drive or something, boot with a live cd and BACKUP your data before you make anything worse.

The live cd you are using must be bad, get another.  You should be able to boot with it as long as there is no hardware problem, but since you were messing with libraries, it shouldn't be.  Are you using a custom filesystem?

---

### Post by adamjomha on 2011-01-22
1. its a sony vaio vpceb27fd ati radeon card and i5 processor and its 64 bit

2. i tried that wubi (wibu?) a while ago and it caused grub problems so i formatted and re installed with the live cd but i mean since the install i havent been able to boot it, i can boot knoppix or dsl fine just not ubuntu

3. it does the same in safe mode, previous kernels same thing as well

4. i thought that might be an issue so im cool for the charity idea

and most important i cant backup because my home folder is encrypted so when i access it on dsl or knoppix live i just get two .desktop files called readme and 'how to access your private desktop" or something similar

---

### Post by tcrapper on 2011-01-22
I just downloaded that game, and looked at the shared libs, and it comes with libz.so.1. So the system is trying to load the incorrect libz library. You must of accidentally over written the system libz.so.1 file. If you can get a live cd of ubuntu working, you could copy the live cd /lib/libz.so.1 to your hard drives lib folder.

---

### Post by tigerstripedcat on 2011-01-22
[QUOTE=adamj
and most important i cant backup because my home folder is encrypted so when i access it on dsl or knoppix live i just get two .desktop files called readme and 'how to access your private desktop" or something similar[/QUOTE]

Well I guess you've learned to keep a running backup then?  I'm not completely sure, but if it is only the home folder, you should have a file somewhere that you can copy so that you can decrypt later if you need to.

[http://askubuntu.com/questions/13879/encrypted-system-backup](http://askubuntu.com/questions/13879/encrypted-system-backup)

[http://ubuntuforums.org/showthread.php?t=1406122](http://ubuntuforums.org/showthread.php?t=1406122)

---

### Post by Vaphell on 2011-01-22
try this
[http://ubuntuforums.org/showthread.php?t=1580999](http://ubuntuforums.org/showthread.php?t=1580999)

---

### Post by adamjomha on 2011-01-22
thank you everyone, im gonna go re burn another ubuntu live since mine could just be a bad copy and try the libz.so.1, im not sure what to expect tho because before i shut down for the first time after the crash i opened ubuntu software center and installed the libz bundle in hopes to overwrite the new bad file but i had no luck. ill report back in a little once this is burned and downloaded!

---

### Post by djeikyb on 2011-01-22
(1) I don't care what kind of encryption you've got on your home folder, if data exists on the hard drive, you can back it up. Granted, file level backup might be impeded, but you can always use [dd](http://www.linuxcommand.org/man_pages/dd1.html).

(2) The other folks commenting are absolutely right. Your live cd is prolly bad. Download the iso, run a md5sum check, burn the cd, run a check on the cd, then try booting. Let us know if this succeeds or fails.

(3) Along the same theme as 2, you prolly borked libz.so.1, and you need to replace it with a good version. Actually, forget your livecd problems, download a good copy of the library, boot with dsl or whatever, copy it over, and reboot. I'd put my money on this solution.

---

### Post by tigerstripedcat on 2011-01-22
Check the download with:

[http://www.linuxfortravelers.com/check-the-ubuntu-file-for-errors](http://www.linuxfortravelers.com/check-the-ubuntu-file-for-errors)

And install to usb if possible as usbs cant get scratches.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by djeikyb on 2011-01-22
I think you can get your proper lib back here (download, extract, etc):
[http://packages.ubuntu.com/maverick/zlib1g](http://packages.ubuntu.com/maverick/zlib1g)

EDIT:
Aha! I found it, here are some steps if you need them.

1a. For 32bit: [http://mirrors.easynews.com/linux/ubuntu//pool/main/z/zlib/zlib1g_1.2.3.4.dfsg-3ubuntu1_i386.deb](http://mirrors.easynews.com/linux/ubuntu//pool/main/z/zlib/zlib1g_1.2.3.4.dfsg-3ubuntu1_i386.deb)

1b. For 64bit: [http://mirrors.easynews.com/linux/ubuntu//pool/main/z/zlib/zlib1g_1.2.3.4.dfsg-3ubuntu1_amd64.deb](http://mirrors.easynews.com/linux/ubuntu//pool/main/z/zlib/zlib1g_1.2.3.4.dfsg-3ubuntu1_amd64.deb)

2. Rip apart the deb. Run ```
ar vx  zlib1g_1.2.3.4*.deb
tar -xvzf data.tar.gz
cp ./lib/libz* /lib/
```

---

### Post by adamjomha on 2011-01-22
ahhh thank you so much for the library link, i could not find it anywhere (bad night for me and google.. hence the hour long delay) 

3 live cds later and no dice, so im going to try out the bootable usb program that tigerstripedcat linked and go from there now. 

if i could express how much i hate booting into windows..

---

### Post by djeikyb on 2011-01-22
Why don't use a different live cd? You said dsl works, use that. Mount your file system, replace the library, and you should be golden, no?

---

### Post by tigerstripedcat on 2011-01-22
So why aren't the live cd's working? Are they giving you the same error message?

---

### Post by LewRockwellFAN on 2011-01-23
> **adamjomha said:**
> 3 live cds later and no dice, . . . 
Does that mean you verified the checksum (md5 or other) on an iso, burned 3 CDs from it, verified the checksum on the CDs (I mean on the actual files on the actual round plastic artifacts, not the iso) and you had the same problem with all of them? Cause if you're sure of that I sure would have lost money if anyone had wanted to bet with me. Did you try any of these CDs in another machine?

---

### Post by adamjomha on 2011-01-23
no but when i tried on a live ubuntu it would say 

```
myname-vpceb27fd login: (id type xinit or anything really) 
init: tty1 main process (1678) killed by SEGV signal
init: tty1 main process ended, respawning

myname-vpceb27fd login: (again, i can type anything here and its the same output) 
init: tty1 main process (1678) killed by SEGV signal
init: tty1 main process ended, respawning

..repeat..

```

so i booted the same iso that would fail on cds using a flash drive, unpacked the deb and copied the libz files to my harddrives /usr/lib and when i boot i no longer get the "elf class 32" error, but it hangs at the 'webcamstudio' part and wont go any further..

[IMG]http://img257.imageshack.us/img257/3906/ubuntuusertwet.jpg[/IMG]

what is going on!:confused::mad:

---

### Post by djeikyb on 2011-01-23
I'm not sure this is a good idea, but.. Maybe you borked some other libs too. Try replacing your current /lib with the one from the liveusb. Probably you should back up /lib first (cp /lib /lib.bkp).

Another option would be to (back up /lib first..) copy the contents of liveusb /lib to your current lib. This way you keep any extra libs you might have/need while replacing the system libs with known good ones.

With both options, there is the danger that your updated system uses updated libs, and the liveusb libs are incompatible. You maybe could minimise this danger by running the updates on the liveusb first. Hopefully you keep your system updated!

---

### Post by adamjomha on 2011-01-23
possibly but i was looking through the live lib and it had no libz* files to start with.. i just dont understand. it cant be a webcam program causing it to hang that just isnt right. so why wouldnt it show any other error message..

i wish there was a restore to date option like in windows.. *gets struck by lightning*

---

### Post by djeikyb on 2011-01-23
Heh. You've always had the option to back up.. But that's neither here nor now. Can you go back into your live environment and look through the system logs? Ubuntu's boot screen is utter sh*te (really frustrates me) but the useful information should be tucked away in /var/log/[boot.log|syslog|dmesg]. If you attach them here or pm them to me or something I'd be happy to look through them.

Btw, the webcam thingy isn't to blame. Notice it checks out okay, and boot hangs after that. It's a long shot, but maybe try flipping through the other terminals (alt-f1, alt-f2, etc), there might be a secondary information screen.

---

### Post by adamjomha on 2011-01-23
will do! it'll be up in a few minutes.

ive used different distros of linux for the last 5 or 6 years and never knew i had f1 and f2 screens on boot.. definitely going to try it out!

---

### Post by djeikyb on 2011-01-23
Not..necessarily during the boot process, but eventually the script that activates /etc/init/tty*conf is run, and voila!: virtual terminals. Also, the boot splash is usually on f7 (presumably because it's running with X), and I think there might be extra info on f8. With Ubuntu, I'm not clear on the timing or the reasoning behind what goes where.

---

### Post by adamjomha on 2011-01-23
well that makes sense then

**[COLOR=Red][here are the logs!]("http://rapidshare.com/files/444067030/logs.tar.gz")[/COLOR]**
i went over quickly and i can assure you regardless of the logs i am not overheating and the computer is plugged in so it has plenty of power..

---

### Post by tigerstripedcat on 2011-01-23
A few things you can try:

1) I think grub has a 'minimal' option to boot up without loading much, that may bypass the problem.
2) I think you can selectively load the init scripts, when you boot but I don't know how to do it on the modern ubuntu distros. Does it give you the option to press any keys to selectively load different scripts?  Might need to google for it, I don't remember it being a kernel argument:

[http://superuser.com/questions/171102/skip-init-scripts-boot-freezes-at-setting-system-clock](http://superuser.com/questions/171102/skip-init-scripts-boot-freezes-at-setting-system-clock)

after you're in get a program called 'bum' (boot up manager) and start disabling startup scripts.  In particular the one you think is stuck.  You can always try and run it from "/etc/init.d/<command> start" when you are actually in gnome/kde and then see what errors it returns there.

---

### Post by adamjomha on 2011-01-23
so it still hangs of course, just doesnt say anything about the webcam script that i removed. it cant be related to that i dont think, it must be from the lib settings i overwrote.

can someone just email me their lib contents? i mean single files in the /var/lib only, not subfolders or their contents. should be undder 50 mbs. and assuming its on a fairly updated version of 10.10 i really think that would be the ultimate fix here!!

---

### Post by djeikyb on 2011-01-23
I'm on 10.04, sorry.

---

### Post by adamjomha on 2011-01-23
can someone on 10.10 message me their email so i can get this going? im desperate for a fix here i have class tomorrow!!

---

### Post by tigerstripedcat on 2011-01-23
That doesn't sound like the best way to do it.  My /dev/lib is over 800mb.  You have all the libaries with you. The live usb has all of them, and if you are looking for all updated you should be able to run the usb in 'persistent mode'


[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Just do an apt-get update && apt-get upgrade and you should have all updated, stock libraries if you want to copy them over.

---

### Post by adamjomha on 2011-01-23
so i fixed the problem and i have 3 hours to submit my paper online how haha thank you all

i did the apt-get update and upgrade that tigerstripedcat said, backed up my bad /usr/lib and /lib on my extra ext4 partition (made it for a backup, finally used it) and sudo cp -r everything from both lib folders on the live ubuntu to my old one, rebooted and cried a little at the sight of my login.

for those who helped, send me a message of your favorite charities so i can pay it forward haha this is too good.

thanks again

EDIT: how do i change to 'solved'?

---

### Post by tigerstripedcat on 2011-01-23
Oxfam America of course ;).

While you're at it look into backuppc or an online backup service like carbonite or mozy (my favorite), both of these services are completely automated so you don't have to worry about manually making backups.

---

### Post by djeikyb on 2011-01-24
Fantastic! You can click on Thread Tools up at the top to mark it as solved.

Fwiw, I wouldn't ever charge for helping people on forums. But if you had come to me IRL, I would've charged a flat $50 or so depending; mebbe more, maybe less. So if you like, donate some to MCC. I recommend their sustainable crop program in Chad, working with families to grow their own food.

**MCC:** [https://donate.mcc.org/project/chad-growing-new-crops](https://donate.mcc.org/project/chad-growing-new-crops)
**Charity rating:** [http://www.ministrywatch.com/profile/mennonite-central-committee.aspx](http://www.ministrywatch.com/profile/mennonite-central-committee.aspx)

---

