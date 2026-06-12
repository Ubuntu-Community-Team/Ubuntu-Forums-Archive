---
title: "Takes forever to install ?"
date: 2006-01-31
forum: General Help
---

### Post by `underOATH on 2006-01-31
I have a pretty bad extra computer that i am going to use to host a game server through my t3 internet connection. The computer is about 6 years old, pentium 3, IBM netvista with 128 mb of ram. I've been trying to install ubuntu for 2 days now. The first time it froze at 6% while installing base system, i redownloaded and put it on a disk again and this time it's stuck at 40% i burned it using magicISO at 4x write speed and still don't know why this installation wont work. I've also downloaded and wrote the liveCD to a cd and it doesn't even detect it as a cd while booting. Please let me know if it is gonna seem like my computer is frozen at times of installation cause it's really old and slow. or if it will really freeze during installation.

Thanks,
Jordan

---

### Post by `underOATH on 2006-01-31
Oh yea, the exact thing it is doing at 40% is "Unpacking util-linux..." maybe that will help a little.

---

### Post by souteneur3190 on 2006-01-31
i remeber my installation freezing at 6%.  The only thing I can tell you is to use Alchol 120% to burn the iso, and make sure that your computer bios is set to boot from the cd rom.  Just reboot the computer and look for "setupa" or something of that manner.

---

### Post by Leigh on 2006-01-31
I had a similar problem to this and it turned out to be a faulty CD drive!

It looked like everything was installing, except it took forever, then when I booted the computer, it wasn't stable, applications wouldn't run. When I tried to install other programs from CD they would fail at different points, etc.

---

### Post by `underOATH on 2006-02-01
all i am installing linux for is to host a game server through my t3 internet connect and i heard this was the best but it doesn't seem to be that great if it wont install properly. i just switched the hardrive to a better copmuter and installed it but i'm getting a graphic error so right now i have the disk in trying to mess with just the graphic settings then finish the installation or something.

---

### Post by ZylGadis on 2006-02-01
This is actually a known problem in the ubuntu world. I bet the 6% freeze happens when installing bsdutils? :) 
I believe the freeze is a direct result of an incompatibility between your cd drive and the cd you are installing from. Some people have successfully solved it by burning the cd on another drive, tweaking options (i.e. using raw dao and such), etc. The only 100% workable solution, though, is to just start the install, interrupt it by pressing alt-f2 before it reaches the 6%, then wget an image of ubuntu from somewhere (luckily wget is installed in the first 5% :) ), unmount the cd drive, and mount the image as a cd. When you resume the installation, it will go smoothly, as it will be actually installing from your hard drive.
I have successfully done that on more than one occasion. There is a very good page with clear step-by-step instructions somewhere on the net, I'll try to google it and post it here.

Edit: I have actually copied it to a file here, don't have the URL though. Here are the instructions:

> 
Alt-F2, hit Enter, (drops you to a shell prompt.)
# cd /target
# wget [http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/4.10/release/warty-install-i386.iso](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/4.10/release/warty-install-i386.iso) 
# umount /cdrom
# mount -o loop warty-install-i386.iso /cdrom

If you get a &#8220;could not find spare loop device&#8221; 
# modprobe loop
and try the mount again.

Obviously you need to wget breezy instead of warty, but other than that, I guarantee it works. Just make sure you stop it before the freeze, as I could not unmount the cdrom if I was too late, and had to start anew.

---

### Post by Randomness on 2007-02-23
Is there any other way around the bsdutils problem? Here's my situation: I'm trying to install Ubuntu Dapper or Edgy on a computer that has Warty (yes, 4.something). The computer has 128MB ram so I have to use the alternative installation CD (desktop failed already). I have already wasted 2 CDs trying to burn Dapper alternative and Edgy alternative (getting the bsdutils error). I would rather not try more random options involving more CD burning if possible. I can't/don't want to use the wget trick because this computer has a limited internet connection and bandwidth. Also, it seems that a one shot dist-upgrade is not recommended and multiple dist-upgrades seem to require too much bandwidth.

I have a 256MB usb key with which I can move data (yes it does mount on Warty). I'm wondering if  I could move the required files to this computer (from another one with a good internet connection, of course) and just install from there somehow. (or if there's some other solution)

Ironically, I had no problem installing 6.06 LTS on 3 old P3's (800-1000mhz) because they all had 256 mb of ram but can't seem to get newer versions of ubuntu on this 2.4ghz celeron because of the ram.

---

