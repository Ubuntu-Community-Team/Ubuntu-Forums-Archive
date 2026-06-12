---
title: "Hide/rename mounted partitions icons"
date: 2006-02-18
forum: General Help
---

### Post by m.musashi on 2006-02-18
I set up my windows and a fat32 partition to mount on boot. An icon for each is placed on the desktop. I'd prefer they not be there as I don't use them much and I don't like clutter.

Is there a way to have them mount and show up in "places" on the Gnome panel but not have an icon on the desktop? There doesn't seem to be an obvious remove icon option.

Also, they are currently named hda2 and hda5 - not very useful names. How can I rename them?

Thanks.

---

### Post by Herman on 2006-02-18
Alright, so you want your other partitions mounted somewhere other than your desktop and having a name of your choice hey? How about having them in your /home/miyamoto folder?

If you like that idea, just open your /home/miyamoto folder and create one folder for each of the two filesystems (partitions) you want to mount, and give them whatever names you like. For example you could make one folder called winxp and one called vfat.

Now you open a terminal and if no backup has ever been made of the file /etc/fstab, then type:
```
sudo cp /etc/fstab /etc/fstab_backup
``` Then: > sudo gedit /etc/fstab When the file /etc/fstab is open, find the column called 'filesystems', scroll down to the entry for '/dev/hda2' and beside it, on the same line, but in the column titled 'mount point', find where it says /media/hda2 and change it from /media/hda2 (delete that) and type in that space: /home/miyamoto/winxp (or whatever you named the folder you made).
Do the same thing for the line with /dev/hda5 in it, changing the entry in the 'mount point' column from /media/hda5 to /home/miyamoto/vfat (or whatever you named the other folder).
Then click 'save' and close the text editor file, and re-boot.
Your partitions should be auto-mounted in their new folders with appropriate names (that you like) inside your /home/miyamoto folder.

Is that near enough to what you wanted? (Herman)

---

### Post by dcstar on 2006-02-18
[QUOTE=m.musashi]I set up my windows and a fat32 partition to mount on boot. An icon for each is placed on the desktop. I'd prefer they not be there as I don't use them much and I don't like clutter.

Is there a way to have them mount and show up in "places" on the Gnome panel but not have an icon on the desktop? There doesn't seem to be an obvious remove icon option.
.....[/QUOTE]
Applications-System Tools-Configuration Editor-apps-nautilus-desktop

Uncheck "volumes_visible"

---

### Post by m.musashi on 2006-02-18
Yes. Thanks Herman. Exactly what I was looking for.

dcstar, worked like a charm. Lot's of little edits like that everywhere but how do you ever find them. Thanks.

---

### Post by dcstar on 2006-02-18
[QUOTE=m.musashi]
......
Lot's of little edits like that everywhere but how do you ever find them. Thanks.[/QUOTE]
Keep reading these forums, you'll stumble over them sooner or later....   ;)

---

