---
title: "Disk space low on flash drive installation"
date: 2010-01-20
forum: General Help
---

### Post by oldmankit on 2010-01-20
Hi,

I'd really appreciate some help understanding my UNR installation on my 4GB flash drive.

I've tried installing UNR on a 1GB flash drive in the past, and on two occasions it completely broke due to lack of disk space.  When I say broke, it was when I was trying to install or upgrade packages, it said it ran out of disk space, everything slowed right down, and in the end I had to restart.  I was put into a recovery shell and after poking around for about 30 minutes, gave up.  Then reinstalled.

Now my shiny new 4GB flash drive is split into two sections, one for documents (1.9GB) and one for the installation+persistency file (1.9GB).

I went about updating the UNR system, adding software I need (some of which is quite big, anti-virus software, lyx etc), and quickly found the old warning message: disk space low.  Thank heavens, this time it didn't break, but I was able to stop adding anything, hastily make some free space (apt-get clean, delete a big firefox cache), and post this message.  My questions:

[LIST]
[*]how do I find out how much disk space is left on this 1.9GB partition - specifically the persistency file?  I've tried disk usage analyzer, also du -h, but can't really understand it.  I want to be able to see ahead of time when I am short of disk space.
[*]I would like to switch to using XFCE instead of gnome for speed and disk space.  Is this possible? What is the best way to switch, without risking maxing-out disk space and crippling the system again?
[*]is there are way to take a snapshot of the whole partition? I would like to back it up in case it goes haywire again.  Would I just want to copy the persistency file, that's it?
[/LIST]
Well, thanks to anyone who's read this far and is willing to help.
Kit

---

### Post by garvinrick4 on 2010-01-20
Have you looked at this device in gparted?

---

### Post by oldmankit on 2010-01-22
> **garvinrick4 said:**
> Have you looked at this device in gparted?

 This partition is full. It is taken up with all the files needed to run UNR (I think stored in a directory called 'casper), plus the persistency file (called 'casper-rw').  casper is about 600 MB, casper-rw is 1.2GB, which completely fills the 1.9GB partition (when added to all the other files).

But I'm still in the dark as to how much of the persistency file is really being used, so I can calculate if I have enough space to install this or that program.  How can I found out how much of this file is being used and how much space is left?

---

### Post by t0p on 2010-01-22
Have you tried the command *df -h*?  I've never used a flash drive installation, but I imagine the command will work the same as on a regular HDD install.

Incidentally, you have left yourself *no* room for installing further applications or updates.  Are you going to disregard security updates?  Not advisable.  You'd be better off using a larger flash drive. I'd say *at least* 8GB, but the bigger the better.

---

### Post by oldmankit on 2010-01-27
> **t0p said:**
> Have you tried the command *df -h*?  I've never used a flash drive installation, but I imagine the command will work the same as on a regular HDD install.

Regarding your first suggestion, I can't try it because now the installation has gone pear-shaped again (sorry for my British slang). I boot in now, X kinda starts up, but all I can see is a terminal window in the upper-left quadrant of the screen. I can start applications like firefox, but the resolution comes out wrong, and alt-tab won't work.  So that will take me a while to fix... joy!

As soon as it's fixed, I'll try that.

> Incidentally, you have left yourself *no* room for installing further applications or updates.  Are you going to disregard security updates?  Not advisable.  You'd be better off using a larger flash drive. I'd say *at least* 8GB, but the bigger the better.Now it seems to me that one of us has misunderstood things badly.  I expect it's me.

I thought that the casper-rw file (which I said is 1.2GB) is used for everything on top of the basic system (which is stored in casper, 600MB).  This includes security updates (which I've already done), any new programs installed, and any files saved, in /home for example.

---

### Post by oldmankit on 2010-02-05
Everything is packed up in a neat little box now.  Thanks to everyone for their suggestions.

[LIST]
[*]To find out how much space is left in the persistency file (casper-rw), type "df -h" in the terminal.  The first filesystem to be displayed (at least on my computer) is 'aufs'.  This gives you right figures.
[*]To run xfce, I simply made a fresh install using the xubuntu-desktop image (downloaded from the ubuntu website), instead of the the ubuntu-desktop image.  The usb startup creator did this painlessly.
[*]To make a backup of the whole installation, I think I'm right in saying make a copy of both casper and casper-rw.
[/LIST]
And a couple of tips:

[LIST]
[*]Use the "apt-get clean" command to remove unnecessary downloaded files.
[*]Fully updating your system involves downloading and installing a lot of files, using over half  a GB of hard drive space.  A lot of this is freed-up again when installation completes, but this shows why it's really squeezing it to try and install on a 1GB flash drive.  If you're in a tight corner, you could remove a bunch of applications *before* updating.
[*]When running with very limited disk space, you can do a 'minimum installation' of software packages with the following command:
[/LIST]
```
sudo apt-get --no-install-recommends install
```I did this with lyx, which got me a barely functional installation of lyx.  In order to display and print documents, however, I needed to get texlive-latex-base.  Again use the no-install-recommends for texlive-latex-base, in order to avoid the hefty documentation which is bundled with it automatically (even if you select the package in synaptic package manager).

It's taken me a while, but I've finally got what I wanted out of a USB installation of ubuntu.  Well, xubuntu to be precise.

---

