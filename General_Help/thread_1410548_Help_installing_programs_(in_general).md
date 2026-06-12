---
title: "Help installing programs (in general)"
date: 2010-02-18
forum: General Help
---

### Post by madtyper on 2010-02-18
Hi. I'm pretty new to linux.

I'm trying to get, if possible, extracted programs to register within ubuntu: 

I just installed azureus/vuze, though when I enter a "azureus" command I get the 'use apt-get .. azureus' output. The only way to access it is by using the "./azureus" command from the vuze directory. What bugs me is I'm pretty sure if I used "apt-get" I'd have azureus icons, and the program would be registered throughout ubuntu. Is there a file(s) I should update or a specific location I should have extracted the program to to make "official"? (I'm in a similar situation w/java, though at least I added the bin directory from my ~/java to what I hope is the global or appropriate "path" file [~/.bashrc]).

Thanks for the help. :popcorn:

edit: i guess what i'm saying is the install doesn't feel "clean." windows does everything for you, so i kind of feel like i'm missing something ...

---

### Post by b_vamsi on 2010-02-18
Try this if it helps..

Add icon to applications menu:

Goto System->Main Menu->Internet->New Item

    Type:Application

    Name: Azureus

    Command: azureus

---

### Post by Girya on 2010-02-18
> **madtyper said:**
> Hi. I'm pretty new to linux.

I'm trying to get, if possible, extracted programs to register within ubuntu: 

I just installed azureus/vuze, though when I enter a "azureus" command I get the 'use apt-get .. azureus' output. The only way to access it is by using the "./azureus" command from the vuze directory. What bugs me is I'm pretty sure if I used "apt-get" I'd have azureus icons, and the program would be registered throughout ubuntu. Is there a file(s) I should update or a specific location I should have extracted the program to to make "official"? (I'm in a similar situation w/java, though at least I added the bin directory from my ~/java to what I hope is the global or appropriate "path" file [~/.bashrc]).

Thanks for the help. :popcorn:

edit: i guess what i'm saying is the install doesn't feel "clean." windows does everything for you, so i kind of feel like i'm missing something ...

you should probably install it in /usr/bin but then you have to add launchers (icons) 

I use synaptic or apt-get if the package is available it just works and save the hassle of adding launchers.

if you are interested you can check out FHS its the stanard for file systems

[http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE20]("http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE20")

---

### Post by 2hot6ft2 on 2010-02-18
> **b_vamsi said:**
> Try this if it helps..

Add icon to applications menu:

Goto System->Main Menu->Internet->New Item

    Type:Application

    Name: Azureus

    Command: azureus
:confused::confused::confused::confused::confused::confused:

The fastest and easiest way to install it is with
```
sudo apt-get install azureus vuze
```
Since you didn't say where you extracted it from (file type)

---

### Post by lidex on 2010-02-19
Here is the official documentation for installing in ubuntu:
[https://help.ubuntu.com/9.10/add-applications/C/index.html]("https://help.ubuntu.com/9.10/add-applications/C/index.html")
It's worth a read ;)

---

### Post by aysiu on 2010-02-19
This will help you:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Bottom line: think of it like the iTunes App Store or Android Market. You don't download individual files and install them. You just browse what you want to install and mark those applications for installation.

---

