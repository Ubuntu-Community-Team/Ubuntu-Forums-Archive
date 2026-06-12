---
title: "Trying to expand linux experience, need help with some simple stuff..."
date: 2010-08-23
forum: General Help
---

### Post by sytheii on 2010-08-23
*If anyone feels this thread belongs elsewhere on this forum, please do not hesitate to move it, I just wasn't sure where to post, and figured "general help" would be alright. *

Please forgive me if this is the kind of thing that you see all the time, but I have been trying to find answers to my questions and I am really getting to the end of my rope. If anyone can help in the slightest way, I would really appreciate it.

I have been using Ubuntu on and off for 2 years, and I really like the experience. As it stands, Ubuntu really is the easiest way to get into linux seeing as these forums and others like it really have almost all questions answered in one form or another, so a quick search usually substitutes needing to post as it has already been asked before.

I have been expanding my linux experience into other distros. I recently installed SliTaz onto a dell laptop that was given to me, and so far I've been having fun. I realised when I did this, that I also had a VERY old laptop, that is super tiny, and I thought what a cool project to install another distro onto that one.

I figured after looking around that Damn Small Linux would be a good candidate....But I have hit a wall in trying to figure out how to get it onto the computer.

Long story short, I've tried a bunch of methods, but invariably hit a wall that I cannot proceed from. The last 3 methods I have tried I get stuck on some little thing I cant seem to find clarification for. And the real kicker is, for some god-awful reason, the board @ damn small linux has some annoying bug where i can register for their forum, but I cannot validate my registration for some odd reason. I tried to look for help there first, even tried 2 email addresses to accomplish registration, but to no avail :(

The laptop only has a external floppy, and a PCMCIA Ethernet adapter. While trying different methods, i was able to get online to get resources with win95, but had major problems with simply just browsing around...and after my most recent attempt, something, I don't know what, happened so that no matter what trick I do, I cannot get it to connect to the Internet any more. I aquired an old usb floppy drive today, so now new options open up since I can use it with my home box...but here is a breakdown of what I have tried.

The first method I tried was a "poorman's" install Floppy with netcard...

