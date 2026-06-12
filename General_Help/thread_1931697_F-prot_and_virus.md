---
title: "F-prot and virus"
date: 2012-02-26
forum: General Help
---

### Post by zerobinary on 2012-02-26
I have successfully installed f-prot on my pc, but the problem is that I could not delete the virus
```
Files: 273338
Skipped files: 4937
MBR/boot sectors checked: 31
Objects scanned: 591081
Infected objects: 1
Files with errors: 13
Disinfected: 0

```
I tried ./fpscan -a -y and it is not working :<

---

### Post by gordintoronto on 2012-02-26
Tell us what you expected, and what you got instead. When you say, "it is not working," we have no information.

---

### Post by zerobinary on 2012-02-26
Not working =The infected item is not deleted!
I rescan it again and the virus is still there :<

---

### Post by gandaran on 2012-02-26
and what is the path of the virus?
most of the times virus are detected on linux they are on firefox or other web browsers cache! simply clearing the browser cache will get rid of the virus.

---

### Post by zerobinary on 2012-02-26
The thing is I don't know anything about the linux :<

---

### Post by PGScooter on 2012-02-26
I have no idea, but maybe you need to execute the command with "sudo" if you want to delete?
ie.
instead of
./fpscan -a -y
you can try
sudo ./fpscan -a -y

You will then need to enter your password.
Again, I have no idea about fpscan.

---

### Post by zerobinary on 2012-02-26
I sudo -i before I type the cmds so...

---

### Post by PGScooter on 2012-02-27
I don't know then. I would suggest reading the documentation, seeing if there is a mailing list for f-prot, or trying another program. clamscan is also a good virus scanner.

---

