---
title: "hddtemp without sudo"
date: 2009-06-27
forum: General Help
---

### Post by ~sHyLoCk~ on 2009-06-27
Hello!
Is there anyway of getting hddtemp to work without having to key in the password? I have tried adding ```
shylock ALL = NOPASSWD: /usr/sbin/hddtemp
```
Also tried:
```
%hwmon ALL = NOPASSWD: /usr/sbin/hddtemp
```
What I'm trying to do is making an alias like I did with gpu temp ```
alias gpu?='nvclock -i | grep temp'
```
For Hddtemp as well. Now my only option left is to echo my password and feed it to sudo, which is not a good idea I think. Any help?

---

### Post by dcstar on 2009-06-27
> **~sHyLoCk~ said:**
> Hello!
Is there anyway of getting hddtemp to work without having to key in the password?
........

Mine works fine without any password, I run it in daemon mode.

---

### Post by AoSteve on 2009-06-27
```

sudo chmod u+s /usr/sbin/hddtemp

```You have to chmod the command so you can use it as a normal user and a super user.  :)

Source :  [Conky Hardcore HDDTemp](http://conky.linux-hardcore.com/?page_id=427)

---

### Post by ~sHyLoCk~ on 2009-06-27
> **AoSteve said:**
> ```

sudo chmod u+s /usr/sbin/hddtemp

```You have to chmod the command so you can use it as a normal user and a super user.  :)

Source :  [Conky Hardcore HDDTemp](http://conky.linux-hardcore.com/?page_id=427)

Doesn't help, I even used chown to give it my user privileges. 
It says /dev/sda: open: Permission denied

So I think it's my /dev/sda not allowing access to hddtemp. No?

---

### Post by AoSteve on 2009-06-27
Can you sudo hddtemp /dev/sda and get a temp?

---

### Post by ~sHyLoCk~ on 2009-06-27
> **AoSteve said:**
> Can you sudo hddtemp /dev/sda and get a temp?

Yes

---

### Post by AoSteve on 2009-06-27
I would imagine it has to do with the privilege of /dev/sda   You'd probably have to CHMod that to get it to work then, though I'm not absolutely sure here.   

It's always worked if I chmod u+s the hddtemp command...   My suggestion is to post on the "post your conky" thread and ask BruceM or one of those guys who have more experience with hddtemp then I.  :)

Sorry I couldn't be much more help.

---

### Post by Ayuthia on 2009-06-27
I am currently in Gentoo, but I am thinking that it might be defined the same.  Have you tried adding yourself to the disk group:
```
sudo gpasswd -a shylock disk
```

I tried it out in Gentoo and it gave me access to /dev/sda.

---

### Post by ~sHyLoCk~ on 2009-06-27
> **Ayuthia said:**
> I am currently in Gentoo, but I am thinking that it might be defined the same.  Have you tried adding yourself to the disk group:
```
sudo gpasswd -a shylock disk
```

I tried it out in Gentoo and it gave me access to /dev/sda.

Yes I added myself to the group. Weird thing now is that I can't even get hddtemp to work with root account. If I do:
```
$ su
$ hddtemp /dev/sda
/dev/sda:open Permission denied.
```

---

### Post by ~sHyLoCk~ on 2009-06-27
Solved the issue using netcat :) Thnx to all those who replied.

---

### Post by Agent ME on 2009-06-27
> **~sHyLoCk~ said:**
> Solved the issue using netcat :) Thnx to all those who replied.
What does netcat have to do with hddtemp?

Anyway, your problem is because you set your user as the owner of hddtemp, after setting the setuid bit on it. The SetUID bit makes it so whenever the executable is run, it has the rights of the user that owns it. You want it to be owned by root so that it runs as root.

"sudo chown root:root /usr/sbin/hddtemp" will fix it.

---

### Post by ~sHyLoCk~ on 2009-06-27
> **Agent ME said:**
> What does netcat have to do with hddtemp?

Anyway, your problem is because you set your user as the owner of hddtemp, after setting the setuid bit on it. The SetUID bit makes it so whenever the executable is run, it has the rights of the user that owns it. You want it to be owned by root so that it runs as root.

"sudo chown root:root /usr/sbin/hddtemp" will fix it.

I changed ownership after trying everything and still it didn't owrk! Then I tried by changing ownership and it didn't work. I then used ```
nc localhost 7634
``` to get the temp. The problem is fixed.

---

