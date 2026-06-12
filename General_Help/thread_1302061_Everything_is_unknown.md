---
title: "Everything is unknown?"
date: 2009-10-26
forum: General Help
---

### Post by realchamp on 2009-10-26
Hello!

I have a Linux Ubuntu Desktop 9.04 32bit OS.

Whenever I do:
sudo apt-get install lib32gcc1 

I get E: Couldn't find lib32gcc1

Or what's the package I need?

-realchamp.

---

### Post by Penguin Guy on 2009-10-26
> **realchamp said:**
> Hello!

I have a Linux Ubuntu Desktop 9.04 32bit OS.

Whenever I do:
sudo apt-get install lib32gcc1 

I get E: Couldn't find lib32gcc1

Or what's the package I need?

-realchamp.
What are you trying to install? gcc, the compiler is already installed by default.

---

### Post by howefield on 2009-10-26
> **realchamp said:**
> I get E: Couldn't find lib32gcc1

Looks like it is only available in the 64 bit repository.

[http://packages.ubuntu.com/jaunty/lib32gcc1](http://packages.ubuntu.com/jaunty/lib32gcc1)

---

### Post by phillw on 2009-10-26
> **realchamp said:**
> Hello!

I have a Linux Ubuntu Desktop 9.04 32bit OS.

Whenever I do:
sudo apt-get install lib32gcc1 

I get E: Couldn't find lib32gcc1

Or what's the package I need?

-realchamp.


Ermmmm all the references i can find to it are for 64 bit :(

Why are you after it for a 32bit system ?

Phill.

---

### Post by realchamp on 2009-10-27
> **phillw said:**
> Ermmmm all the references i can find to it are for 64 bit :(

Why are you after it for a 32bit system ?

Phill.

Ohh well!

Whenever I do "./someprogram" it tells me it's unknown and some more.

I was using Server edition with 64bit a while ago, it worked there.

How am I supposed to fix it on 32bit?:popcorn:

> **Penguin Guy said:**
> What are you trying to install? gcc, the compiler is already installed by default.

I am trying to install Steam, Adobe Flash Player(for Youtube)

---

### Post by phillw on 2009-10-29
> **realchamp said:**
> Ohh well!

Whenever I do "./someprogram" it tells me it's unknown and some more.

I was using Server edition with 64bit a while ago, it worked there.

How am I supposed to fix it on 32bit?:popcorn:



I am trying to install Steam, Adobe Flash Player(for Youtube)

Try,

```
$sh ./someprogramme
```

Phill.

---

