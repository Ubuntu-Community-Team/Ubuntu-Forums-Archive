---
title: "Minimal hardware requirements for 9.10?"
date: 2009-10-20
forum: General Help
---

### Post by ilembitov on 2009-10-20
Hi, people! Couldn't find it anywhere on the official website, no luck. Wouldn't ask with my current laptop (Dell Inspiron 1525 with a 2.4 Core 2 Duo), but I'm seriously considering a switch to a second-hand HP Compaq TC1100: it's lightweight, it's flexible, it's sexy. And I love the idea of getting a cool desktop computer with it's docstation. The thing is, however, that it only has Pentium M 1.2 GGhz and 2 gigs of RAM. So the question is: as long as I'm only running the apps from the default set, can I expect decent performance with Ubuntu 9.10 (and I mean GNOME edition). I mean, people have been running it on netbooks, and this CPU seems to be much more powerful than Atom.

---

### Post by P4man on 2009-10-20
the most limiting factor is almost always RAM. With 2GB if anything, you got way more than is needed. Yes it will run it fine, though the real question I think is, will it support the touchscreen?

edit: looks like even ubuntu 7.04 supported pretty much everything out of the box:
[http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

Looks good to me

**edit2: videocard might be a bit of a problem. Looks like it has an old nvidia card. I dont think youll be able to install binary nvidia drivers, meaning you wont be able to do much if any 3d or compiz. I fear even browsing webpages might be sluggish**

---

### Post by Giblet5 on 2009-10-20
> **ilembitov said:**
> Hi, people! Couldn't find it anywhere on the official website, no luck. Wouldn't ask with my current laptop (Dell Inspiron 1525 with a 2.4 Core 2 Duo), but I'm seriously considering a switch to a second-hand HP Compaq TC1100: it's lightweight, it's flexible, it's sexy. And I love the idea of getting a cool desktop computer with it's docstation. The thing is, however, that it only has Pentium M 1.2 GGhz and 2 gigs of RAM. So the question is: as long as I'm only running the apps from the default set, can I expect decent performance with Ubuntu 9.10 (and I mean GNOME edition). I mean, people have been running it on netbooks, and this CPU seems to be much more powerful than Atom.

It should work fine as long as you don't want tons of eye-candy.

I have 9.10 running on an Omnibook 6100 (1.3GHz Pentium III, 512MB RAM). That's not a fast system.

It serves as a media server, DNS server, POP3 and IMAP server, smtp relay, Samba server, and a web server. Always on.

Performance is decent, even with all of those services running.

---

### Post by ilembitov on 2009-10-20
The thing is 5-6 years old. So the problem is not really whether Ubuntu supports the hardware, but rather how well - there are lots of quirks (automatic portrait/landscape switching, etc), extra buttons, etc. I've seen the howto for 9.04, I wonder how many manual actions still needed with 9.10

---

### Post by P4man on 2009-10-20
does anyone know how well a geforce4 is supported in jaunty or karmic?

---

### Post by Giblet5 on 2009-10-20
> **ilembitov said:**
> The thing is 5-6 years old. So the problem is not really whether Ubuntu supports the hardware, but rather how well - there are lots of quirks (automatic portrait/landscape switching, etc), extra buttons, etc. I've seen the howto for 9.04, I wonder how many manual actions still needed with 9.10

Again, it depends on what you want it to do:

High-end 3D graphics workstation stuff: no way!

Very capable workstation/server for image editing, surfing, and IMing: sure.

Your laptop is a lot more capable than the one I'm using for a rather massive server, and it does just fine for general use.

The fan on that OB never even comes on... :)

---

### Post by Giblet5 on 2009-10-20
> **P4man said:**
> does anyone know how well a geforce4 is supported in jaunty or karmic?

Pretty well, once you install the "restricted" nvidia driver.

Compiz performance might be jittery at high (1920x1200+) resolutions and trickier effects, but it'll work well.

---

### Post by P4man on 2009-10-20
> **Giblet5 said:**
> Pretty well, once you install the "restricted" nvidia driver.
.

There still is one for jaunty and newer? I thought the geforce4 **mobile** had the same driver requirements as the geforce2 and was no longer supported by anything other than "nv" (unlike geforce4 Ti's and even MXs). I could be wrong though. perhaps worth checking on nvidia's site before buying.

---

### Post by Giblet5 on 2009-10-20
> **P4man said:**
> There still is one for jaunty and newer? I thought the geforce4 **mobile** had the same driver requirements as the geforce2 and was no longer supported by anything other than "nv" (unlike geforce4 Ti's and even MXs). I could be wrong though. perhaps worth checking on nvidia's site before buying.

I just helped a guy running Jaunty. He's having performance problems using gnome-shell on his geforce4 ti 4200 (config issue, I think).

The nnnM nvidia chips are poorly supported on *every* OS. Nvidia doesn't want to test them all, so they exclude them automatically. There's a website that fixes the .inf files and makes them available. How bad is that?

It's supported on Jaunty for now, but it'll probably be supported for a long time. That's a decent and popular card.

---

### Post by philinux on 2009-10-20
> **ilembitov said:**
> Hi, people! Couldn't find it anywhere on the official website, no luck. Wouldn't ask with my current laptop (Dell Inspiron 1525 with a 2.4 Core 2 Duo), but I'm seriously considering a switch to a second-hand HP Compaq TC1100: it's lightweight, it's flexible, it's sexy. And I love the idea of getting a cool desktop computer with it's docstation. The thing is, however, that it only has Pentium M 1.2 GGhz and 2 gigs of RAM. So the question is: as long as I'm only running the apps from the default set, can I expect decent performance with Ubuntu 9.10 (and I mean GNOME edition). I mean, people have been running it on netbooks, and this CPU seems to be much more powerful than Atom.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

For eye candy I think the gforce4 might be a problem. Best way is try out the live cd.

---

### Post by P4man on 2009-10-20
> **Giblet5 said:**
> I just helped a guy running Jaunty. He's having performance problems using gnome-shell on his geforce4** ti** 4200 (config issue, I think).
A ti, yes. But  I think the geforce 4 **mobile** (not Ti or MX)  really is a GF2 based card, Ill look for it later. I think it was one of those renaming tricks nvidia is so good at

---

### Post by philinux on 2009-10-20
Just checked synaptic and the nvidia-glx-96 supports the gforce4.

---

### Post by P4man on 2009-10-20
Yeah it looks like I was wrong. Geforce4 Go is supported by the same drivers and the GF4 Ti and MX

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

I could have sworn it was different, but I guess not :)

---

