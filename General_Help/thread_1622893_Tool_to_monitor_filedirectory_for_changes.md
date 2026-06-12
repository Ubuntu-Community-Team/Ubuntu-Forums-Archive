---
title: "Tool to monitor file/directory for changes?"
date: 2010-11-16
forum: General Help
---

### Post by dabbi2000 on 2010-11-16
I've installed Lubuntu 10.10 on a decent 4gb USB flash drive. It's pretty ok but I am horrified with terrible write times which seriously affect system response time when writing.

This especially affects playback of video from browser, e.g. megavideo which likes to buffer a lot before playing. So I made a soft link for the Mozilla user profile directory to a external hard drive and while certainly faster it still pauses every now and then obviously because the buffer  isn't catching up.

I want to find out what directory/file the system is using for buffer to soft-link that one too. Is there any simple command-line tool for that?

---

### Post by yota on 2010-11-16
[IOtop]("http://guichaz.free.fr/iotop/") can help monitoring which write operations are going on in your system.

It's in the repositories so you don't have to download it from the linked site.

But I suppose that the problem is that usb flash drives indeed have real terrible write performance and sooner or later you'll face some performance degradation again.
Instead of triyng to symlink single write-intensive folders I'd suggest to mount /home /tmp and /var/tmp on another drive (see "mount --bind" eventually).

Hope this helps!

---

### Post by dabbi2000 on 2010-11-16
Thanks!

If I remount /home to hard drive the point of having a USB flash is pretty much gone, since most read/write is to the home folder. Isn't that right?

---

### Post by paulsarmiento on 2010-11-16
Try using 'tripwire'

```

apt-get install tripwire

```

see how it works...

---

### Post by yota on 2010-11-16
> **dabbi2000 said:**
> Thanks!

If I remount /home to hard drive the point of having a USB flash is pretty much gone, since most read/write is to the home folder. Isn't that right?

I wouldn't say so because still the whole system is located on the flash drive.
I suppose that a good compromise would be to let on the flash drive all that is mostly read, and seldom written (like /usr for instance, which it happens to be one of the biggest folder) because common flash drives shines at read performance but have terrible write times.
All other folders, and expecially the ones that are mainly written like /tmp and /var/tmp can be put on a place that can better handle them.

Where /home has to be placed it largely depends on usage patterns and what you desire to achieve...
[QUOTE=paulsarmiento]
Try using 'tripwire'
[/QUOTE]
tripwire is a great tool to monitor day-to-day changes with emphasis on security, but I would not recommend it to real time track IO operations or filesystem modifications.

---

### Post by dabbi2000 on 2010-11-16
Have to agree, tripwire was an overkill!

Tried iotop and it tells me process
"plugin-container /usr/lib/flashplugin-installer/libflashplayer.so 2101 plugin true"

is writing lots to the disk but I cannot see to which folder/file? I have the PID, can it be used to find the particular file/folder?

---

### Post by yota on 2010-11-16
> **dabbi2000 said:**
> Have to agree, tripwire was an overkill!
 I have the PID, can it be used to find the particular file/folder?

```

lsof -p <pid>

```

should tell you (eventually look at man for further details, especially lsof returns also network activity I don't remember the switch to restrict it to FS only...)

Hope it helps!

---

### Post by dabbi2000 on 2010-11-17
thx everyone, I tracked it down - turns out flash player was writing to the /tmp directory (I had assumed it was using ./mozilla/firefox/profile/cache

mounted it to ramdisk and voila it's a speedy gonzales again!

Also found some tips for making better use of Ubuntu on USB installation
[http://beastie.cs.ua.edu/cs150/configuration.html](http://beastie.cs.ua.edu/cs150/configuration.html)

---

