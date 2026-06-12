---
title: "Rhythmbox not reading iPod Touch"
date: 2010-12-26
forum: General Help
---

### Post by prettymess on 2010-12-26
Just got a new iPod Touch, but unfortunately Rhythmbox isn't reading it.  The iPod shows up on the desktop, so I know it's reading it, but it shows up as a camera, which I assume is the problem.  Is there a way I can force rhythmbox to read it?

I'm using ubuntu 10.04, by the way.

---

### Post by IWantFroyo on 2010-12-26
This is a common problem. Linux doesn't have support for it yet. (This probably won't work but...) see if you can open the sd card with my computer. You might be able to find your music somewhere in there, and then try moving/copy/pasting it in. If that doesn't work you could try using terminal to read what's in there...

---

### Post by prettymess on 2010-12-26
It's not about getting files off it, I'd like to be able to manage it.  

Just to add some more information: when I either open rhythmbox or click "scan removable media," my ipod makes a beeping noise like it's being read, but it still doesn't show up in rhythmbox.  There HAS to be some way to make it work.

---

### Post by IWantFroyo on 2010-12-26
Try this:
Enter synaptic package manager
Settings-Repositories
Add this source: ppa:pmcenery/ppa (if you use the URL bar it would be [https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa"))
Close and reload
Search for libimobiledevice1
Install both results
Open terminal, closing synaptic so the changes are set
Type [B]sudo apt-get dist-upgrade
[/B]It should get iOS 4 supported.
It is true this came from a website almost word for word (ubuntugeek) but I hope it helps!

---

### Post by prettymess on 2010-12-27
That didn't work either, unfortunately.

Has anyone had any luck running iTunes through Wine?  Think that could work?

---

### Post by tredegar on 2010-12-28
My itouch works fine with linux.

You say yours is "new". You should know that it has to be connected to a win or mac computer running itunes at least _once_, so it can be registered with apple, and have its HDD formatted.

If its an apple, the hdd will be apple-formatted, if win, NTFS.

---

### Post by prettymess on 2010-12-28
Yeah, I've already hooked it up to a windows computer.  From what I've read, 10.04 should be able to read it, I'm guessing it's just one of those random situations where it just doesn't work with mine.  I'm gonna try running iTunes through wine now.  If it doesn't work, I'll probably just reinstall ubuntu and hopefully that'll work.  I've been meaning to upgrade to 10.10 anyway.

---

### Post by tredegar on 2010-12-28
10.04 works fine with my itouch.
See [this thread]("http://ubuntuforums.org/showthread.php?t=1654334")

---

### Post by prettymess on 2011-01-05
> **tredegar said:**
> 10.04 works fine with my itouch.
See [this thread]("http://ubuntuforums.org/showthread.php?t=1654334")
I did the stuff in that thread and it got rhythmbox to read it, but when I added songs to my iPod, it looked like it transfered them, but when I checked it, they weren't on there.  I even tried deleting the couple songs i already had on my iPod (from when I hooked it up through windows), but again, when I checked, nothing had changed, the songs were still on there.

Any ideas?

---

### Post by tredegar on 2011-01-06
Try this thread: 
[http://ubuntuforums.org/showthread.php?t=1628529](http://ubuntuforums.org/showthread.php?t=1628529)

---

