---
title: "can't login after grub rescue"
date: 2010-08-27
forum: General Help
---

### Post by whimsica on 2010-08-27
I have a vista/ubuntu system.
I tried to restart the computer into vista and it came up grub rescue.
 
I did what someone suggested and typed in
grub rescue> set prefix=(hd0,5)/boot/grub
grub rescue> insmod (hd0,5)/boot/grub/normal.mod
rescue:grub> normal
Anyway that got me into a menu where the ubuntu server is.
I chose it and it sends me into tty1 where it asks for my login
 
My login when the machine used to come up log/pass was
dan/mypass
 
but in the tty1 it says login incorrect.
 
I need to get back into my server. I'm not sure why it's messed up. So how do I do it.
And is there some service that can help me get it back up. I've spent all morning on this and have got nowhere.
 
Thanks,
 
Dan

---

### Post by whimsica on 2010-08-27
now I went into rescue mode on the disk and reinstalled grub on the root.
Now when I restart. I get a boot menu with choices.
 
Chosing linux. I get tty1 and login.  The username and login I was using was dan/mypass.
 
But exiting to shell and doing ls /home it shows only dansav a different user maybe the first user.
 
So how do I get back to the dan/mypass. 
 
It appears that dansav does not have any of the files I was working on or even the gnome interface?
 
How do I get back to normal?
 
Thanks,
 
Dan

---

