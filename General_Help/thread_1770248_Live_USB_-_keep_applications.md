---
title: "Live USB - keep applications"
date: 2011-05-29
forum: General Help
---

### Post by layers on 2011-05-29
So, is it possible? To run any Linux distro, and have thunderbird for instance installed always, and it keeping its data on the usb?

---

### Post by linuxinstalledfromhdd on 2011-05-29
The word for what you are trying to do is "persistent". Yes, you can make a persistent USB of Ubuntu with Startup Disc Creator in Ubuntu.  You can also make a clone of your current entire system with Remastersys, and then take the ISO it creates and use Startup Disc Creator to make a USB Live persistent Ubuntu clone of your entire setup. It comes in really handy when I forget to bring my laptop somewhere, but I have the USB stick with me to use on someone elses laptop or desktop computer. And since you make it with Remastersys, that means you can always install a clone of that USB disto to any other computer if you wish directly from that USB stick of custom Ubuntu in less than like 15 minutes. No hassle or having to reconfigure everything again. It's one of my favourite things about Ubuntu.

---

### Post by layers on 2011-05-29
Alright, let me ask you another question: 
If I take the HDD off from one laptop, put it into another, is it going to boot up like the laptop it used to be in? (if that HDD had ubuntu installed on it)
If yes, when making a USB with Remastersys, is it going to copy over Documents and other media stuff?

I realize, the above is kind of confusing without a proper description.
What I am asking is, what is going to happen when you put a new hard drive into a laptop. The hard drive was taken from another laptop, and that laptop was running ubuntu from it no problem. Is there any boot records that are kept in the BIOS with respect to the previous hard drive that would mess things up, and prevent the laptop just booting from this "foreign" HDD?

---

### Post by MoebusNet on 2011-05-29
I'm certainly not an expert on this, but I believe that unless the first and second computers are identical hardware, or at least use all the same drivers, you likely will not be successful swapping hard drives like that. The Live-CD/USB's detect the hardware in use and choose the drivers accordingly. A hard drive installation already has the drivers chosen.

"You can also make a clone of your current entire system with Remastersys, and then take the ISO it creates and use Startup Disc Creator to make a USB Live persistent Ubuntu clone of your entire setup." This will detect your hardware to choose the correct drivers.

If someone more knowledgeable would like to expand on or correct my analysis, please feel free.

---

### Post by oldfred on 2011-05-29
Ubuntu is good about running on different systems except now for video drivers. If you do not install proprietary video then it will work on most systems.

If you have a USB hard drive or flash of 8GB or more, you do not want to do a persistent install but a full install. The installer version is smaller and works well for those with small flash drives. With persistence you can make it reusable and probably works best with a 4GB flash drive. Anything larger the  limits of the installer and how persistence works limits your use.

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Other version have slight differences in screens shown, but process is the same.
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **layers said:**
> Alright, let me ask you another question: 
If I take the HDD off from one laptop, put it into another, is it going to boot up like the laptop it used to be in? (if that HDD had ubuntu installed on it)
If yes, when making a USB with Remastersys, is it going to copy over Documents and other media stuff?

I realize, the above is kind of confusing without a proper description.
What I am asking is, what is going to happen when you put a new hard drive into a laptop. The hard drive was taken from another laptop, and that laptop was running ubuntu from it no problem. Is there any boot records that are kept in the BIOS with respect to the previous hard drive that would mess things up, and prevent the laptop just booting from this "foreign" HDD?

You can only swap out a hard drive like you are suggesting for exact like hardware architecture.

You would be better off installing a pesistant Live Ubuntu clone to a USB Micro HDD Stick. Flash sticks can eventually wear out rather quickly.  But the USB Micro HDD Sticks are mini hard drives essentially and they are not flash sticks in the normal sense, and have a much greater life span. 

Try creating a USB stick with persistance in Startup Disc Creator in Ubuntu for now until you get a feel for the entire process.

Remastersys needs to be installed from a PPA as well.

And yes it will save your home folder documentation if you select BACKUP verses DIST in the gui-configuration settings for Remastersys. Remember you are limited to 4.7 Gb total because that is as big as remastersys will allow you to go. Once you have actually created your Micro HDD stick of Ubuntu that is "persistant" (meaning you can continue to add to it after it is created), you should be able to add above the 4.7Gb limit until USB Micro HDD capacity, theoretically. I haven't tested this though.

---

### Post by layers on 2011-05-29
Thanks for all the explanations and suggestions: I will be using an 8GB USB, and honestly, both options seem viable, and I doubt it will make a difference when it comes to the way I will be using my computer for the summer.

