---
title: "Unofficial Howto- Bootsplash install and themes (different than usplash)"
date: 2006-05-16
forum: General Help
---

### Post by Jvaldezjr on 2006-05-16
I haven't written a real HOWTO before- so this is my first.  I've been using Kubuntu now since Breezy release, and I've been using Ubuntu since April of 05.  Most of what I've learned and tweaked have been from the Ubuntu community, and I thnk you all for creating one of the best supported linux distributions ever.  This is unofficial so it can be tested by the community, and tweaked, then finally a real HOWTO can be written.

On to the good stuff.  Have you ever seen some bootup screens of Gentoo or SUSE and wondered why your installation only has 16 colors, and a 640x480 resolution?  Ubuntu packages with the default installation its own utility called Usplash.  Now there are themes out there that are meant to be used with Usplash, and there is a wiki page about Usplash and customization of boot themes [here]("https://wiki.ubuntu.com/USplashCustomizationHowto") and [here.]("http://doc.gwos.org/index.php/Change_Usplash")
This is not what this HOWTO is about.  This HOWTO focuses on the [bootsplash utility.]("http://www.bootsplash.org")  SUSE by default supports it, and ubuntu can be made to support it by some tweaking of scripts and grub files, and compiling a custom kernel to support bootsplash.
[B]
FIRST THINGS FIRST!!![/B]
The default ubuntu kernel or any of the updated ubuntu prepackaged kernels do not have bootsplash support included in the kernel.  So you need to recompile your kernel and include support for bootsplash and higher res boot screens.  Compiling the kernel is beyond the scope of this howto, there are several good ones [here]("http://doc.gwos.org/index.php/PowerTweaking") for reference.  I am not a linux pro, I consider myself to be just a step above newbie, and I compiled my first kernel a few days ago using the howtos I found, and low and behold I have an updated kernel with optimized features I didnt have before.  It was not as hard as it seems.  When you compile your kernel, make sure you apply the patch from the [kernel section of the bootsplash site.]("http://www.bootsplash.org")
The patch command when you will need looks something like this:
```
cat ../bootsplash-<version>.diff | patch -p1
```

[COLOR="Blue"]Once you have patched the kernel source, you need to include the correct menu options to be built into the kernel.  They are:
1- Support for frame buffer devices &#8211; should be in device drivers, under graphics or graphics support
2- Select &#8220;VESA VGA graphics support&#8221; option and press Y.
3- Select &#8220;Video mode selection support&#8221; and press Y.
4- Select &#8220;Console display driver support&#8221; and press Enter.
5- Select &#8220;Video mode selection support&#8221; and press Y. (You should see a check or a *)
6- Select &#8220;Framebuffer Console Support&#8221; and press Y. (You should see a check or a *)
7- Exit from this submenu.  Now find the option Bootsplash Configuration, and when you see the only selection, &#8220;Bootup splash screen&#8221; press Y.
[SIZE="2"]** Note you might see a frame-buffer driver specifically written for your video card and be tempted to use it instead of the VESA VGA driver.  This can lead to serious problems if you also use an accelerated graphics driver for your video card.  For example, NEVER select &#8220;nVidia riva&#8221; frame-buffer support if youplan to use the third-party NVIDIA accelerated graphics drivers.  These drivers do not play well together and you will have video crashes.**[/SIZE][/COLOR]

Your kernel should be configured properly for bootsplash.  Now put the utilities on your system.  Now there are 2 ways of getting bootsplash installed on your system.  One is building from source, which you can get [here]("ftp://ftp.openbios.org/pub/bootsplash/rpm-sources/bootsplash/") and download the current version.  The 2nd way is via apt by adding a debian unstable tree source into your sources.list.  I got bootsplash working via the debian package, and installing it via apt.

[SIZE="2"]**NOTE: At the time of this, I had issues with apt and the debian package.  It probably has something to do with the fact that it is not a supported ubuntu package, and there are conflicts that resulted from trying to install and remove the package.  Basically if you install it via apt, you will get errors, however it will install correctly.  You will not be able to remove it via apt due to those same errors, so you'll have to track down all the files it installed and remove them manually.  If you are familiar with building from source, then I think that is the better way- I have not done it yet, and plan to do so since I don't like having messed up dependencies and packages installed on my system. **[/SIZE]

