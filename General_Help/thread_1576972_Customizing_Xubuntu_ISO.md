---
title: "Customizing Xubuntu ISO"
date: 2010-09-18
forum: General Help
---

### Post by kenny2009 on 2010-09-18
First of all - I hope this all makes sense and doesn't sound confusing. I'm really, really, sleepy right now.

I'm attempting to customize a Xubuntu LiveCD ISO so it will have adobe flash player for FireFox, remove all languages except English, Spanish, French, and German, install codecs for .mp3 and .avi, and a few other miscellaneous programs. I'm currently using Ubuntu 10.04 LTS (been using it since the beta). I assume that I don't need to have Xubuntu installed and that I can just follow these steps using Ubuntu and still modify Xubuntu.

I have no problem just following a guide word for word... until the guide asks me to make a choice. I'm following [this]("https://help.ubuntu.com/community/LiveCDCustomization") tutorial but when I get to the part that says "If you need the network connection within chroot" I get stuck. How do I know if I need the network connection? Would it help if I knew what chroot meant? I understand what the root of a drive is and I understand root when it comes to the root user account... what is chroot? All I can think of is 'change root'. I'm not sure how that helps me.

Then, the next step says this: "Depending on your configuration, you may also need to copy the hosts file"  How will I need to know what my configuration needs to be? Do I just copy & paste these commands into the command line and if they work I needed them, if it didn't work I didn't need them?

I'm just not sure how to determine if I need things like this. I think the tutorial just assumes I know. I love *nix, I really do. I've been dual booting with Windows for years. I'm just not as familiar with it as I am with Windows. I'm taking a Linux Admin class at college but we're using Fedora 13 and learning commands like "cal" and "shutdown"... That doesn't really help me with these kinds of real life situations, lol.


I'm going to get some sleep and look at this again tomorrow. Hopefully someone is nice enough to offer some help here. If not, hopefully I'll understand it after I sleep.

---

### Post by WorMzy on 2010-09-18
/ is your root directory, chroot makes another directory take over this role for the shell it is run in (so the rest of your system isn't affected, just the terminal that you run chroot in)

The part you're stuck on is asking you whether or not you need to connect to the internet (presumably so that you can install packages from the repos). If you do, then you need to copy over your current internet setup information so that the chrooted shell can use it to access the internet.

chroot is a temporary thing, and can be exited out of with "exit" if something isn't working. So try it without copying over the hosts file and see if you can do what you need to; if you can't, then exit out of it, copy over the hosts file, and try again.

---

