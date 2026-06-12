---
title: "Uninstalling Ubuntu?"
date: 2010-05-01
forum: General Help
---

### Post by Premium Jersey Milk on 2010-05-01
OK, so the 9.10-10.4 upgrade keeps breaking things, now I have no graphics card according to it, my task bar has disappeared and I can't reenable it and worst of all I can't boot into windows seven which has lightroom and photoshop on it which I need to process my photos for a client.

My plan is to uninstall ubuntu, do my stuff on windows 7 then download 10.4 when the servers get a little less busy (in a few days) Then, do a clean install of Ubuntu 10.4 and go form there.

Problem one is I don't know how to uninstall ubuntu while having it the only usable system on my computer.

All the tutorials online use a different OS to delete the Ubuntu partition.

Any help will be appreciated.

---

### Post by zaphod777 on 2010-05-01
just put in the Win7 disk and tell it to format the drive and install Windows I believe is what you want to do. 

****All data will be lost.

---

### Post by Premium Jersey Milk on 2010-05-01
I have 2 HDD's

One of them is running this ubuntu system

the other has windows seven and vista.



Is there any way I can do this with out installing another copy of windows? I don't mind losing all my ubuntu data, thats all backed up. I'd rather do it without ruining my install of 7. All my programs would have to be reinstalled etc.

---

### Post by zaphod777 on 2010-05-01
I see I think you have 2 options 

1. from windows in the disk manager format the ubuntu HDD 
2. from a live CD format the Ubuntu HDD using gparted

just be really careful and check what your boot manager is. if you are using grub and remove ubuntu you might not be ale to boot at all.

Check your guide you referred to. I don't usually dual boot I just have a separate OS in a virtual machine.

---

### Post by Premium Jersey Milk on 2010-05-01
Thanks for the help! I'll try the live CD trick.

---

### Post by zaphod777 on 2010-05-01
no problem hopefully you have better luck in a few days. I always like a fresh install anyway.

---

### Post by aysiu on 2010-05-01
You need to restore the Windows boot loader to the MBR:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Then you can delete the Ubuntu partition and still be able to boot Windows.

This is why I recommend Wubi for dual-boots instead:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by zaphod777 on 2010-05-01
> **aysiu said:**
> You need to restore the Windows boot loader to the MBR:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Then you can delete the Ubuntu partition and still be able to boot Windows.

This is why I recommend Wubi for dual-boots instead:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

ahh yes I figured there was something along those lines. 

That pesky MBR. :)

---

### Post by Premium Jersey Milk on 2010-05-02
Alright the live CD trick worked, I deleted all my partitions and now I'm writing from a flawlessly working 10.4.

Thanks guys!

---

### Post by zaphod777 on 2010-05-02
\\:d/

---

