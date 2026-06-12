---
title: "E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)"
date: 2011-07-12
forum: General Help
---

### Post by npattillo on 2011-07-12
This is the error that I am getting when I am trying to update an application or manage something through synaptic package manager. I am still learning the system. Any suggestions on how to remove the bad line?

E: Malformed line 48 in source list /etc/apt/sources.list (dist parse)

---

### Post by Vaphell on 2011-07-12
what does
```
cat -n /etc/apt/sources.list
```
show in line #48?

to edit the file use gedit (with admin rights)
```
gksu gedit /etc/apt/sources.list
```

if you don't know what's wrong with the line, comment it with #

---

### Post by wildmanne39 on 2011-07-12
Hi, you maybe able to fix it with these two commands.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by npattillo on 2011-07-12
> **Vaphell said:**
> what does
```
cat -n /etc/apt/sources.list
```
show in line #48?

to edit the file use gedit (with admin rights)
```
gksu gedit /etc/apt/sources.list
```

if you don't know what's wrong with the line, comment it with #
48    deb [http://winff.org/ubuntu](http://winff.org/ubuntu) 10.04

I was trying to get the latest update on winff and screwed it up. How do I remove it? Thanks for your help.

---

### Post by npattillo on 2011-07-12
> **wildmanne39 said:**
> Hi, you maybe able to fix it with these two commands.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
I ran the first code and the update but it is still giving me the same error on line 48

---

### Post by npattillo on 2011-07-12
> **Vaphell said:**
> what does
```
cat -n /etc/apt/sources.list
```
show in line #48?

to edit the file use gedit (with admin rights)
```
gksu gedit /etc/apt/sources.list
```

if you don't know what's wrong with the line, comment it with #
Sweet. I knew I had to open gedit and delete the line but I didn't know how to do it. Thanks for your help.

---

### Post by wildmanne39 on 2011-07-12
Hi, if your problem is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

