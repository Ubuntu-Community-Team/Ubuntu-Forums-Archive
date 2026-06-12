---
title: "Editing fstab-What will happen?"
date: 2006-03-08
forum: General Help
---

### Post by ronmarley1 on 2006-03-08
Hi Folks,
I've created a couple of mount points to a couple of shares on a Windows server here at school.  I'd like to add them to fstab so that they are mounted automatically at boot.  The question I have is, when I take my laptop home and boot it up and fstab tries to mount the shares that are here at school, what will happen?  Will I get an error message (I'm guessing I will)?  Will it stop booting since it cannot connect to the shares?  I can live with an error message, but if the boot process dies, that will be more difficult.
Thanks in advance for any thoughts!

---

### Post by Prospero2006 on 2006-03-08
Bad fstab entries won't halt the boot process.
I actually have an fstab entry that is non-functional 
on my machine at home. I don't even get an error message.
Thus, I haven't bothered to fix it because I don't even notice it.

Pros

---

### Post by ronmarley1 on 2006-03-08
Hi Pros,
Thanks for the reply.  I'm gonna add the entries to fstab here at school and the disconnect my laptop from the network and reboot and see what happens.

---

### Post by ronmarley1 on 2006-03-08
Hi Again Pros,
You called it.  I added the entries to fstab.  When I boot UNconnected form the network, everything boots normally, it just doesn't mount the Windows shares.  Thanks for the reply.
Ron
PS, one step close to telling Gates to take a flying leap!

---

### Post by AndrewCaul on 2006-03-08
Yep. No biggie. I had entered some incorrect values for mounting my NTFS partition, and it just gave me an error message and continued booting. So there's no problem with unmountable partitions.
I think (hope) I have the correct stuff entered now. :)

---

