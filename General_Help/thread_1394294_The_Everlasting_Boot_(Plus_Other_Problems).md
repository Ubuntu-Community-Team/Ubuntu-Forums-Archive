---
title: "The Everlasting Boot (Plus Other Problems)"
date: 2010-01-30
forum: General Help
---

### Post by Kemono on 2010-01-30
Here we go

For two days now I have been trying to install Kubuntu on my external hard drive which had a Mint 7 installation that worked just fine. The thing is, the install is going fine but after that everything goes downhill. Honest to god this makes me so mad I'll smash, I'll bash, I'll... probably cry myself to sleep.

Anyway, here are the problems I'm facing:

[LIST]
I reach GRUB no problem but when I choose Ubuntu 9.10 (the first one) and press enter it takes about a minute to exit grub, then about 20 seconds to reach boot screen and then 30 to 'till I reach KDM.[/LIST]

[LIST]
After I type in my user name and password I press enter and in the middle of the login screen everything goes black with my courser shaped like a black X with white outline in the center of the screen. When that happens nothing works, not &#8220;Ctrl+Alt+Delete&#8221;, not &#8220;Ctrl+Alt+Backspace&#8221;, not even the virtual terminals. I have to do a hard reboot which makes my hard drive useless for a while.[/LIST]

When I (barely) entered recovery mode I tried to start X and I got a whole screen of **EXT3-fs error device (sdb5) something about not reading something**; I should've written it down, I know. At first I thought my hard drive was failing. I ran the Knoppix Live USB to check it and it was fine.

For the love of everything that computes I cannot solve this puzzle. Why is it doing this? Is it because I installed it from a USB stick? Is it because of GRUB 1.97 Beta4 (really? Beta loader software in an official release?). Is it because of something faulty in Kubuntu?

Any help is welcome. Thanks.

---

### Post by Kemono on 2010-01-31
I found an old Kubuntu 9.04 x84_64 CD and installed it. Everything went fine and it booted no problem. So far this makes me 100% sure the new Kubuntu installation fails either because it's installed from USB or there's something buggy in the 9.10 version.

Anyone? No? OK, I'll wait.

---

### Post by Kemono on 2010-01-31
Anyone, please?

---

### Post by theozzlives on 2010-01-31
I don't like KDE 4.x. That and Amarok 2.x don't work well in my opinion. I'd go with genuine Ubuntu that's always worked for me. If you absolutely must have KDE I think Pioneer Linux still uses 3.5, it's based on Ubuntu.

---

### Post by Kemono on 2010-01-31
I don't mind Gnome. I know it can look good but somehow to me it doesn't look as exciting as KDE. I haven't tried the new Amarok (mind you I haven't used a computer since September) but that doesn't mean I'll use it. There are other players.

P.S. I don't think the DE is causing the problems.

---

### Post by Kemono on 2010-01-31
Does anybody have any idea why this is happening?

---

### Post by Kemono on 2010-02-01
Could it be GRUB2? No clue.

---

### Post by J V on 2010-02-01
```
man md5sum
```Check the sum

---

### Post by Kemono on 2010-02-01
It checks out.

---

### Post by Kemono on 2010-02-02
Here's the error I get: **EXT4-fs error (device sdb5): ext4_find_entry: reading directory #** (some random number) **offset 0**. Hope someone knows something I don't.

---

