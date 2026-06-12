---
title: "Mounting Blank CDR issues"
date: 2006-05-16
forum: General Help
---

### Post by disabled_20220313 on 2006-05-16
Hi there,

Having trouble with a friends PC. It seems none of the users are able to mount a blank CDR correctly. I don't know the exact error message as havn't had a chance to look.

But what I'd like to know is, what does the computer do once a blank CD-R is inputted? What programs are run by the machine? And where do they exist?

This is to help me research possible ways of fixing it.

Thanks.

---

### Post by Googler on 2006-05-16
try 
```
sudo mount /dev/cdrom /media/cdrom
```
it will be mounted to /media/cdrom so you can burn files to it
you will not be allowed to eject the cdrom until
```
umount /dev/cdrom
```

try also to check /etc/fstab file it should allows you to automount

---

### Post by disabled_20220313 on 2006-05-16
Thanks I'll try that.

To be a little bit more specific, it detects and seems to "mount", as it starts up all the "What do you want to burn to CD" stuff.

---

### Post by easyease on 2006-05-16
hi! my surname is Mooney to, have you got any family in Downpatrick? :-k

---

### Post by disabled_20220313 on 2006-05-16
Erm nope. Only Mooney's that I'm related to in the UK, live in my house. The rest are in Dublin, and thats only my Grandad.

Sorry.

---

