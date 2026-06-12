---
title: "Monitor troubleshooting got tedious?"
date: 2012-07-30
forum: General Help
---

### Post by Jay Christnach on 2012-07-30
Maybe I should have posted this as a general discussion. But I have some questions about how things have changed with monitors and the Xserver.

A friend of mine often calls me for IT related poblems and I was often able to help her over the phone. When we still lived together I convinced her to switch to linux. She is quite happy with it, especially since things got really userfriendly on the desktop. Now she has 2 "specialists" she can rely on if things get more complicated and involve the use of a terminal.

The last time she called was when her monitor stopped working and she had hooked another one up. The monitor complained about wrong resolution settings and didn't show the desktop. 

Years ago we had CRTs and struggled with graphic card drivers and the xf86.conf file and the screen modes. Back then I was even used to type startx because I wanted at least a command prompt if X was unable to start.

The main question now is this one: How do you expect fixing a monitor problem, if you don't even see what you type? I did a quick search and found xrandr, but how do you want to use a command line if you can't see what you type or even if you're using a terminal?

So I recalled the shortcuts that had been useful in the days of Xfree86. So I told her to try ctrl+alt+numplus and -minus. Didn't change anything. I tried it myself on my computer, it seemed this function had gone.

Then I thought, ok, we will at least need a terminal and told her to try ctrl-alt-f1 to login to a normal console. No hope, didn't work. I tried it myself (had not done this for some time). No! My monitor which I'm really happy with because of its really sharp image would solely show an "out of range" message. This one now has a dvi input connected to the hdmi output of my onboard graphics card.

Next thing we tried was to login with ssh from her laptop (I knew the server was installed because I did it to be able to do remote troubleshooting for her). But she did not know an ip address (remember we were talking on the phone) and the router wasn't configured to do port forwarding....

One thing I really appreciated about linux was the possibility to be informed and to tweak things if necessary. (I was running gentoo for years and eventually got tired of the geekyness) These days boot messages are gone and you only see some screen flickering until you get to the desktop login screen. 

I'm sure one could still today change some configuration files to get these keyboard shortcuts back or get to a plain console again. Why are these functions gone now, or are there now other ways to interact with the computer if you have trouble with the display driver for instance? Do we have to keep an old crt in the attic or be sure we can login remotely?

Sorry for the long post. I'm looking forward to your suggesstions.

Kind greetings,
Jay

---

### Post by cpugeek on 2012-07-30
I understand the woes of Xserver I have dealt with it not working many a time. I can't say that they expect you to be able to work without a monitor but I can make a suggestion, try booting into single user mode to make changes to get it working again. [Here]("http://www.computersecuritystudent.com/UNIX/UBUNTU/lesson2/index.html") is a link to how to boot into it. Ignore the fact that it is a virtual machine and you should be able to boot into single user mode to make changes.

Hope this helps!

---

### Post by Jay Christnach on 2012-07-31
Thanks for the suggestion. That's of course a simple and good solution, I didn't think of it straight away.
This would be the same as booting to "recovery mode", I think.
The scripts add such an entry to grub2 for every new kernel.
Grub2 got far more complicated than the old grub.
Nowadays the menu doesn't even show up if you don't hit the right key at the right moment when starting up the computer.
On my machine here I changed the time-out values in /etc/default/grub. I also removed the quiet and splash optionsand set the graphic mode to text.  I also set verbose to yes in /etc/default/rcS. So now I have my boot messages again and a few seconds to choose to boot with other options.
I still could not figure out how to get to a vty with ctrl-alt-1. I think the monitor can't handle that mode. This would be nice to have sometimes. Perhaps for killing the x server when settings weren't right. 

best regards

---