First, set up your apt sources.list to include the correct debian package source.  You might want to backup your sources.list but it is not necessary.
```
deb http://www.bootsplash.de/files/debian unstable main
```
Then update apt:
```
> sudo apt-get update
```
Then install bootsplash and say yes to the included theme package:
```
> sudo apt-get install bootsplash
```

[SIZE="2"]**You will get a message suggesting to install the package sysv-rc-bootslpash.  I have not had success with installing this package, and I got bootsplash to work without it.  If someone figured out why you need this package, and how to install it without problems, please post and let everyone else know.**[/SIZE]

Now the bootsplash package installs a directory called	**/etc/bootsplash** which contains the themes it uses.  I would suggest using this directory, since you can just use sudo to create your own themes.  Bootsplash also will install the utilities associated with the software package from [www.bootsplash.org]("http://www.bootsplash.org").  Now this is where I got some errors with the package install (you may or may not get them, post them here if you do) however, the installation completed.  You just need to hack some of the bootsplash startup scripts.

According to the debian package site, and SUSE, there is supposed to be a **/proc/splash** file installed in **/proc**.  It does not exist on my system, so I don't know if that's due to the errors from the package install, or if the script created calls the wrong binary as far as I can tell.  Here is how I fixed it.

First backup the original bootsplash script:
```
> sudo cp /etc/init.d/bootsplash  /etc/init.d/bootsplash.backup
```
Then open the file **/etc/init.d/bootsplash** in your fav text editor (gedit, kate, vim) make sure you use sudo!
```
> sudo kate /etc/init.d/bootsplash
```
Find the line that says:
```
# default settings
test -z "${THEME}" && THEME="default"
```
and replace [COLOR="Red"]&#8220;default&#8221;[/COLOR] with [COLOR="Red"]&#8220;current&#8221;[/COLOR]

then find the line that says:
```
SPLASH=$(which splash)
```
and replace it with:
```
SPLASH=/sbin/splash
```
then find this next sequence of code (just a couple of lines down):
```
# Only do this if the kernel has support
     if [ -f /proc/splash ]
```
and replace [COLOR="Red"]/proc/splash[/color] with [COLOR="Red"]/sbin/splash[/color]
then find this sequence of lines:
```
# Stop doesn't really stop, it actually changes the image
# on vt1 back to the bootsplash image.
# Only do this if the kernel has support
     if [ -f /proc/splash ]
```
and replace [COLOR="Red"]/proc/splash[/color] with [COLOR="Red"]/sbin/splash[/color]

Now your scripts are setup correctly so that the bootsplash themes will work.  I would recommend keeping the default location for bootsplash themes, since the scripts associated with bootsplash all point to that directory, otherwise you will have to hack more scripts to point to the correct directory.

The bootsplash themes are installed at **/etc/bootsplash/themes**
There is a link called current which points to the current bootsplash theme.  If you don't have any themes installed in that location, go to [www.kde-look.org]("http://www.kde-look.org") and look for bootsplash themes (these are different from login themes, grub splashes, and KDM themes).  Always use sudo and extract the tar file into **/etc/bootsplash/themes**
```
> sudo tar xzvf your-downloaded-theme.tar.gz /etc/bootsplash/themes
```

This should created a folder called **<your-downloaded-theme>** which contains an **image/** and a **config/** directories.

Now you need to append your initrd.img file to include the config script for your bootsplash theme.  First determine what your initrd.img file is.  For example, my kernel is 2.6.16.16-athlon64 since I compiled it and labeled it that way.  You can find out what your kernel version is by typing **&#8220;uname -r&#8221;**.  The **initrd.img** will be in **/boot**, and it will be listed as **initrd.img-`uname -r`**, where **uname -r** is your kernel version.  You want to append the bootsplash theme to that initrd.img file.  Also backup your current initrd.img file incase something goes wrong you can restore it and boot back to a non broken img.
```
> sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.backup
```
Become a root user ( you will get permission violations if you do not become root).
```
> sudo -s -H
```
Now append the config file to the initrd.img
```
> splash -s -f /etc/bootsplash/theme/your-theme/config/bootsplash-<res>.cfg >> initrd.img-`uname -r`
exit
```

