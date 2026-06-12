---
title: "jailkit and all commands = Segmentation fault"
date: 2009-08-10
forum: General Help
---

### Post by shadowhywind on 2009-08-10
Hi all, I have an ubuntu server running, with a jailkit. Everything has been running great for the past 2ish years that it has been running, however I decided to try to install a program (mogrify) for users inside the jail. During the process of copying all the libs that mogrify required (i used ldd /usr/bin/mogrify, to get what was required). I ended up screwing up bash. (The user could log in, but the prompt was garbage text, and then it just froze there). I fixed that problem with a 'jk_cp -v -f /home/chrootusers /bin/bash' command. The users were able to log back in, however I now have a slightly larger problem. Nearly every command that a user inside the jail runs, equals a segmentation fault. (ls, date, wget, etc) However cat, echo, cd, exit all works. Any ideas would be great. Thanks

---

### Post by rohan21 on 2009-08-11
i am not sure about the server but on ubuntu 9.04 Gnome setup the following worked for me - please give it a try

1) gksuo nautilus (enter root password)
2) go to /var/cache/apt
3)rename srcpkgcache.bin and pkgcache.bin to srcpkgcache.bin_old and pkgcache.bin_old
4) Run the update again:- 
sudo apt-get update or Update manager GUI way

This time it will re-create the files again and update should work just fine.

Hope this helps.
Regards
Rohan

---

### Post by michcook on 2011-01-28
> **shadowhywind said:**
> Hi all, I have an ubuntu server running, with a jailkit. Everything has been running great for the past 2ish years that it has been running, however I decided to try to install a program (mogrify) for users inside the jail. During the process of copying all the libs that mogrify required (i used ldd /usr/bin/mogrify, to get what was required). I ended up screwing up bash. (The user could log in, but the prompt was garbage text, and then it just froze there). I fixed that problem with a 'jk_cp -v -f /home/chrootusers /bin/bash' command. The users were able to log back in, however I now have a slightly larger problem. Nearly every command that a user inside the jail runs, equals a segmentation fault. (ls, date, wget, etc) However cat, echo, cd, exit all works. Any ideas would be great. Thanks

Did you resolve this?  I have just run into this problem after attempting to jk_init bash for ssh functionality within a jail.  Now all commands seg-fault.

---