[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29")

I was able to make a boot disk with tomsrtbt, as well as the 2 disc BG rescue boot disk, but when i try toms disk, when i get to running ifconfig...i get this message:

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LPBACK RUNNING MTU:3924 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

i cannot seem to figure out how to proceed from here using this method.

I next tried the BG rescue boot disks, and after i load the first one, it goes through its processes fine, and then the last line to display is:

VFS: Insert inittar floppy disk to be loaded into RAM disk and press ENTER

after which I am not sure what to do, because no-one went into detail concerning how to proceed...I tried putting in the second part of the BG Rescue disk, but after i do that and hit enter, it just continually spins the floppy drive and essentially just stays that way...so i figure i'm doing something wrong there.

Then I tried the ultra-uber-long method here called, Floppy Only Install (No Netcard, Linux Only)

[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_%28No_Netcard,_Linux_Only%29](http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_%28No_Netcard,_Linux_Only%29)

The instructions seem simple enough, untill i get to;

You will need:
...

    * A copy of the script from [http://www.fpx.de/fp/Software/fsplit](http://www.fpx.de/fp/Software/fsplit) on a floppy.

...

I don't know how to put a copy of that script on a floppy :( I also don't know how to " Copy the fsplit script onto your host box and do the following mode change.," or how to "Run fsplit on the iso and cut it into 1.4mb chunks. "

I'm not a dolt, but I am somewhat ignorant about some of these things, but I am assuming that these sort of things will be really easy for most Linux users out there...

So what I am hoping, is that someone who has taken the time to read this, will either point me in the right direction with which method to continue with, or at least provide me with some rudimentary instructions on how to do, what I am assuming, is really simple stuff.

Thank you to anyone who responds in advance.

Ian.

---

### Post by gzarkadas on 2010-08-23
The documentation there is not what I would call "user friendly"; they assume quite a level of experience (and experimentation) from the user, IMHO. I would suggest to use an entirely different approach, which although seems more complex it is actually easier to perform and will finish the installation faster than having to use 60 floppies or figuring out how to manually setup your network:

[LIST]
[*]Detach the laptop's hard disk and plug it onto a working laptop with a cdrom as a second hard drive.
[*]Then follow the instructions for [installing DSL to a usb pen]("http://www.damnsmalllinux.org/wiki/index.php/Install_to_USB_From_within_Linux").
[/LIST]
It is much faster to write directly to hard disk, and also the doc page is much more detailed than the other options. When you are finished, put the hard disk back to the old laptop.

---

### Post by sytheii on 2010-08-23
> **gzarkadas said:**
> The documentation there is not what I would call "user friendly"; they assume quite a level of experience (and experimentation) from the user, IMHO. I would suggest to use an entirely different approach, which although seems more complex it is actually easier to perform and will finish the installation faster than having to use 60 floppies or figuring out how to manually setup your network:

[LIST]
[*]Detach the laptop's hard disk and plug it onto a working laptop with a cdrom as a second hard drive.
[*]Then follow the instructions for [installing DSL to a usb pen]("http://www.damnsmalllinux.org/wiki/index.php/Install_to_USB_From_within_Linux").
[/LIST]
It is much faster to write directly to hard disk, and also the doc page is much more detailed than the other options. When you are finished, put the hard disk back to the old laptop.

I can install dsl to a pen drive no problem...And honestly, unless I'm missing something :scratches head: I don't think that will help seeing as the target laptop does not have usb...

Also, I'm not sure about taking out the hard drive from this little laptop...i dont even know if it will link up with the only other laptop I have... for refrence, its an old hitachi laptop my mom uh...stole...when she quit working for the city. I've had in in a bag forever and just decided to do this for shits and giggles. Here is a pic for refrence... it's an old hitachi visionbook traveler 3000! sounds cool huh?

[IMG]http://i20.photobucket.com/albums/b210/sytheii/hitachi.jpg[/IMG]

Ok wait, thinking while writing...i take the hd out of target laptop, put it into my other laptop (if possible,) then boot from usb flash drive that has DSL live image on it...then install to hd, remove that hd, and put it back into target laptop? What then is important about having quote "a cdrom as a second hard drive?"

---

### Post by sytheii on 2010-08-24
Ok, well, I opened up the laptop and raised the keyboard...unfortunately it looks like the hard drive is underneath the motherboard...and I have no idea how to *exactly* remove it, nor do I know what random unscrewing will result in...so I am kind of loathe to try.

Can anyone chime in on one of the other methods I mention in my thread? any help in those areas?

---

### Post by gzarkadas on 2010-08-24
The phrase you mention was intended to be read as "plug it onto _a working laptop with a cdrom_ [,] as a second hard drive" (sorry, I missed a comma :)). You need the cdrom for the distro's livecd, in order to make a standard livecd install (assuming DSL has a livecd).  

If one doesn't feel confident for doing this, an even simpler alternative to ensure the hdd of the working system will not be touched, is to take it off too and put the hard disk from the want-to-install-DSL laptop in its place. Then do a standard install. Afterwards, put the hard disks in their original places.

Now, the problem is that there is no dissasembly guide for your traveler laptop; and [the only one I found]("http://boole.stanford.edu/travdisk.html") suggests that getting to the hard drive is quite involved (you 'll have to take all the laptop parts apart). Unless you are quite handy in such jobs, it is better to change direction and try to make a [floppy only install with netcard]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29").

This brings us to your original post. Now, regarding this:

Tomsbtrt does not seem to recognise your card (thus you have no interface except lo). So, try to repeat the process with BG rescue, ensuring first that you have a set of floppies with no defects (I believe that the second one you tried had one). If you manage to get along, the next step is to test / configure your network card, as the DSL guide says.

---

### Post by sytheii on 2010-08-24
Hehe, 

Your first point still confuses the **** out of me :0) 

Secondly, yes, it looks like a pita to take out the HD, and often times when i do that sort of thing, i don't get it right on the first go, and I would rather avoid that happening as this is mainly me ****'n around as opposed to getting something done that *needs* to be done :)

I'm surprised to found *a *manual :) I couldn't find anything conclusive about that model whatsoever. Where did you find it?

Lastly, thank you! So Toms doesn't seem to recognize my card...that is why lo pops up? can you give me a definition of lo?, ie, lo=loopback? i still don't know what that is.

So you think my bg floppies might have been bad...well, considering that i downloaded them from this dinky-rinky-do laptop and made them there...i'm not suprised :) 

