---
title: "Fail to mount filesystem"
date: 2010-01-08
forum: General Help
---

### Post by Mr Nemo on 2010-01-08
Something very strange happened. Firefox was acting a little strange, so I decided to restart my system. When ubuntu started to boot it showed an error that said filesystem failed to mount. It gave me an "emergency" command line and told me ctrl-D would retry the mount. Why would this happen? I haven't modified any system files for a very long time. It told me to run fsck (I think thats what it was) and that seemed to fix the problem. Just curious as to what could have happened. Anyone else have this problem? Anything I should try to fix so this won't happen in the future?

---

### Post by Moozillaaa on 2010-01-08
I don't know exactly what's wrong in your situation, but when I occasionally have that problem, this is what I try first (4 steps, totally reversible)

```
sudo gedit /etc/fstab
```highlight the entry for the device in question, then 'cut'.

Save the file and close.

Select the icon for the device, double click to mount.

Re-open the /etc/fstab file, and re-enter the fstab entry by 'paste' function.

Save, close.

You should be able to mount and re-mount without a problem...


edit:
I'm just re-reading your post; is this the boot device that's failing to mount??? If so, you'll have to do this in a slightly different manner...

---

### Post by Mr Nemo on 2010-01-08
My desktop wouldn't load. When it said failed to mount filesystem, It was talking about the main filesystem for my OS.

Im fairly new to linux. So I think it was the boot device. Grub opened, I selected ubuntu, it started to load and then I got the error. I didn't even reach my login screen

---

