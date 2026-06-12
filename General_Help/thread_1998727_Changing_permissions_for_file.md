---
title: "Changing permissions for file"
date: 2012-06-07
forum: General Help
---

### Post by famebu on 2012-06-07
I am trying to edit etter.conf and when i edit it and try to save i get: For file /etc/etter.conf no backup copy could be created before saving. If an error occurs while saving, you might lose the data of this file. A reason could be that the media you write to is full or the directory of the file is read-only for you. 
So I try to save "nevertheless" and get: The document could not be saved, as it was not possible to write to /etc/etter.conf.

Check that you have write access to this file or that enough disk space is available.

I checked the permissions and owner has read/write and I thought I would be owner so how do I change the permissions to be able to edit the file or how do I get root to be able to edit it?

I am still new to most of this so thank you for the help!

---

### Post by timgood on 2012-06-07
Sorry, just realised you are using Kubuntu. That should be:

> **famebu said:**
> how do I get root to be able to edit it?


```
kdesu kate etter.conf
```

Enter your password. Robert should be your father's brother.

---

### Post by famebu on 2012-06-07
> ```
kdesu kate etter.conf
```

That didn't work i got: kdesu: command not found

---

### Post by zombifier25 on 2012-06-07
Shouldn't it be kdesudo?

---

### Post by dino99 on 2012-06-07
this for kde installation: kdesu kate etter.conf
and that on gnome one : gksu gedit etter.conf

---

### Post by mastablasta on 2012-06-07
kdesudo kate etter.conf
 
or 
kdesudo kate
 
and then open the file from the menu as you woudl normally.
 
the important thing is you need to launch the programmes with elevated privilages (ie. graphical sudo) in kde this is done by kdesudo.
 
here is an answer to why: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
and here is a full explanation of sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
basically it gives administration access to GUI programmes.

---

### Post by Erik1984 on 2012-06-07
(just my opinion) Save yourself the headache and edit system files with nano from the terminal, works on many distros.

```
sudo nano -B /path/to/importantfile
```

With the -B option nano automatically creates a backup of the original (state of the file before you started editing) when you hit CTRL+O (save).

---

### Post by famebu on 2012-06-09
> kdesudo kate etter.conf

or 
kdesudo kate

and then open the file from the menu as you woudl normally.

the important thing is you need to launch the programmes with elevated privilages (ie. graphical sudo) in kde this is done by kdesudo.

here is an answer to why: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
and here is a full explanation of sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

basically it gives administration access to GUI programmes.

Thank you that worked, thank you for the explanations of it also!

---