What I really want to know about BG...is whether or not that message I got when the first disk ran its course is a message to insert the second bg disk, or something else. You *suspect* that i might have made a bad floppy...and so I will try it again. Wish me luck, and thank you again, will post up result.

---

### Post by sytheii on 2010-08-24
Nope, nothing new, but i did forget to include the last line that pops up after it says

VFS: Insert inittar floppy disk to be loaded into RAM disk and press ENTER

i put in disk 2, hit enter, then it spins up the floppy disk, and says,

VFS: Mounted root (tmpfs filesystem).

and thats it...nothing new after that point. :(

---

### Post by sytheii on 2010-08-24
Ok, so i tried to use Hal 91...saw a link from BG to it, 

[http://chris.silmor.de/hal91/](http://chris.silmor.de/hal91/)

and i get it up and running, but then i notice " Limited support for ethernet cards (NE2000 only) is also included. Support for scsi adapters, parallel zip drive and other ethernet cards is possible by loading kernel modules from an optional package (see below)."

I go below and i read this, " The following packages do not fit on the disk. However, after booting HAL91, they can be unpacked in the /bin directory with the command tar xzf package.tgz"

I really don't understand why people dont elaborate just a little bit more on little things like this...I'm sure its not that hard, I just dont know/cant find instructions on how to perform simply fraking commands. :(

If anyone can chime in, please lend me a hand.

---

### Post by gzarkadas on 2010-08-24
What is the memory of your hitatchi notebook? BG Resque needs 20 MB of memory in order to work; maybe you run out of memory when the 2nd disk is loading its data to memory.

>  after booting HAL91, they can be unpacked in the /bin directory with the command tar xzf package.tgz"

This means that after HAL91 has booted and you are at the command prompt, you can eject the initial boot disk, enter the add-on disk with the <package>.tgz file  and type the command. You need to know where the floppy is mounted; it will be either in /floppy or somewhere inside /mnt. Do a ```
cd / && ls
``` to find out. Then ```
cd /bin && tar xvf /floppy/<package>.tgz
``` (or another path if floppy is not mounted on /floppy).

You will probably need the [kernel modules addon]("http://chris.silmor.de/hal91/modules-hal91.tgz").

lo is indeed the loopback interface. To know that your card has a driver and is recognised, you should read at the output of `ifconfig' a section that starts with "eth0".

At the moment you need to find a floppy distro that can boot at your machine **and** can recognise your pcmcia adapter. You could try [blueflops]("http://blueflops.sourceforge.net/") also; its feature set fits with your hardware and it has a recent kernel which supports many pcmcia cards.

If you can't find one, then the only solution that remains is the pure floppy install.

---

### Post by sytheii on 2010-08-24
Laptop has 24 mb of RAM i believe. Maybe 28...im not sure.

OK, after booting up HAL91, i did 

cd / && ls, and got

total 25
2 bin/            1 floppy/           1 linuxrc*           0 proc/
3 dev/           2 hal91.ini*      12 lost+found/     ` tmp/
1 etc/            1 lib/                1 mnt/        

I then tried this line...

cd /bin && tar xvf /flippy/net.tgz   (I renamed the modules.tgz file )

and then I got

tar: Cannot open /floppy/net.tgx: No such file or directory.

It could be that the method i used to put that file on the floppy disk was bad, i used that rawwrite program to do it...now that i think about it, it seems silly to do so. I will boot up in ubuntu to simply "copy" that file over and see if it works better when i do that.

Also, I tried blueflops, and the boot part goes splendidly, but when it comes time to do a setup, under network setup, after probing, it does not automatically find my network card...so i took a look at the list, and nothing looks similar to the card i have. The card I have for this laptop is a 3com Megahertz Lan+modem...

[IMG]http://i20.photobucket.com/albums/b210/sytheii/card1.jpg[/IMG]

[IMG]http://i20.photobucket.com/albums/b210/sytheii/card2.jpg[/IMG]

[IMG]http://i20.photobucket.com/albums/b210/sytheii/card3.jpg[/IMG]

I have never seen anything like it except on this small little laptop. Perhaps that is the problem? I have another card I could use, the one from my other usable laptop....but i don't want to have to swap them out (if it would work) let alone buy another card for this little box...kind of wanted to just use it as is, not spend any money on this experiment.

---

### Post by sytheii on 2010-08-24
Well this is really frustrating. Now for some reason ubuntu isn't recognising my floppy drive :( wahhh. 

I had edited my modules file in /etc, to read

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

floppy
lp
rtc

And that had seemed to make ubuntu recognize it as a floppy and put in in computer in places...but now i have this in places instead:

Shuttle Technology inc. E-USB Bridge (with a little usb icon)

Tried unplugging it, and plugging back in...but that does not seem to help either. Very annoying.

---

### Post by gzarkadas on 2010-08-24
First check the spelling of your tar command; the error text you present indicates a possible mispelling of the tar file (.tgx instead of the correct .tgz) and this can certainly prevent tar from finding the file.

Also check whether you can write to the device in ubuntu even if it appears as a usb drive; put a floppy in and try to copy something to the drive.

According to [http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS) :
>     [3c574_cs driver] [x86,ppc]
    3Com Megahertz 3CCFEM556B, 3C3FEM556C
your card is supported. However pcmcia-cs is not used by the 2.6. kernels, so you 'll probably need a distro with a 2.4 kernel (unless the driver has been ported to 2.6 which is something I don't know). Check [this thread]("http://ubuntuforums.org/showthread.php?t=405666") also, it seems relevant.

---

### Post by sytheii on 2010-08-24
> **gzarkadas said:**
> First check the spelling of your tar command; the error text you present indicates a possible mispelling of the tar file (.tgx instead of the correct .tgz) and this can certainly prevent tar from finding the file.

Also check whether you can write to the device in ubuntu even if it appears as a usb drive; put a floppy in and try to copy something to the drive.

According to [http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS) :
your card is supported. However pcmcia-cs is not used by the 2.6. kernels, so you 'll probably need a distro with a 2.4 kernel (unless the driver has been ported to 2.6 which is something I don't know). Check [this thread]("http://ubuntuforums.org/showthread.php?t=405666") also, it seems relevant.

Initially when the floppy was working in ubuntu, it did show up as a usb drive, but still functioned like a floppy. Now no matter what i try, i cant get it to work like a floppy, i cant even get it to mount for some reason. I mean...it pops up in places, computer, but it wont mount and show up on the desktop. 

I corrected my spelling, and it doesn't even access the floppy disk on the little laptop, i just get the error message. I am starting to think that my original desire to try and use the floppy only install is the best way to you, and if you can give me clarification on thier instructions, that would be great, and again, thank you for all your help.

I looked at the thread, and i'll be honest, i didn't read it word for word...it appears to be a similar issue...but i think its getting a little more involved in diagnostic investigation than I am competent to do. Also...i don't see anywhere written exactly what he is trying to install...ubuntu?

---

### Post by gzarkadas on 2010-08-26
The attached script will download and break into pieces the current DSL cdrom in the directory /home/<your-account>/dsl-floppy-install/ ; this will save some steps :). You need ***not*** sudo to execute it. I added also an md5sum on each diskette file (they are stored in floppies.md5.txt), to ease check for defective diskettes if the need arises. Put it anywhere, remove the .sh extension and make it executable with `chmod u+x DSL-prepare-floppy-install'. Then run it.

After the script completes, you just have to copy each one xxNN file to a diskette (in the ubuntu box you can do it from nautilus), move the diskette to the target machine and copy the file inside to the hard disk. Use the commands described in **Steps 7 - 10** of the [DSL floppy install guide]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_%28No_Netcard,_Linux_Only%29"). 

I suggest you use a full set of 36 diskettes, so that if there is a need to reinstall your DSL system you 'll have them ready; it will save a lot of time. 

If you don't understand what a command does, type in a terminal `man <command>' (in your ubuntu box). You can also use the [ubuntu man pages,]("http://manpages.ubuntu.com/") if you prefer to use a browser.

