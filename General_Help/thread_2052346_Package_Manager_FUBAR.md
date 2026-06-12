---
title: "Package Manager FUBAR"
date: 2012-09-03
forum: General Help
---

### Post by Bob Saget on 2012-09-03
I am using a Toshiba Satellite L655D-S5159 Laptop with Win7 and Ubuntu.  I decided to boot in Ubuntu today, and just played music through VLC media player.  I had to go somewhere, so I locked my computer.  I came back, logged back in, and I'm getting system program errors, and they all seem to be focused around the Synaptic Package Manager program.  Any time I tried to open it, it will simply crash, and I get the following error message on my top toolbar:

> An error occured, please run Package manager from the right click menu or apt-get in terminal to see what is wrong.  The error message was: ' Error:  Opening the cache (E: encountered a section with no Package: header, E: Problem with Mergelist/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The Package Lists or status files could not be parsed or opened.)'.  This usually means that your installed packages have unmet dependencies.

The error message that this lists is what I get when I open up Synaptic Package Manager.
Update:  This also affects Ubuntu Software Center.
What can I do to fix this?

---

### Post by 2F4U on 2012-09-03
Can you please try

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

