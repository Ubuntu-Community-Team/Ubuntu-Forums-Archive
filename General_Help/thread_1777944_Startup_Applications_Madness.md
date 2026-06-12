---
title: "Startup Applications Madness"
date: 2011-06-08
forum: General Help
---

### Post by ernz on 2011-06-08
I'm really struggling to get my head around a very simple task. I've tried searching this forum and searching online elsewhere for about an hour with no working solutions. It's driving me mental.

What I'm trying to do is very simple. On startup, I want to run nautilus at a network location and then close it 2 seconds later. Essentially, I want to mount an smb location silently using nautilus. (I know, I know, there are less hacky ways of accomplishing this, read on though)

Here's what I've got as an entry in startup applications:
```
bash -c "nautilus smb://10.10.10.2/Share/ && sleep 2 && wmctrl -c \"10.10.10.2\""
```

... as you can see, it loads nautilus at smb://10.10.10.2/Share/ (this is a shared folder on another PC) and then it waits 2 seconds and uses wmctrl to close windows with "10.10.10.2" in the title.

I've tried it in gnome-terminal, I've tried from Run Dialog and they both do exactly what I expect (open the window, automatically mount the share and then close the nautilus window).

**However!, **as soon as this command gets put into startup applications and the PC is rebooted, it loads nautilus and never closes it! I've tried all sorts of crazy combinations of scripts, /bin/sh to launch the commands and I even tried launching gnome-terminal -x a_script_with_same_commands.sh but it just won't work.

I'd really appreciate some expert help on this one.

Additional: I know about smbfs/fstab/autofs mounting. I promise I have good reasons for not using those methods.

**Update**

All resolved. Here's what's happened. smbfs is ridiculously slow for me. Something like 2MB/s. If the network locations are opened with Nautilus then gvfs is used and the network speeds are much quicker, around 35MB/s. This is why I want the network shares mounted and accessed via nautilus and symlinks rather than smbfs and fstab. I installed gvfs-mount and added this to startup applications:

```
gvfs-mount smb://10.10.10.2/Share
```

...symlinks then resolve to the proper remote locations and don't appear broke.

I Don't know why, but somewhere along the way, nautilus broke and no longer ran on logging in which meant no desktop icons or mounts. I fixed this by manually adding nautilus to run from startup applications with:

```
nautilus -n
```

... which appears to open in it silent mode.

What a cluster.

---

### Post by matt_symes on 2011-06-08
Hi

> I'd really appreciate some expert help on this one.From me ? Have you seen me ?

Anyhow, i may have a suggestion.

Open a terminal and type

```
gconftool-2 -g /apps/nautilus/preferences/media_automount_open
```If this returns true then (i think.....) Nautilus will open every time you mount the share. I think this is also how Nautilus opens, say, rythmbox for music etc.

You might want to disable this for all applications or you may try to disable it in your scriupt before mounting the share and re-enable it afterwards. 

That may or may not work. No promises.

To disable

```
gconftool-2 -s -t boolean /apps/nautilus/preferences/media_automount_open false
```and to re-enable

```
gconftool-2 -s -t boolean /apps/nautilus/preferences/media_automount_open true
```

Make sure the script is run as your user and not root.

Kind regards

---

### Post by ernz on 2011-06-08
Hi Thanks for that. I've maybe not been very clear though. I actually want nautilus to open. It's the opening of the smb:// location that mounts mounts it. Until nautilus is run at that location, the smb share isn't mounted.

To elaborate, I've got symlinks in my home directory that point to smb://10.10.10.2/Share/Documents and some others under Share/. These symlinks are dead until smb://10.10.10.2 is visited by nautilus and then everything under 10.10.10.2/Share becomes available via my symlinks.

---

### Post by matt_symes on 2011-06-08
Hi

> To elaborate, I've got symlinks in my home directory that point to  smb://10.10.10.2/Share/Documents and some others under Share/. These  symlinks are dead until smb://10.10.10.2 is visited by nautilus and then  everything under 10.10.10.2/Share becomes available via my symlinks.That's interesting. There may be a difference between Nautilus displaying and window and Nautilus actually doing its work.

Give it a try.

If not have you tried sending a TERM signal to Nautilus window using a PID ?

Kind regards

---

### Post by Morbius1 on 2011-06-08
> **ernz said:**
> Hi Thanks for that. I've maybe not been very clear though. I actually want nautilus to open. It's the opening of the smb:// location that mounts mounts it. Until nautilus is run at that location, the smb share isn't mounted.
When you open nautilus to a remote location Nautilus runs this command to actually mount it - and so can you:
```
gvfs-mount smb://10.10.10.2/Share
```

---

### Post by ernz on 2011-06-08
Hi, this was EXACTLY what I was after! Thanks! I actually found this about 10 mins ago myself and tested it and it works. (yay?)

Unfortunately, I appear to have broken nautilus a little whilst tinkering. It fails to load desktop icons (or anything nautilus) for that matter on boot. I can launch it manually from Places and that seems to open stuff. I suspect gconf commands above may have borked it a bit. Any ideas?

I tried disabling the gvfs-mount command but nautilus still won't launch on boot (no desktop icons until manually launched)

---

### Post by Morbius1 on 2011-06-08
I've managed somehow to never get to this condition but as a guess go to gconf-editor and see if the following is checked:
```
/apps/nautilus/preferences/show_desktop
```Description:> If set to true, then Nautilus will draw the icons on the desktop. 



---

### Post by matt_symes on 2011-06-08
Hi

 > I suspect gconf commands above may have borked it a bit. Any ideas?
That should not have created any problems in nautilus drawing the desktop. It is how i have mine setup.

```
gconftool-2 -a /apps/nautilus/preferences | grep show_desktop
```That will show if your desktop is being drawn by nautilus.

Kind regards

---

### Post by ernz on 2011-06-08
I'm thinking it's got nothing to do with gconftool now. I've checked out the process list after a reboot and nautilus doesn't appear to be showing.

In a funny way, we're back to square one - how do you manually load nautilus silently?

**Update**

I checked the gconf-editor values mentioned and they are all as they should be. I don't know why nautilus isn't starting but I added "nautilus -n" to the startup applications. This appears to start the nautilus service without any windows popping up.

Finally, all fixed. Thanks for all the help.

---