---

### Post by silverglade00 on 2010-08-26
There might be an easier, but pricier way around this...

[USB ports on a PCMCIA adapter (it says Linux 2.4.20 support)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16839101111&cm_re=usb_pcmcia-_-39-101-111-_-Product") plus your DSL on a USB stick.

---

### Post by sytheii on 2010-08-26
> **gzarkadas said:**
> The attached script will download and break into pieces the current DSL cdrom in the directory /home/<your-account>/dsl-floppy-install/ ; this will save some steps :). You need ***not*** sudo to execute it. I added also an md5sum on each diskette file (they are stored in floppies.md5.txt), to ease check for defective diskettes if the need arises. Put it anywhere, remove the .sh extension and make it executable with `chmod u+x DSL-prepare-floppy-install'. Then run it.

After the script completes, you just have to copy each one xxNN file to a diskette (in the ubuntu box you can do it from nautilus), move the diskette to the target machine and copy the file inside to the hard disk. Use the commands described in **Steps 7 - 10** of the [DSL floppy install guide]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_%28No_Netcard,_Linux_Only%29"). 

I suggest you use a full set of 36 diskettes, so that if there is a need to reinstall your DSL system you 'll have them ready; it will save a lot of time. 

If you don't understand what a command does, type in a terminal `man <command>' (in your ubuntu box). You can also use the [ubuntu man pages,]("http://manpages.ubuntu.com/") if you prefer to use a browser.

