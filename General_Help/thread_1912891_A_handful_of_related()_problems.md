---
title: "A handful of related(?) problems"
date: 2012-01-21
forum: General Help
---

### Post by freedert11 on 2012-01-21
Hi! It's my first time posting in the forums. :3

I am using 11.10 with unity, and with all updates, uhm, updated.

For two days now, I have been experiencing these problems. It all happened one night when I started up my machine.

1. The wallpaper was restored to the default one. I am unable to change the wallpaper in the usual manner.
(Well, this one bugged me the most so I replaced the default wallpaper file with the one I want.)

2. Unity launcher icons are back to default.
I can add/remove icons, but rebooting would just bring it back to default.

3. Power settings are back to default.
Similarly, I can change them but rebooting brings them back to default.

4. I can't access Computer, Network and Trash in nautilus.
I guess this one's the most serious. I get these messages:

"Nautilus cannot handle "computer" locations."
"Nautilus cannot handle "network" locations."
"Sorry, could not display all the contents of "trash": Operation not supported"

(And because of this, I can't access my external drives in the way I know?)


I have checked thread titles of up to two days for anything similar, but have found nothing helpful.
I'd be glad to be redirected to a thread discussing this problem, if it exists.
I've also searched around the web and saw this unanswered problem:
[http://askubuntu.com/questions/95477/dont-have-access-to-change-various-things-system-dont-recognize-usb-trash-etc](http://askubuntu.com/questions/95477/dont-have-access-to-change-various-things-system-dont-recognize-usb-trash-etc)
So I know I'm not the only one with this problem! ^^

I hope you can help me. Thanks!

---

### Post by HermanAB on 2012-01-21
Hmm, create a new user account.  If that one works right, copy all your data over to the new account.

---

### Post by freedert11 on 2012-01-22
That didn't work, unfortunately.
The new user account has the same problems. ^^

Any more suggestions?

Well, perhaps I could live with these inconveniences, except for the nautilus one.

Thanks!

---

### Post by davethewave83 on 2012-01-22
> **freedert11 said:**
> Hi! It's my first time posting in the forums. :3

I am using 11.10 with unity, and with all updates, uhm, updated.

For two days now, I have been experiencing these problems. It all happened one night when I started up my machine.

1. The wallpaper was restored to the default one. I am unable to change the wallpaper in the usual manner.
(Well, this one bugged me the most so I replaced the default wallpaper file with the one I want.)

2. Unity launcher icons are back to default.
I can add/remove icons, but rebooting would just bring it back to default.

3. Power settings are back to default.
Similarly, I can change them but rebooting brings them back to default.

4. I can't access Computer, Network and Trash in nautilus.
I guess this one's the most serious. I get these messages:

"Nautilus cannot handle "computer" locations."
"Nautilus cannot handle "network" locations."
"Sorry, could not display all the contents of "trash": Operation not supported"

(And because of this, I can't access my external drives in the way I know?)


I have checked thread titles of up to two days for anything similar, but have found nothing helpful.
I'd be glad to be redirected to a thread discussing this problem, if it exists.
I've also searched around the web and saw this unanswered problem:
[http://askubuntu.com/questions/95477/dont-have-access-to-change-various-things-system-dont-recognize-usb-trash-etc](http://askubuntu.com/questions/95477/dont-have-access-to-change-various-things-system-dont-recognize-usb-trash-etc)
So I know I'm not the only one with this problem! ^^

I hope you can help me. Thanks!

that's really strange problems, if possible, I would suggest backing up your home directory and then re-installing ubuntu. Seems like something went wrong, maybe the drive is in read-only mode? You can make changes, but it reverts to what it was before, that's strange. 

Did you add any alternative repositories to the sources.list before this? I ask because, I added Debian repositories once and it rendered my system unworkable after doing an upgrade. Stick to proper repositories ;) they used to be reverse compatible but I think they aren't anymore.

---

### Post by freedert11 on 2012-01-23
I don't think I installed anything improper..
I've been building gstreamer from source, but I'm quite certain it's not the one that caused these..

Yes, I think a reinstall would solve all my problems.
If only I could figure out how to mount and access my external drives..?
^^

Anyway, I won't be reinstalling soon because things are pretty hectic right now.
So, if anyone knows any workaround especially for the nautilus one, that'd be very helpful!

Thanks!

---

### Post by dargaud on 2012-01-23
I've had somewhat similar problems after I launched some programs as root, and it changed the permissions on important config files, making them non-writable or non-accessible to my normal user. Run the following to check it out:
```
find ~ ! -user $(whoami)
```
If I'm wrong, there shouldn't be anything. Otherwise resume control with:
```
sudo chown -R yourusername /home/youruserhome
```

---

### Post by freedert11 on 2012-01-23
I tried it and it did find a bunch of disowned files, but they don't seem to be the cause..
(But thanks for this; it'll be helpful for other things. :3 )

---

