---
title: "Getting Started"
date: 2011-04-19
forum: General Help
---

### Post by benc1213 on 2011-04-19
I have just downloaded ubuntu 10.10 and I am burning it on a cd to be installed completely on my laptop alongside nothing. Do you guys have anything you can recommend to be to help get started using ubuntu? What are some good programs to use? What are some things I should tweak stuff like that.

I do have one question though. What kind of slim os can I run on a virtual machine to allow me to steam netflix? What do you guy use and what should I use? I want it to be really lightweight and slim due to the fact I will only be streaming netflix on it and possibly installing a program or two.

Thanks, Ben

---

### Post by K_45 on 2011-04-19
I'd get a book like Practical Guide to Linux 2nd edition + Ubuntu LInux Toolbox 1000 commands to really learn something, but otherwise it depends on what questions you have?

For media playback

```
sudo apt-get install vlc
```

```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

Flash

```
sudo apt-get install flashplugin-nonfree
``` - Restart your browser

Text editor

```
sudo apt-get install vim
```

---

### Post by idi0tf0wl on 2011-04-19
The very first thing you should do is delete the bottom panel, download Avante Window Navigator, and set that to start at login. The GNOME-panel is on its way out anyway with future Ubuntu releases, mostly because it's horrible.

Other than that, what sorts of things do you do with computers? I might could recommend something in a specific category. Google should suffice for a good idea of a good "standard" application set.

Welcome!

Also, I think you can get Silverlight for Netflix. Can anyone back this up?

---

### Post by K_45 on 2011-04-19
> **idi0tf0wl said:**
> The very first thing you should do is delete the bottom panel, download Avante Window Navigator, and set that to start at login. The GNOME-panel is on its way out anyway with future Ubuntu releases, mostly because it's horrible.

Other than that, what sorts of things do you do with computers? I might could recommend something in a specific category. Google should suffice for a good idea of a good "standard" application set.

Welcome!

Also, I think you can get Silverlight for Netflix. Can anyone back this up?

Not everyone wants the iCrap look in their system, and I don't think Netflix is supported for Linux.

---

### Post by El3mentGamer on 2011-04-19
I would reccomend writing all your Wifi/Internet info down. Basically (as i personally found it) you have to manually connect to the internet with wifi using the EXACT settings from your router (or w/e you use).

---

### Post by BertN45 on 2011-04-19
Ubuntu 10.10 comes with a lot of good stuff. I would recommend to use "Ubuntu Software Center" to install other software, you avoid typos. 

I would and did add:

- Skype
- Picasa 3.0 Beta (beta forever, but still the best photo organizer / editor for the hobbyist) Download from the Google site.
- Virtualbox 4.04 from the .org side for the USB support.
- Chromium Web Browser
- Quod Libet music player, robust, flexible and excellent tag handling/editing. It misses an equalizer. Use the album view and use the search view to select exactly what you want to see/play
- Banshee, best media player, but crappy library scan function, so you needs both one for playing the other to change the tags.
- Pulseaudio Volume Control if you have more then one audio device connected. I use it to assign my USB headset to Skype and my media players to the speakers.
- Samba, a small Gui to manage file and printer sharing.

You realize that on the 28th of April Ubuntu 11.04 will be released. If that happens, I would recommend Xubuntu 11.04. I skip Ubuntu 11.04, which comes with a completely new desktop. It probably needs another release (6 months) to regain the flexibility and reliability of the 10.xx releases.

---

### Post by K_45 on 2011-04-20
> **BertN45 said:**
> Ubuntu 10.10 comes with a lot of good stuff. I would recommend to use "Ubuntu Software Center" to install other software, you avoid typos. 

I would and did add:

- Skype
- Picasa 3.0 Beta (beta forever, but still the best photo organizer / editor for the hobbyist) Download from the Google site.
- Virtualbox 4.04 from the .org side for the USB support.
- Chromium Web Browser
- Quod Libet music player, robust, flexible and excellent tag handling/editing. It misses an equalizer. Use the album view and use the search view to select exactly what you want to see/play
- Banshee, best media player, but crappy library scan function, so you needs both one for playing the other to change the tags.
- Pulseaudio Volume Control if you have more then one audio device connected. I use it to assign my USB headset to Skype and my media players to the speakers.
- Samba, a small Gui to manage file and printer sharing.

You realize that on the 28th of April Ubuntu 11.04 will be released. If that happens, I would recommend Xubuntu 11.04. I skip Ubuntu 11.04, which comes with a completely new desktop. It probably needs another release (6 months) to regain the flexibility and reliability of the 10.xx releases.

Xubuntu is GNOME that pretends to be XFCE. If you want a lightweight environment you want a Debian net install with XFCE and no or very little GNOME dependencies.

---

### Post by BertN45 on 2011-04-20
> **K_45 said:**
> Xubuntu is GNOME that pretends to be XFCE. If you want a lightweight environment you want a Debian net install with XFCE and no or very little GNOME dependencies.

I am not against Gnome and I am not especially in favor of XFCE. I simply like the end result, a nice, reliable, fast and flexible desktop that works out of the box.

---

### Post by K_45 on 2011-04-20
> **BertN45 said:**
> I am not against Gnome and I am not especially in favor of XFCE. I simply like the end result, a nice, reliable, fast and flexible desktop that works out of the box.

 That Debian netinstall is for you. You'll learn more about Linux, and depending on what environment you install, it can use less than 100-150mb on boot.

---

### Post by BertN45 on 2011-04-20
> **K_45 said:**
> That Debian netinstall is for you. You'll learn more about Linux, and depending on what environment you install, it can use less than 100-150mb on boot.

OK I try it in VirtualBox, I am torrenting the ISO now. Maybe I could use it on ancient P-II of 400mHz used almost continuously by the kids of my sister in law. I installed Ubuntu 10.4 there one year ago, but I think they only use Firefox and sometimes RhythmBox and the CD burner

---

### Post by idi0tf0wl on 2011-04-21
> **K_45 said:**
> Not everyone wants the iCrap look in their system.
Not everyone who uses computers knows wtf to do with vim, either. I have the capacity to understand that my suggestions derive from opinions. Go post on a BBS or something when you're feeling self-righteous and nerdy with newcomers. When someone asks for opinions, it is not your place to deride them on behalf of the asker.

---

### Post by K_45 on 2011-04-22
> **idi0tf0wl said:**
> Not everyone who uses computers knows wtf to do with vim, either. I have the capacity to understand that my suggestions derive from opinions. Go post on a BBS or something when you're feeling self-righteous and nerdy with newcomers. When someone asks for opinions, it is not your place to deride them on behalf of the asker.

 Defending Apple now are we? And its your place to bitch about other opinions? Vim seems to be beyond your comprehension but not the OP's.

---

### Post by idi0tf0wl on 2011-04-23
Actually, I was just defending **choice**, so thank you for remaking my original point.

And personally, I prefer nano (yes, I'm aware of exactly what that is and what it can and can't do), though I'm also not the sort of programmer that insists on using archaic technology for modern tasks.

**You** are exactly the kind of person that is stifling open source progress. I know this because you're obviously the kind of person that hijacks someone else's thread to propound your own rigid philosophies on what should be allowed or not allowed on other, presumably (and hopefully) singularly autonomous persons' systems. You may or may not remember that to be almost the **entire** reason for the birth of your operating system.

I absolutely will not respond to you on this thread again, so hopefully you can walk away thinking you "won" or something. Congratulations.

---

### Post by CharlesA on 2011-04-23
Thread is closed.

Trolling is not allowed.

---

