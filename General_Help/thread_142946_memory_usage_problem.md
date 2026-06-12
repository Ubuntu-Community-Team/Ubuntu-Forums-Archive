---
title: "memory usage problem"
date: 2006-03-11
forum: General Help
---

### Post by javaperl on 2006-03-11
Recently I noticed that my ubuntu box's memory usage keeps going up after each reboot, even I don't do anything with it.

When I use "top", I see the memory being used keeps going up.  From after reboot's 256M to 1.5G in a day.  I think this memory leak speed is crazy.  I also noticed most of the time the hard drive light keeps blinking as well which indicates it has heavy disk access.

Is there any tool (gui preferred) which I can use to identify which process/service is doing this kind of activity (like memory usage, disk access, etc)?  How to diagnose this kind of issue and how to fix (like disable some services/processes) it?

Any input is highly appreciated.  Thanks!

-- javaperl

---

### Post by Perfect Storm on 2006-03-11
```
gnome-system-monitor
```

---

### Post by aysiu on 2006-03-11
If it's just numbers you're worried about, [this thread](http://www.ubuntuforums.org/showthread.php?t=126349) may make you feel better.

Do you actually notice a difference in *performance* (visible slowness), or is it just the numbers getting higher?

---

### Post by javaperl on 2006-03-11
thanks much for the info.

i am using it, and have some questions.

1.  it shows the real memory usage, but how can i see which processes are accessing the disks now?
2.  there are many processes shown are not listed in the active services (System->Administration->Services), how can i configure/disable them?

thanks!

---

### Post by Perfect Storm on 2006-03-11
If you have universe installed (avaible from 'universe')

```
sudo apt-get install bum
gksudo bum

```

Just be careful, there also a howto to disable stuff in the HOWTO forum.

---

### Post by javaperl on 2006-03-11
i believe is the number shown on "top" scares me.  my physical memory is 1.5G and after a day of each reboot, about 250M virtual/swap memory is used.  i doubt it is normal.

in addition, the disk light keeps blinking which show heavy disk activities.  i will take a look at the thread you mentioned.

thanks!

---

### Post by javaperl on 2006-03-11
wow, that's a nice tool.  let me try to play around with it.  thanks!

---

### Post by Perfect Storm on 2006-03-11
I don't think you should be scare that ubuntu/linux uses your ram. It just make sure you get the fullest of your computer so you don't waste anything.

---

