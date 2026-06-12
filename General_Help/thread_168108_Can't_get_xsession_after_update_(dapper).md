---
title: "Can't get xsession after update (dapper)"
date: 2006-04-29
forum: General Help
---

### Post by flebber on 2006-04-29
I just updated my system dapper and after reboot cannot login to xsession. I get to the kdm login screen login and I receive this error message > Xsession: error cannot write to /tmp

Has anybody else had this I see the new graphics briefly then it keeps returning to kdm after i see this error.

---

### Post by flebber on 2006-04-30
I tried to fix X-org with > sudo dpkg-reconfigure -phigh xserver-org however this hasn't fixed it either and i still cannot get X up and running.

I noticed an error in xorg.conf where it had replaced all my input devices with /dev/wacom, which is odd since i don't have any wacom.

So next I restored backup of working Xorg that is mv xorg.conf.bak xorg.conf. Tried to startx but still receive the same /tmp error.

Filed a bug report Bug #42198:

---

### Post by [S|G] on 2006-04-30
Have you tried to login into the shell and copy anything into /tmp ? You could try that and, if you can't, you could try to set write permissions for /tmp

---

### Post by flebber on 2006-05-01
Thanks SIG I will have a look. I tried to move a file to /tmp and it states there is no space available. how can I clean out temp files ? Because that should resolve issue I believe.

I changed to /tmp and did Dir to see what was there and the only thing there is 1 file called "1445761048"

---

### Post by flebber on 2006-05-01
I have found that on reboot /tmp keeps filling with nonsensical number directories such as 034010885 and 21239751437. This leaves X with no space to  write to /tmp and hence the error. What is going on this seems crazy ?

---

