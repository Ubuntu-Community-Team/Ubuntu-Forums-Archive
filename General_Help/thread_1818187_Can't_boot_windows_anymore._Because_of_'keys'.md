---
title: "Can't boot windows anymore. Because of 'keys'?"
date: 2011-08-04
forum: General Help
---

### Post by n0c0d3 on 2011-08-04
Hi,

I need to use bluetooth, but for some yet unknown reason I don't seem to be able to switch on the bluetooth-card (it should be as simple as to press the Fn+F6 buttons on the keyboard to switch it on though and then the bluetooth indicator should light up, which is not happening, but I don't know if this is because of (X)ubuntu) and Ubuntu says it can't find the bluetooth card. That's not what I wanted to discuss now, but I think some history is always welcome when trying to do fault-finding ;)
I thought I maybe might be able to do it from Win7 . So after months of not having booted Win7 I thought to give it a try, but I get stuck right after the grub boot-screen. All I get is a blinking cursor for minutes and there's no HD activity. Then I booted Xubuntu again and it needed to do some check, which I passed and Xubuntu started as normal.
This check was done by "Keys". I don't really know what this Keys is, but since a couple of days I always get this word below the word Xubuntu in the boot-splash-screen. This is only after I installed WinFF or DVD::RIP.  There was some error during install telling me that it needed something with 'keys', so I entered the command quoted, something was installed and then the rest of the installation went okay. I've been looking in the bash_history files (user and root) but I can't find the command which I entered to install this keys-thing anymore, which is of course strange on itself.

Now I've got the idea (I'm not sure though) that I can't boot Windows because of this keys thing, but I have no clue how to get rid of it. Or could there be other problems causing Windows not to boot?

I really hope someone can help me getting back in Windows again, because losing the Windows partition really is not fun, even though I hardly use it. I can enter the Windows partition from  Linux with a file manager though, so it's not vanished. Just wish to be able to boot Win7 when I need it.

Any help is really appreciated.

Bart

---

### Post by zero2xiii on 2011-08-04
As no-one yet responded I though I might.

I don't fully follow exactly WHAT was installed (as you just point it to being "keys something" or the like). I assume it is something in the lines of the keyring manager or some of that usage. Synaptic search for "keys" made this to look like the best possibility.

However, i HIGHLY doubt that it can break windows, I suggest running a live cd, and checking the windows drive for errors (dont do this from the system installed on the computer, as running it on a mounted device can SERIOUSLY cause errors, I didn't believe the warning, and trust me, its there for a very good reason).

Also, try de-activating and then re-activating the bluetooth device from withing BIOS itself, it helped fix my bluetooth device on my laptop. Also make sure the currently logged in user can access this device (has the rights to do so) aswell as that it is activated (right click the networking icon and make sure all possible networking options is enabled including wireless)

Hope this points you in some better direction

---

### Post by n0c0d3 on 2011-08-04
The problem is that I don't know what this 'keys-thing' is. That's why I just call it a 'keys-thing", that's because of the lack of a better description ;)  As I said, the word 'keys' is even added to the bootscreen-splash and it wasn't there before I installed this keys-thing. That doesn't just happen for nothing, so I was hoping someone would recognize this description. I don't think it has something to do with a keyring of some sort. It also did a check of the Ubuntu-partition after the failed attempt to boot in Windows. It said something like: 'keys is currently checking Ubuntu'  or something like that with a progress-bar behind it. I don't think keyrings show this kind of behavior.
I also checked the install histories in synaptic and the Software Center, but I'm not able to identify the culprit. If I would know what command I used, then I could uninstall it I suppose, but I can't find it in my bash-history files. I wanted to rip a DVD and tried 2 programs (which I mentioned before), but I don't remember which one wanted me to install this 'keys-thing'. 

I searched the BIOS already if I could find a bluetooth device, but I can't see any bluetooth device at all there. Neither other devices like video or sound-cards, only drives. But I'll try to figure that out later. One thing at a time ;)

For the windows-drive-check, do I need an up-to-date live-CD, or will a 10.04 CD do? (I currently have 11.04 installed). And do I need to use some particular menu or something like that?
I also have a GParted 6.2.2-2 CD. Maybe there's something on that that I could use to check the partition for errors?

---

### Post by zero2xiii on 2011-08-06
Hmmm,

Oka I cant seem to find any info (using google) on any form of application that does what you describe. Maybe you installed some form of encryption program that encrypts your home directory (like that which can be selected to do so during install). But I don't really have any ideas on this..

Continuing though. Yes you can use pretty much any live cd:

[LIST=1][*]Boot the live cd[*]Open a terminal (Applications > Accessories > Terminal)[*]enter command "sudo ntfsfix" followed by the drive of your windows partition
[/LIST]

