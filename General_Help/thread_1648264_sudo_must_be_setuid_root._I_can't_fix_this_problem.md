---
title: "sudo must be setuid root. I can't fix this problem. Need help."
date: 2010-12-18
forum: General Help
---

### Post by rcayea on 2010-12-18
Hi Everyone,
As the subject says, i have the problem when trying to use sudo, I get this message: "sudo: must be setuid root". I think this might be something to do with the fact that I changed the ownership of the /usr/local folder to me. 

I found this solution online but it doesnt work because when I try it, the terminal says I need permission, I try sudo and obviously I can't use sudo.

To fix the error above chown and chmod the sudo file as root, in my case the file is in /usr/bin

root>chown root:root /usr/bin/sudo
root>chmod 4111 /usr/bin/sudo


I also tried sudo -L  and was asked permission....same problem.




Any help out there?
Thanks,
Randy

---

### Post by colobix on 2010-12-18
Have you tried the graphical way?
gksudo nautilus /usr/
Right click on the local folder go to preferences > permission and change it that way.

---

### Post by jocko on 2010-12-18
> **rcayea said:**
> I think this might be something to do with the fact that I changed the ownership of the /usr/local folder to me.
If you really only did it to your /usr/local, sudo should not be affected, so I'm guessing you had a typo in the command and changed the ownership on the whole /usr folder or even the entire file system...
But why would you want to change the permissions on a system folder? That's a sure way of breaking your system...

Easy way: complete reinstall. Time spent: 20 min + time for reinstalling applications.

Hard way: Find out exacly which files you changed, what their proper permissions are and change them all back from recovery mode. Time spent: hours to days or even weeks until you have everything back the way it's supposed to be...

---

### Post by surfer on 2010-12-18
you could try booting with a live system (e.g. the ubuntu disc you used for the installation), mount the partition your / is on (e.g. /dev/sda1) and try to chmod /usr/bin/sudo from there. this will be something along
```

$ sudo mount /dev/sda1 /mnt
$ sudo chmod 4111 /mnt/usr/bin/sudo

```

---

### Post by rcayea on 2010-12-19
Thanks. I'll give these tips a try.

---

### Post by BioCoDeR on 2011-06-05
Hmm... I have the same problem right now... how about you try

chmod -R root:root /

In my case, I changed the ownership of the entire filesystem / to myself, meaning that i can no longer access sudo. I am now doing:

chmod -R root:root / 

to see if it resolves the problem.


EDIT: Ah, crap, it doesn't make any difference at all, for some reason I can change the permissions of everything from root to myself, but 'myself' cannot change the permissions back to root. Seems a reinstall is the only way through.

---

