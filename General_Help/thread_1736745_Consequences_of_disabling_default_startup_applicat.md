---
title: "Consequences of disabling default startup applications"
date: 2011-04-22
forum: General Help
---

### Post by LewRockwellFAN on 2011-04-22
Is there a reliable guide somewhere explicitly telling the consequences of disabling each of the default startup applications in System/Preferences/StartupApplications? I'm finding a lot of conflicting claims about the function of these programs when I google their names. some of these seem obvious but I'll include the whole list both because despite SEEMING obvious I might be wrong and because having it all in one place might help someone. Since I've googled for a guide and not found one this post may become that guide if it gets good response and I doubt I'm the only one to look for such. It would be nice if the entries in the Startup Applications Preferences box had links to longer discussions of what they did. A lot of people running 'nixes do so partially because they are generally so much better than Windows at supporting older hardware and some of us don't have memory and drive space to spare. This is even truer if we try nonstandard things like virtual boxes or live disks. So the little things that eat resources can be important. TIA if you can comment.

Bluetooth Manager
This is just for one type of wireless communication isn't it? If my wireless devices still work when I disable it I don't need it, right?

Certificate and Key Storage
Is this needed to authenticate updates and packages from the repositories or other sources or is it just for storing passwords to websites and such?

Check for New Hardware Drivers
Is it necessary to run this every time I start up? Is this what runs when I do System/Administration/HardwareDrivers or does that just check locally available (i.e, already downloaded) drivers? Couldn't I just run this if I have a reason to suspect a problem?

Disk Notifications
Like drive full or SMART warnings?

Evolution Alarm Notifier
This is the "remind me of Sue's Birthday" ap, right? So if I don't use it I can uncheck it without calamity?

Gnome Login Sound
I've got sound theme set to "no sounds" and alert sound muted anyway. I hate a noisy computer. So I can get rid of this presumably. Incidentally, could I save some disk space by uninstalling something related to this and deleting some wav files somewhere?

Network Manager
If I'm always using the same hardwired ethernet, I can unset it. Correct me if I'm wrong. Could I even uninstall it?

Nvidia X server settings
This one puzzles me. Do I only need it to CHANGE things or do I need it all the time?

Personal File Sharing
This is like making a folder available to someone else on another computer?

Policy Kit Authentication Agent
???

Power Manager
Is this only needed if I change something or needed for using any of those electricity conserving settings? If I unset it, at most it just means my monitor won't go into power saving mode, my drives won't turn off, etc., right?

Print Queue Applet
Unimportant if I'm not printing, I assume.

Pulse Audio Sound System
I need this if I'm going to use any sound at all? Or will it start automatically if I play a wav for example?

Remote Desktop
Don't guess we need this if we aren't running another system remotely or letting ours be run. Correct me if I'm wrong.

Secret Storage Service
Shades of 007! Is this only for an encrypted home? If the only encryption I ever knowingly use is whatever https uses or applications like gpg, scramdisk, or truecrypt, or whatever kind of authentication is going on when I use the repository, do I need this to run every time? Do I need it AT ALL? Is there something here I could uninstall even?

SSH Agent
Sounds like a tough guy with a concealed weapon. What's he do?

Ubuntu One
That's some kind of Cloud thing? If I don't use it knowingly, I'm not using it, right? So I can uncheck it until I get around to checking it out, right?

Update Notifier
This one seems pretty clear. Of course I could turn it off and still do updates manually, right?

User Folders Update
Can't make head nor tails of this one. "Update common folders names to match current locale." OOOO K. I'm still clueless. Sounds like something that would be done on installation. Is this for new user accounts? Do I only need it to add new accounts?

Visual Assistance
The only "visual assistance" I use is to normally run the High Contrast Inverse theme with the pointer customised to large and the fonts reset to 20, and to use zoom a lot in Firefox. This is just for Orca, isn't it? So if we don't use Orca, we can uncheck it?

---

### Post by Yellow Pasque on 2011-04-22
Bluetooth Manager - disable it if you don't need bluetooth

Certificate and Key Storage - keep it

Check for New Hardware Drivers - disable it (and you can uninstall jockey if you're not interested in proprietary drivers)

Disk Notifications - keep it (mounting volumes and stuff)

Evolution Alarm Notifier - disable it

Gnome Login Sound - disable it. Remove ubuntu-sounds package if you wish.

Network Manager - disable it. Use simple text setup (/etc/network/interfaces) for a wired network instead.
```
man interfaces
```

Nvidia X server settings - I'm an ATI/AMD guy so not sure

Personal File Sharing - disable if you don't need it (you description is accurate)

Policy Kit Authentication Agent - keep it unless you enjoy entering your password every two seconds.

Power Manager - your description is accurate, so it's your choice. Some Gnome apps use theses settings (like Totem suspending the screesaver if you're watching a movie).

Print Queue Applet - disable it (unless you need to see the print queue)

Pulse Audio Sound System - keep it (unless you're a sound engineer)
Remote Desktop - disable  it

Secret Storage Service - keep it

SSH Agent - you can probably disable it, but I'm not sure

Ubuntu One - disable it

Update Notifier - disable it

User Folders Update - disable it unless you're going to have other users that speak different languages on your system

Visual Assistance - disable it and see if it impacts you (probably won't)

---

### Post by mikewhatever on 2011-04-22
There are lighter *buntu derivatives for older hardware, that will probably do a better job then disabling startup processes.

---

### Post by LewRockwellFAN on 2011-04-24
Thanks for the the tips, Temüjin and for taking the time to put them in so orderly a fashion. I was surprised when google didn't show me just such a summary already published. I'm sure a lot of people will find this thread with the same question. Your answers are quite enough for me to act on but I'll hold off marking this solved a few days lest it discourage anyone who might want to elaborate on any of these programs.

Thanks for your thoughts, Mike. Yes, lighter distros are worth exploring for these purposes, even much lighter distros not even in the debian family, even Slack. I've tried some others and will keep trying more but for the moment I'm interested in tweaking this one and trying different variations of it in different environments including portable virtual boxes and live disks.

---

### Post by 3rdalbum on 2011-04-24
I personally don't recommend turning off any of the startup services or login services, even if you think you know what they do. A few years ago, people using desktop computers turned off Gnome Power Manager ("That's only for laptops, right?") and then started complaining that it took a full minute to display the "logout" screen.

The services don't take up much RAM and, if you don't need them, they take up 0% CPU time.

---

### Post by Rubi1200 on 2011-04-24
I think Temüjin hit the nail on the head with what to disable and what to leave alone. The thing is, though, I haven't noticed a significant difference with, for example, booting times by disabling these things.

However, the less unnecessary services running the better, in my opinion.

Of course, you don't need to remove the entry, just uncheck it. If something causes a problem, enable it again.

---