LMAO. Thank you for all of that, both of you, I figure with your help, I should be able to do this...But there is just one problem...For some reason Ubuntu doesnt want to mount my external usb floppy drive. I don't understand it at all. It mounted up fine the first time, and everything I have tried to get it to recognise it for what it is has failed. 

For reference, it is an imation Super Disk, says its "for macintosh," but it worked once before no problem. 

Perhaps someone could recommend something to do to try and get it to work for me?

EDIT: I just tried something else...I had a disk in there that I am sure was formatted for windows 3.1 or some such thing...and then I put in one of the BG boot disks i had made earlier, and lo and behold, it mounts the disk and puts it on the desktop... yay!

---

### Post by gzarkadas on 2010-08-27
[FONT=Fixedsys][SIZE=2]Glad I could be of help. Also, just for reference, this laptop has been successfully used to serious scientific work (see the [paper]("http://www.dtic.mil/cgi-bin/GetTRDoc?Location=U2&doc=GetTRDoc.pdf&AD=ADA419910"), specifically the (12) label of the last page's schematic) and thus it deserves to host a GNU/Linux distribution!

@sytheii: When you finish copying all those floppies, please report how much time it took (just from curiosity, to calculate the needed beer and pizza :)). 
[/SIZE][/FONT]

---

### Post by sytheii on 2010-08-28
> **gzarkadas said:**
> [FONT=Fixedsys][SIZE=2]Glad I could be of help. Also, just for reference, this laptop has been successfully used to serious scientific work (see the [paper]("http://www.dtic.mil/cgi-bin/GetTRDoc?Location=U2&doc=GetTRDoc.pdf&AD=ADA419910"), specifically the (12) label of the last page's schematic) and thus it deserves to host a GNU/Linux distribution!

@sytheii: When you finish copying all those floppies, please report how much time it took (just from curiosity, to calculate the needed beer and pizza :)). 
[/SIZE][/FONT]

LOL, i've been insanely busy past couple days, will try to get you a time when I'm done :)

---

### Post by sytheii on 2010-08-31
> **gzarkadas said:**
> The attached script will download and break into pieces the current DSL cdrom in the directory /home/<your-account>/dsl-floppy-install/ ; this will save some steps :). You need ***not*** sudo to execute it. I added also an md5sum on each diskette file (they are stored in floppies.md5.txt), to ease check for defective diskettes if the need arises. Put it anywhere, remove the .sh extension and make it executable with `chmod u+x DSL-prepare-floppy-install'. Then run it.

After the script completes, you just have to copy each one xxNN file to a diskette (in the ubuntu box you can do it from nautilus), move the diskette to the target machine and copy the file inside to the hard disk. Use the commands described in **Steps 7 - 10** of the [DSL floppy install guide]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_%28No_Netcard,_Linux_Only%29"). 

I suggest you use a full set of 36 diskettes, so that if there is a need to reinstall your DSL system you 'll have them ready; it will save a lot of time. 

If you don't understand what a command does, type in a terminal `man <command>' (in your ubuntu box). You can also use the [ubuntu man pages,]("http://manpages.ubuntu.com/") if you prefer to use a browser.

Gzarkadas! wow! you're the man :) It took me a little bit to understand how to run that script...after enabling it to be executable, it took me like half an hour to realise to run it all i had to do was double click :)

