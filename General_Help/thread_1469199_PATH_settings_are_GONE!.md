---
title: "PATH settings are GONE!"
date: 2010-05-02
forum: General Help
---

### Post by Madonkadonk on 2010-05-02
I need to reset my PATH settings, this is what i get from the terminal 
madonkadonk@madonkadonk-laptop:~$ echo $PATH
:/home/madonkadonk/Downloads/android-sdk-linux_86/tools

ALMOST NOTHING WORKS RIGHT NOW!

---

### Post by dcstar on 2010-05-02
> **Madonkadonk said:**
> I need to reset my PATH settings, this is what i get from the terminal 
madonkadonk@madonkadonk-laptop:~$ echo $PATH
:/home/madonkadonk/Downloads/android-sdk-linux_86/tools

ALMOST NOTHING WORKS RIGHT NOW!

/etc/environment should contain this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by Madonkadonk on 2010-05-02
> **dcstar said:**
> /etc/environment should contain this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

It does contain that already!

---

### Post by WorMzy on 2010-05-02
It'll probably fix itself after a reboot, but for now, try typing this into a console:
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Madonkadonk on 2010-05-02
Yes thank you!

---

