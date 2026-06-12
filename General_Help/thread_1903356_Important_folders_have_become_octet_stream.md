---
title: "Important folders have become octet stream"
date: 2012-01-02
forum: General Help
---

### Post by Largaroth on 2012-01-02
Fancy a nice laugh ? Then keep reading ^^.

Okay, so I've been doing some web work, and testing it on my machine (thus requiring php).

But I got tired of opening apps as root just to modify the files and folders in the /var/www/ folder.
I proceeded to try some chmod commands on these folders to gain full access to them and modify things at will.
However, in the process of doing this, all the folders in my /var/ directory have changed to octet stream files with unknown type.

My computer will no longer boot (it blocks on startup right around when it has loaded Alsa and TiMidity++).

As you can imagine I am quite put out, and would be very grateful for a little hand in rectifying these horrendous mistakes.
Any ideas ?

For info, the machine is running Oneiric.

---

### Post by sdowney717 on 2012-01-02
perhaps you can chroot into your OS from a live USB or live cd
chroot means your running the os as if it was booted, so then you can make some changes.
for example 
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

I have chrooted into my os from an ubuntu live cd before.

---

### Post by Largaroth on 2012-01-02
Thanks for the tip, but I can actually log on with tty1, and If I run

```
su
```

I can navigate the directories with no problem. The only problem is, that I can't log on using tty7 and graphic mode, because it is freezing just after it displays 

```
Starting TiMidity++ Alsa midi emulation...        [OK]
```

---

### Post by fdrake on 2012-01-02
> 
However, in the process of doing this, all the folders in my /var/ directory have changed to octet stream files with unknown type.

you did that using chmod?
can you post here the exact command you used if you can rember?
use the command "history | less" to navigate through your command history.

---

### Post by Largaroth on 2012-01-02
I say I did it using chmod, i'm only assuming, I don't know the inner workings of the chmod and if could actually cause that sort of problem.

I actually performed a number of chmod commands on the directories because I was trying to cd to them while not being root.

So here we are :

as regular user :
```
sudo chmod 666 /var
```

as Super User:
```
$cd /var/
ls -l
chmod 666 www
```

 I was actually quite stupid and careless with it all, going in and out of super user, trying to access some stuff.
Though it only ever concerned the contents of /var/www.
as SU:
```
cd /
chmod 666 var
```

I don't understqnd what may have gone wrong in all of this.

---

### Post by fdrake on 2012-01-02
well it looks like you did not use a recursive command! that's good it makes it easier. recursive command looks like this "chom -R 666 /var"
so lets try to give them back the original permissions:
```

sudo chmod 751 /var
sudo chmod 755 /var/www

```
try is that works

---

### Post by Largaroth on 2012-01-02
Ah I see, i took away execution privileges to the /var directory, thus preventing a proper booting sequence ?

Well it booted now so thank you very much =)

---

### Post by audiomick on 2012-01-02
> **Largaroth said:**
> 
But I got tired of opening apps as root just to modify the files and folders in the /var/www/ folder.


Had you tried opening an instance of nautilus with root priviliges?
```
gksudo nautilus
```

From there, I think you can just click on files belonging to root to have them open in an editor. Be careful in there, though. You have root priviliges, and can do thing like accidently changing permissions so that your system wont boot. :-\"

---

### Post by fdrake on 2012-01-02
glad it worked. don't forget to mark the threat as "Solved".bye!

---