I ran it in terminal, and it grabbed and chopped everything peachy...But now I am at the point where i need to copy each file to a diskette, and I am hitting a wall... When I put in a disk that is formatted specifically for linux, ie, a bootfloppy, (which are the only linux floppies that I have) it will SOMETIMES recognise the disk and put it on the desktop. I believe that ubuntu should recognise that there is a floppy in the USB floppy drive and mount it regardless, correct?

I need to solve this strange issue before I can copy those files to each diskette.

Any thoughts?

EDIT: Under Palimpsest Disk Utility, It registers the device, but when there is a disk in there, it simply doesn't find it.
[IMG]http://i20.photobucket.com/albums/b210/sytheii/disk.png[/IMG]

---

### Post by gzarkadas on 2010-08-31
From a quick search, it seems this is a gnome / device-kit bug. (See refs. [#1]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480163"), [#2]("http://forums.fedoraforum.org/showthread.php?t=233365")).  The recipe given (there and also in [this thread]("http://ubuntuforums.org/showthread.php?t=1154034")) is to manually mount the floppy from the command line. 

I give steps for this below, using the floppy group as a means for access control.

1. Make sure your account is member of the floppy group. To do this open a terminal window and type:
```

cat /etc/group | grep floppy

```If should output a line similar to "[noparse]floppy:x:25:[/noparse]" and then either nothing or a comma separated list of account login names.

If your account login is in there, then there is no need to do anything; you are member of the group. If not, at the same terminal type:
```

sudo adduser [your-account-login-name] floppy

```2. Make the mount point for the floppy:
```

sudo mkdir -p /media/floppy
sudo chmod 775 /media/floppy
sudo chown root:floppy /media/floppy

```3. Modify your /etc/fstab so that users can mount / unmount the floppy:
```

sudo nano /etc/fstab

```Inside the editor, go to last line, press ENTER and type this:
```
/dev/fd0  /media/floppy  auto  rw,user,noauto  0  0
```Then press Ctrl+O and then yes at the prompt, to write the file. Then Ctrl+X to close nano.

4. Mount the floppy as your normal login user:
```
mount /dev/fd0
```If this works, the floppy should now appear at desktop and you can copy the files to it using the normal nautilus methods (drag n' drop, Ctrl+C, Ctrl+V, etc.)

---

### Post by sytheii on 2010-09-01
> **gzarkadas said:**
> From a quick search, it seems this is a gnome / device-kit bug. (See refs. [#1]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480163"), [#2]("http://forums.fedoraforum.org/showthread.php?t=233365")).  The recipe given (there and also in [this thread]("http://ubuntuforums.org/showthread.php?t=1154034")) is to manually mount the floppy from the command line. 

I give steps for this below, using the floppy group as a means for access control.

1. Make sure your account is member of the floppy group. To do this open a terminal window and type:
```

cat /etc/group | grep floppy

```If should output a line similar to "[noparse]floppy:x:25:[/noparse]" and then either nothing or a comma separated list of account login names.

If your account login is in there, then there is no need to do anything; you are member of the group. If not, at the same terminal type:
```

sudo adduser [your-account-login-name] floppy

```2. Make the mount point for the floppy:
```

sudo mkdir -p /media/floppy
sudo chmod 775 /media/floppy
sudo chown root:floppy /media/floppy

```3. Modify your /etc/fstab so that users can mount / unmount the floppy:
```

sudo nano /etc/fstab

```Inside the editor, go to last line, press ENTER and type this:
```
/dev/fd0  /media/floppy  auto  rw,user,noauto  0  0
```Then press Ctrl+O and then yes at the prompt, to write the file. Then Ctrl+X to close nano.

4. Mount the floppy as your normal login user:
```
mount /dev/fd0
```If this works, the floppy should now appear at desktop and you can copy the files to it using the normal nautilus methods (drag n' drop, Ctrl+C, Ctrl+V, etc.)

]Hmmm...I followed your instructions, and @ the last step I receive this message in the terminal:

mount: special device /dev/fd0 does not exist

There is a floppy icon in places now...but it just says it cant mount that...

The only thing I might have done incorrectly is where to put that line you have.

```
/dev/fd0  /media/floppy  auto  rw,user,noauto  0  0
```You say "go to the last line, press ENTER and type this" 

I am assuming you just meant to add that line underneath the final line  that is there...which is not what happens if i navigate to the last line  and then hit enter...what would happen then is that line of code would  be written in directly in front of original last line of code.

Perhaps I did it wrong...thoughts?

PS: How do you pinpoint find all this info? You must just know what to type in the search box. :)
Also...I looked for a refrence to my laptop in that Army DOC, but couldnt find it...which page is it on? LOL

---

### Post by gzarkadas on 2010-09-01
Hmm, it must be that it is a pcmcia floppy. Try to change /dev/fd0 to /dev/sdc (since this is the device name that appears in disk utility). Please note that this is a hack, it is not guaranteed to work; we 'll have to go by trial and error (and guessing, because I have not such stuff any more).

It doesn't matter the order of the lines (there was an implicit "go to end of line before hitting enter" in that instruction, but since it was implicit it naturally didn't happen :)); as long as each line is separate you should be fine.

The reference is in the last page, right above the image. It is just a label in the middle of a line, so look carefully.

---

### Post by sytheii on 2010-09-03
> **gzarkadas said:**
> Hmm, it must be that it is a pcmcia floppy. Try to change /dev/fd0 to /dev/sdc (since this is the device name that appears in disk utility). Please note that this is a hack, it is not guaranteed to work; we 'll have to go by trial and error (and guessing, because I have not such stuff any more).

It doesn't matter the order of the lines (there was an implicit "go to end of line before hitting enter" in that instruction, but since it was implicit it naturally didn't happen :)); as long as each line is separate you should be fine.

