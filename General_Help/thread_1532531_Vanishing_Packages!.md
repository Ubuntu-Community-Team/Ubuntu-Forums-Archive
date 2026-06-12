---
title: "Vanishing Packages!?"
date: 2010-07-16
forum: General Help
---

### Post by xteraco on 2010-07-16
Hello, I'm new to Ubuntu. I'be been using Linux for quite some years now off and on. I come from Slackware and Gentoo heh. Anyway...

At first I blamed the synaptic package manager. I installed Filezilla, rebooted, and when I got back Filezilla was missing. I used Ubuntu Software Center to get it back and thought I was done.  Then a few hours later I notice that a few more apps were missing! These apps had been installed with the Ubuntu Software Center, so my original suspicion of synaptic being the problem was wrong.

Why would my installed software be disappearing at random?

---

### Post by xteraco on 2010-07-19
bump

---

### Post by WorMzy on 2010-07-19
Is it actually disappearing, or merely just not showing up in gnome-panel menus?

Can you run the program through a terminal or by pressing Alt+F2?

---

### Post by xteraco on 2010-07-19
I tried running them from the terminal emulator with no success. :???:

---

### Post by WorMzy on 2010-07-20
That's worrying. Packages require root access to remove, so they shouldn't just disappear.

I'd boot into a LiveCD and run e2fsck on the partition that you've installed Ubuntu on. To find out which one you installed on, run
```
sudo blkid -c /dev/null
```
and look at the output for
```
/dev/sdc2: LABEL="Lucid" UUID="097bbeed-7751-448f-bfb5-01f9bc9d76ac" [COLOR="Red"]TYPE="ext4"[/COLOR]
```

Once you know which is the right partition (in this case it's /dev/sdc2), run
```
sudo e2fsck -fp /dev/sdc2
```

e2fsck will check the partition for problems, fixing any simple problems it can find, and alerting you to any serious problems it encounters. After it's finished (presuming you get no serious errors), try booting back into Ubuntu.

---

