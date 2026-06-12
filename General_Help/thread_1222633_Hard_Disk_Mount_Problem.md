---
title: "Hard Disk Mount Problem"
date: 2009-07-25
forum: General Help
---

### Post by yousof on 2009-07-25
Hello all,
I have Windows XP (Media Center) and Ubuntu, as usual windows crashed without reasons.
I was able to access C partition from Ubuntu. I restart ubuntu then I could not able to access the content of C Drive, I checked its properties and there is used space (50 GiG) but I see nothing.
I tried to make mount and unmount but I could not see the content. I made restart again, then when I click on C Drive I got this message : 
[COLOR=Red]Error org.freedesktop.Hal.Device.UnknownError.[/COLOR]
Details[COLOR=Red]
libhal.c 1399 : worng reply from hald. expecting an array.org.freedesktop.Hal.device.Volume.UnknownFileSystemType[/COLOR]

then Ubuntu says it opens the drive and after seconed I got this message : 
[COLOR=Red]DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/COLOR]


by the way the FileSystem is NTFS, and It was work fine without any problem with ubuntu.

could you please help me, I have important Data on C Drive and I do not want to lose it.

---

### Post by pro003 on 2009-07-25
> **yousof said:**
> Hello all,
I have Windows XP (Media Center) and Ubuntu, as usual windows crashed without reasons.
I was able to access C partition from Ubuntu. I restart ubuntu then I could not able to access the content of C Drive, I checked its properties and there is used space (50 GiG) but I see nothing.
I tried to make mount and unmount but I could not see the content. I made restart again, then when I click on C Drive I got this message : 
[COLOR=Red]Error org.freedesktop.Hal.Device.UnknownError.[/COLOR]
Details[COLOR=Red]
libhal.c 1399 : worng reply from hald. expecting an array.org.freedesktop.Hal.device.Volume.UnknownFileSystemType[/COLOR]

then Ubuntu says it opens the drive and after seconed I got this message : 
[COLOR=Red]DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/COLOR]


by the way the FileSystem is NTFS, and It was work fine without any problem with ubuntu.

could you please help me, I have important Data on C Drive and I do not want to lose it.

in terminal

```
sudo apt-get update && sudo apt-get install ntfs-config
```

then again

```
sudo ntfs-config
```

mount your drives... 

although it may be an unclean shutdown of windows...

---

