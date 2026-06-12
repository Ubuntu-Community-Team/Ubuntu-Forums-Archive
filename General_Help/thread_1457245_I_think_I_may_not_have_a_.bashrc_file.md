---
title: "I think I may not have a .bashrc file"
date: 2010-04-18
forum: General Help
---

### Post by MCVenom on 2010-04-18
The title explains it all, I just got done looking for my .bashrc file, and I can't seem to find it.  I tried to open it in the terminal, looked for it in Nautilus (with hidden files viewable), I can't find it.  ](*,)

Is that a file I have to create myself, or is it supposed to be there automatically? Thanks in advance for an answer to my noob question!:lolflag:

---

### Post by Serpher on 2010-04-18
Is there any output when you execute:

```
$ls -a|grep .bashrc
```

---

### Post by MCVenom on 2010-04-18
> **Serpher said:**
> Is there any output when you execute:

```
$ls -a|grep .bashrc
```
Nope, no output.

---

### Post by john newbuntu on 2010-04-18
Just create one:
touch .bashrc
chmod 744 .bashrc

---

### Post by Terl on 2010-04-18
You can easily make one.  Ubuntu does not have a .bashrc but you can make one.

---

### Post by MCVenom on 2010-04-18
> **john newbuntu said:**
> Just create one:
touch .bashrc
chmod 744 .bashrc
Alright thanks, I'll go ahead and make it myself :D

---

### Post by sisco311 on 2010-04-18
> **john newbuntu said:**
> Just create one:
touch .bashrc
chmod 744 .bashrc

The default permissions of the file are 644 (no execute permission is needed)

> **BlackOtaku said:**
> Alright thanks, I'll go ahead and make it myself :D

You can copy the default .bashrc file from the /etc/skel directory:
```
cp /etc/skel/.bashrc ~/
```

---

### Post by howhy on 2013-01-06
> **sisco311 said:**
> The default permissions of the file are 644 (no execute permission is needed)



You can copy the default .bashrc file from the /etc/skel directory:
```
cp /etc/skel/.bashrc ~/
```
thats a good answer:guitar:

---

### Post by sisco311 on 2013-01-06
Thanks! :)

Old thread closed.


[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

