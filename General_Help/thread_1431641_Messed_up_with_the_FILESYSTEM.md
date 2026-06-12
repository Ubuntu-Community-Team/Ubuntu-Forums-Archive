---
title: "Messed up with the FILESYSTEM"
date: 2010-03-16
forum: General Help
---

### Post by siemprepeligroso on 2010-03-16
Dear friends I am stuck into stupid and I can;t move at all, I guess iI managed "somehow" to destroy my operating system...

It is a Asus Eee netbook that came up with Edubuntu 7.04 installed on it, everything was ok until I decided to create e new user that could share same privileges as root. I created a new user and wanted to have full privileges (read-write) on the Filesystem (main directory) on Computer, so I decided to change the Properties at the Filesystem, I opened it and right-clicked ---> Properties.... and changed the settings at Permissions, and in the end I clicked "Apply this to all files and folders" (or something like that, sorry I can't remember the exact phrase) then I waited some time and restarted my netbook...

unfortunately when I try to logon now it gives me no GUI so I am at "tty1" and getting the message: 
"modprobe: FATAL: could not load /lib/modules 2.6.28.9/modules.dep: No such file or directory...
and then it asks for login in terminal-like interface...
I tried modprobe -a but I see no change...I tried ctrl+Alt+BackSpace but no difference at all

Now I don't know what I have to do, can I manage to save the OS without formatting netbook, any variation by using LiveCD edubuntu 7.04, or should I try to upgrade to edubuntu 7.10, what do you prefer, the problem would be easier to me, but the netbook is a government property that's why I do not like to format it, but if it is the last resort I will...

Thanks in advance for your help
God Bless You

---

### Post by prodigy_ on 2010-03-16
> **siemprepeligroso said:**
> 7.04
Whoa, that's really dated. ;-)

Anyway, cheer up - your files are most probably intact. But, if I understand the situation correctly, you might have prohibited root access to some system folders. That's bad, because, depending on what **exactly** you've done, reverting these changes might be a tricky task.

Do you have a backup of your data? If not, I suggest you to boot into a Live CD and make a backup before you'll try anything else.

---

### Post by srs5694 on 2010-03-16
If I understand your description correctly, you changed the permissions on every file on the computer, almost all of them to something inappropriate. If I'm right, this will be so difficult to correct that it will be much simpler to re-install the OS from scratch. Your user files should be retrievable with the help of an emergency boot disc (or bootable flash drive -- Eee netbooks don't have CD/DVD drives, do they?), although you may need to fiddle with their permissions when you restore them to a reinstalled system.

Let this be a lesson: *Do not* change permissions globally on system files! Your goal of giving an ordinary user full access to the entire computer runs counter to very basic principles of Linux security. Depending on your reasons for doing this, there may be a safe way to satisfy your needs, but changing permissions on system files is definitely not something to be done unless you fully understand the implications.

---

### Post by siemprepeligroso on 2010-03-17
Thankfully I have no important data on the netbook, so what is the next thing to do, it there any method to make a system restore to a previous state (date) by using a livecd or the only thing to do is to reinstall the edubuntu from the beginning what do you suggest...

(this time difference between locations we live will kill me)

---

### Post by 3rdalbum on 2010-03-17
Install Ubuntu or Edubuntu from scratch. Despite that this is government property, I think you should install a later version such as 9.10. Anything older than 8.04 will have security flaws and the repositories will be inactive. And 8.10 goes end-of-life in a month too, so don't pick that.

---

