---
title: "Dual boot vista and ubuntu (vista installed first)"
date: 2009-08-02
forum: General Help
---

### Post by tinh_si on 2009-08-02
I am an absolute beginner at ubuntu and much so at trying to do dual booting

I installed ubuntu and got it to boot find with vista.  However, i wanted to set vista to be in charged of things.  I then found the instruction on how to have it done from the link below

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

i followed the instruction down to the letters but now i can't boot into ubuntu any more.  It keep saying that the file can't be found.  Please help me fix this.

Thank you all in advance and hope to get some help from some of you experts soon

---

### Post by merlinus on 2009-08-02
If you restored vista to the mbr, after installing ubuntu, that is why grub is no longer available.  Even with using grub, you can set vista to boot first.

If you like, you can restore grub using the live cd.  Open a terminal and enter these commands, one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

and restart.

---

### Post by tinh_si on 2009-08-02
thank you for your help but when i typed in this command 

find /boot/grub/stagel

i got this msg

Error 15: File not found
????

---

### Post by merlinus on 2009-08-02
Post results of

```
sudo fdisk -l
```

---

### Post by louieb on 2009-08-02
> **tinh_si said:**
> thank you for your help but when i typed in this command 

find /boot/grub/stagel

i got this msg

Error 15: File not found
????

Its stage1 (0ne at the end)

> **merlinus said:**
> Post results of

```
sudo fdisk -l
```

and thats a Lowercase L at the end.

---

