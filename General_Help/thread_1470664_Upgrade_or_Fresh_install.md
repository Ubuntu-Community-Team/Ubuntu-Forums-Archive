---
title: "Upgrade or Fresh install?"
date: 2010-05-03
forum: General Help
---

### Post by warrior_juggalo on 2010-05-03
I now have 9.10 installed on my desktop, Everything is to a "T" of what i need/want, I would be more than happy to stay with 9.10 100%, It's perfect to me, Only problem is i can't go on with 9.10 when i know that 10.04 is out there, Plus I hate the look of the buttons, The lay out, If i upgrade instead of a fresh install, Will the buttons change too, Does EVERYTHING change...

I've also heard a lot of horror story's from upgrading opposed to a fresh install.

Please let me know.....

I'm not too over fussed with the look of the new look of Ubuntu cause i know i can change all that back/to what i want it to look like.....

I'd just rather upgrade, Is it worth it?

---

### Post by Ginsu543 on 2010-05-03
Some people have great success simply upgrading each time a new release comes out, while others have all kinds of trouble from upgrading. I personally have always done fresh installs, since I like to, well, start fresh when I install a new OS.

Having said that, there really is no great need to upgrade to 10.04 if 9.10 does everything exactly the way you want. In fact, it is possible that you may lose some functionality with 10.04 which you had in 9.10. That has been my experience. I *really* like Lucid, but there a few features (or loss thereof) which I miss from Karmic. For example, my keyboard button for CD eject no longer works as well as it did in Karmic. In Karmic, the CD tray will open and close when I press the button. Now in Lucid, the button only works when there is a CD already in the drive. And once I open it and take the CD out, I can't use the button to close the tray again. I have to reach down and actually press the close button on the drive itself (annoying!). Another problem I'm having is that the Nabi keyboard input system which comes with the Korean language support doesn't work with Lucid. I am English/Korean bilingual and I like having the option of being able to toggle back and forth, but so far I can't get it to work in Lucid. Finally, I'm finding that screenlets no longer work in Lucid. So, as you can see, there is something to be said about having 9.10 working perfectly which you might sacrifice if you upgrade.

My solution to all this has been to dual-boot Lucid and Karmic. In fact, I have partitioned my 4 1TB WD drives so that I can install up to four Ubuntu releases. Most likely, I will cycle between two. If it is at all possible, I'd recommend that you keep your 9.10 as it is and simply find some unused hard drive space (or maybe go buy another drive) and install 10.04 there, rather than writing over your 9.10.

---

### Post by john newbuntu on 2010-05-03
My preference would be to go to an LTS rather than stay in Karmic.  I'd suggest backing up your root partition (and other associated partitions if applicable), do an upgrade, check if things are ok.  If things are bad in Lucid, do a fresh install and see if it is any better.  You can always use 'dselect' to install any extra package.  If Lucid is still horrible, restore Karmic from backup.
FYI, I use Lucid.  I went for a fresh install from Karmic and used dselect.  Things are pretty much the same as they were in Karmic except for a slightly faster boot time.

---

### Post by clhsharky on 2010-05-03
HI warrior_juggalo

I would wait 2 weeks then upgrade.
They will have some of this stuff worked out then.
You can fresh install any time.

Sharky

I liked Karmic also, the only install that I didn't have to do anything.

---

### Post by Orographic on 2010-05-03
I always do a fresh install. I have three internal drives (only one plugged in at a time) and one is my production machine (Karmic) and the other one is testing (Lucid) whilst the third is XP.

Download Clonezilla Ubuntu Testing version and make an image of your current Ubuntu so you can restore it, if there are problems. Its really worth spending time getting to know Clonezilla, its a very helpful friend.

Lucid is very good for me now since I disable my floppy drive in BIOS. Faster boot and faster file copying from usb drives and Flash in iView is better too.

---

### Post by warrior_juggalo on 2010-05-03
So i upgraded, But when i restarted my computer it hangs on......

"Ubuntu 10.04 LTS mitch-desktop tty1

mitch-desktop login: _"

How to i fix this?

---

### Post by warrior_juggalo on 2010-05-03
Fixed, I got in by typing xstart, Or startx whatever it was...

Well now i'm in and either A. My mouse does not work with it or B. It froze on me, I KNEW i should have stuck with 9.10.

---

### Post by Orographic on 2010-05-03
Did you Clonezilla your Karmic setup before you tried the upgrade? Never a wise move to upgrade without some image created unless you are happy to re-install Karmic.

---

### Post by Keith1212 on 2010-05-03
I upgraded both my pcs via Update Manager and it worked flawlessly. I was just like you I didn't see any problem with 9.04. But I couldn't do without 10.04. So I just decided to update and its even better than 9.04. The Software center has vast improvements,and the Gwibber social network is integrated into the panel which is awesome. You can log into all your chat accounts and your broadcast accounts(facebook,twitter etc..) and chat and watch the newest broadcasts from your sites.

I'm 100% impressed with 10.04 and have not even considered to go back to 9.04.

---

### Post by warrior_juggalo on 2010-05-03
BUMP!

Is there a fix to this keyboard and mouse problem, I tried both, ps1 and ps2 AND USB????

No go for any of them.

---

### Post by warrior_juggalo on 2010-05-04
Bump!

---

### Post by john newbuntu on 2010-05-04
Reboot your compute.  When you get your login prompt in Ubuntu, type:
```

sudo apt-get update
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo service gdm start

```If that did not help, take a look at this post:
[http://ubuntuforums.org/showthread.php?t=1413976](http://ubuntuforums.org/showthread.php?t=1413976)

---

### Post by warrior_juggalo on 2010-05-04
Nothing worked, ****'s me, Cause i have Fedora witch everytime i log on it just brings me back to the log in screen, Than i got Ubuntu 10.04 witch the mouse does not work......

Trying this on my mandriva laptop.

---

### Post by warrior_juggalo on 2010-05-04
I suppose I'll just have to throw a live cd in, Back up the stuff on the HD and do a fresh install.

---

