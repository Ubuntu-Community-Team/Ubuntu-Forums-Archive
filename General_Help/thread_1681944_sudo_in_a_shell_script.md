---
title: "sudo in a shell script"
date: 2011-02-05
forum: General Help
---

### Post by whatthefunk on 2011-02-05
Im trying to write a shell script that outputs system info.  I want to include this line of code:

```
du -s /home/* | sort -nr
```

The command du requires sudo permissions so when I try to run the script I get loads of error messages.  I dont want to include my password in the code.  What is the best way to go about doing this?

Thanks

---

### Post by dollzii on 2011-02-05
Running the script with sudo??

```
sudo sh "nameofscript"
```

---

### Post by nathan726 on 2011-02-05
```
gksu du -s /home/* | sort -nr
```

---

### Post by whatthefunk on 2011-02-05
> **nathan726 said:**
> ```
gksu du -s /home/* | sort -nr
```

Yep.  When I run the code, it asks for my password and then runs it perfectly.  Thanks!

---

### Post by hakermania on 2011-02-05
Please mark the thread as Solved!

---

### Post by whatthefunk on 2011-02-05
Marked as solved.

I also put this code at the front of the script to limit the users who can have access to it:

```
if [ "$(id -u -n)" = "my_user_name" ]; then
...
fi
```

I think I did that right.  It runs fine but I havent tested running as another user yet.

---

### Post by TeoBigusGeekus on 2011-02-05
Just being curious here, but why does du require sudo permissions on your system?

---

### Post by whatthefunk on 2011-02-05
> **TeoBigusGeekus said:**
> Just being curious here, but why does du require sudo permissions on your system?

I think thats the default setting.  It probably would have been easier to edit the sudoers file or something, but I wanted to figure out sudo in shell scripting.

---

