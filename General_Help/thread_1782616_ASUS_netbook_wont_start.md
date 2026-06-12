---
title: "ASUS netbook wont start"
date: 2011-06-14
forum: General Help
---

### Post by yipyip123 on 2011-06-14
My dad has an ASUS EEE PC 900 that stopped starting up. Ubuntu2.6.31-14-generric-pae  is the OS. He doesn't remember the password. He said he didn't change anything before it stopped working.

After GRUB it says

```
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):
```When I hit Ctrl+D, I get this:

```
mountall start/starting
fsck from util-linus-ng 2.16
swapon: /dev/disk/by-uuid/(blah blah blah): swapon failed: Device or resource busy
mountall:(blah blah) terminated with status 255
mountall: Problem activating swap: (blah blah)
fsk from util-linus-ng n.16
/dev/sda1: Superblock last mount time (Wed Aug 11 01:55:19 2010,
now = Mon Dec 31 19:16:09 2001) is in the future.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck /home [1405] terminated with status 4
mountall: Filesystem has errors: /home
init: mountall main process (1398) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
give root password for maintenance
(or type Control-D to continue):

```Sorry if there are any errors- I had to type that out. I can hold down control-d and nothing different happens.

Any guesses on this? I tried to boot from my USB with ubuntu on it but just get "Boot error." and nothing else...


Thanks:popcorn:

---

### Post by eltonw on 2011-06-14
> **yipyip123 said:**
> My dad has an ASUS EEE PC 900 that stopped starting up. Ubuntu2.6.31-14-generric-pae  is the OS. He doesn't remember the password. He said he didn't change anything before it stopped working.

After GRUB it says

```
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):
```When I hit Ctrl+D, I get this:

```
mountall start/starting
fsck from util-linus-ng 2.16
swapon: /dev/disk/by-uuid/(blah blah blah): swapon failed: Device or resource busy
mountall:(blah blah) terminated with status 255
mountall: Problem activating swap: (blah blah)
fsk from util-linus-ng n.16
/dev/sda1: Superblock last mount time (Wed Aug 11 01:55:19 2010,
now = Mon Dec 31 19:16:09 2001) is in the future.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck /home [1405] terminated with status 4
mountall: Filesystem has errors: /home
init: mountall main process (1398) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
give root password for maintenance
(or type Control-D to continue):

```Sorry if there are any errors- I had to type that out. I can hold down control-d and nothing different happens.

Any guesses on this? I tried to boot from my USB with ubuntu on it but just get "Boot error." and nothing else...


Thanks:popcorn:
If he doesn't remember the password, then he would need to reset it:
[http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/]("http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/")

---

### Post by yipyip123 on 2011-06-14
Hmm... I had some difficulty.

Holding ESC only brought me to a blue box, which brought me to the GRUB screen again. From there, pusshing "b" did not boot anything. Also, there was no line beginning with "kernel" after pushing "e" in the GRUB menu.

---

### Post by wildmanne39 on 2011-06-14
> **yipyip123 said:**
> Hmm... I had some difficulty.

Holding ESC only brought me to a blue box, which brought me to the GRUB screen again. From there, pusshing "b" did not boot anything. Also, there was no line beginning with "kernel" after pushing "e" in the GRUB menu.Hi, boot from a live cd and see if you can repair the disk damage to your files system. When you get the livecd booted choose try then open disk utility a run a disk check. If you are unsure post the results here we can take a look at them and run this script also and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. Make sure you use the same version of livecd to boot from as you installed ubuntu from.

---

### Post by yipyip123 on 2011-06-15
I tried with both a new version of ubuntu desktop and an old version of ubuntu netbook .ISO, from my USB stick. Both just gave me "Boot error".

Is it my USB stick?

---

### Post by wildmanne39 on 2011-06-15
> **yipyip123 said:**
> I tried with both a new version of ubuntu desktop and an old version of ubuntu netbook .ISO, from my USB stick. Both just gave me "Boot error".

Is it my USB stick?Hi, I am not sure can you check your usb stick on another system and see if it boots? Make sure you created the usb stick correctly it has to be bootable. If you are going to attempt a repair you need the same version of ubuntu on the usb stick as what is on the system.

---

