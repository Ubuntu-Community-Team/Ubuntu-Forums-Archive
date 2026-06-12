---
title: "boot up is slow now..."
date: 2009-10-26
forum: General Help
---

### Post by tempus on 2009-10-26
after upgrading to karmic koala mu laptop boot up time is now slower than before. What should i check/look at to correct this? Thanks   :popcorn:

---

### Post by Giblet5 on 2009-10-26
The first time Karmic boots, it takes about the same time as Jaunty to boot. Subsequent boots are significantly faster.

Something is wrong.

Can you post your /var/log/syslog file?

---

### Post by shadow120 on 2009-10-26
did you upgrade or do a clean install?

---

### Post by tempus on 2009-10-26
> **shadow120 said:**
> did you upgrade or do a clean install?

i did the upgrade option.

---

### Post by Giblet5 on 2009-10-26
> **tempus said:**
> i did the upgrade option.

So did I.

Post your /var/log/syslog file. It has the log of your system's bootup process.

---

### Post by cariboo on 2009-10-26
If you are looking at bootchart to judge your boot speeds, remember it now times the boot from grub to desktop.

---

### Post by tempus on 2009-10-27
> **Giblet5 said:**
> So did I.

Post your /var/log/syslog file. It has the log of your system's bootup process.

the problem is it is a huge file. Should I post the entire file? How can I delete the log to start a new one?

---

### Post by alphaniner on 2009-10-27
> **tempus said:**
> the problem is it is a huge file. Should I post the entire file? How can I delete the log to start a new one?

Post it as an attachment.  Click the paperclip icon when making a post, then browse to /var/log and select syslog.

---

### Post by zzzBrett on 2009-10-27
It seems like the new grub version takes an awfully long time.

---

### Post by shadow120 on 2009-10-27
> **zzzBrett said:**
> It seems like the new grub version takes an awfully long time.

not 100% but i think if you upgrade you dont get grub 2

---

### Post by tempus on 2009-10-27
> **shadow120 said:**
> not 100% but i think if you upgrade you dont get grub 2

How can that be checked? I was trying to avoid a clean install becuase of all the extra stuff I had set up. Upgrading seemd to be the best option...at the time.

---

### Post by zzzBrett on 2009-10-27
On the grub menu at boot, I believe it will say something like "Grub 1.97~beta" -- that is the new version.

---

### Post by alphaniner on 2009-10-27
Maybe try **grub --version** from within Ubuntu.  Or check the man page.

---

### Post by tempus on 2009-10-27
> **alphaniner said:**
> Maybe try **grub --version** from within Ubuntu.  Or check the man page.

the grub version is 0.97.

---

### Post by tempus on 2009-10-27
> **Giblet5 said:**
> So did I.

Post your /var/log/syslog file. It has the log of your system's bootup process.

/var/log/syslog attached

---

