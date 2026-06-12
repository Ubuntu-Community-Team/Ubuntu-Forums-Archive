---
title: "Could not open location 'file:///home/"
date: 2009-11-11
forum: General Help
---

### Post by endre_bp on 2009-11-11
Hello,

I am using ubuntu 9.04, and i am a happy user! :p 

A strange message pops up when i want to open the hard disk and a message comes up. First i tougth that i have a virus so i scanned the pc with avast for linux but no viruses. The error message is:

Error
Could not open location 'file:///home/
No application is registered as handling this file.


What is even more wierd that earlier I was able to open the hard disk and to select files, but now a cannot.

I would appreciate your help.

regards
Endre

---

### Post by Somme on 2009-11-11
My best bet would be to reinstall Nautilus. Before doing that, let us know the output of:
```
 
nautilus $HOME

```

---

### Post by prshah on 2009-11-11
> **endre_bp said:**
> 
I am using ubuntu 9.04, and i am a happy user! :p 

Error
Could not open location 'file:///home/
No application is registered as handling this file.


Hi and this is a known bug, please see [this post]("http://ubuntuforums.org/showpost.php?p=6082327&postcount=2") for a more detailed explanation.

Did you by any chance upgrade from 8.10, or was this a fresh install of 9.04? Just curious)

---

### Post by endre_bp on 2009-11-12
Hello

First of all, many thanks for your kind responses! :p :KS

To be more clear, I have installed Ubuntu 9,04 from cd. I used the update manager for the upgrades and Ubuntu was working fine. After a time I could not open the Hard disk (please note: this is my slave "hd2", as the master "hd" i have only programs installed and on the slave hd2 private stuff). Interestingly I was able to open files from the hd2 with the open office programs. Only I could not open the hd from the "places" menu.

Yesterday i have upgraded from 9,04 to 9,10 as i lost patiance. Now I have the hard disk icon on the desstop. I can open the hd2 (slave) and i can also open the files from it but cannot unmount it. I have the error message:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdb5 from /media/HD2

As i wrote earlier, this is the HD2, the second (slave) hard disk in my pc.

Although i can use the hd2, i thought i should be able also to unmount it. Not quite sure why i cannot.

I'd appreciate your suggestions. 

Regards
Endre

---

