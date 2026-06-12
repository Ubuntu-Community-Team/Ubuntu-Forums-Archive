---
title: "Accidently set Grub Tmeout too low"
date: 2011-08-04
forum: General Help
---

### Post by Ooimo on 2011-08-04
I set the default os to boot as windows 7 with a timeout of 1 second. 
I thought that this would be enough time to switch os ubuntu when i need to, but I am unable to.
 How can i reset the timeout to 3 seconds? I also cannot view the ubuntu partition within windows because of ubuntu's file system.

Thanks

---

### Post by CowzRule on 2011-08-04
I would try accessing the config file via a LiveCD

---

### Post by Wim Sturkenboom on 2011-08-04
Keep <shift> pressed while booting; should give you the menu so you can get in Ubuntu.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
or just spam the up arrow key or esc key if you have the menu hidden

---

### Post by raja.genupula on 2011-08-04
sudo gedit /boot/grub.grub.cfg 

find this line (2nd set timeout) 

set timeout=1 or what ever you want

---

### Post by Ooimo on 2011-08-05
> **CowzRule said:**
> I would try accessing the config file via a LiveCD


> **raja.genupula said:**
> sudo gedit /boot/grub.grub.cfg 

find this line (2nd set timeout) 

set timeout=1 or what ever you want

I tried to edit the config file from a live cd but didn't have permission. Is there another way?

---

### Post by hakermania on 2011-08-05
> **Ooimo said:**
> I tried to edit the config file from a live cd but didn't have permission. Is there another way?

from the live cd you can
```

sudo su

```
and it won't ask you for password.
When you type the above command you will become super user, be careful with this!
After being super user you can use 'nano', its a cli command and it is something like a text editor. It will help you edit the config file. Its syntax is:
```

nano /path/to/file

```
Hit, Ctrl+O and [Enter] when you're finished editing, then Ctrl+X and you're done.

---

### Post by Ooimo on 2011-08-05
> **Wim Sturkenboom said:**
> Keep <shift> pressed while booting; should give you the menu so you can get in Ubuntu.

> **pqwoerituytrueiwoq said:**
> or just spam the up arrow key or esc key if you have the menu hidden

I tried both of these but no matter how much I press the keys it isn't enough time. I have also tried pressing the keys before seeing the screen.

---

### Post by hakermania on 2011-08-05
> **Ooimo said:**
> I tried both of these but no matter how much I press the keys it isn't enough time. I have also tried pressing the keys before seeing the screen.

Try my suggestion, super user has all the rights to do whatever she/he wants

---

### Post by Ooimo on 2011-08-05
> **hakermania said:**
> from the live cd you can
```

sudo su

```
and it won't ask you for password.
When you type the above command you will become super user, be careful with this!
After being super user you can use 'nano', its a cli command and it is something like a text editor. It will help you edit the config file. Its syntax is:
```

nano /path/to/file

```
Hit, Ctrl+O and [Enter] when you're finished editing, then Ctrl+X and you're done.

Thanks, can you please tell me exactly what to edit because I don't want to corrupt grub.

---

### Post by hakermania on 2011-08-05
> **Ooimo said:**
> Thanks, can you please tell me exactly what to edit because I don't want to corrupt grub.
Read the last post here:
[http://ubuntuforums.org/showthread.php?t=1567456](http://ubuntuforums.org/showthread.php?t=1567456)
I assume that you have GRUB 2 of course

---

### Post by Ooimo on 2011-08-05
> **hakermania said:**
> Read the last post here:
[http://ubuntuforums.org/showthread.php?t=1567456](http://ubuntuforums.org/showthread.php?t=1567456)
I assume that you have GRUB 2 of course

Thanks!

To fix i used: 

```

Sudo su
Chmod -w /boot/grub
Sudo gedit /boot/grub/grub.cfg

```

Then changed the timeout string to another value

---

