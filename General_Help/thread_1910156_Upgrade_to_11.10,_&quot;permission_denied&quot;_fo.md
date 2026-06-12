---
title: "Upgrade to 11.10, &quot;permission denied&quot; for simple folder copying"
date: 2012-01-16
forum: General Help
---

### Post by jjjjeremy on 2012-01-16
As I've just installed 11.10 from 10.04, I've been messing around with icon sets. From what I remember, I didn't have to use [ gksu nautilus ] to copy files in and out of /usr/share/icons. I get "Permission Denied" when I try to paste into the folder

 For the moment, I'm using [sudo cp], but that's getting clunky, and I'd rather use plain nautilus.

I don't think I should have this problem, because I'm an administrator, and the only user on this computer. Any ideas?


Facts that may be relevant:

I'm using Gnome Classic instead of Unity.
When I click on "Places" in the panel, "File System" doesn't show up, but my Windows and shared partition do.
"File System" shows up in Nautilus, but with a blank icon, instead of the harddrive icon I'm used to.
"File System" isn't listed under "Devices" in Nautilus, which I am used to in 10.04.

---

### Post by cortman on 2012-01-16
> **jjjjeremy said:**
> As I've just installed 11.10 from 10.04, I've been messing around with icon sets. From what I remember, I didn't have to use [ gksu nautilus ] to copy files in and out of /usr/share/icons. I get "Permission Denied" when I try to paste into the folder

 For the moment, I'm using [sudo cp], but that's getting clunky, and I'd rather use plain nautilus.

I don't think I should have this problem, because I'm an administrator, and the only user on this computer. Any ideas?


Facts that may be relevant:

I'm using Gnome Classic instead of Unity.
When I click on "Places" in the panel, "File System" doesn't show up, but my Windows and shared partition do.
"File System" shows up in Nautilus, but with a blank icon, instead of the harddrive icon I'm used to.
"File System" isn't listed under "Devices" in Nautilus, which I am used to in 10.04.

You will have to use gksu to copy/paste/move anything outside of your /home/user folder.

---

### Post by ajgreeny on 2012-01-16
> **jjjjeremy said:**
> As I've just installed 11.10 from 10.04, I've been messing around with icon sets. From what I remember, I didn't have to use [ gksu nautilus ] to copy files in and out of /usr/share/icons. I get "Permission Denied" when I try to paste into the folder

 For the moment, I'm using [sudo cp], but that's getting clunky, and I'd rather use plain nautilus.

I don't think I should have this problem, because I'm an administrator, and the only user on this computer. Any ideas?


Facts that may be relevant:

I'm using Gnome Classic instead of Unity.
When I click on "Places" in the panel, "File System" doesn't show up, but my Windows and shared partition do.
"File System" shows up in Nautilus, but with a blank icon, instead of the harddrive icon I'm used to.
"File System" isn't listed under "Devices" in Nautilus, which I am used to in 10.04.
If you made no permission changes to the /usr folders/filesystem in 10.04, nor made any edits of system files such as /etc/sudoers, you most definitely will have needed to use sudo to paste to the /usr/share/icons folder, but not to copy from the same folder.  All files and folders in /usr are owned by root as the default, so you can not write to/copy to anywhere in /usr without root permissions, ie, using sudo.

If it annoys you having to use the command ```
gksu nautilus
```just make a launcher for that command and you can open the root privilege file manager that way; it will still need your password, of course to open it.

---

