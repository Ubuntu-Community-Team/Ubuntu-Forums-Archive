---
title: "VirtualBox help"
date: 2010-01-22
forum: General Help
---

### Post by prem1er on 2010-01-22
I have ubuntu running inside of a virtualbox on an xp machine. Is there any way to mount the hard drive that the virtual machine isn't using? AKA the C: drive of the computer?

---

### Post by MaindotC on 2010-01-22
No.

---

### Post by JiuJitsu500 on 2010-01-22
Nope :) I don't think so at all.... there shouldn't be a reason to, but out of curiosity why do you wonder?

---

### Post by prem1er on 2010-01-22
How can I get files between the two? I can't use a usb.

---

### Post by tagrat on 2010-01-22
There is a shared folder option in the Virtualbox setup. I don't use it though. You could also share your C: drive using windows file sharing and then see if it shows up under ubuntu file manager. This could be a security issue though I'd be sure my network was secure before sharing my c: drive.

---

### Post by davec64 on 2010-01-22
If your using the non-free version you could install Guest Additions and this give you USB support and also the ability to mount shares.

Have a google for "Guest Additions", I'm assuming it works the same way in a Windows environment as it does in Linux though!  :)

---

### Post by JiuJitsu500 on 2010-01-22
Yeah... sharing.... my friend had to do it by creating his own network, and share them that way (I don't know how he did it).... but using USB is easy enough, any reason you can't do it? (unless it's the obvious because it's your internal your trying to share lol)... But, USB support is not enabled in the OSE version and no workarounds are available I've found

---

### Post by prem1er on 2010-01-22
Can't use usb because I am at work and I'm not allowed to connect. I found a workaround though. I just ftped them. Thanks everyone.

---

### Post by MaindotC on 2010-01-25
> **prem1er said:**
> Can't use usb because I am at work and I'm not allowed to connect. I found a workaround though. I just ftped them. Thanks everyone.

Very 1.0 solution - it's more work than it's worth.  Just set up a shared folder and connect to it in winblows by typing in the run box:
```

\\vboxsvr\<shared_folder_name>

```

Come on people don't be using USB and FTP - do this the smart way.

---

