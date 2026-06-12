---
title: "Desktop Cube, right click, nautilus help"
date: 2010-02-08
forum: General Help
---

### Post by cro_409 on 2010-02-08
Hi all,

I am having a massive set of problems on my Ubuntu 9.10.

First off, is there a way to get individual backgrounds for different workspaces on the desktop cube.  There is on the Windows version of the desktop cube and I can't imagine Linux, a group that prides themselves on things like this, could overlook such a large feature.

Second, my right click button my mouse doesn't do anything on the desktop.  But if I use it on an icon, it pulls it up.  Shouldn't there be a right-click menu on the desktop?

Lastly, I added a program from the synaptic manager called nautilus-wallpaper, hoping it would help with my first problem, but I can't find the download anywhere.  I even alt-f2 gconf-editor to get into the nautilus.

For the most part I am new to Ubuntu, so I will need very specific insturctions, I did have Ubuntu in the past but nothing I used would work on it.  My video games weren't compatible, my internet connection wasn't accepted.  Please tell me that Linux has made improvements, because so far almost everything offered here I can also get on Windows, except for the painting fire on my screen and making it rain on my desktop, but those reasons are not enough for Ubuntu to run 300 gigs on my 500 gig laptop.

---

### Post by darolu on 2010-02-08
Yes, you can get individual backgrounds for each workspace; first do the alt-f2 gconf-editor and go to apps/nautilus/preferences and disable "show desktop"; then from the same alt+F2 window open your CCSM (if you don't have it install with sudo apt-get install compizconfig-settings-manager) and go to the Wallpaper option and choose your wallpapers. If you need more detailed help click [HERE]("http://tinyurl.com/yasnuuf").

Second problem = configure your video drivers properly, this **may** be caused by compiz, if you have a laptop with integrated video card you may need help to do this, create a new thread with your video card model number in the title. Notice that the previous method (disabling nautilus show-desktop) disables contextual menu on the desktop, if this bothers you there are other solutions (like wallpapoz).

Programs added from synaptic are already downloaded and installed you won't find and don't need to find "the download", if you do need the .deb file go here: [http://packages.ubuntu.com/en/karmic/nautilus-wallpaper](http://packages.ubuntu.com/en/karmic/nautilus-wallpaper) and get it (you'll find what this package does there too).

Lastly, Ubuntu (or any other linux distro) is NOT MS Windows, do NOT expect it to work like Windows (actually developers work hard to make it different), Windows programs do NOT run on Linux platforms, there are win-emulators like Wine that let you run **some** Windows applications, but they won't run like they run in the platform they are designed for. Linux (the kernel) is improved constantly, most distros (like Ubuntu) release improvements (updates) regularly, we get new versions of Ubuntu every 6 months, if you want to know about improvements read the release notes; you can find Linux (the kernel) notes here: [http://kernel.org/](http://kernel.org/) and Ubuntu notes here: [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

You can determine how much hard disk space you want Ubuntu to use, when you install it, you can configure partitions to whatever you need using the manual option at the "prepare disk" step.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by cro_409 on 2010-02-11
Please understand that I am not a fan of Windows.  They are a monopoly and I look forward hopefully for a day where they will be taken over by better programs.  But I need an OS that accepts my programs and is efficient and convenient.  While Linux is fun, pretty, and has many many features, I still feel clumsy using it.  I hope I get used to it, my experience with computers is advanced, but Ubuntu has given me a set of problems I am inexperienced with, such as these two new problems that have been presented to me.

First off, everytime I try to open Firefox I am told that it is already running but not responding and that session needs to be closed first.  Well, I have checked all of my workspaces and can not find another Firefox session, responding or not.

Also, when I am on the Ubuntu side, the sound doesn't work.  I have checked the computers volume settings, the Ubuntu volume settings up on top, and several different website's volumes control.  I have also tried plugging in my desktop speakers, which don't work either.  Interestingly, the system sounds, such as when an alert comes up, work fine, but anything that runs off my CD's, internet, aMSN, and VLC don't work. This problem is resolved when I go back to the Windows side.

Currently I am on my secondary laptop, since I cannot connect to Firefox due to a hiding session on Ubuntu. 

Thank you in advance for the specific help.  That is one nice thing about Ubuntu, the support is for the most part, friendly, thorough, and free.

---