The reference is in the last page, right above the image. It is just a label in the middle of a line, so look carefully.

Just to reiterate, this is a USB floppy drive. I did what you suggested, and to be honest i didnt notice if it was on the desktop right after i booted...but after i made that edit, a USB icon with "1.5 MB filesystem" appeared on the desktop. I was able to open a nautilus window to see the file on the disk. 

I then tried taking the disk out, but it wouldnt respond. Then I tried rightclicking and going to "eject" and that didnt work either, I actually got some kind of error message about it not being able to. I then repeatedly tried to push the button on the drive to eject the disk...wouldnt work.

I rebooted, and then tried to hit the eject button on the drive, and it did eject. I was able to do this with a few different disks.

My question is...did we get it to work? is there a command I will have to perform each time i put in a new disk? that would be awful :(

My patience with this is wearing thin I have to say...If you don't feel like trying to figure out new ways to get this drive to work, please don't feel obligated to do so.

Thanks again.

---

### Post by gzarkadas on 2010-09-03
I guess you will have to execute  ```
mount /media/floppy
``` to mount the disk *after* you have put it in and ```
umount -l /media/floppy
``` *before* you eject it. This is the price to pay for your floppy drive not behaving well with your ubuntu version. 

However, you can create two launchers for these commands and put them wherever it suits you (at the deskbar, on the desktop, etc) so that the only additional work is a couple of double-clicks.

Note that you need _*not*_ sudo for this, since the floppy is specified to mount with the user option in /etc/fstab.

PS: Patience :) ; driver problems are the most annoying, since they *are* difficult to fix. But most things at the end are indeed doable.

---

### Post by sytheii on 2010-09-03
> **gzarkadas said:**
> I guess you will have to execute  ```
mount /media/floppy
``` to mount the disk *after* you have put it in and ```
umount -l /media/floppy
``` *before* you eject it. This is the price to pay for your floppy drive not behaving well with your ubuntu version. 

However, you can create two launchers for these commands and put them wherever it suits you (at the deskbar, on the desktop, etc) so that the only additional work is a couple of double-clicks.

Note that you need _*not*_ sudo for this, since the floppy is specified to mount with the user option in /etc/fstab.

PS: Patience :) ; driver problems are the most annoying, since they *are* difficult to fix. But most things at the end are indeed doable.

I tried  "mount /media/floppy

and i get this message in terminal
" dev/sdc is not a valid block device"

