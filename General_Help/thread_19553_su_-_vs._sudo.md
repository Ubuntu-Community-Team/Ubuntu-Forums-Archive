---
title: "su - vs. sudo"
date: 2005-03-12
forum: General Help
---

### Post by DaBigUA on 2005-03-12
Hello.  Semi-clueless newbie here.

When wanting to work as root, I open a terminal and use 

```
su -
```

But when I try something like

```
sudo mkdir /media/windows
```

it rejects the very same password that worked with su -.

I assume both su - and sudo are asking for the root password.  Is this correct?

---

### Post by bored2k on 2005-03-12
[QUOTE=DaBigUA]Hello.  Semi-clueless newbie here.

When wanting to work as root, I open a terminal and use 

```
su -
```

But when I try something like

```
sudo mkdir /media/windows
```

it rejects the very same password that worked with su -.

I assume both su - and sudo are asking for the root password.  Is this correct?[/QUOTE]
 sudo works with your user password.
su works with, well, your superuser password.


edit > by the topic I thought this was going to be a su vs sudo discussion lol . 8)

---

### Post by CowPie on 2005-03-12
[QUOTE=DaBigUA]Hello.  Semi-clueless newbie here.

When wanting to work as root, I open a terminal and use 

```
su -
```

But when I try something like

```
sudo mkdir /media/windows
```

it rejects the very same password that worked with su -.

I assume both su - and sudo are asking for the root password.  Is this correct?[/QUOTE]
 Also, remember that you have to create a root password ot use su or kde apps (which use su).  So: "sudo passwd" should do it

---

### Post by bored2k on 2005-03-12
[QUOTE=CowPie]Also, remember that you have to create a root password ot use su or kde apps (which use su).  So: "sudo passwd" should do it[/QUOTE]
 Is it a necessity really?
If I change KDE apps icons to open with gksudo I would think there is no need for this.

Or is it?

---

### Post by DaBigUA on 2005-03-12
[QUOTE=bored2k]sudo works with your user password.
su works with, well, your superuser password.
[/QUOTE]

Thank you for your quick reply.  A tiny spot of fog lifts.  ;)

My mistake was thinking sudo wanted my root password.  It wanted my regular account password.  

I am running/learning Ubuntu-Debian-Linux on a single user machine.  Am I right in assuming sudo would be useful to give a limited power to regular users?   Specifically, joeuser can perform certain superuser tasks without possessing the root password?

Also, is this the right forum for this kind of question?

Thanks again!

---

### Post by bored2k on 2005-03-12
[QUOTE=DaBigUA]Thank you for your quick reply.  A tiny spot of fog lifts.  ;)

My mistake was thinking sudo wanted my root password.  It wanted my regular account password.  

I am running/learning Ubuntu-Debian-Linux on a single user machine.  Am I right in assuming sudo would be useful to give a limited power to regular users?   Specifically, joeuser can perform certain superuser tasks without possessing the root password?

Also, is this the right forum for this kind of question?

Thanks again![/QUOTE]
 Guess so. This or Desktop Support.

I mostly click on New Posts so I don't even notice what category is it in .

---

### Post by CowPie on 2005-03-14
[QUOTE=bored2k]Is it a necessity really?
If I change KDE apps icons to open with gksudo I would think there is no need for this.

Or is it?[/QUOTE]

Oh, it may hvae changed.  Apparently kde now supports sudo root with 3.4.

---

