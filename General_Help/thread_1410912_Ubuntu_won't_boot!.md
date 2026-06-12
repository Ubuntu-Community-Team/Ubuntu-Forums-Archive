---
title: "Ubuntu won't boot!"
date: 2010-02-19
forum: General Help
---

### Post by FuzzWig on 2010-02-19
I'm posting this from windows because obviously ubuntu won't boot.
What happens is when I choose ubuntu in GRUB it shows the ubuntu sign for a while and then the screen just goes black.
So I had a look in the recovery mode to see if that worked and what it said that caught my eye were 2 things.

1: "Gave up waiting for root device"
2: Alert! /dev/disk/by-uuid/697f8ba3-e068-41de-beef-b3b86f866d2b does not exist, dropping to a shell.

I don't know what either of these mean so any help would be appreciated, thanks :)

---

### Post by FuzzWig on 2010-02-20
Hasn't anyone had this problem before?

---

### Post by someone235 on 2010-02-20
I have the same problem :(

---

### Post by FuzzWig on 2010-02-20
> **someone235 said:**
> I have the same problem :(

I think I'm going to have to try uninstall then reinstall. If it works I'll tell you

---

### Post by jpl888 on 2010-02-20
In a round about way Ubuntu is telling you that it can't find the root filesystem. If you don't have anything you need to keep in the Ubuntu install a reinstall might be the easiest thing.

---

### Post by _khAttAm_ on 2010-02-20
Did you remove/add partitions?

---

### Post by egalvan on 2010-02-20
> **_khAttAm_ said:**
> Did you remove/add partitions?

+1 to check on this...

when you make a change to a partition, the UUID will change.

GRUB uses UUID to indetify partitions, so it gets lost.

If you are using legacy GRUB (0.97), then use recovery console or a LiveCD to find yout what menu.lst shows as the UUID that it is looking for ...

It is possible to reset the UUID to the old value.
Copy it from the menu.lst, and use the proper command to write the UUID.
I´m on windows right now, so I don´t have the commands handy...
maybe another member will chime in with the proper incantations.

note... this will show the current UUID values
```
blkid
```


Under the new grub, it may be possible to update GRUB with the update-grub command, but I have NO experience with this...
YMMV

---

### Post by someone235 on 2010-02-20
> **jpl888 said:**
> In a round about way Ubuntu is telling you that it can't find the root filesystem. If you don't have anything you need to keep in the Ubuntu install a reinstall might be the easiest thing.
I can't reinstall it, cuz when I insert the live cd for installation, It got stuck too, and my screen becomes blank...

---

### Post by egalvan on 2010-02-20
> **someone235 said:**
> I can't reinstall it, cuz **when I insert the live cd for installation, It got stuck too**, and my screen becomes blank...


Are you SURE you are booting the LiveCD?

Are you getting any error messages?


Ooops, not the OP, sorry.

---

### Post by GSF1200S on 2010-02-20
When booting the liveCD, ensure that you hit F4 at the initial load screen (where it asks you to select language before you start the liveCD loading) and select Safe Graphics Mode. That will likely take care of your blank screen.

**EDIT** Beyond here deleted. Talk to egalvan..

---

### Post by GSF1200S on 2010-02-20
> **egalvan said:**
> +1 to check on this...

when you make a change to a partition, the UUID will change.

GRUB uses UUID to indetify partitions, so it gets lost.

If you are using legacy GRUB (0.97), then use recovery console or a LiveCD to find yout what menu.lst shows as the UUID that it is looking for ...

It is possible to reset the UUID to the old value.
Copy it from the menu.lst, and use the proper command to write the UUID.
I´m on windows right now, so I don´t have the commands handy...
maybe another member will chime in with the proper incantations.

note... this will show the current UUID values
```
blkid
```


Under the new grub, it may be possible to update GRUB with the update-grub command, but I have NO experience with this...
YMMV

**EDIT** Post Deleted- egalvan is your man/woman here..

---

### Post by egalvan on 2010-02-20
> **GSF1200S said:**
> 
```
/dev/disk/by-uuid/
```
 Then you copy the UUID in properties, go back to /etc/fstab (sudo gedit /home/ubuntu/Desktop/linux) and paste that UUID in the line next to root, or /. So, it would look something like this:

```
UUID=7be9e4b1-c58a-472f-bbf0-a5a800a7658d /               ext4    errors=remount-ro 0       1
```



The problem her is that you are using the CURRENT UUID, which is giving the boot loader problems...
The (old) UUID is also coded into the initramfs, and also points to some other locations in other files.

It IS possible to update all these,,,

but it would be easier to simply go back to the original UUID that was in place...
this is almost always still in GRUB´s files....
look it up, and if different than what GRUB expects,
then write the OLD one to the partitiion using the correct command...

no need to update anything else, or any other files or pointers.

note... new GRUB may be different, I have no experince with it yet.

And this is also why I use **LABEL** to indetify my `partitions, rather than **UUID**.
LABEL is appled my me, to suit me...
UUID is applied by the partitioin editor, to suit itself...

---

### Post by GSF1200S on 2010-02-20
> **egalvan said:**
> The problem her is that you are using the CURRENT UUID, which is giving the boot loader problems...
The (old) UUID is also coded into the initramfs, and also points to some other locations in other files.

It IS possible to update all these,,,

but it would be easier to simply go back to the original UUID that was in place...
this is almost always still in GRUB´s files....
look it up, and if different than what GRUB expects,
then write the OLD one to the partitiion using the correct command...

no need to update anything else, or any other files or pointers.

note... new GRUB may be different, I have no experince with it yet.

I stand corrected. I said I was rusty ;) gonna delete my post content so he doesnt get confused. Thanks for the info :)

---

### Post by someone235 on 2010-02-21
> **GSF1200S said:**
> When booting the liveCD, ensure that you hit F4 at the initial load screen (where it asks you to select language before you start the liveCD loading) and select Safe Graphics Mode. That will likely take care of your blank screen.

**EDIT** Beyond here deleted. Talk to egalvan..
F4 do nothing. How can I remove ubuntu???

---

### Post by FuzzWig on 2010-02-24
Thanks for the help all you guys, i just ended up reinstalling it, all my important files were either on vista or my memory stick anyway.
Cheers!

---

