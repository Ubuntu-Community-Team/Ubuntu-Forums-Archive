---
title: "System Rescue CD"
date: 2009-08-15
forum: General Help
---

### Post by PRMan on 2009-08-15
I don't suppose anyone knows anything about the Linux System Rescue CD.

I know it's not Ubuntu-related, but you guys are all so helpful I was hoping somebody knows about it.

In the instructions, it says to type something like the following command:

/opt/drbl/sbin/ocs-iso -O clonezilla-44-restore-dvd.iso \
-I "Restore Windows XP (Home PC) - hda1" \
-V "Win XP Restore" -P "Spiros Georgaras <sng@hellug.gr>" \
-W "-j0 -b -c --nogui restoreparts win_img hda1" win_img

The problem is that there is no drbl directory in the opt directory.  I have no idea how to find ocs-iso if it is there and they moved it somewhere else.  Can anyone help me?  I need to be able to image these computers for a church tomorrow morning and I'm 90% of the way there and now I can't do anything.  I'm stuck!

A linux command that could find that file would be great.  Thanks.

---

### Post by starcraft.man on 2009-08-15
I not sure know where ya got that command but it looks like gobbeldigoop to me. A friend of mine agrees, don't use that command from a system rescue CD. Can you please link me to these instructions? They on the CD itself? I think they need to be looked at then, I neither think they are user friendly nor in fact useful.

For drive imaging please go right to the source, get a Clonezilla CD from [here]("http://clonezilla.org/") and image partitions from that. It's fairly straight forward, if ya have trouble they provide docs on download page or ask here. As long as ya know the paths of what ya want to backup and where to, it won't be problem. Read every page carefully and fill in as needed.

---

### Post by PRMan on 2009-08-15
I got the command from this guy's instructions here, which so far have been good.

[http://clonezilla-sysresccd.hellug.gr/restore.html#auto](http://clonezilla-sysresccd.hellug.gr/restore.html#auto)

There are several other people with similar instructions using the same command but it simply isn't there.

I already have my disk imaged, now I am just trying to make a self-booting auto-install DVD, which is what this command is supposed to do (make a self-booting ISO).

---

### Post by firen on 2009-08-15
The search command for your need would be, open a terminal and type

```
find / -name ocs-iso 
```

This would search for "ocs-iso" in root partition.

---

### Post by starcraft.man on 2009-08-15
I'm still a bit suspicious, the site isn't directly or indirectly affiliated, it doesn't seem to intend malicious intent. Use firen's command to look for what ya need. Be careful where ya get code from, we've had plenty of instances of people posting bad commands just to mess with people (here and on other sites even looking nice).

As to creation of ISO, that also can be done from the main live Clonezilla CD. I'd advise you to use it in future, it has a text based gui that is quite easy to use even for novices (read pages carefully nonetheless). It backs up and restores partitions and whole drives as well as creates ISOs after creating backups unless I'm mistaken. It must, since your leveraging clonezilla in the commands.

---

### Post by PRMan on 2009-08-15
I e-mailed the author in Greece and he was really nice.  It turns out that I still needed to be on the Clonezilla half of his CD for this.  It's all good now.  Thanks for the help.

---

