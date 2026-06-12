---
title: "Disaster! Ubuntu won't boot! :'("
date: 2010-01-19
forum: General Help
---

### Post by G_Alexander on 2010-01-19
Hi All

Hope you can help. I had a powercut today, after the power came back on, I reset the date/time in the BIOS (nothing new there, battery on motherboard dead).

But... Ubuntu won't boot! I get this message and then nothing happens.

```

usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL+D will terminate this shell and re-try.
root@glen-desktop:~#  * Starting init crypto disks...      [OK]

```

If I try to boot in to recovery mode I get a similar message and access to a prompt. (screenshot: [http://img706.imageshack.us/img706/507/img0691rw.jpg](http://img706.imageshack.us/img706/507/img0691rw.jpg))

Will I have to reinstall and lose everything? Please say no :)

Thanks

---

### Post by cenzorrll on 2010-01-19
when you get into the shell try typing

```
fsck /dev/sda5
```

this should check your filesystem and fix any errors

---

### Post by G_Alexander on 2010-01-19
That solved it, thanks so much! :D

---

### Post by 07leepar on 2010-01-19
well im sorta a n00b on pc but if u have or order an ubuntu disk----
put the disk in your cd drive and shut down ur pc without doin anythin then boot up by rinning the disk select test hardwere if urs dont show that then u will have to reinstall ubuntu

---

