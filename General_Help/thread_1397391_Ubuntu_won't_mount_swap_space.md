---
title: "Ubuntu won't mount swap space"
date: 2010-02-03
forum: General Help
---

### Post by flihot on 2010-02-03
Hi there,

When i first installed ubuntu about 2 weeks i left about 30gb left for windows vista. I have not used vista at all so i decided to delete it and use the whole hard drive for ubuntu. I got the liveCD out and went into the partition editor on that  (i had ubuntu,swap,vista in that order) and deleted the swap space and vista and increased the size of the Ubuntu partition to so there was only 4gb left for swap. I then booted up again from the hard drive and i get this message "one or mounts cannot be mounted" or something to that effect and it talks about the swap partition and offers to boot in recovery mode which does work.

Once in recovery mode i go in and try and make swap partition with Disk Utility and i do that and it works. I go to restart Ubuntu to test it out and the same problem happens again, cannot mount swap ect. so i go back into Disk Utility and it now says 4gb Unrecognized instead of swap.

Anyone have any idea's?

---

### Post by flihot on 2010-02-03
OK I went into disk utility again and formatted the swap and then remade it and now it seems to hold when i start up but it still gives the same message about not being about to mount ect.

Also another symptom here is going onto the Computer page and right clicking the ubuntu partition only says 250gb which was what i had before i extended the partition although the Disk Utility does give the proper partition size.

---

### Post by bakegoodz on 2010-02-03
Your swap partition is set to be used at startup in the /etc/fstab, you can either use the device name such as /dev/sda2. Or you can run blkid to find the swap partition's UUID, and replace the UUID in fstab.
remember lines in fstab with "#" are comments or lines "commented out", or not currently being used.

---

### Post by flihot on 2010-02-03
Okay thanks heaps that got rid of the cannot mount thing. Before it the login screen comes up it flashes with a page of text i honestly can't remember if it used to do that. Does it normally do that?

Also another question is how can i stop grub menu coming up every time i boot? with vista gone i don't really want to be given boot options anymore.

---

### Post by bakegoodz on 2010-02-06
You can change set timeout= in /boot/grub/grub.cfg to shorter time or even to 0

---