I was just trying to find a way of recovering my old hard disk. Is the only option buying cables and such?

---

### Post by layers on 2011-05-29
Actually, I am having a little trouble with finding what my options are. Can anyone advise?

---

### Post by farkinid on 2011-05-29
You can try building a persistent Live USB based on the steps shown in [http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/). Try browsing around to find something that will fit your needs.

Alternatively, you may use Unetbootin. You can find it at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/). It is also available in the repos

---

### Post by oldfred on 2011-05-29
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by layers on 2011-05-30
Well, apparently, Sony, with all their wisdom, do not support USB booting in their VAIO's. :shock:

Even if I set it to "External Device" first in the boot order, it goes into the hard drive. I followed [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by linuxinstalledfromhdd on 2011-05-30
That's interesting. :) 

What is the exact make and model of laptop so I can cross reference this really quick for you?

---

### Post by oldfred on 2011-05-30
BIOS has to see bootable device. But only computers in the last 4 or 5 years have BIOS that boot from USB. Older computers may have had floppy drives or just relied on CD.

Some have said this works, others have had issues. I have not used it.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by layers on 2011-05-30
> **oldfred said:**
> BIOS has to see bootable device. But only computers in the last 4 or 5 years have BIOS that boot from USB. Older computers may have had floppy drives or just relied on CD.

Some have said this works, others have had issues. I have not used it.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Yeah, I too find mixed stories: some cannot stop booting from a USB, others cannot at all.
I assume the "External Device" option is for an ext. HDD. To me, it doesn't look much different from a USB. I will keep looking.
And it's a brand new machine.

---

### Post by layers on 2011-05-30
> **linuxinstalledfromhdd said:**
> That's interesting. :) 

What is the exact make and model of laptop so I can cross reference this really quick for you?

My bad, I hadn't saved it properly.
USB booting works.

I tried Pinguy 11.04 x64, that froze.
While setting Wary Puppy USB, it said it encountered error, so the USB won't be bootable.
It doesn't even show the openSUSE iso image.
I'm trying others as I speak. Or type.

I did boot from the old 9.10 cd I had, but there is not touchpad. Anyone else experienced that?

You have no idea how happy I was once I saw terminal again lol

---

### Post by layers on 2011-05-30
Uhm, last problem.

Two different distributions so far - 
I load the CD, 
boot into live mode, 
and proceed onto making a LiveUSB with their tool. 
It completes, 
I restart the machine, 
it picks up the USB, 
loads the options, 
I select the Live mode one, 
it shows the screen of the system, 
starts loading, 
and then I get ```
initramfs) Unable to find a medium containing a live file system
```

What am I not doing properly? I've never had a problem with this.

---

### Post by dmizer on 2011-05-30
> **linuxinstalledfromhdd said:**
> You can only swap out a hard drive like you are suggesting for exact like hardware architecture.

This is true in Windows, but not in Linux. I have moved HDD from one machine to another with completely different hardware without any difficulty at all. I have also done this many times between many different kinds of hardware.

Linux is very forgiving.

---

### Post by layers on 2011-05-30
> **dmizer said:**
> This is true in Windows, but not in Linux. I have moved HDD from one machine to another with completely different hardware without any difficulty at all. I have also done this many times between many different kinds of hardware.

Linux is very forgiving.

Where did you boot from?

---

### Post by layers on 2011-05-30
> **layers said:**
> Uhm, last problem.

Two different distributions so far - 
I load the CD, 
boot into live mode, 
and proceed onto making a LiveUSB with their tool. 
It completes, 
I restart the machine, 
it picks up the USB, 
loads the options, 
I select the Live mode one, 
it shows the screen of the system, 
starts loading, 
and then I get ```
initramfs) Unable to find a medium containing a live file system
```

What am I not doing properly? I've never had a problem with this.

Could this mean that if I just install everything onto the hard disk, I could run into the same error?

---

### Post by dmizer on 2011-05-31
> **layers said:**
> Where did you boot from?
Many many times, I have installed Ubuntu on a hard drive. Then later, I removed the hard drive from the computer, moved it to another computer, pushed the power button on the new computer (with completely different hardware) and it booted fine.

I have even (with an adapter) used a laptop hard drive to boot a desktop computer.

> **layers said:**
> Could this mean that if I just install everything onto the hard disk, I could run into the same error?
According to this: [http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing](http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing)

The problem may be related to using a USB 3.0 slot instead of a USB 2.0 slot.

No, you would not see that error if you installed directly to your hard drive.

---

