---
title: "USB Drive with Ubuntu HELP"
date: 2010-05-11
forum: General Help
---

### Post by Oh T3h Noez on 2010-05-11
Recently not know what I was doing, I downloaded ubuntu 9.10 installer onto my USB Drive. Now, I need help removing it from the USB drive. I have tried deleting it with no work (It will delete but when removing the USB and putting it back in it's still there). I have also tried formatting it on Windows XP but no success. Does anyone know how I can fix this?

---

### Post by efflandt on 2010-05-11
Is it a USB hard drive or memory stick and roughly what size is it?

If you have a working Linux or live/install CD, post the output of **sudo fdisk -l** (small L) showing it.

Install gparted (or that is on live/install CD or burn a gparted-live CD) and see if that can remove and then reformat the partition(s).

---

### Post by Lightstar on 2010-05-11
Sometimes when you delete stuff, it's not fully deleted until you empty the trash.  And after that make sure you 'safely remove' it.

Formatting it should fix it also.

---

### Post by Oh T3h Noez on 2010-05-11
> **Lightstar said:**
> Sometimes when you delete stuff, it's not fully deleted until you empty the trash.  And after that make sure you 'safely remove' it.

Formatting it should fix it also.

When trying to empty trash it does nothing just sits there saying preparing.

> **efflandt said:**
> Is it a USB hard drive or memory stick and roughly what size is it?

If you have a working Linux or live/install CD, post the output of **sudo fdisk -l** (small L) showing it.

Install gparted (or that is on live/install CD or burn a gparted-live CD) and see if that can remove and then reformat the partition(s).

It's roughly 15.6 GB. And I don't know what you are talking about.

---

### Post by bredman on 2010-05-11
This post contains a very dangerous command, read carefully and stop if  you are not confident. If any of these commands returns an error, stop  immediately.

Make sure the USB drive is not connected.

Open a terminal by pressing Ctrl-Alt-t. Enter the command
mount

You should see a list of all the disks in the system.

Plug in your USB drive, wait for it to settle, and re-enter the command
mount

You should see a new drive in the list, something like /dev/sdb1.  /dev/sdb1 is the device name, and beside it you will find the logical  name, it should look like
/dev/sdb1 on /mount/16GB     (plus some extra text)

Enter the command
cd /mount/16GB
(using exactly what was returned by the previous mount command)

Enter the command
ls
and make sure that the light flashes on your USB drive. This is how you  make sure that you are working on the correct drive. Repeat the ls  command a few times and watch the drive light if you are not sure. It is  very important that you use the correct drive because you are going to  wipe its contents.

-This is the dangerous part-
If you are sure you are using the correct drive, enter the command
?? -r *
(note that the actual command is sent to Oh T3h Noez by private message, it's just asking for trouble posting it or the fd??? commands on a public forum)

Enter the command
cd /

Enter the command
umount /dev/sdb1                 (your name may vary slightly, see  above)

You can now remove the USB drive, and it should be empty.

---

