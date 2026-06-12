---
title: "Can no longer use Ubuntu wireless issues. Other Debian-based recommendations?"
date: 2010-02-15
forum: General Help
---

### Post by narnie on 2010-02-15
Hello,

I am a Ubuntu/Ubuntu-based linux fan but sadly I have a computer based on the intel 3945ABG chipset that Canonical as broken (the drivers for this chipset work fine in Debian. It is evidently due to patchs Canonical has added to the drivers). In a nutshell, I need a Debian-based Gnome distro with good driver/codec support built in that doesn't worry as much about "free-ness" nor legal pitfalls in certain countries about codecs.

This is seen at bug report:

[http://intel 3945ABG]("http://intel 3945ABG")

Sad, too, is that Canonical seems to not be interested in fixing this bug. In fact, with each new distro update, the bug seems to get worse. With this track recored, I don't have high hopes for Lucid.

I really need to update the laptop it is on. I am looking for a good Gnome-based debian distro, but prefer one where I won't have to do a whole bunch of downloading "non-free" things like drivers and such (not even sure how to do this since medibuntu is for Ubuntu base distros and I'm not sure if it will work with a "non-patched" Debian repo.

Seems like most debian branches are in fact also Ubuntu branches. I had high hopes for Mepis, but it is KDE-based, and I don't want to go that way. After making the switch to Gnome almost a decade ago, I'm not wanting go mess with KDE anymore.

I have to avoid the Ubuntu distros as they have the same problem (for example, Linux Mint is what I have on this laptop as the wireless sort of worked if just browsing the web but download large files breaks it. It is essentially non-function in Jaunty and Karmic.)

I will keep using Ubuntu Netbook Remix on the 4 netbooks we own. And Mint on the desktop and My personal laptop. I would just like advise on a good Debian to use for this other certain laptop.

With thanks,
Narnie

---

### Post by pastalavista on 2010-02-15
Have you tried [PCLinuxOS]("http://pclinuxos.com/")? It works well on all my machines but I still like Ubuntu better. You can add any deb repository to Ubuntu if the ones Canonical supplies don't work. Actually any Linux driver can be used. It isn't always easy but it's almost always doable.

---

### Post by narnie on 2010-02-16
> **pastalavista said:**
> Have you tried [PCLinuxOS]("http://pclinuxos.com/")? It works well on all my machines but I still like Ubuntu better. You can add any deb repository to Ubuntu if the ones Canonical supplies don't work. Actually any Linux driver can be used. It isn't always easy but it's almost always doable.

Evidently from reading the bug, the issue is in the kernel (courtesy of Ubuntu patches), not the driver itself, so using a different deb package won't work I'm afraid. It is interesting reading to see the hoops people have gone through to try to get this working. All to no avail.

PCLinuxOS is not on my list because as I stated above, I want a Gnome desktop, not a KDE like PCLinuxOS. I am asking for Debian-based distros (not Madriva like PCLinuxOS) because I want to stick with .deb package managers based on apt/Synaptic.

I know I'm being picky, hehe. I really thought there would be more Debian-based distros (that are current, at least).

Yours,
Narnie

---

### Post by pastalavista on 2010-02-16
> **narnie said:**
> Evidently from reading the bug, the issue is in the kernel (courtesy of Ubuntu patches), not the driver itself, so using a different deb package won't work I'm afraid. It is interesting reading to see the hoops people have gone through to try to get this working. All to no avail.

PCLinuxOS is not on my list because as I stated above, I want a Gnome desktop, not a KDE like PCLinuxOS. I am asking for Debian-based distros (not Madriva like PCLinuxOS) because I want to stick with .deb package managers based on apt/Synaptic.

I know I'm being picky, hehe. I really thought there would be more Debian-based distros (that are current, at least).

Yours,
Narnie

You should have at least looked into the link I gave you. PCLinuxOS has a Gnome version and it uses Synaptic/apt/dpkg package management. I was aware of what you were looking for because I did read your post.

---

### Post by MCVenom on 2010-02-16
> **narnie said:**
> Evidently from reading the bug, the issue is in the kernel (courtesy of Ubuntu patches), not the driver itself, so using a different deb package won't work I'm afraid. It is interesting reading to see the hoops people have gone through to try to get this working. All to no avail.

PCLinuxOS is not on my list because as I stated above, I want a Gnome desktop, not a KDE like PCLinuxOS. I am asking for Debian-based distros (not Madriva like PCLinuxOS) because I want to stick with .deb package managers based on apt/Synaptic.

I know I'm being picky, hehe. I really thought there would be more Debian-based distros (that are current, at least).

Yours,
Narnie
What about **Debian?** :D

---

### Post by MCVenom on 2010-02-16
Oops, just noticed the 'current' thing... Did somebody say SOL? :p

---

### Post by narnie on 2010-02-17
> **BlackOtaku said:**
> What about **Debian?** :D

Debian doesn't seem to meet my requirements because there is soooo much that needs to be installed that are not in the repos like one can get in medibuntu, etc.

I was hoping to just use Debian until I started to research it on this.

---

### Post by narnie on 2010-02-17
> **pastalavista said:**
> You should have at least looked into the link I gave you. PCLinuxOS has a Gnome version and it uses Synaptic/apt/dpkg package management. I was aware of what you were looking for because I did read your post.

Well, I didn't notice the link, but went to distrowatch and didn't see a gnome option but I'll check further on this and on further research saw that it uses apt/Synaptic BUT uses rpms as the package, NOT debs.

Thanks,
Narnie

:)

---

### Post by michaelzap on 2010-02-17
You might try the latest Eeebuntu (version 4 beta). Despite the name, this version is based on Debian and isn't specific to the Eee PC. Should be out of beta shortly.

---

### Post by wojox on 2010-02-17
I know you like Gnome but have you seen Gnome-3.0 ?

You should try KDE-4.4

---

### Post by waynefoutz on 2010-02-17
> **narnie said:**
> Well, I didn't notice the link, but went to distrowatch and didn't see a gnome option but I'll check further on this and on further research saw that it uses apt/Synaptic BUT uses rpms as the package, NOT debs.

Thanks,
Narnie

:)

Here is the link to the gnome version:

[http://pclinuxos.com/?page_id=184]("http://pclinuxos.com/?page_id=184")


I hope you have better luck with it than I did. Virtually nothing worked out of the box for me.

---

### Post by MCVenom on 2010-02-17
> **wojox said:**
> I know you like Gnome but have you seen Gnome-3.0 ?

You should try KDE-4.4

I second that, when it starts appearing (hopefully that 'when' is an if) in Ubuntu I'm switching to Kubuntu :p

---

