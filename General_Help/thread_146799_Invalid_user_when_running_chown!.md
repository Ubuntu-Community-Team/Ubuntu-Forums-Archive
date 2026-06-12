---
title: "Invalid user when running chown?!"
date: 2006-03-19
forum: General Help
---

### Post by Leiki on 2006-03-19
I'm following this guide: [https://wiki.ubuntu.com/InstallingE17Howto](https://wiki.ubuntu.com/InstallingE17Howto)

and I'm at the part to do "sudo chown -R user:USERNAME ~/.ecore" but when I enter in my username (andrew) it says Invalid user. I tried user:**andrew**, user:**andrew_(lastname)**, user:andrew_(lastname), and none of them worked. What is going on?!

---

### Post by dermotti on 2006-03-19
sudo chown -R andrew ~/.ecore

---

### Post by dpaint4 on 2006-03-19
[QUOTE=Leiki]I'm following this guide: [https://wiki.ubuntu.com/InstallingE17Howto](https://wiki.ubuntu.com/InstallingE17Howto)

and I'm at the part to do "sudo chown -R user:USERNAME ~/.ecore" but when I enter in my username (andrew) it says Invalid user. I tried user:**andrew**, user:**andrew_(lastname)**, user:andrew_(lastname), and none of them worked. What is going on?![/QUOTE]

You need to use your actual username, not variations on it. That might be a dumb answer. But for instance, on my machine, I'm 'curtis'. so the command would be:

```
sudo chown -R curtis:curtis /directory/im/claiming/as/mine
```

---

### Post by dermotti on 2006-03-19
Bah, i hate sudo, i got rid of it :-P

---

### Post by dpaint4 on 2006-03-19
[QUOTE=dermotti]Bah, i hate sudo, i got rid of it :-P[/QUOTE]

You what? Really? How? Why? That's really interesting, but I think I feel pretty safe with sudo. I like not being the admin at all times.

---

### Post by dermotti on 2006-03-19
Well i use sudo for the "lilttle things" When its convienient. But if im compiling kernels, or doing big jobs, its just easier for me to use su.

How?

sudo passwd

---

### Post by henriquemaia on 2006-03-19
In chown, you can put only your **username** or, if you like to change the group owner as well, you use

**username:group**

so, in my case, I have something like this:

```
sudo chown -R **henriquemaia:henriquemaia** ~/whatever_folder
```

You can skip the group part. In my case, that would be:

```
sudo chown -R **henriquemaia** ~/whatever_folder
```

---

