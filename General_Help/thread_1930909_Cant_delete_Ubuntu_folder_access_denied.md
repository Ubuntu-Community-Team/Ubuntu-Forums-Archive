---
title: "Cant delete Ubuntu folder access denied?"
date: 2012-02-24
forum: General Help
---

### Post by bbno3 on 2012-02-24
Ubuntu 11.10 64bit

There is a folder called "backup" on my desktop *not made by Deja dup( but made by another program*lucky backup if i rember* and when i attempt to delete it, it says i do not have permission.
Im new to the terminal and all i know is the command will need something like 'Sudo' in front of it to make it root, so if you could help.


 :confused:

---

### Post by roelforg on 2012-02-24
```

sudo rm -rf /home/<username>/Desktop/backup

```

---

### Post by Diametric on 2012-02-24
If it's your folder you can run

```
sudo chmod u+x /path/to/file
```

then run

```
sudo rmdir -rf /path/to/file
```

---

### Post by roelforg on 2012-02-24
> **Diametric said:**
> If it's your folder you can run

```
sudo chmod u+x /path/to/file
```then run

```
sudo rmdir /path/to/file
```
You're assuming the folder's empty.
rmdir will fail if it isn't.

---

### Post by Diametric on 2012-02-24
> **roelforg said:**
> You're assuming the folder's empty.
rmdir will fail if it isn't.

yup...thanks for that catch.

---

### Post by roelforg on 2012-02-24
> **Diametric said:**
> yup...thanks for that catch.
sure, no problem

@bbno3
Diametric's way should also work, just replace rmdir with ```
rm -rf
```
Don't forget the path!!!

---

### Post by bbno3 on 2012-02-24
Wouldn't be able to tell me how that piece of code worked roelforg?
and thanks!

:guitar:

---

### Post by roelforg on 2012-02-24
> **bbno3 said:**
> Wouldn't be able to tell me how that piece of code worked roelforg?
and thanks!

:guitar:
Which one?

EDIT: The quote option is useful here.

---

### Post by bbno3 on 2012-02-25
> **roelforg said:**
> ```

sudo rm -rf /home/<username>/Desktop/backup

```

this one?

---

### Post by Paqman on 2012-02-25
**sudo** = Super User DO = Elevates your privileges enough to do the task

**rm** = remove

**-rf** = recursive and force = applies the remove command to all folders and file within the target, and ignores any complaints from the system

**/home/<username>/Desktop/backup** = the target for the remove command

---

### Post by Thorsen V on 2012-02-25
just to add another fly to the ointment ... :)

$ sudo chattr +i -RV some-dir/

Now try deleting  some-dir (or anything it contains) with anything so far mentioned.

Actually this is a great way to protect files you own from accidental deletion.

Linux is brilliant :)

---

