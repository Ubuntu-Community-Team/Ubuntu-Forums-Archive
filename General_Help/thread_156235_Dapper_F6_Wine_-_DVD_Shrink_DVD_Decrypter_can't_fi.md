---
title: "Dapper F6 Wine - DVD Shrink DVD Decrypter can't find DVD drives"
date: 2006-04-06
forum: General Help
---

### Post by kshitij on 2006-04-06
I can't get DVD Shrink and DVD decrypter recognize my DVD drives.

I have symlinks in ~/.wine/dosdevices folder for my dvd drives as:

```
ln -s /media/cdrom0 d:
ln -s /dev/hdc d::

ln -s /media/cdrom1 e:
ln -s /dev/hdd e::
```

And Windows version is configured as WinNT40 for these apps.

With the same setup, it used to work fine on breezy.

What has changed in Dapper? Any ideas?

Thanks
-Kshitij

---

### Post by NobodySpecial on 2006-04-06
Two things here:

1.  List output from:
ls -la ~/.wine/dosdevices/

2. Did you do the step where you type:
winecfg
Then navigate to drive tabs, then click on Add, type /media/cdrom, Click Show Advanced button and set the Type to CD-ROM, click ok

---

### Post by kshitij on 2006-04-06
Thanks dude!
Setting device type from winecfg helped.

But still I don't remember doing that in breezy. I had just set the symlinks from terminal and it had worked then.

Anyways it's working now. Thanks a lot

---

### Post by akiro.yamamoto on 2006-04-06
Setting in it winecfg is the correct way.
Well at least that's what I did ;)

---

