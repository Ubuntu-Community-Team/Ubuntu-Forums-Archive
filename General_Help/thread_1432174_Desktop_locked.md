---
title: "Desktop locked"
date: 2010-03-17
forum: General Help
---

### Post by sam45 on 2010-03-17
my Desktop is locked
can't right click on it, but I can right click on every other window, so its not the mouse.

tried [this]("http://ubuntuforums.org/showthread.php?t=538038")
but it wasn't working..
first gave me a permission denied ( cannot access `/home/sam/.gvfs')
and second did nothing

any help would be appriciated

---

### Post by n0dix on 2010-03-17
Maybe a permission problem.
Post the output of: ls -la /home/sam/.gvfs

---

### Post by sam45 on 2010-03-17
> **n0dix said:**
> Maybe a permission problem.
Post the output of: ls -la /home/sam/.gvfs

sam@ubuntu:~$ ls -la /home/sam/.gvfs
total 4
dr-x------  2 sam sam    0 2010-03-17 18:20 .
drwxr-xr-x 68 sam sam 4096 2010-03-17 18:20 ..

---

### Post by _h_ on 2010-03-17
Try this command:

[http://ubuntuforums.org/showpost.php?p=3275650&postcount=2](http://ubuntuforums.org/showpost.php?p=3275650&postcount=2)

---

### Post by prodigy_ on 2010-03-17
Yes, sudo chown can't access ~/.gvfs. This is normal behavior. And chmod won't give you any output if there were no errors.

It seems your problem isn't permissions. To be sure, try this command ```
touch ~/Desktop/test_file
``` If **test_file** will appear on your Desktop, do ```
rm ~/Desktop/test_file
``` to delete it. If both commands work, the permissions are ok and perhaps something is wrong with Gnome or nautilus.

---

### Post by sam45 on 2010-03-17
> **_h_ said:**
> Try this command:

[http://ubuntuforums.org/showpost.php?p=3275650&postcount=2](http://ubuntuforums.org/showpost.php?p=3275650&postcount=2)

as I said in my first post, both commands in that link aren't working..

sam@ubuntu:~$ sudo chown -R sam:sam /home/sam
[sudo] password for sam: 
chown: cannot access `/home/sam/.gvfs': Permission denied
sam@ubuntu:~$

---

### Post by sam45 on 2010-03-17
> **prodigy_ said:**
> Yes, sudo chown can't access ~/.gvfs. This is normal behavior. And chmod won't give you any output if there were no errors.

It seems your problem isn't permissions. To be sure, try this command ```
touch ~/Desktop/test_file
``` If **test_file** will appear on your Desktop, do ```
rm ~/Desktop/test_file
``` to delete it. If both commands work, permissions are ok.

nothing appears on my desktop after entering first command :S

---

### Post by _h_ on 2010-03-17
> **sam45 said:**
> as I said in my first post, both commands in that link aren't working..

sam@ubuntu:~$ sudo chown -R sam:sam /home/sam
[sudo] password for sam: 
chown: cannot access `/home/sam/.gvfs': Permission denied
sam@ubuntu:~$

Oops, sorry...couldn't see that you had linked the topic already. :oops:

---

### Post by prodigy_ on 2010-03-17
> **sam45 said:**
> nothing appears on my desktop
Yet "touch" gave you no errors? I'm sorry, but can you repeat ```
touch ~/Desktop/test_file
```command again? And use ```
ls -al ~/Desktop
``` to see if the file is really there.

---

### Post by sam45 on 2010-03-17
> **prodigy_ said:**
> Yet "touch" gave you no errors? I'm sorry, but can you repeat ```
touch ~/Desktop/test_file
```command again? And use ```
ls -l ~/Desktop|grep test
``` to see if the file is really there.

seems like the file is there.. but I can't see it on my desktop

sam@ubuntu:~$ touch ~/Desktop/test_file
sam@ubuntu:~$ ls -l ~/Desktop|grep test
-rwxr--r-- 1 sam sam   162 2010-03-17 18:04 ~$test.docx
-rwxr--r-- 1 sam sam 10110 2010-03-16 19:35 test.docx
-rw-r--r-- 1 sam sam     0 2010-03-17 19:12 test_file
sam@ubuntu:~$ 


@_h_ np at all, I'm glad you tried to help :)

---

### Post by prodigy_ on 2010-03-17
Strange. I think it's safe to blame it on nautilus. Unless someone will give you a better idea, you'll probably need to reinstall gdm:
```
sudo apt-get remove gdm ubuntu-desktop
sudo apt-get autoremove
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by sam45 on 2010-03-17
> **prodigy_ said:**
> Strange. I think it's safe to blame it on nautilus. Unless someone will give you a better idea, you'll probably need to reinstall gdm:
```
sudo apt-get remove gdm ubuntu-desktop
sudo apt-get autoremove
sudo apt-get install gdm ubuntu-desktop
```

Did exactly what you told..
but no improvement, desktop is still locked..

---

### Post by sam45 on 2010-03-18
No one knows?..
I really need help with this =/

---

### Post by hatalar205 on 2010-03-18
> **sam45 said:**
> my Desktop is locked
can't right click on it, but I can right click on every other window, so its not the mouse.

tried [this]("http://ubuntuforums.org/showthread.php?t=538038")
but it wasn't working..
first gave me a permission denied ( cannot access `/home/sam/.gvfs')
and second did nothing

any help would be appriciated

What were you doing before your Desktop is locked?

---

### Post by sam45 on 2010-03-18
> **hatalar205 said:**
> What were you doing before your Desktop is locked?
Ehm.. I can't really say for sure.. because I didn't notice it right away.
but last things I did was changing visual effects and settings.
(like getting 4 different wallpapers on my cube and such)

---

### Post by hatalar205 on 2010-03-18
If your panel works, just try to install Dolphin (file manager). If it works and then we can be sure that nautilus is the reason of your problem.

---

### Post by sam45 on 2010-03-18
> **hatalar205 said:**
> If your panel works, just try to install Dolphin (file manager). If it works and then we can be sure that nautilus is the reason of your problem.

my panel works and so does dolphin :)
Do you know how I can fix nautilus?

---

### Post by hatalar205 on 2010-03-18
> **sam45 said:**
> my panel works and so does dolphin :)
Do you know how I can fix nautilus?

Unfortunately "No". But I had -not exactly but similar- problem 4 days ago. Maybe you want to look at my threat.
[http://ubuntuforums.org/showthread.php?t=1429822](http://ubuntuforums.org/showthread.php?t=1429822)

---