To find out what the drive of the windows partition is (it's something like /dev/sda1):

[LIST=1][*]Goto disk manager (System > Administration . Gparted)[*]Now select the device from the top right hand combo box[*]Look for the partion with filesystem as "ntfs"[*]Note the partition to the left (some thing like /dev/sda1)[*]Thats it.
[/LIST]

Now you can also right click on that partition and say "check" but the command line utility gives you much more details on the errors (if it so happens to find anything).

Try this, and after is finishes up, reboot and see if you can then boot into your windows OS.

Easier than the "gparted" method above, just run in terminal:

sudo fdisk -l
(thats a lowercase L)

---

### Post by n0c0d3 on 2011-08-06
That's useful info. One more question:
I have 3 Win7 partitions. /dev/sda1, /dev/sda2 and /dev/sda3. sda3 is the big one with win7 on it, sda1 is named 'PQSERVICE' and sda2 is 'SYSTEM RESERVED'. I think sda2 is the recovery-partition and I presume I'll need /dev/sda3 to be checked/repaired. But I just want to be sure. Can anyone confirm this?

Btw, I did my part of Googling as well, but with little more than keywords like 'keys' (pun intended), there's not much to be found that could be of interest. I even dreamed about it last night and when I woke up right after the dream I thought there might be an explanation of what 'keys' is. But you know how it works with dreams, details are gone right after you open your eyes...

I can't remember having installed encryption software lately. I do have CryptKeeper and TrueCrypt installed, but I have them already long time and hardly ever used them. This 'key'-thing' is really something that happed long after I installed those and I never used them to encrypt anything else then some files and I'd never use them to encrypt whole user directories, just because I might expose myself to not being able to enter them ever again.
But yesterday I thought it might have to do with some morse-trainer software I wanted to try. Creating Morse-code is called 'keying'. But I hardly ever reboot my computer (once a weeks or even weeks), so I could be confused about when 'it' happened. But why would morse-software announce itself in the boot-splash??
I also installed wxFormBuilder lately. But the more I think about it, the less sure I am when this 'key-thing' happened first.

But to make a long story short, should I check sda3 or one of the other 2 ntfs partitions?

---

### Post by zero2xiii on 2011-08-06
Hay again,

Haha wow yea, seems confusing (if only we could record our dreams...........)

AAAANY way.. haha back to the real world here, I would suggest doing it on both SDA-2 and 3.

I have very little knowledge about windows seven (know XP like the back of my harddrive... loz) works internaly and its file system. 

But the words "SYSTEM RESERVED" rings a bell of being of some importance... and then obviously sda3 being the root windows partition it will need to be scanned.


As to exactly what happend, I'm still amazed. (I am a ham myself, and know keying :D).. I wonder, have you ever check your boot logs? To see if it shows something funny? Might give us insight into the mysterious program...

---

### Post by n0c0d3 on 2011-08-06
I've never checked the boot.log before, so everything in there is funny ;) But there's nothing alarming I think.

I'm busy doing other things right now and I better have some spare-time when doing things like this, but when I have the time later today I'll see what happens if I check/repair sda3. I don't want to damage/modify the recovery-partition. That's also where the blueprint of the installation-CD lives, as it's no longer delivered on CD with the computer anymore nowadays. MS-customers have to burn it themselves. Silly, but that's how the world seems to turn nowadays. I did burn the CD, but one can never know, so better be careful with that partition...

I'm homing in on the cause of all of this though (I don't know if it's because of this dream ;) ). I think it has something to do with the wxWidgets I installed. I browsed through the bash_history again and I noticed that after installing wxWidgets I changed my password and after reading this I remembered having some problems entering root-mode after installing wxWidgets because my password wasn't recognized anymore.

This is what's in the .bash_history:
```

curl http://apt.wxwidgets.org/key.asc | sudo apt-key add -
apt-get update
apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n
sudo apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev
passwd

```After this I rebooted and then the 'keys' word was in the bootsplash if I remember well.  I think the last line, right before my password-change, is what's causing the harm, so maybe I just need to remove some of these packages? Maybe I better ask that on the wxWidgets forum... I think I better try to check/repair sda3 first. 

I used to know morse years ago, but never used it for real though. But I forgot it all, so we can't beep to each other ;)

I'll report back after the fix-attempt.

Thanks for the support so far!

---

### Post by n0c0d3 on 2011-08-06
I found out how to get Windows running again: Threaten it with a Xubuntu-CD! Put it in the tray but don't close it and give Windows a last chance to do it itself. Then it boots again... At least, this is what happened in my case... I hope it will boot next time again and this wasn't just a fluke of nature.

I'm sorry for bugging everybody with something that didn't turn out to be broken after all. Now I'm onto the bluetooth problem, but I don't think this is a Ubuntu problem in particular. I can't find and switch the adapter on in Win7 either. But I haven't really searched yet.

Thanks to the people trying to hep me out!

---

### Post by n0c0d3 on 2011-08-07
And by the way to those who are still interested as I forgot to mention, this 'keys-word' also has mysteriously disappeared from the bootsplash again.
I didn't remove any package. The mystery has gone so I don't need the key anymore ;)

---

### Post by zero2xiii on 2011-08-07
>  The mystery has gone

> Threaten it with a Xubuntu-CD!

=D>=D>

Seems like they have managed to invent some form of AI afterall,
one of these days our PCs is going to take us over and rule us and and and...... :shock::evil::evil::shock:


:-({|=[-o<

---

### Post by n0c0d3 on 2011-08-07
> **zero2xiii said:**
> 

Seems like they have managed to invent some form of AI afterall,
one of these days our PCs is going to take us over and rule us and and and.....


:-({|=[-o<
I don't want to sound too alarming, but computers already run the world ;) Not as a brain, but as interpreter, our connection to the physical world we can't do without. Without computers we'd fall right back to the stone-age, not to say that many African people will be more developed than the Western world, because they better know how to survive in the wild than we do.

:popcorn::guitar:

---

