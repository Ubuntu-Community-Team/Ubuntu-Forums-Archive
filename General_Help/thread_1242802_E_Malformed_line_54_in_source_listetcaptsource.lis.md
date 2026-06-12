---
title: "E: Malformed line 54 in source list/etc/apt/source.list(uri parse)"
date: 2009-08-17
forum: General Help
---

### Post by soot on 2009-08-17
I am obviously new to Ubuntu. I recently installed 8.10 after years of frustrations using Windows. I would be grateful for any help !

---

### Post by SuperSonic4 on 2009-08-17
Likely suspects:

1) Typo in sources list
2) line runs on

----------------

1) Can you go into a terminal (System --> Administration --> Terminal) and paste in the following code

```
cat /etc/apt/sources.list
```

After that can you post it all or just the area around line 54.

-----------

2) Open /etc/apt/sources.list as root: ```
gksu gedit /etc/apt/sources.list
``` and put a hash '#' (without the quote marks) in front of line 54 and save and exit

-----------

In both cases attempt to run ```
sudo apt-get update
``` from the terminal

---

### Post by soot on 2009-08-17
I inputted your instructions into the terminal and got a response but how do i post them 4 you to see?

---

### Post by aysiu on 2009-08-17
> **soot said:**
> I inputted your instructions into the terminal and got a response but how do i post them 4 you to see?
Highlight.

Copy.

Paste.

---

### Post by soot on 2009-08-17
How do i identify line 54?

---

### Post by plucky on 2009-08-17
> **soot said:**
> How do i identify line 54?

Use ```
gksu gedit /etc/apt/sources.list
``` Then go to **Edit > Preferences** and tick the box **Display Line Numbers** or post your sources.list as pointed out by aysiu so that we can have a look.


Good Luck

---

### Post by outcast302 on 2013-04-26
> **plucky said:**
> Use ```
gksu gedit /etc/apt/sources.list
``` Then go to **Edit > Preferences** and tick the box **Display Line Numbers** or post your sources.list as pointed out by aysiu so that we can have a look.


Good Luck

Hey, I know I'm pretty late to this game, but I found this thread after a search concerning the same problem with v.11.10.

When I followed the instructions above (very helpful because all I know about programming is 'print "hello world"'), line 54 showed "deb libgdata-common libgdata13 lzma".

Is that sufficient to diagnose the problem, or do you need to see the rest of the source.list file?

---

### Post by wildmanne39 on 2013-04-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

