---
title: "Root Pass Word Problem"
date: 2011-05-24
forum: General Help
---

### Post by UBuntinator on 2011-05-24
If I Try To Open A Terminal Window, It Doesnt Show Up, And If I Try To Edit Sources, The Password Is Wrong(Or Not), I Am The Admin Account, But It Says I'm Using An Incorrect Password?

---

### Post by jd.jayded on 2011-05-24
ctrl+alt+t 
type sudo software-center, hit enter
Should open the software center, assuming your password is right.
Also, capitalizing every word makes your post hard to read.

---

### Post by matt_symes on 2011-05-24
Hi

> **UBuntinator said:**
> If I Try To Open A Terminal Window, It Doesnt Show Up, And If I Try To Edit Sources, The Password Is Wrong(Or Not), I Am The Admin Account, But It Says I'm Using An Incorrect Password?

Press ALT + F2 together to get the run dialog. Enter 

```
gnome-terminal
```

Does that get you the gnome terminal ?

Press ALT + F2 together again and type

```
gksu-properties
```

Make sure the authenication mode is set to **sudo** in the dropdown box.

Kind regards

---

### Post by coffeecat on 2011-05-24
> **jd.jayded said:**
>  
type sudo software-center, hit enter

You would be well advised **never** to run software-center with sudo. It can cause serious problems. Software centre should be run as a non-elevated user. It will prompt you for your password if it needs elevated privileges. Also - running a graphical app with sudo can cause other problems. You should use gksu or gksudo. See this link:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

@UBuntinator, you might want to read that link as well. It tells you all about the Ubuntu admin model.

---