:(
How do I create a "launcher"? That would be helpful to know...Nevermind, found instructions.

So...that didnt work. Any other ideas?

---

### Post by gzarkadas on 2010-09-03
> **sytheii said:**
> I tried  "mount /media/floppy

and i get this message in terminal
" dev/sdc is not a valid block device"

...

Did you had a floppy inside the device when you issued the command? If not, put one inside and repeat.

---

### Post by sytheii on 2010-09-03
> **gzarkadas said:**
> Did you had a floppy inside the device when you issued the command? If not, put one inside and repeat.

Yes, floppy is inside when I try the command, same error message.

---

### Post by gzarkadas on 2010-09-03
Ok, we need to search deeper. Get the attached script, put it somewhere, open a terminal and go to the directory where you have placed it. Then type:
```

mv greplogs.sh greplogs
chmod u+x greplogs
sudo  ./greplogs  <your-account-login-name>

```Use your real account name instead of "<your-account-login-name>". 

The script greps a number of key log files (as well as their compressed older versions; hence the complexity) for strings relating to the problem and puts the result in `/tmp/diag/mergelog.gz'. 
After posting that file here you can safely delete /tmp/diag.

Do this procedure twice: 
-- First with your current setup, right now. Post mergelog.gz and delete /tmp/diag.
-- Then, remove the floppy line from /etc/fstab and also delete /media/floppy, to restore the changes I suggested in the previous posts. 
-- Then reboot and try to use the device to read a floppy. Do this a couple of times. 
-- Then, finally, run the greplogs script for second time. Post the new mergelog.gz and delete /tmp/diag.

Hopefully, these files will provide enough insight to the problem, without having to exchange a lot of question/answer posts.

A final question: did this floppy ever worked right? if yes, then maybe we have to look better in what changes you have done to loaded modules, just before this issue appeared here.

---

### Post by sytheii on 2010-09-03
> **gzarkadas said:**
> Ok, we need to search deeper. Get the attached script, put it somewhere, open a terminal and go to the directory where you have placed it. Then type:
```

mv greplogs.sh greplogs
chmod u+x greplogs
sudo  ./greplogs  <your-account-login-name>

```Use your real account name instead of "<your-account-login-name>". 

The script greps a number of key log files (as well as their compressed older versions; hence the complexity) for strings relating to the problem and puts the result in `/tmp/diag/mergelog.gz'. 
After posting that file here you can safely delete /tmp/diag.

Do this procedure twice: 
-- First with your current setup, right now. Post mergelog.gz and delete /tmp/diag.
-- Then, remove the floppy line from /etc/fstab and also delete /media/floppy, to restore the changes I suggested in the previous posts. 
-- Then reboot and try to use the device to read a floppy. Do this a couple of times. 
-- Then, finally, run the greplogs script for second time. Post the new mergelog.gz and delete /tmp/diag.

Hopefully, these files will provide enough insight to the problem, without having to exchange a lot of question/answer posts.

A final question: did this floppy ever worked right? if yes, then maybe we have to look better in what changes you have done to loaded modules, just before this issue appeared here.

K. Got that file uploaded for the initial post. I actually just started the process, and realize that I have to leave. I will finish this when I get home in a couple of hours.

---

### Post by sytheii on 2010-09-04
Hey. I found something out that is interesting. I rebooted my machine, since I had to put it into windows for a bit, and after booting up and going to ubuntu, I realised that I had unplugged the USB for the floppy drive.

So what I did was I plugged the USB back in the computer, and then the drive started to read the disk in it, and "floppy" was mounted and placed on the desktop! I was able to delete whatever was on there...format it...and then copy the first file out the the 36 xx00's. I then "unmounted it" after a right click, And then I was able to eject the disk from the drive itself. Note: Shuttle Technology Inc. E-USB Bridge still appears in the Computer places, in addition to "floppy" on the desktop.

I then put in another disk...but it would not go through the same process of mounting it. Strange no? Perhaps this will give you some insight into what needs to be changed. I believe if I did the same thing again, rebooting, and then plugging in the drive, it would be reproduced. 

I will finish the process you wanted me to do earlier now, and see if that can give you some insight.

---

### Post by sytheii on 2011-06-21
Hello, 

I was recently going through all of my bookmarks and cleaning out ones that I no longer needed, and came upon this thread. Just wanted to say, in frustration I had abandoned the project for its seemingly endless supply of setbacks. 

But, I wanted to thank gzark and others who had tried to help. I have since aquired a macbook, and have enjoyed playing with it, and now I have successfully incorporated latest ubuntu with snow leopard, and a litestep shell of xp, and I love it.

Good night, and good luck.

---

