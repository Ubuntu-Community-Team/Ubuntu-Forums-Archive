---
title: "Speed up the Ubuntu LiveCD by adding a ToRAM Feature"
date: 2010-10-22
forum: General Help
---

### Post by terminator14 on 2010-10-22
**[SIZE="4"]About the Project[/SIZE]**

Have you ever wanted the Ubuntu LiveCD to have a ToRAM feature like knoppix? I know I have. Looking around online, a HOWTO that focuses on this exact topic is [https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM"). [https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM") hasn't been updated since Ubuntu 9.10 was released however, and some things it mentions no longer work as it describes (especially things dealing with the bootloader). It also isn't the easiest HOWTO to follow (maybe that's just me) mainly because of the multiple things that need to be mounted and kept track of. This is why I spent a few days developing a script that will take an Ubuntu ISO, and add a ToRAM feature to it. I used [https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM") and [https://help.ubuntu.com/community/LiveCDCustomizationMaverick]("https://help.ubuntu.com/community/LiveCDCustomizationMaverick") as my two main sources of information so thanks to the authors of both those pages for making this script possible.

**[SIZE="4"]What is a ToRAM feature?[/SIZE]**

A ToRAM feature is something that copies the entire CD to RAM before running the live environment. I first saw this done by knoppix, one of the first linux distributions I've ever tried, and now this can be done with Ubuntu as well.

**[SIZE="4"]Why do this?[/SIZE]**

There are several reasons:

**Speed:** A LiveCD environment is usually considered to be slower than a regular install of Ubuntu. This is because instead of running from the hard drive, the LiveCD runs right from your CD, and since CDs are slower than hard drives, this results in a slower Ubuntu then you may be used to. A ToRAM feature addresses this issue. This is because when the LiveCD environment runs from your RAM, it is not only faster than a regular hard drive install (due to RAM's insane speeds), it is also faster than any SSD.

**Getting your CD Drive back:** If you boot into a LiveCD environment from a CD, Ubuntu needs that CD to operate. If you have a single CD drive (like most of us do), you can no longer use that drive. If this is a problem for you, the ToRAM feature addresses this as well since it doesn't need the Ubuntu CD to operate, allowing you to remove it and replaces it with any other CD.

**Fast Install:** Although Ubuntu's install process is fast, it can still take a while before it finishes. If you install Ubuntu often, and don't have the patience to wait for it to finish every time, you can speed up the process by using the ToRAM feature. As an added bonus, if you are installing Ubuntu on many machines at once (like in a library or a computer room), the ToRAM feature allows you to do this in parallel since you won't need the CD for 99% of the installation (only to start it).

**[SIZE="4"]What will this work on?[/SIZE]**

This should work for Ubuntu 10.10 x86 or amd64, but keep in mind:

[QUOTE=https://help.ubuntu.com/community/LiveCDCustomizationMaverick]The architecture (Amd64 or i386) to be stored on the LiveCD should be the same as the architecture used to perform the customization, or the LiveCD may not run. It is not trivial to customize an AMD64 LiveCD using an i386 operating system, for example.[/QUOTE]

**[SIZE="4"]Word of Warning[/SIZE]**

Although I try to build safeguards into any script I upload to the internet to keep them from doing anything unexpected, including this one, you may want to run this script in a VM where it's safe. You could also try running it from a live CD where, if it goes rouge for some reason, it won't kill anything.

**[SIZE="4"]Final words[/SIZE]**

Please post a comment to let me know if this works, or if anything needs fixing.

---

### Post by JustinR on 2010-10-22
I've also been looking for a feature like this! It sounds cool - the script is very nicely made!

I look forward to trying it out!

---

### Post by terminator14 on 2010-10-23
> **JustinR said:**
> I've also been looking for a feature like this! It sounds cool - the script is very nicely made!

I look forward to trying it out!

Thanks. Let me know how it goes.

---

### Post by ruselreyes on 2010-10-29
Hello there,
I have a question: sorry but I'm a new on Ubuntu, can you give me a small explanation to how to get this going, like where shuld I put the iso etc. when I run the script i get this error:
./live_cd_customizer.sh
Usage: ./live_cd_customizer.sh [arg]
	Arg: The location of the Ubuntu iso file

thanks.:confused:

---

### Post by oldos2er on 2010-10-29
You're much more likely to get help if you start a new thread.

---

### Post by terminator14 on 2010-10-29
> **ruselreyes said:**
> Hello there,
I have a question: sorry but I'm a new on Ubuntu, can you give me a small explanation to how to get this going, like where shuld I put the iso etc. when I run the script i get this error:
./live_cd_customizer.sh
Usage: ./live_cd_customizer.sh [arg]
	Arg: The location of the Ubuntu iso file

thanks.:confused:

First, download the Ubuntu iso from the main Ubuntu website and put it into the same folder as the live_cd_customizer.sh script. The ISO will be named something like ubuntu-10.10-desktop-amd64.iso. Once you do this, open the terminal and 'cd' to the folder both the iso and the script are in. For example, if both are on your desktop, run:

```
cd ~/Desktop
```

then make sure you have permissions to execute the script:

```
sudo chmod a+x ./live_cd_customizer.sh
```

and finally, run the script, passing it the location of the iso as an argument like so:

```
sudo ./live_cd_customizer.sh ubuntu-10.10-desktop-amd64.iso
```

Technically, the iso can be placed anywhere as long as you specify where it is as the argument so if the iso was in your home folder, you could run:

```
sudo ./live_cd_customizer.sh ~/ubuntu-10.10-desktop-amd64.iso
```

instead.

---

### Post by terminator14 on 2010-10-29
> **oldos2er said:**
> You're much more likely to get help if you start a new thread.

Why in the world would he start a new thread when he has a question about the script I created and posted in this thread?

---

### Post by ruselreyes on 2010-11-01
Thanks Terminator14 I'll give this a try.
hava a good day.

---

### Post by oldos2er on 2010-11-01
> **terminator14 said:**
> Why in the world would he start a new thread when he has a question about the script I created and posted in this thread?

My bad.

---

### Post by ruselreyes on 2010-11-01
TErminator14,
thanks for the tip, it worked great I followed your instructions and created the iso nicely,
maybe you can give me some tips to how to boot from the cd and have load to ram automatically!!..thanks a lot I really need it this to get working.
take care.
RReyes

---

### Post by terminator14 on 2010-11-03
> **ruselreyes said:**
> TErminator14,
thanks for the tip, it worked great I followed your instructions and created the iso nicely

Awesome - good to know it works for others too and not just me, thanks. 

> **ruselreyes said:**
> maybe you can give me some tips to how to boot from the cd and have load to ram automatically!!..thanks a lot I really need it this to get working.
take care.
RReyes

Just taking a quick look, you could try this:

-open the script in a text editor like gedit
-find the following lines:

```
#Make menu actually show up
echo "Make menu stop hiding..."
sed -i 's/\(hidden-timeout=\)[0-9]/\10/' ${UBUNTU_ORIG_PATH}/isolinux/gfxboot.cfg

#Change timeout value of boot menu
sed -i 's/\(timeout \)[0-9]*/\1300/' ${UBUNTU_ORIG_PATH}/isolinux/isolinux.cfg
```

and change them to:

```
#Make menu actually show up
#echo "Make menu stop hiding..."
#sed -i 's/\(hidden-timeout=\)[0-9]/\10/' ${UBUNTU_ORIG_PATH}/isolinux/gfxboot.cfg

#Change timeout value of boot menu
#sed -i 's/\(timeout \)[0-9]*/\1300/' ${UBUNTU_ORIG_PATH}/isolinux/isolinux.cfg
```

or just delete them.
-save the script
-run the script

If that doesn't work, let me know and I'll look into it.

---

### Post by dcstar on 2010-11-03
So does this also work if you use the "converted" ISO to create a Live USB device?

---

### Post by terminator14 on 2010-11-03
> **dcstar said:**
> So does this also work if you use the "converted" ISO to create a Live USB device?

I've never tried this but ya, in theory it should still work fine. If you're gonna try this, let us know if it works.

---

### Post by chang5562 on 2010-11-03
I tried the script on my Ubuntu 9.04 system, but failed.
Here are what I did.
1. refreshed a new install of 9.04 from my customerized Ubuntu 9,04 LiveCD on a Laptop.
2. use remastersys to recreate an iso under the /home/remastersys/remastersys  (default)
3. download the script and made the change according to the suggestion.
4. copied the script to /home/remastereys and run 'sudo ./live_cd_customerizer.sh remastersys/my.iso
5. failed to recreate a new iso (or at least I did not see the change or original iso)

My first failed message told me that there was not enough space under the /var (original only 2 G), so i increased it to 11G.
the second trial showed that 
" failed to add menu entry to /var/ubuntu_1010raw/isolinux/txt.cfg"
"sed: can't read ../isolinux/txt.cfg"

The system was not connected to internet during the process.

---

### Post by terminator14 on 2010-11-04
> **chang5562 said:**
> I tried the script on my Ubuntu 9.04 system, but failed.
Here are what I did.
1. refreshed a new install of 9.04 from my customerized Ubuntu 9,04 LiveCD on a Laptop.
2. use remastersys to recreate an iso under the /home/remastersys/remastersys  (default)
3. download the script and made the change according to the suggestion.
4. copied the script to /home/remastereys and run 'sudo ./live_cd_customerizer.sh remastersys/my.iso
5. failed to recreate a new iso (or at least I did not see the change or original iso)

My first failed message told me that there was not enough space under the /var (original only 2 G), so i increased it to 11G.
the second trial showed that 
" failed to add menu entry to /var/ubuntu_1010raw/isolinux/txt.cfg"
"sed: can't read ../isolinux/txt.cfg"

The system was not connected to internet during the process.

I am not familiar with remastersys, but from a quick search online, it looks like what it does is create a bootable iso (live cd) from your existing installation of Ubuntu. If that's right, then chances are that it uses one of a thousand other ways to make the live cd bootable, which no doubt differs from the way the original Ubuntu LiveCD does it. Since my script was written specifically with the original Ubuntu LiveCD in mind and not a product of remastersys, there will no doubt be problems when the script tries to edit bootloader files that don't exist.

Also, if your ISO is Ubuntu 9.04, and not 10.10 like the script was designed for, you will run into problems since the bootloaders used on the two LiveCDs also differ (AFAIK).

If your goal is to make your Ubuntu installation run from RAM, maybe this isn't the thread you should be looking at. Try this one instead: [http://ubuntuforums.org/showthread.php?t=1594694]("http://ubuntuforums.org/showthread.php?t=1594694") which specifically deals with making your installation run from RAM. Unfortunately, it only works with newer versions of Ubuntu (10.04 and 10.10).

---

