---
title: "How Do I Go Back A Directory?"
date: 2011-01-03
forum: General Help
---

### Post by Sanchenzo on 2011-01-03
I'm very new to Linux, please go easy on me I...how do I return to a directory in terminal?

Fore Example:

```
/home/user#
cd Documents
/home/user/Documents#
cd Terminal
/home/user/Documents/Terminal#

```

How do I return to /home/user/Documents# without having to create a new terminal?

P.S

I'm not sure if this is the right place to post this...

---

### Post by anystupidname1 on 2011-01-03
```
cd ..
```
OR
```
cd ~/Documents
```
OR
```
cd /home/user/Documents
```

[http://www.ice2o.com/bash.php](http://www.ice2o.com/bash.php)
[http://www.ice2o.com/bash_quick_ref.html](http://www.ice2o.com/bash_quick_ref.html)

---

### Post by uRock on 2011-01-03
Use the **cd** command with no arguments or [B]cd ~/<location>

[/B]Examples; ```
rabbit@me:~$ cd ~/Desktop
rabbit@me:~/Desktop$ cd ..
rabbit@me:~$ cd ~/Desktop/Desktop-Backup
rabbit@me:~/Desktop/Desktop-Backup$ cd ~/Desktop
rabbit@me:~/Desktop$ cd ~/Music
rabbit@me:~/Music$ cd
rabbit@me:~$ 
```

---

### Post by Sanchenzo on 2011-01-03
When I try,

```
cd Documents
```

I get this,

```
bash: cd: Documents: No such file or directory

```

---

### Post by Sanchenzo on 2011-01-03
> **uRock said:**
> Use the **cd** command with no arguments or [B]cd ~/<location>

[/B]Examples; ```
rabbit@ronnie-desktop:~$ cd ~/Desktop
rabbit@ronnie-desktop:~/Desktop$ cd ..
rabbit@ronnie-desktop:~$ cd ~/Desktop/Desktop-Backup
rabbit@ronnie-desktop:~/Desktop/Desktop-Backup$ cd ~/Desktop
rabbit@ronnie-desktop:~/Desktop$ cd ~/Music
rabbit@ronnie-desktop:~/Music$ cd
rabbit@ronnie-desktop:~$ 
```

Thank you uRock

---

### Post by Vaphell on 2011-01-03
to make your life easier learn to use tab to autocomplete names so you avoid those nasty typos - it requires only few chars to fill the rest for you, if there are multiple names that fit, it will print it out for you so you can further narrow the scope.

also:
~ your home dir
. current dir
.. parent dir

eg you can do
cd ~/.. to get to the parent dir of your home, which is /home

---

### Post by uRock on 2011-01-03
Use **cd ~/Documents**

---

### Post by tgm4883 on 2011-01-03
> **Sanchenzo said:**
> When I try,

```
cd Document
```

I get this,

```
bash: cd: Documents: No such file or directory

```

Probably because the directory is called Documents (notice the s on the end)

---

### Post by Sanchenzo on 2011-01-03
That was a typo...

---

### Post by TeoBigusGeekus on 2011-01-03
> **uRock said:**
> Use the **cd** command with no arguments or [B]cd ~/<location>

[/B]Examples; ```
rabbit@me:~$ cd ~/Desktop
rabbit@me:~/Desktop$ cd ..
rabbit@me:~$ cd ~/Desktop/Desktop-Backup
rabbit@me:~/Desktop/Desktop-Backup$ cd ~/Desktop
rabbit@me:~/Desktop$ cd ~/Music
rabbit@me:~/Music$ cd
rabbit@me:~$ 
```

A tiny correction, if you allow me...
cd with no arguments does not go back a folder, it just goes to your home folder from wherever you are.

---