Done, now you've applied your config file for your boot theme, you need to update grub to use the correct reolution settings for your bootsplash image, and you can choose if you want the default, verbose, or silent image.  You may want to backup your grub config file before you edit it.
```
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
> sudo kate /boot/grub/menu.lst
```
Find a sequence of lines  similar to this, keep in mind your menu.lst may be different than mine.
```
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,8)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/hda9 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
```
and replace:
```
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda9 ro quiet splash
```
with:
```
kernel          /boot/vmlinuz-2.6.16.16-athlon64 ro root=/dev/hda9 vga=791 splash="silent"
```
where vga is the option is the decimal number that sets the console to the resoltion and color depth.  Here is a table for possible options.
[color="blue"]Color Depth      
640x480: 8-bit=769, 15-bit=784, 16-bit=785, 24-bit=786
800x600: 8-bit=771, 15-bit=787, 16-bit=788, 24-bit=789
1024x768: 8-bit=773, 15-bit=790, 16-bit=791, 24-bit=792
1280x1024: 8-bit=775, 15-bit=793, 16-bit=794, 24-bit=795[/color]

The splash option is where you can use the silent variable (which is the default) or the verbose variable (which is where you see all the text messages).  Just use either **splash=&#8221;silent&#8221;** or **splash=&#8221;verbose&#8221;**

Now reboot and enjoy the eye candy.  One thing to note is if you login under console mode, you will see the verbose image in the background of your console.  Kinda neat!

One more thing to note- I don't know if installing the bootsplash utilities through the source build installs the tools in the same places as the debian package.  I have not built the tools from source to know.  I plan on trying to do so from source, since I dont like that I had errors using the debian unstable packages with apt.  Due to the apt errors I mentioned in the beginning, I have to manually remove the packages, and build from source.  I'll add to this howto with the source build once I get a chance to do so.

References
[color="blue"]Linux Desktop Hacks, O'Reilly Publications: Chapter 1, Hack #8 - Jazz Up Your Debian System Boot[/color] (Blue Text are taken from the book directly).
[Sourcemage Howto]("http://wiki.sourcemage.org/HOWTO-Bootsplash")

Enjoy the howto, if you have things to add or other problems post here, I'll try to help out.  Keep in mind that the bootsplash themes are different from the default Kubuntu boot theme, and totally different from any usplash themes you may already use.  I read a post about bootsplash from an ubuntu rep that the reason bootsplash was not included in the ubuntu kernel was because it broke something with the installer and they couldn't get it to function like it supposed to.  So this is the only way I was able to determine to get bootsplash to work.

-JValdezjr

---

### Post by Jvaldezjr on 2006-05-19
Has anyone tried this yet, and if so, has it worked?  If not, what problems are you having?  I would like to post this in the HOWTO section if there aren't any huge issues.

Thanks

---

### Post by T-One on 2006-05-21
I'm trying it now...so far, it worked ( I got a lovely bootsplash, but I think I borked my driver settings when I rebuilt a new kernel, as I got a kernel panic - unable to mount root filesystem)

---

### Post by Jvaldezjr on 2006-05-22
I had that problem too at first, and I forgot that some of the kernel build instructions didn't mention the RAMdisk issue.  Depending on which method or website you followed, some of the compile commands may or may not have included an image to be built (the initrd.img file under /boot).  I've found a couple I researched when fixing my problem...hopefully this helps.

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#EXTRACT-PATCH]("http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#EXTRACT-PATCH")
or this thread
[http://ubuntuforums.org/showpost.php?p=124822&postcount=7]("http://ubuntuforums.org/showpost.php?p=124822&postcount=7")

---

### Post by MetalMusicAddict on 2006-05-22
Thanx sir. Hope all goes well. I dont know why the Ubuntu devs decided to reinvent the wheel with this one. Any info as to why is cool.

---

### Post by Jvaldezjr on 2006-05-23
There is an answer to that question, I actually found a post by one of the devs that basically said the reason why they had to use usplah, and not bootsplash was because the kernel patch broke something with the installer, and the bootsplash would work, but the installer wouldnt, or visa versa.  There was too much of a conflict for some reason that they didn't try  to get it to work, they just went to usplash instead.
I can't find the original post or I would just provide a link.

---

