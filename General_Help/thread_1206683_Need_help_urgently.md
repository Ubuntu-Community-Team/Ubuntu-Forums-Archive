---
title: "Need help urgently"
date: 2009-07-07
forum: General Help
---

### Post by wongpk on 2009-07-07
Hello all,

I follow the instruction here at [http://ubuntuforums.org/showthread.php?t=987244](http://ubuntuforums.org/showthread.php?t=987244)

And I ended up getting some permission denied at etc/ folder and cannot boot into my system. Now I cannot login to my system... Any help would be much appreciate!!!

---

### Post by Idefix82 on 2009-07-07
Can you describe exactly what you have done?

Have you tried booting into the recovery shell?

---

### Post by wongpk on 2009-07-07
These are the steps I did...

1, Login as root

2, Edit etc/init.d/rc

3, Save, close and restart

4, Cannot restart or shutdown, so I press power button.

5, I boot up it gave me this error message

/etc/init.d/rc: Permission Denied
init: rc2 main process terminated with status 2

6, I boot into Recovery mode

7, Choose "Drop to root shell prompt" and chmod -R 755 /etc

8, Still cannot boot in.

How? Please, I don't want to reinstall the system..

---

### Post by DeMus on 2009-07-07
> **wongpk said:**
> These are the steps I did...

1, Login as root

2, Edit etc/init.d/rc

3, Save, close and restart

4, Cannot restart or shutdown, so I press power button.

5, I boot up it gave me this error message

/etc/init.d/rc: Permission Denied
init: rc2 main process terminated with status 2

6, I boot into Recovery mode

7, Choose "Drop to root shell prompt" and chmod -R 755 /etc

8, Still cannot boot in.

How? Please, I don't want to reinstall the system..

Why did you edit the file /etc/init.d/rc? What did you add to or delete from it?
The file's permission is 755, owner is root in group root.
Try booting from a live CD and change the file back to what it was before you edited it.

---

### Post by wongpk on 2009-07-07
I edit it only... I edit CONCURRENCY=none to CONCURRENCY=shell

How can I edit if I boot from live CD?

---

### Post by Idefix82 on 2009-07-07
> **wongpk said:**
> 
1, Login as root


How?

> **wongpk said:**
> 
2, Edit etc/init.d/rc


Can you be more specific, please.

> **wongpk said:**
> 
7, Choose "Drop to root shell prompt" and chmod -R 755 /etc


That's likely to have made things worse, since some files (e.g. symbolic links in /etc/rc1.d - /etc/rc6.d) need permissions 777.

---

### Post by wongpk on 2009-07-07
I login by logout user account and login to root account.

I edit CONCURRENCY=none to CONCURRENCY=shell in etc/init.d/rc file

So is there anyway to make it back? Or I need to reinstall the whole system?

---

### Post by oldos2er on 2009-07-07
It isn't CONCURRENCY=shell that's the problem; it's the change in file permissions.

---

### Post by wongpk on 2009-07-07
I don't know, I did not change the permission or anything. I just open the file with a text editor and save it, close.

So... Is there anywhere to reverse whatever I did? :P

---

### Post by oldos2er on 2009-07-07
You said "Choose "Drop to root shell prompt" and chmod -R 755 /etc", which is most definitely changing permissions.

 There's no easy way to undo that, since you'd need to restore every permission on each file and directory in /etc. I read the thread you referenced in your first post, but I can find any direction to run chmod -R 755 /etc.

---

