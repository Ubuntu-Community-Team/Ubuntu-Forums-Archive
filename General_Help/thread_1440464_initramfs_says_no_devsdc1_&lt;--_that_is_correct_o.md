---
title: "initramfs says no /dev/sdc1 &lt;-- that is correct only /dev/sdc all of a sudden"
date: 2010-03-27
forum: General Help
---

### Post by Miki800 on 2010-03-27
This is probably the last of me using ubuntu for a while,
its like this every few years, I use ubuntu then I realize I use more time making it work properly then I do using it.

when I boot ubuntu, it brings me to initramfs which then tells me that to mount root I need to have the /dev/sdc1 partition file thingy which I do not posses.

that was correct, apparently I lost my /dev/sdc1 and all I had left was /dev/sdc.

this was really wierd, maybe was due to the fact that when ubuntu froze and did not respond to any keys for over an hour I restarted the computer.

then it brought me to the same situation, so I had no idea what to do then I restarted and it automagically fixed itself.

after the next restart I had to do because something was stuck I was in that same situation again but it never automagically fixed itself again after whatever restarts...


I tried in initramfs to mount /dev/sdc on to /mnt/root_temp which I then made just for that

but it failed.

edit: I guess I need to run fsck with live-cd or something which is kind of a trouble right now to do.

a shame the shell I get can not give me that but oh well

---

