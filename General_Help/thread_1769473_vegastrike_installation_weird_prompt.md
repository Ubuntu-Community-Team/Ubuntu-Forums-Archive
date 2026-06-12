---
title: "vegastrike installation weird prompt"
date: 2011-05-28
forum: General Help
---

### Post by elitejarod on 2011-05-28
Okay, so I installed the vegastrike game.

When I try to run the vssetup file
I get this error

```
~/Downloads/vegastrike-0.5.0$ vssetup
Found data in /home/jarod/Downloads/vegastrike-0.5.0
Error opening terminal: xterm.
~/Downloads/vegastrike-0.5.0$
```For the life of me, I can't figure out what the hell is wrong with my xterm?  I can run xterm fine in another window, and even when I run xterm as the terminal I'm typing vssetup into, it says it can't open the program.

Anyone have any idea, what the hell I'm doing wrong?  I just switched to linux about a week ago so I'm a uber noob.

I know this is probably something stupid.  Please throw me a bone.

---

### Post by wildmanne39 on 2011-05-28
> **elitejarod said:**
> Okay, so I installed the vegastrike game.

When I try to run the vssetup file
I get this error

```
~/Downloads/vegastrike-0.5.0$ vssetup
Found data in /home/jarod/Downloads/vegastrike-0.5.0
Error opening terminal: xterm.
~/Downloads/vegastrike-0.5.0$
```For the life of me, I can't figure out what the hell is wrong with my xterm?  I can run xterm fine in another window, and even when I run xterm as the terminal I'm typing vssetup into, it says it can't open the program.

Anyone have any idea, what the hell I'm doing wrong?  I just switched to linux about a week ago so I'm a uber noob.

I know this is probably something stupid.  Please throw me a bone.
Hi, did you make the game executable?

---

### Post by elitejarod on 2011-05-28
I scoured the websites last night and figured out a work around for the xterm issue.

so I'm going to solve this one now.  But I will be posting another issue that you could probably help me with very shortly, thank you.

```
2. For error message "Error opening terminal: xterm"
mkdir -p /usr/share/terminfo/x
cd /usr/share/terminfo/x
ln -s /lib/terminfo/x/xterm xterm

```
The above worked excellent for my issue, if anyone else is having the same issue.

website I got it from is here:
[http://www.terabyteunlimited.com/kb/article.php?id=454](http://www.terabyteunlimited.com/kb/article.php?id=454)

---

### Post by fsh4fun on 2011-08-21
hello everyone i am having this issue on my laptop using ubuntu 11.04 and i have no clue what i am doing i tried the suggestion above and it seems to work but when i try to run the privsetup it still says error opening terminal: xterm what am i doing wrong?

---

### Post by Capt. Noobuntu on 2012-01-13
Just installed 11.10, and I've been trying to install vegastrike, but have had this xterm error coming up during installation. When I then try to run the game, I get a black screen with a white mouse cursor, but it won't exit or proceed to anything else from there. 

I tried the solution linked to by elitejarod, but when running the cd /usr... line I get a "no such command" response. I've run the lines both *exactly* as they appear, and by substituting my username for "usr", but both approaches yield the same result. Any thoughts on what I'm bungling up here? Thanks!

---

