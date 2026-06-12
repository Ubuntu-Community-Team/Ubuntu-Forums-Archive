---
title: "ubuntu 12.04 crash?"
date: 2012-06-10
forum: General Help
---

### Post by nick725536 on 2012-06-10
hello


i'm completely new to ubuntu/linux so please excuse my ignorance. anyway i installed ubuntu 12.04 32bit on a 1 year old asus laptop. after installation i immedately did a check for software updates and updated everything that came up, about 250 updates. so whenever i start ubuntu everything is fine but about 5 minutes in like clockwork i get an error that just says system program problem detected. this happens even if i start no programs. also did not install any other software. if this were windows i would check the event logs to see if i could find any clues but i'm clueless on linux. how can i find out exactly what this problem is? thank you in advance for your help,.

---

### Post by chienpo on 2012-06-10
> **nick725536 said:**
> hello


i'm completely new to ubuntu/linux so please excuse my ignorance. anyway i installed ubuntu 12.04 32bit on a 1 year old asus laptop. after installation i immedately did a check for software updates and updated everything that came up, about 250 updates. so whenever i start ubuntu everything is fine but about 5 minutes in like clockwork i get an error that just says system program problem detected.

How is the error displayed? Is it in a pop-up window? Does the whole screen change and display the message? Is it in a dialog box?

> **nick725536 said:**
> this happens even if i start no programs. also did not install any other software. if this were windows i would check the event logs to see if i could find any clues but i'm clueless on linux.

What happens after the message is displayed. Does the system still run? What works? What doesn't? Is it completely frozen?

> **nick725536 said:**
> how can i find out exactly what this problem is? thank you in advance for your help,.

You're on the right track by asking for help. Go ahead and give us as much detail (even if it seems superfluous) and we'll continue to try and help you figure it out.

---

### Post by nick725536 on 2012-06-10
1) it's a small pop up
2) i get two choices send or dont send. whatever i click the pop up goes away and the system seems stable


hope i can get this fixed as i'm a tried and true windows user but really want to give ubuntu a try. except for this problem i like it so far.

---

### Post by nick725536 on 2012-06-11
anyone?

---

### Post by chienpo on 2012-06-11
You ought to take a look at:

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Something is probably crashing and the wiki guide above explains how to get more details on the problem and how to report a bugs to the appropriate location.

At the very least, you'll need to look for files in the "/var/crash" directory to see if/what is in fact crashing. If you need help interpreting what's there, you can always do a detailed directory listing "ls -la /var/crash" in a terminal window and paste the output here.

You may also be asked to post or share the contents of any applicable log files.

---

