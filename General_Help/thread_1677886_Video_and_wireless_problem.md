---
title: "Video and wireless problem"
date: 2011-01-29
forum: General Help
---

### Post by w0nker on 2011-01-29
First let me say that I am new with Linux and I am trying to learn as much as possible.

My first issue is with the Nvidia drivers, after installing I restarted and no longer had a gui, just command line. While attempting a few fixes I have found on these forums, I ran into another issue...

I cannot seem to get connected to the internet from command line to try any fixes for my video problem. I am trying to connect via wireless. I have been using this page as reference [http://linux.die.net/man/8/iwconfig](http://linux.die.net/man/8/iwconfig)

While I do have access to a wired connection, I would like to figure out this wireless issue as well.

I have a Samsung Q430 laptop and it was up and running in Ubuntu just fine until I tried to update the video drivers.

Any help or info is appreciated!

---

### Post by SeijiSensei on 2011-01-29
> **w0nker said:**
> My first issue is with the Nvidia drivers, after installing I restarted and no longer had a gui, just command line.

Can you log in with your user name and get a console prompt (the dollar sign)?  If so, try typing "startx" at the prompt and see what happens. 

If it crashes, try running "sudo nvidia-xconfig" and see if that helps.

---

### Post by w0nker on 2011-01-29
> **SeijiSensei said:**
> Can you log in with your user name and get a console prompt (the dollar sign)?  If so, try typing "startx" at the prompt and see what happens. 

If it crashes, try running "sudo nvidia-xconfig" and see if that helps.

Yes, I can log in from the command line, startx does result in an error. 
Entering sudo nvidia-xconfig gives me

Using X configuration file: "/etc/X11/xorg.conf"
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

But nothing changes after that. I think I am stuck without internet access to try the other fixes I have found on here.

---

### Post by w0nker on 2011-01-29
So does anyone have any info on how to connect via wireless from a command line, or can point me in the right direction to find that info?

---

### Post by w0nker on 2011-01-29
Ok, well one of my issues has been resolved, the video problem with xserver not starting after installing Nvidia driver. Found this on another thread here.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure -phigh xserver.xorg
sudo reboot now

After that, the gui was working again.

Still dont know how to connect to my wireless router through command line though.

---

### Post by gusbeto37 on 2011-02-05
Hi,

I have a similar problem with wifi. I am using 10.04 and installed the backport-module-wireless-lucid , also tried the bleeding edge drivers and have had no luck at all. 

The adapter is an  athero wireless AR9285 and it does seem to "work" as it is detected by ubuntu, sees the networks available but fails to connect to anyone of those. It continoulsy asks for the password

---

