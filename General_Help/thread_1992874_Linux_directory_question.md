---
title: "Linux directory question"
date: 2012-06-01
forum: General Help
---

### Post by apejam on 2012-06-01
Hello all, I have a relatively short and simple question that I couldn't find the answer to anywhere.


is there a way to encapsulate the "/home/username/" part of a directory into one directory for any  linux user.

I've looked into ~/ but it doesn't work, keeps saying "no such file or directory"

---

### Post by dcstar on 2012-06-01
> **apejam said:**
> Hello all, I have a relatively short and simple question that I couldn't find the answer to anywhere.


is there a way to encapsulate the "/home/username/" part of a directory into one directory for any  linux user.

I've looked into ~/ but it doesn't work, keeps saying "no such file or directory"

The base folder for a user is a System Folder with specific security settings and should not be "encapsulated" anywhere else.

If you want to link folders under that level you can - provided you set the permissions appropriately.

---

### Post by apejam on 2012-06-01
I probably should have mentioned my intent. I'm writing a python script that takes gimp brushes that I have downloaded and moves them into my gimp brush folder, simple enough and the script works but only when I have the full source there which begins with "/home/username/"

What I would like to do is make it so that the script will work on any linux box without having to change the username parameter in the source code, so I was hoping there was some kind of default pathway that could point to any "/home/username/"

Sorry for the lack of elaboration, does such a thing exist or am I looking at the problem wrong?

---

### Post by steeldriver on 2012-06-01
can't you use the python os module and look at os.environ['HOME'] ?

[http://docs.python.org/dev/library/os.html](http://docs.python.org/dev/library/os.html)

---

### Post by Cheesemill on 2012-06-01
How about using
```
/home/$USER/
```

---

### Post by MG&amp;TL on 2012-06-01
> **Cheesemill said:**
> How about using
```
/home/$USER/
```

```
michael@laptop:~$ echo /home/$USER
/home/michael
michael@laptop:~$ echo $HOME
/home/michael
michael@laptop:~$
```

;)

---

### Post by apejam on 2012-06-01
Thanks for all the help guys! This would have been 10x easier just creating a bash script to do the same thing, but where would the fun have been in that? :)

The suggestions didn't work, only because there is currently a bug between python3 and the os.enivron module. However You guys pointed me in the right direction and I gained a lot better understanding of linux directories and the python OS module so it was a win for me.

I ended up making it so whoever is using the script has to enter their username first and then I just concatenated it to the rest of the source. Not exactly what I wanted but it'll do.

---

### Post by Turovskii on 2012-06-01
Good dispatch and this post helped me a lot in my college assignment. Gratefulness you as your information.

---

