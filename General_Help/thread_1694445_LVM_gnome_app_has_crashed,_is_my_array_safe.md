---
title: "LVM gnome app has crashed, is my array safe?"
date: 2011-02-24
forum: General Help
---

### Post by garethsimpsonuk on 2011-02-24
Hi all I'm a little concerned...

I have removed a drive from my LVM using the gnome LVM tool but it seems to have crashed. I've added drives and extended the LVM using this app before and it sometimes goes unresponsive but I just leave it to do its thing and it works. This time however, it's been processing all day and I'm starting to get a bit worried. 

One good sign is that the HDD light is still flashing rapidly which tells me that it's still running. What do you guys think..? 

I'm going to leave it for at least 24 hours but was just hoping for some re-assurance!

Regards

---

### Post by garethsimpsonuk on 2011-02-24
The app has just come back to life with this error:

pvmove command failed. Command attempted: "/sbin/pvmove --config 'log{command_names=0}' --alloc normal /dev/sdi1:0-178849" - System Error Message:   ABORTING: Can't find mirror LV in bravo for /dev/sdi1

Can anyone shed some light on what this means? Thanks

---

