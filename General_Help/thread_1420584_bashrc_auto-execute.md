---
title: "bashrc auto-execute"
date: 2010-03-03
forum: General Help
---

### Post by cucuru on 2010-03-03
hello, I understand that ~/.bashrc should execute when I login in ubuntu server, isnt it?

It doesnt do it, what may I change to do it?

I have the file in /home/user and I login as user.

Thanks for your help! regards

---

### Post by gmargo on 2010-03-03
From the **bash(1)** man page:> 
 When bash is invoked as an interactive login shell  ... 
 it first reads and executes commands from the file **/etc/profile**, if that file exists.
After reading that file, it looks for **~/.bash_profile**,  **~/.bash_login**,  and  **~/.profile**,  in  that  order, and reads and executes commands from the _first_ one that exists and is readable.
Usually, your **~/.profile** contains the command to run the **~/.bashrc** file.  But that part may be commented out, or you may have one of the other files that precludes it.  Or you may not have any of those files.  If you need them, you can find the pristine system defaults in **/etc/skel/.profile** and **/etc/skel/.bashrc**.

---

### Post by cucuru on 2010-03-04
Thanks!

---

