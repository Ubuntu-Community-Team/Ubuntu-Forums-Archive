---
title: "Jaunty: Issues with blank discs"
date: 2010-01-04
forum: General Help
---

### Post by Thanh-BKK on 2010-01-04
Hi.

This is on my boss' machine, running Ubuntu Jaunty.

For some reason, the computer only recognizes the FIRST inserted blank disc (CD-R or DVD-R) as a blank disc and burns it just fine. However to burn a second one the computer has to be rebooted.

If a blank disc is inserted (first one) a window pops up as usual offering to copy files to it and k3b works fine as it should. Any subsequent disc yields no window and k3b states "no media in drive" or some such. 

The computer has two IDE DVD-writers, both of them brand new (few weeks old now) and the problem is with both, i.e. the first disc in any one of them works and the second and subsequent in any of them won't. Which makes a total of one disc writeable before a reboot is required.

Obviously this is annoying and needs to be changed.

How..?

Many thanks in advance for a quick reply.

Kind regards.....

Thanh

PS the writers are Samsung and the discs are Verbatim DVD+R in case that matters. And READING all sorts of discs is fine in either drive even after one disc has been burned.

---

### Post by Thanh-BKK on 2010-01-05
BUMP

Anyone? I am sitting in front of the machine in question right now and it does not even READ discs anymore before the machine is rebooted.

Appreciate some replies here, thanks.

Thanh

---

### Post by jamesisin on 2010-01-05
Are the inserted discs mounted?  Does an icon appear in the usual places (desktop &c)?

---

### Post by Thanh-BKK on 2010-01-05
Hi.

No icon appears at all. The first disc after a reboot works fine, i.e. the icon appears, a window pops up offering some action such as playing with movie player or copying files etc, however any subsequent disc in either drive yields nothing at all and trying to open the disc from "Places" yields "No Media In Drive". 

When inserting the disc and closing the drive bay the disc spins up (audible) and the drive's light flashes for a little while as if it was reading the disc but the OS doesn't respond. 

Upon reboot it works fine again, but again only for the very first disc that is inserted.

The discs are ejected with the "eject" command as they should (right click the icon, "eject"). Using "unmount" does the same. 

Best regards

Thanh

---

### Post by jamesisin on 2010-01-05
> **Thanh-BKK said:**
> No icon appears at all... any subsequent disc in either drive yields nothing at all and trying to open the disc from "Places" yields "No Media In Drive".

The discs are ejected with the "eject" command as they should (right click the icon, "eject"). Using "unmount" does the same.

What icon do you right-click to get to eject if no icon appears?

---

### Post by Thanh-BKK on 2010-01-05
Hi.

Obviously the icon that appears upon inserting the first disc after a reboot. As any subsequent disc yields no icon, none can be clicked......

I just wanted to clarify that the (first!) disc is properly ejected/unmounted so that can be ruled out as a reason for the second disc to refuse mounting.

Regards

Thanh

---

### Post by jamesisin on 2010-01-05
Ok.  I was confused.

Have you tried manually mounting the disc using the mount command?

---

### Post by Thanh-BKK on 2010-01-05
Hi.

No sorry, i didn't try that...... and now i am no longer there (back at the office) so can't try that now. What would the command be? And, in case that works, how would i go to make the "normal" procedure (i.e. auto-mount upon inserting a disc) work again?

Many thanks....

Thanh

---

### Post by jamesisin on 2010-01-05
The normal syntax for mounting a drive:

sudo mount /dev/sdb1 /media/[mountfolderwhichyoumake]

I've not used it for CD's though.  Could be slightly different.

Here is my /etc/fstab entry for the CD drive:

# /dev/sda5
UUID=1ca057d1-b6ef-4665-bd55-23df06a64f94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Hope that helps you out.

---

