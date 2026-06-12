---
title: "intriguing"
date: 2010-09-04
forum: General Help
---

### Post by miklu on 2010-09-04
I have recently shifted to Ubuntu ):P and found it to behave in the following manner.
I created a desktop shortcut through the following actions (courtesy eastwoodzhao.com):
"Drag desired file onto desktop. Without letting go of the mouse, press Shift and Ctrl simultaneously. "
However, after a restart, these links are still there, but have become unusable.
The links are reinstated after the icon for the relevant partition is brought on the desktop through the Places menu on the tab.
Would anyone out there, be interested in this behaviour? :)

---

### Post by aloshbennett on 2010-09-04
What you have created using the drag and drop is a 'soft link'. It's a shortcut to the original file.

The thing with soft links is, you could make a shortcut to a file even on a removable media (like a pendrive). Once the pendrive is removed, the link would still exist, but broken. The link would work again once you insert the pendrive.

Open a command prompt, and try this:
cd Desktop
ls -l

This will give the details behind the shortcut. Lets see from there.

---

### Post by blazemore on 2010-09-04
Well that seems reasonable, expected behavior.
What's on the desktop is a link to a location that doesn't exist, so a "broken" icon is put in its place.

I'm curious as to the method you are using.
Perhaps you could try this method instead, to create a Symbolic Link (which shouldn't care if its destination disappears)

[LIST=1]
[*]Delete any existing attempts from your desktop
[*]Click & Drag the file you want to link over the desktop
[*]While holding the "ALT" key, release the file
[*]Choose "Link here" from the list
[/LIST]

---

### Post by miklu on 2010-09-07
Thank you both. However, the behaviour persists.

Another ubunter (or ubuntist) tells this neophyte that it may have something to do with not having run gconfig editor.

Let me see.

---

### Post by miklu on 2010-09-07
Done that too.

The bottomline seems to be - 
No link to partition on desktop, no link to anything in that partition anywhere.

This is what is intriguing to one migrating from the Windows OS.

---

### Post by aloshbennett on 2010-09-08
I think I understand what you are saying.

You have a link to a file on a partition. The link is broken as soon as you boot into the system, but starts to work once you access the partition from "Places".

The reason is, your partition is not mounted automatically (this gets configured while you install ubuntu). So the link is pointing to a path that doesnt exist. Once you access the partition from "Places", it is mounted and your link becomes valid.

Can you post the output of
```

cd Desktop
ls -l *

```
and
```

cat /etc/fstab

```

We can then automount the partition when your system boots.

---

### Post by miklu on 2010-09-18
Taking a cue from the suggestion to automount as well as to create a symbolic link,

I installed the program pysdm and the problem seems to have been solved.

Thank you both.

---

