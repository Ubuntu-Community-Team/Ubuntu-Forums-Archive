---
title: "upgrade 9.10 to 10.04 / keyboard not detected"
date: 2010-11-24
forum: General Help
---

### Post by d3v1150m471c on 2010-11-24
Against my instinct, I decided to upgrade 9.10 to 10.04 via update manager. After rebooting i was missing several packages. I was missing my login screen and post "startx" left many things to be desired as my desktop was royally screwed. Also, after launching the desktop mode with startx my keyboard no longer worked. I did a backup with apt-oops_2.0-0 which fixed everything except the keyboard. My keyboard works in recovery mode but as soon as I start "X" and go graphical i get nothing. my Xorg.log is saying keyboard not detected. I have (had) a very complex configuration setup on my account for 9.10 and I'd really like to keep it. So reinstalling is not an option I am currently considering. Can someone please help me to get my keyboard functional? Thanks in advance. Also, would upgrading to 10.10 fix this problem? I have restricted bandwith during the day, and i actually sleep at night, so i'd prefer to do this with minimal downloading. I'm gonna try reinstalling x and see if it helps any. lol please help.

---

### Post by khelben1979 on 2010-11-24
Are the keyboard connected by [USB]("http://en.wikipedia.org/wiki/Usb")? **lsusb** gives output of the exact model number and choice of brand.

---

### Post by d3v1150m471c on 2010-11-24
i reinstalled  xserver-xorg-core with no progress, btw.

---

### Post by d3v1150m471c on 2010-11-24
> **khelben1979 said:**
> Are the keyboard connected by [USB]("http://en.wikipedia.org/wiki/Usb")? **lsusb** gives output of the exact model number and choice of brand.

no but thanks for asking. it's an acer 5515 laptop. lspci nor lshw give me my keyboard, at least not that i've noticed. thus trying to do dpkg-reconfigure console-setup is kinda useless. I tried it already and selected the acer laptop option with no luck.

---

### Post by d3v1150m471c on 2010-11-24
Fixed it :D
```

cat /etc/apt/sources.list > ~/file
cat ~/file | sed 's/lucid/maverick/g' > /etc/apt/sources.list
apt-get update
apt-get remove xserver-xorg-core
apt-get install xserver-xorg-core
shutdown -r 0

```

---

