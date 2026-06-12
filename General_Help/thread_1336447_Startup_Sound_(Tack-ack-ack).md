---
title: "Startup Sound (Tack-ack-ack)"
date: 2009-11-24
forum: General Help
---

### Post by Seregwethrin on 2009-11-24
Hello;

I'm using Karmic Koala netbook remix. I can open my netbook some quit places like classes so I want the disable the sound.

I've already unchecked **Gnome Login Sound at Startup Applications** at System pane and it disabled the Login Sound plays at appearing desktop.

But still a short "tack-ack-ack" sound plays before the login window appears at startup. I want to disable it too but I can't find how.

Thanks.

---

### Post by DeMus on 2009-11-24
> **Seregwethrin said:**
> Hello;

I'm using Karmic Koala netbook remix. I can open my netbook some quit places like classes so I want the disable the sound.

I've already unchecked **Gnome Login Sound at Startup Applications** at System pane and it disabled the Login Sound plays at appearing desktop.

But still a short "tack-ack-ack" sound plays before the login window appears at startup. I want to disable it too but I can't find how.

Thanks.

I don't know the netbook remix version but in Ubuntu in menu System -> Preferences -> Sound you can disable all system sounds. Maybe the UNR has also something like that.

---

### Post by Seregwethrin on 2009-11-24
Are you using 9.10? Because as far as I know it changed in 9.10 and System > Sound doesn't have effect...

---

### Post by firedrake on 2009-11-24
alt+F2
gconf-editor

untick the *active* key in order to **disable the login ready drums sound** in
 /apps/gdm/simple-greeter/settings-manager-plugins/sound/

:popcorn:

---

### Post by Seregwethrin on 2009-11-24
Did it

But still plays...

---

### Post by firedrake on 2009-11-24
> **Seregwethrin said:**
> Did it

But still plays...


No sudo on the terminal..Just do your account..

Another option..On terminal type:

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

---

### Post by billdozor on 2009-12-15
two other options to disable GDM Drum sound...

Open a terminal
cd /usr/share/sounds/ubuntu/stereo

Either rename or remove the "system-ready.ogg" file.

1) sudo rm system-ready.ogg
OR
2) sudo mv system-ready.ogg system-ready.ogg.disabled

---

### Post by chmmr on 2010-01-01
There are several threads on this forum that deal with this issue in the older version of GDM used in versions of Ubuntu prior to 9.10.  All of those threads showed up earlier on a search result listing than this thread, but it was only this thread that got me pointed towards the solution.  So as a side note, it would be really nice to have a way to rate posts or even threads for helpfulness the way you can on amazon.com, to help people find the best answers.

Firedrake's first solution worked for me when I ran gconf-editor as root to change this key:

/apps/gdm/simple-greeter/settings-manager-plugins/sound/active

(if you're more comfortable using the GUI for this, alt-F2 and type "gksu gconf-editor" to open gconf as root to change the above key)

It would seem that it doesn't matter what the setting is for any user other than root.

The delete-or-rename sound in /usr/share/sounds solution also worked for me, but I was initially nervous about it because it's not certain that gdm handles missing files gracefully, and if it doesn't, the user might be stuck unable to log in.

What's especially nasty about this issue are two things:

A) Many, many users out there do not want their OS to ever make a sound.  Ever.  Many of these users will shut off system sounds first thing when they start using a new OS install.  These users will be very displeased that gdm, because it doesn't run under their username, is an exception to this setting.

B) There are several things in the GUI and in gconf that *look* like they should address the problem, but don't due to various non-obvious quirks of gdm and general system configuration.  I tried all of them before I found the one that worked.

The option to disable sounds was present in previous versions of gdmsetup.  It should be reinstated for future versions so that people don't encounter this problem.

---

### Post by VastOne on 2010-01-01
Just for my knowledge, but wouldn't the Netbook have a mute button on it?

---

### Post by Seregwethrin on 2010-01-02
I can't mute my netbook before it opens.

---

### Post by JHSaunders on 2010-01-18
chmmr solution worked for me, but this really should be an obvious setting, in a real settings GUI.

---

### Post by bluestar14 on 2010-01-18
mute it on first boot, before you go to quiet places, and then wouldn't it stay mute in class?

---

