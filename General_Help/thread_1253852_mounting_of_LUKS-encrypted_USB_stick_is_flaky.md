---
title: "mounting of LUKS-encrypted USB stick is flaky"
date: 2009-08-30
forum: General Help
---

### Post by Pollywoggy on 2009-08-30
I have two Jaunty systems on which I mount a USB "thumb" drive that has been LUKS-encrypted according to the procedure described in the July 2009 issue of Linux Magazine ('Linux Pro' in USA) beginning on p 34.  It works about half the time on both systems and with two different thumb drives.  Sometimes (under both KDE and Gnome), after I enter the LUKS password, the drive will not mount.  If I reboot the machine and then insert the thumb drive, it sometimes successfully mounts.

Does anyone have some idea of why it works about half the time I insert the drive?  I would expect that it would work either all of the time or not at all.  It is not that I entered an incorrect password; if I enter the wrong password, an error message will state that the password was not correct.  BTW, the partition on the thumb drive is formatted ext3.


thanks

---

### Post by t0p on 2009-08-30
Sorry, this isn't an answer to your question.  I was just thinking: if your encrypted usb sticks are proving "flaky", you may want to try a different method of encryption.  In which case I recommend [truecrypt]("http://www.truecrypt.org").  Unfortunately it's not in the repos (licensing issues) but a .deb for ubuntu is available at their site.

---

### Post by Pollywoggy on 2009-08-30
> **t0p said:**
> Sorry, this isn't an answer to your question.  I was just thinking: if your encrypted usb sticks are proving "flaky", you may want to try a different method of encryption.  In which case I recommend [truecrypt]("http://www.truecrypt.org").  Unfortunately it's not in the repos (licensing issues) but a .deb for ubuntu is available at their site.

Thanks, I have been using Truecrypt and it is mainly because of the licensing issues that I tried LUKS.

---

