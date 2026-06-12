---
title: "Ops! I locked myself out!"
date: 2006-05-31
forum: General Help
---

### Post by brsseb on 2006-05-31
Ok. It began with me removing the IP6-stuff under network connections (to speed up  firefox). But i ALSO deleted the following line:

```

127.0.0.1       localhost.localdomain   localhost       ubuntu

```

So, now if i run stuff like "sudo su" or "sudo somethingelse", and I enter a password, i get a "Autehcication failed"-error. Also, EVERY application that normally would require password, just crashes! 

That means i cant go back into network dialog and fix the line, OR use a terminal to sudo gedit /etc/hosts manually! 

I tried "su root" and enter my password, but i get the same autentication error. It wont even try to validate my password. 

So...hehe...what do i do now? Im stripped of my root powers! (Its like being back in windows ](*,) )

---

### Post by ????? on 2006-05-31
Have you tried booting into the Ubuntu recovery console?

---

### Post by sadjack on 2006-05-31
I did something similar and hosed my /etc/hosts file with the result that I got similar errors.

The only way I found to fix it was to use a live CD and edit the files from that to get back to the original config.

If you don't have one handy, you could try downloading something like damn small linux which is a small download, I take it you have internet or you would not be posting! ;) 

Good luck

---

### Post by glotz on 2006-05-31
Or using a kernel parameters or a livecd. See [http://makuchaku.info/amnesty/#gainrootwithoutlogin](http://makuchaku.info/amnesty/#gainrootwithoutlogin)

---

### Post by brsseb on 2006-05-31
I fixed it :-D 

As the first reply said, i just rebooted into recovery mode and fixed it from there. 

If anyone else get this "problem" (its more like a clear case of  SUE - Supid User Error :mrgreen: ), here is the solution:

```

vi /etc/hosts

## And put this line back in there
127.0.0.1    localhost.localdomain     localhost     ubuntu

## Note: replace "ubuntu" with whatever your machine name is

```

Now it works. Thankz ppl.

---

