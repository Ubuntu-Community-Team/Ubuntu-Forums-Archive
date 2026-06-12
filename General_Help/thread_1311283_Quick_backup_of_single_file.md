---
title: "Quick backup of single file"
date: 2009-11-02
forum: General Help
---

### Post by Zilioum on 2009-11-02
I want to install grub2, but firs I want to make a backup of my menu.lst file. In a lot of tutorials on different topics, there was terminal command which copied the file you were going to work with under a new name, as a backup.
Lets say you want to work with menu.lst, then you created something like menu_bkp.lst in the same location. 
Until now I never did that, and I cant find any of those old tutorials I saw it in.
Anybody has an idea what am talking about and could tell me the command?

Thanks in advance.

---

### Post by alphaniner on 2009-11-02
Don't know about any special commands, but ```
cp file file.bak
``` has never let me down.  In the case of menu.lst you will need to use sudo if you are going to copy it to the same directory.  Though you might want to copy the file to your home directory, shouldn't need sudo for that:```
cp /boot/grub/menu.lst ~
```

---

### Post by Zilioum on 2009-11-02
Thats it! Thank you! If I put it in my home directory it works, but as soon as I try to put it in the same folder with

```
sudo cp /boot/grub/menu.lst boot/grub/menu.list.bak
```

I get 

```
cp: cannot create regular file `boot/menu/menu.lst.bak': No such file or directory

```

What does that mean?

---

### Post by jpshortstuff on 2009-11-02
> **Zilioum said:**
> ```
sudo cp /boot/grub/menu.lst boot/[color=red]**grub**[/color]/menu.list.bak
```

I get 

```
cp: cannot create regular file `boot/menu/menu.lst.bak': No such file or directory

```

What does that mean?It means you are missing **grub** from the destination path.

---

### Post by alphaniner on 2009-11-02
> **Zilioum said:**
> Thats it! Thank you! If I put it in my home directory it works, but as soon as I try to put it in the same folder with

```
sudo cp /boot/grub/menu.lst boot/grub/menu.list.bak
```

I get 

```
cp: cannot create regular file `boot/menu/menu.lst.bak': No such file or directory

```

What does that mean?

You left out the leading [COLOR="Red"]**/**[/COLOR]:

```
sudo cp /boot/grub/menu.lst [COLOR="Red"]/[/COLOR]boot/grub/menu.list.bak
```

---

### Post by Zilioum on 2009-11-02
I found the mistake. It has to be:
```
sudo cp /boot/grub/menu.lst [COLOR="Red"]/[/COLOR]boot/grub/menu.lst.bak
```
Now it works, thanks for the help.

---

