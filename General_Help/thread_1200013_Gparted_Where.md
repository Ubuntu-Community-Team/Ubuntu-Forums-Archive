---
title: "Gparted Where?"
date: 2009-06-29
forum: General Help
---

### Post by zacharyrs on 2009-06-29
I followed these instructions to install GParted;
Open a terminal window and type in:
sudo apt-get install gparted
 After that you can find GParted in the Gnome menu under [Applications]("http://www.ubuntux.org/how-to-install-partition-editor-gparted#") -> System Tools.


However, under Apps I do not see Sys Tools. See attached.


Where is this? Do I have to reboot?


Any help would be greatly appreciated.

---

### Post by credobyte on 2009-06-29
```
System -> Administration -> Partition Manager ( gparted )

```

---

### Post by akakingess on 2009-06-29
Or you could just open a terminal and type in GParted (or sudo Gparted) whichever is required.

akakingess

---

### Post by credobyte on 2009-06-29
> **akakingess said:**
> Or you could just open a terminal and type in GParted (or sudo Gparted) whichever is required.

akakingess

You can't run GParted from terminal without using sudo ( root ).

---

### Post by Chronon on 2009-06-29
Though, better to use 

```
gksudo gparted
```

since it's a graphical frontend for parted, right?

---

### Post by zacharyrs on 2009-06-29
Thank you so much!

Now, if you could only give your precious insight to my Brasero Burning issue today would be wonderful :)

Thank you so much for your help!!!!

---

### Post by credobyte on 2009-06-29
> **zacharyrs said:**
> Thank you so much!

Now, if you could only give your precious insight to my Brasero Burning issue today would be wonderful :)

Thank you so much for your help!!!!

What, where .. ?

---

### Post by zacharyrs on 2009-06-29
> **credobyte said:**
> What, where .. ?
[http://ubuntuforums.org/showthread.php?t=1199891](http://ubuntuforums.org/showthread.php?t=1199891)

---

### Post by akakingess on 2009-06-29
> **credobyte said:**
> You can't run GParted from terminal without using sudo ( root ).
Thanks for the clarification Credobyte, but at least I did add in there that that may be neccessary to do. I just hadn't had to do it in a while.

akakingess

---

### Post by credobyte on 2009-06-29
> **akakingess said:**
> Thanks for the clarification Credobyte, but at least I did add in there that that may be neccessary to do. I just hadn't had to do it in a while.

akakingess

Np - that was meant to be a post for everyone, not for you or myself :) Many of us have started by copy-pasting commands ( in this case, it would lead into another question - why I can't launch it ).

---

### Post by akakingess on 2009-06-29
I understand, I wasn't upset or anything, and I'm glad that there are more knowledgeable people out there like yourself to help keep others in line or at least well informed. Thanks for your help.

akakinges

---

