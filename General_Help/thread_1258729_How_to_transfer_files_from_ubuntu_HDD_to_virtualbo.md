---
title: "How to transfer files from ubuntu HDD to virtualbox xp virtual drive?"
date: 2009-09-05
forum: General Help
---

### Post by Hoobes1 on 2009-09-05
hi, i just installed windows xp with virtualbox and want to know how to transfer files from my ubuntu hard disk to my virtual xp hard disk. 

Thanks

---

### Post by Liolikas on 2009-09-05
**makeisofs** from folder and mount it on virtual box cdrom.

---

### Post by Hoobes1 on 2009-09-05
what's a makeisofs? and how can i mount it?

---

### Post by Liolikas on 2009-09-05
ups mkisofs, read **man mkisofs**. maybe there is gui way to do same all you want is iso file with data and that command can do this.

---

### Post by Hoobes1 on 2009-09-05
oh ok, so how would i put it into the terminal?

---

### Post by Liolikas on 2009-09-05
mkisofs -o data.iso ~/Desktop/data

---

### Post by Hoobes1 on 2009-09-05
thanks! i'll try it out ^^

---

### Post by P4man on 2009-09-05
I think what the OP wants is sharing files between the virtual XP and the ubuntu host. You can do that through shared folders. Create a shared folder in virtualbox, and then inside the VM (in windows) browse to 

\\vboxsvr\

you should see the share(s) there, and you can read/write to them.

---

### Post by Hoobes1 on 2009-09-05
oh ok, so this way it would be like sharing files through a network connection. if i understood correctly

---

### Post by Hoobes1 on 2009-09-05
i made a shared folder but for some reason i can't access it on windows.

---

### Post by P4man on 2009-09-05
You did make the shared folder in virtualbox configuration, right?

If so, have a look here: [http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

---

### Post by Hoobes1 on 2009-09-05
yeah, and on this tutorial i found on the internet, it says that one should go explorer -> (on the left hand side of the window) right click on My Networks -> browse for the folder that is shared, and then click ok. but when i browse for the folder, it doesn't appear under workgroup, which it should.

---

### Post by P4man on 2009-09-05
then try typing in the explorer address bar:

\\vboxsvr\nameofshare

you can also assign it a drive letter in windows. Open a terminal (yes, a terminal in windows :p  start > run > cmd.exe ) and type

```
net use x: \\vboxsvr\name_of_your_share
```

that should make an X: drive pointing to the virtualbox share.

---

### Post by Hoobes1 on 2009-09-05
lol, terminal in windows ^^

when i put it in, it said that it can't find this network path. =(

---

### Post by P4man on 2009-09-05
Then I bet you didnt install the guest additions.

First make sure you dont have a mounted cdrom in the VM.

Then boot the VM, and once its booted, in the menu select devices > install guest additions

this will pop a virtual cd in the virtual windows. Install the drivers, reboot.

---

### Post by Hoobes1 on 2009-09-05
wow, i can't believe it finally worked! thanks, you really helped me out here =)

---

### Post by rocthrttle on 2011-01-30
this was huge. thanks so much. i really appreciate it. now if i could just get usb thumbdrives to work in it.

---