### Post by Seregwethrin on 2010-01-19
> **bluestar14 said:**
> mute it on first boot, before you go to quiet places, and then wouldn't it stay mute in class?

Do you think this is really a solution?

Softwares exist to make life easier, not harder. One shouldn't need to think every time when shutting down the netbook "Will I go to a quiet place?".

---

### Post by warfacegod on 2010-01-19
> So as a side note, it would be really nice to have a way to rate posts or even threads for helpfulness the way you can on amazon.com, to help people find the best answers.

A fine idea but it would end up being virtually useless in the long run. Each person here has a unique computer. Many users may have identical hardware but their setup, apps, preferences, etc. will always be different. A rating system for answers would quickly prove pointless because the answers will never work for every user.

Hardware configurations are another aspect. A fix that works for one users hardware may not work for another or, in some cases, even be possible.

A third aspect is the fact that there are four main OSes being utilized by the people of this forum. Aside from those four, there are another two dozen or so other Linux OSes thrown into the mix. On top of that you have a solid number dual boot systems of two or more of Linux. Linux and Windows XP, Vista, and 7. There are also the Mac users to spice this stew (read glop) up with.

The variables are myriad. Trying to keep track of them would be impossible.

---

### Post by natrik on 2010-03-29
Surely there is a script or something that makes a call to play the sounds?  I recall there being something like /usr/lib/gdm/gdmplay or some such, but on karmic, I cannot find it.  (I had rewritten it to use sox, which did a much better job of not outputting choppy audio).

How are the greeting sounds played now?

Thanks.

---

### Post by abid_naqvi83 on 2010-08-31
I am running Ubuntu 9.10. *Firedrake's* solution (using gconf-editor) didn't work for me whilst using every possible permutation of my own and root's account setting. *Billdozor's* idea (renaming the system-ready.ogg file) is guaranteed to work but I share *chmmr's* reluctance in leaving a file-handle empty especially during start-up so I modified the idea a little, as follows:

```
cd /usr/share/sounds/ubuntu/stereo
sudo mv system-ready.ogg system-ready.ogg.original
```

I then used **Audacity** (a very useful and powerful sound editor available in the Ubuntu Software Center) to create a 1 second long **silent** .ogg sound file, named it sytem-ready.ogg and copied it in to /usr/share/sounds/ubuntu/stereo. Now whenever the system calls the file on startup it plays a 1 second long silent audio file. Problem solved.

Details on creating silent file in Audacity:

1. Open Audacity
2. File>>New
3. Tracks>>New Track>>Stereo Track
4. Generate>>Silence - Choose Duration to be 1 second
5. File>>Export - Skip Metadata - Name file system-ready.ogg and choose File Type as 'Ogg Vorbis Files' in the lower-right corner

and voila!

---

### Post by rene8 on 2010-09-02
Thanks to everyone. This thread helped me to 'mute' the system-ready sound *without* disabling system alerts. Never thought about actually changing the sound file.

Since (at least in 10.04) the system-ready.ogg file is actually a symbolic link to the dialog-question.ogg sound file, you might as well just redirect the symbolic link to the bell.ogg sound (a more discrete sound) or to a silence file like @*abid_naqvi83* suggested:

```
sudo ln -s your_silence_file.ogg system-ready.ogg
```

You may need to remove the original system-ready.ogg link first.


Further comments (in a 'social networking' style):

@*warfacegod*: Agreed. When you combine all possible variables and how they interact with each other, you get a chaotic (i.e., umpredictable) system (mathematically speaking). 

@*Seregwethrin*: Agreed. A software solution for disabling (any kind of) sound should be an out-of-the-box option (as it used to be).

We should see the facts: Ubuntu is a distro with a lot of Linux newcomers - many of them changed when they discovered Linux can be as user-friendly as their (win | mac) OS and better in many ways; I believe Ubuntu / Gnome Desktop should keep this Philosophy, while encouraging new users to learn Linux-basics (e.g., to use the terminal) and not be afraid on making a couple of mistakes.

@*abid_naqvi83*: Thanks a lot! - I also agree on not just *deleting* a system file / link, as it would probably leave a filehandle empty.

Cheers to all!

---

### Post by COKEDUDE on 2010-12-24
Thx for all of this information.

---

