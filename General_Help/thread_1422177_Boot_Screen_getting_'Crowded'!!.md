---
title: "Boot Screen getting 'Crowded'!!"
date: 2010-03-05
forum: General Help
---

### Post by Saurabhdua on 2010-03-05
Hello There!:popcorn:

Iam using Ubuntu 9.04, probably the latest release!?

However, please steer me through the ever-growing entries cropping up during the boot, that lists various releases of past Ubuntu flavors along with their respective 'Recovery Modes'!!!;)

Things are really getting crowded...Is there a way to hide/get rid of the past releases?

---

### Post by wojox on 2010-03-05
Are you talking about the kernels or different versions like Kubuntu and xubuntu?

You could use System>Admin>Computer Janitor.

Or Synpatic. Search the kernel number and mark for removal/complete removal.

---

### Post by Saurabhdua on 2010-03-05
Yes, Iam exactly talking about various Kernels(Herd of Kernels)!
What's the worth of these? ....& aren't there must be a mechanism by default through 'Updates' that can prevent such a thing?

---

### Post by BbUiDgZ on 2010-03-05
> **Saurabhdua said:**
> 
What's the worth of these?

if a new kernel update breaks anything you can boot into an older one to fix the issue.

I remove them all except the last known working one just incase

---

### Post by doas777 on 2010-03-05
I always used Startup-manager to limit it to 2 kernels, but last I heard it did not work with grub2, so I have been waiting for a good front end. will probably have to do it by hand, as I'm in the same boat. have to scroll down several pages to get to my dualboot entries if I wanna play a game

---

### Post by Nburnes on 2010-03-05
I use Computer Janitor to erase all the other older kernels, except for the last two. I keep the one I am using, the new one, and the one that worked previously before.

---

### Post by suntom on 2010-03-05
[QUOTE=Easy Linux tips project]After a kernel update, the old kernel still shows in the Grub boot menu. Because you might want to start your machine with the old kernel, if the new kernel shouldn't function well.
[/QUOTE]
Read more of it **[here]("http://sites.google.com/site/easylinuxtipsproject/faq#TOC-B.-Remove-old-kernels")** and how to remove old kernels.

---

### Post by Enigmapond on 2010-03-05
From what I understand, it's always a good thing to keep one or two of the older kernels just in case you have a mishap with a new one. The others I delete with Ubuntu Tweak which I find to be a very helpful programme. This will also clear out old cache entries and packages that are no longer in use plus numerous other things.

---

### Post by oldfred on 2010-03-05
If still using grub legacy you can edit menu.lst to show just two kernels. The do not take much room and I only periodically delete very old kernels.
 Find the last line in this section and change the howmany to 2 like my entry:
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]2[/COLOR]

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

### Post by hatalar205 on 2010-03-05
Try "Ubucleaner.sh". A simple and useful script. Search in the google and try it. Also it will make your computer a bit faster.

---

### Post by Enigmapond on 2010-03-05
> **hatalar205 said:**
> Try "Ubucleaner.sh". A simple and useful script. Search in the google and try it. Also it will make your computer a bit faster.

I like this script, except for the fact it deletes all old kernels. I like to keep one just in case but I have never had to use an old kernel. It works well though...:) Thanks for the tip but next time try not to tell someone to Google it. It's actually against the rules here. Just post the link...

[http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html](http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html)

Cheers!

---

### Post by ssulaco on 2010-03-05
Another option

> **ssulaco said:**
> Keep the two most current kernels and remove the rest,you can remove unwanted kernel images and headers via the terminal
```
sudo apt-get remove --purge 2.6.xx-xx-*
```
where xx is the kernel you want to remove,

---

### Post by Saurabhdua on 2010-03-07
Thanks for the post, I have used 'Computer Janitor' to remove whatever was getting listed over there. However, working with 'Synaptic' is intimidating & would rather avoid even seeing the same again!

---

### Post by Saurabhdua on 2010-03-07
As per the link quoted by Suntom, one should NEVER use Computer Janitor to clean System as this is "Buggy" & is "hardly of any good"?!

---

### Post by Saurabhdua on 2010-03-07
Hello There!

Please help me with 'Synaptic Manager' as there are plethora of entries in it related to past kernels. I wish to retain 2.6.28.18(along with respective Recovery Mode) as well as 2.6.28.17(with respective Recovery Mode).

Wish to get rid of other 4 entries coming up in Grub Menu viz. 2.6.28.16 & 2.6.28.11(respective Recovery Modes included).

I made a 'Search' with Kernel 28 & a lot of entries came up with few marked in 'Green Boxes' on the left(probably indicating as installed)?! Now, should I 'Right Click' on every 'Green Box' associated with .16 & .11 & mark them for complete removal? There are a No. of these like generic, Server....etc....etc.

Is this a correct way to proceed?

---

### Post by Saurabhdua on 2010-03-07
> **Enigmapond said:**
> From what I understand, it's always a good thing to keep one or two of the older kernels just in case you have a mishap with a new one. The others I delete with Ubuntu Tweak which I find to be a very helpful programme. This will also clear out old cache entries and packages that are no longer in use plus numerous other things.

Please guide me more on where to find & how to install your 'Ubuntu Tweak' software?

---

### Post by vallvi on 2010-03-07
If the issue is a crowded boot screen, just install 'startup manager' from the software center. Under the 'advanced' tab of this little program you can set the number of kernels shown at startup. I've set it to 2, you don't really need more.

I wouldn't start deleting kernels, unless you know exactly what you're doing

Good luck!

---

### Post by Saurabhdua on 2010-03-07
Iam sorry but, What do you mean by 'Software Center'? Is that the Add/Remove Programs section?

---

### Post by Swagman on 2010-03-07
You get ubuntu-tweak from get-deb

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=ubuntu+tweak](http://www.getdeb.net/updates/Ubuntu/9.10/?q=ubuntu+tweak)

Your'll need to follow the destructions to enable GetDeb repositories first though. (and getdeb is crawling at the minute)

---

### Post by doas777 on 2010-03-08
> **vallvi said:**
> If the issue is a crowded boot screen, just install 'startup manager' from the software center. Under the 'advanced' tab of this little program you can set the number of kernels shown at startup. I've set it to 2, you don't really need more.

I wouldn't start deleting kernels, unless you know exactly what you're doing

Good luck!

has startup-manager been upgraded for grub2 in the repos?

---

### Post by drs305 on 2010-03-08
> **doas777 said:**
> has startup-manager been upgraded for grub2 in the repos?

Yes and no. The latest version in the standard repositories is now 1.9.13. It has been updated, but only to exclude the features that are no longer available for Grub 2. 

The following are listed as options in Lucid:
Timeout
Default OS
Display resolution/bit depth
Boot splash/text options
Bootloader menu resolution
Rescue floppy creation

I haven't tried using all these options with Grub 2 but the redesigned interface and elimination of some of the older options suggests they will work with G2.

There are workarounds for some of the missing features. A few are detailed in the links in my signature line but you would have to be a real geek to want to try to use them. ;-)

---

