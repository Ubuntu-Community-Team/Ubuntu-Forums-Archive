---
title: "mount after hibernate"
date: 2009-09-14
forum: General Help
---

### Post by Eoghan Murray on 2009-09-14
Hi,

I've an external drive on /dev/sdc1 that has a separate power button which gets automatically mounted at **/media/extusb1** when I turn it on.

Here's the entry in **/etc/fstab**:
```
/dev/sdc1 /media/extusb1 ntfs-3g defaults 0 0
```

When the computer wakes up after hibernation, if I turn on the external drive, it doesn't automatically mount.

When I manually run the command **sudo mount -a**
I get the error 
```
fuse: failed to access mountpoint /media/extusb1: No such file or directory
```
This is because **/media/extusb1** does not exist.

If I create that directory, **sudo mount -a** works correctly, but the next time I turn on the computer, the automatic mount process doesn't reuse it, but creates a new directory at **/media/extusb1_**

So this is all very annoying as none of my apps are looking for files in **extusb1_**!

I'm looking for one of the following solutions:

[LIST=1]
[*]A command I can run instead of **mount -a** which creates the required folder (like the automatic mount process does) and (I assume) destroys it on shutdown.

[*]An instruction to tell the automatic mount process to reuse the existing folder **/mount/extusb1** rather than creating a new folder at **/mount/extusb1_**

[*]A fix to the automount process to make it work after ubuntu has woken up from hibernation!
[/LIST]

---

### Post by Eoghan Murray on 2009-10-05
Also **sudo mount -a**

can give:
```
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
```

after waking up from hibernation.

---

