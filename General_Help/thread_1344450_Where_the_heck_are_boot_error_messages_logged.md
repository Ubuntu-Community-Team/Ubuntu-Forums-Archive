---
title: "Where the heck are boot error messages logged?"
date: 2009-12-03
forum: General Help
---

### Post by klausner on 2009-12-03
Where the heck are boot error messages logged? I can't find anything in /var/log. Tried setting /etc/default/bootlogd BOOTLOGD_ENABLE=yes, but /var/log/boot is still empty.

---

### Post by wojox on 2009-12-03
It's been deprecated. Don't know why. Read post #32

[http://ubuntuforums.org/showthread.php?t=49925&page=4](http://ubuntuforums.org/showthread.php?t=49925&page=4)

---

### Post by klausner on 2009-12-03
> **wojox said:**
> It's been deprecated. Don't know why.

OK. So what's it been replaced with? As the other thread noted, setting up a serial console just to read boot messages is absurd.

---

### Post by klausner on 2009-12-05
Bump.

---

### Post by falconindy on 2009-12-05
Not sure how Ubuntu does it, but Arch Linux uses a mini logger at the start of the boot process, until syslog picks up. Before mini logger terminates, it sends what it collected to /var/log/dmesg.log. If you're expecting to see here what you saw on the screen during bootup, you're SOL.

A bit of a hack solution, but you can remove the 'quiet' and 'splash' options from your boot options and then use scroll lock to "pause" the boot process when you see the error.

---

### Post by klausner on 2009-12-10
Bump!

---

### Post by hawthornso23 on 2009-12-10
dmesg | more

will display them. As to where they are logged though, I don't actually know.

---

### Post by klausner on 2009-12-11
> **hawthornso23 said:**
> dmesg | more

will display them. As to where they are logged though, I don't actually know.

This does not capture errors flashed to console during boot, which I am particularly looking for.

---

### Post by klausner on 2009-12-26
Bump.

---

### Post by klausner on 2010-01-23
Bump.

---

### Post by klausner on 2010-01-30
So bootlogd doesn't work anymore. Is there a way to get the functionality back without having to roll your own packages? Is there any hope that Lucid will have a fix?

---

### Post by oldos2er on 2010-01-30
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/125710](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/125710)

It appears this bug still exists in Lucid, at least for the moment.

---

### Post by klausner on 2010-01-30
> **oldos2er said:**
> [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/125710](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/125710)

It appears this bug still exists in Lucid, at least for the moment.

Right. So....... What's the answer?

---

### Post by oldos2er on 2010-01-30
As of now, there isn't an answer. I wouldn't hold my breath for a solution either, seeing as this is a years-old bug.  :(

---

