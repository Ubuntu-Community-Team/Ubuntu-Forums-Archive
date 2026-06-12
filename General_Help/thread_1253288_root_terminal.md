---
title: "root terminal"
date: 2009-08-29
forum: General Help
---

### Post by loosescrew on 2009-08-29
Hello, I have been looking through the system menu. I went to preferences-main menu. system tools-root terminal. applications-system tools and clicked on root terminal. Nothing came up on screen. So my question is I, dont want to be in root. I don't have enough knowledge to stay in root. I assumed that clicking on root terminal would have opened a terminal asking for password. Is system in root now ? I ask because I used to have to supply a password when i clicked on firestarter. now it just opens. Thanks Joe

---

### Post by phantasmik on 2009-08-29
open up a regular terminal window and execute the command
```
whoami
```

---

### Post by loosescrew on 2009-08-29
Thanks,phantasmik,I appreciate the reply. I did open a terminal and it shows me $. So what happens when you click on the root terminal??? Tanks Joe

---

### Post by Rocket2DMn on 2009-08-29
I believe you (and I) are suffering from bug [lpbug]328575[/lpbug].
In the meantime you can start a normal terminal and do 
```
sudo -i
```
to get a root login terminal.  Please be careful with this!

Is there any particular reason you need a root terminal?

---

### Post by loosescrew on 2009-08-29
Rocket2DMn, Thanks. I was just finding my way around. I didn't need a root terminal. I have just been looking around. I believe your right. When i enter- sudo gnome-terminal. i get failed to connect. So I believe your right. I will read about that error and ways to fix. Thanks joe

---

### Post by CatKiller on 2009-08-30
> **loosescrew said:**
> Is system in root now ?

No. That launcher used to function as a way to get a terminal as root. It doesn't currently work. Running one application as root only runs that application as root. It doesn't affect any other running applications.

If you do want a root terminal at some point in the future, you can run ```
sudo -i
```

---

