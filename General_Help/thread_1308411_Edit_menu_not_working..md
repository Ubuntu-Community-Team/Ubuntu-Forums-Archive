---
title: "Edit menu not working."
date: 2009-10-31
forum: General Help
---

### Post by bhishan on 2009-10-31
I am using Karmic 64 bit. I installed google earth today. I cant find google earth in the application menu. I tried to edit the menu if I could add a application. When I reght click application and select edit menu nothing happens. System>Preferences>main menu also doesnt open anything. Help:(

---

### Post by nikgare on 2009-10-31
How did you install google earth?

---

### Post by bhishan on 2009-11-01
> **nikgare said:**
> How did you install google earth?

I downloaded it from the google website and installed it. It appeared in the application menu after a restart but I cant still open edit menu.

---

### Post by nikgare on 2009-11-02
The program that should appear when you edit the menus is called **alacarte**

What errors do you get when you run this command in a terminal?

---

### Post by bhishan on 2009-11-02
> **nikgare said:**
> The program that should appear when you edit the menus is called **alacarte**

What errors do you get when you run this command in a terminal?

I have included the screenshot.

---

### Post by AlNaimi on 2009-11-02
Edit menu dose not work with me too.. Ubuntu 9.10 64bit...
No third-party software was instelld..
Thanks

---

### Post by bhishan on 2009-11-06
bump

---

### Post by bhishan on 2009-11-11
:cry:

---

### Post by bhishan on 2009-12-22
Help

---

### Post by lavinog on 2009-12-23
did you happen to run alacarte with sudo?...if so I wonder if it messed up the permissions of the menu.

---

### Post by bhishan on 2009-12-23
> **lavinog said:**
> did you happen to run alacarte with sudo?...if so I wonder if it messed up the permissions of the menu.

Haha, it worked. Why didnt I even try it .... lol. Thanks!! But how can I make it work without the need to go to the terminal?

---

### Post by lavinog on 2009-12-23
> **bhishan said:**
> Haha, it worked. Why didnt I even try it .... lol. Thanks!! But how can I make it work without the need to go to the terminal?

I was trying to say using sudo with alacarte could be what is causeing the permission issues.
see what this gives you:
```

find ~/ -xdev -user root

```

you shouldn't get many things if any.

---

### Post by bhishan on 2009-12-23
> **lavinog said:**
> I was trying to say using sudo with alacarte could be what is causeing the permission issues.
see what this gives you:
```

find ~/ -xdev -user root

```

you shouldn't get many things if any.

bhishan@DevilsWorkshop:~$ find ~/ -xdev -user root
/home/bhishan/.local/share/desktop-directories
/home/bhishan/.config/menus
find: `/home/bhishan/.config/menus': Permission denied

---

### Post by lavinog on 2009-12-23
> **bhishan said:**
> 
/home/bhishan/.config/menus
find: `/home/bhishan/.config/menus': Permission denied
That is what I suspected.


try this:
```

sudo chown -Rv bhishan /home/bhishan/.config/menus

```

then try
```
alacarte

```
Do not use sudo with alacarte from now on.

chown is a command to change the owner of files and folders...in this case we are changing the menu folder owner from root to your user name...at some point the folder was changed to root which is why you couldn't use the menu editor.

---

### Post by bhishan on 2009-12-24
> **lavinog said:**
> That is what I suspected.


try this:
```

sudo chown -Rv bhishan /home/bhishan/.config/menus

```

then try
```
alacarte

```
Do not use sudo with alacarte from now on.

chown is a command to change the owner of files and folders...in this case we are changing the menu folder owner from root to your user name...at some point the folder was changed to root which is why you couldn't use the menu editor.

It worked :) Thanks a lot.

---

