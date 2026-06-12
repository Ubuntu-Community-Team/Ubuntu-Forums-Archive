---
title: "I need FileZilla for Ubuntu 9.4"
date: 2010-06-09
forum: General Help
---

### Post by NeonOnion on 2010-06-09
I tried the 'download' button and either I don't know how to make it work, or the download didn't work. Help?


SOLVED.

---

### Post by linuxman94 on 2010-06-09
Use Add/Remove programs in the applications menu. Just search for filezilla.

---

### Post by NeonOnion on 2010-06-09
I got "There is no matching application available." Even though I see the block on my desktop. =(

---

### Post by NeonOnion on 2010-06-09
Wait, figured that out. Now if I try to add it I get this:
"FileZilla FTP client cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by linuxman94 on 2010-06-09
Okay, try this command.

```
sudo apt-get install filezilla
```

---

### Post by mick222 on 2010-06-09
```
sudo aptitude install filezilla
```]
Make sure all repositories are enabled except for source code in software sources if you get an error.

---

### Post by NeonOnion on 2010-06-09
"E: Invalid operation isntall"

---

### Post by spiky001 on 2010-06-09
it, s

install

have you looked in synaptic manager ?

---

### Post by linuxman94 on 2010-06-09
Oops, typo! :P It is fixed now.

---

### Post by NeonOnion on 2010-06-09
> **spiky001 said:**
> it, s

install

have you looked in synaptic manager ?
Thank you. This worked. <3

---

### Post by mick222 on 2010-06-11
> **NeonOnion said:**
> Wait, figured that out. Now if I try to add it I get this:
"FileZilla FTP client cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Can i ask were you trying to install the windows Filezilla . You should always use synaptic or add remove to install software.Downloading from the internet is a last resort.

---

