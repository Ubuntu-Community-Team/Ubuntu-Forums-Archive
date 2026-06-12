---
title: "Linux newbie has another question"
date: 2012-06-16
forum: General Help
---

### Post by RimSide on 2012-06-16
I decided to go with Ubuntu as the main os on my computer. I backed up my data on a removable drive, and proceeded to install over a live cd. The installation got as far as to format the drive, then said it won't work.

i don't know what's wrong or how to fix it, so I was wondering if someone could maybe connect over teamviewer or something to try to fix it?

Any help would be appreciated.

---

### Post by codemaniac on 2012-06-16
Hello RimSide ,

Please provide more information on what error messages you are getting while installation .Have you created necessary partitions before moving ahead with the installation .

Some screenshots may help .

---

### Post by RimSide on 2012-06-16
There is only one error that happens (and if I have to set up partitions, and ubuntu doesn't do it itself if you don't choose the option to manually set the partitions, this is where I have gone wrong), and it's a little dialogue box that pops up that says:

The ext4 file system creation in partition #1 of Serial ATA RAID isw_bigffgecb_ARRAY (mirror) failed


I don't know what that means, but it exits the intstallation.

---

### Post by UltimateCat on 2012-06-16
Just to give you a heads up; of the details of the installation process;
During the process you should be given these 3 options:

-Replace your existing Operating System
-Install alongside
-Or do your own thing manually

Which version of Ubuntu are you trying to get installed?

---

### Post by RimSide on 2012-06-16
> **UltimateCat said:**
> Just to give you a heads up; of the details of the installation process;
During the process you should be given these 3 options:

-Replace your existing Operating System
-Install alongside
-Or do your own thing manually

Which version of Ubuntu are you trying to get installed?


It's 10.04, and I tried choosing Install alongside a while ago, but it never worked. I decided to go with replace your existing operating system.

---

### Post by kc1di on 2012-06-16
> **RimSide said:**
> There is only one error that happens (and if I have to set up partitions, and ubuntu doesn't do it itself if you don't choose the option to manually set the partitions, this is where I have gone wrong), and it's a little dialogue box that pops up that says:

The ext4 file system creation in partition #1 of Serial ATA RAID isw_bigffgecb_ARRAY (mirror) failed


I don't know what that means, but it exits the intstallation.

we really need more information on your machine. 

ram, is the H.D. currently formated to windows.?
the live cd boot ok?

---

### Post by codemaniac on 2012-06-16
However I opt for manually plan and create my partitions using gparted from livecd before going forward with installation .

---

### Post by RimSide on 2012-06-16
> **kc1di said:**
> we really need more information on your machine. 

ram, is the H.D. currently formated to windows.?
the live cd boot ok?


It has about 2 gigs of ram. And the H.D is completely wiped. I'm running the os off of the live cd right now.

---

### Post by RimSide on 2012-06-16
> **codemaniac said:**
> However I opt for manually plan and create my partitions using gparted from livecd before going forward with installation .


I don't know how to set that up or I might have done that.

---

### Post by codemaniac on 2012-06-16
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by RimSide on 2012-06-16
> **codemaniac said:**
> [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I shall look at this. Thank you. I hope it helps me

---

### Post by RimSide on 2012-06-16
I don't suppose anyone could connect to me and do it for me? It would take too long for me to learn and figure it out myself and my dad is getting mad at me and wanting me off the internet, so I need to get it fixed now.... :/

---

### Post by RimSide on 2012-06-16
[IMG]http://i.imgur.com/6bKmg.png[/IMG]

that's what the error message looks like when I try to install ubuntu.

This is what the partitions look like after I open gparted after the installation fails.

[IMG]http://i.imgur.com/oa70M.png[/IMG]

---

### Post by SDX0 on 2012-06-16
Is it possible that the file you downloaded and burned to the DVD was corrupted in some way?  Or perhaps it was burned to a bad DVD?

---

### Post by RimSide on 2012-06-16
> **SDX0 said:**
> Is it possible that the file you downloaded and burned to the DVD was corrupted in some way?  Or perhaps it was burned to a bad DVD?

I didn't download it or it would have been something I would have thought about. It is an actual live cd that came with an ubuntu bible I have gotten from the local library.

I have decided though to download the new version of ubuntu and make a live usb. Do you know where I can get one and how to compile it?

---

### Post by codemaniac on 2012-06-16
If you have no data to save you can try deleting the existing partitions and create newer ones using gparted .Then during install choose Something else select the created partitions, format them and assign to / and /home. If swap created in advance it will automatically use it.

Another pictorial turorial using gparted .
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by kc1di on 2012-06-16
> **RimSide said:**
> I didn't download it or it would have been something I would have thought about. It is an actual live cd that came with an ubuntu bible I have gotten from the local library.

I have decided though to download the new version of ubuntu and make a live usb. Do you know where I can get one and how to compile it?

you can download it from here:

[http://www.ubuntu.com/download]("http://www.ubuntu.com/download")

Here's a page telling you how to make the usb image with a windows machine. 

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
just shout if you need help.

you can also use unetbootin for windows from here:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by scouser73 on 2012-06-16
I've seen the screenshots that you've provided, you need to format /dev/sda2 for the process to complete; so if you format it to EXT4 it will install with no problems.

One question though, is there a specific purpose you're trying to install 10.04 rather than 12.04 which is the latest LTS (Long Term Support)?

---

### Post by RimSide on 2012-06-17
Thank you all for all of the help and tips! I decided to download and try to install Ubuntu 12.04, and it turns out something is wrong with the disk I had. My computer now is working nicely. Thank you for the help

---

