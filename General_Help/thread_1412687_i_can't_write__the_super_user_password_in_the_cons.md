---
title: "i can't write  the super user password in the console!"
date: 2010-02-21
forum: General Help
---

### Post by unKnowcommand on 2010-02-21
when i try to write the password this happens

[http://s890.photobucket.com/albums/ac101/03190319_photos/?action=view&current=Screenshot.png](http://s890.photobucket.com/albums/ac101/03190319_photos/?action=view&current=Screenshot.png)
spawn this black thing and i cant write.
any idea?

---

### Post by llamabr on 2010-02-21
In ubuntu, we're not supposed to tell you how to enable root's password, or let you use su.

but what are you trying to do?  If you just want access to the root user for a few commands, 
```
sudo -i 
```
will keep it running.

for security reasons, it doesn't make any output when you type the password, but it's definately reading it.

---

### Post by Swagman on 2010-02-21
lol

Your a n00b right ?

That's ok... This is a standard n00b issue.

There will be no visual clue that you are typing in your password. just type it in and press enter

---

### Post by mali2297 on 2010-02-21
The system does not echo any symbols when you write the password but it still reads it. Just type your password and press enter.

---

### Post by unKnowcommand on 2010-02-21
> **Swagman said:**
> lol

Your a n00b right ?

That's ok... This is a standard n00b issue.

There will be no visual clue that you are typing in your password. just type it in and press enter
1 i always use windows yes im a noob in linux
2 i press all the damn keys in the keyboard and no one work

---

### Post by unKnowcommand on 2010-02-21
> **llamabr said:**
> In ubuntu, we're not supposed to tell you how to enable root's password, or let you use su.

but what are you trying to do?  If you just want access to the root user for a few commands, 
```
sudo -i 
```will keep it running.

for security reasons, it doesn't make any output when you type the password, but it's definately reading it.
im tryimg to install a drivers i need become a super user and i cant write the pass i prees all the keys and no one work

---

### Post by Iowan on 2010-02-21
> **unKnowcommand said:**
> ... i prees all the keys and no one workThey are probably working - enter your password and press [ENTER].

---

### Post by nishant.singh28 on 2010-02-21
sudo -s
and type in your password(you will NOT see any of your password characters typed in)

---

### Post by Baneblade on 2010-02-21
OP, how many times do people have to tell you the solution to your "problem". 
Simply enter your password and hit return (enter). It will work.

The terminal doesn't show your password as a security measure. This is normal. Nothing is broken.
Enjoy.

---

### Post by unKnowcommand on 2010-02-21
> **Baneblade said:**
> OP, how many times do people have to tell you the solution to your "problem". 
Simply enter your password and hit return (enter). It will work.

The terminal does show your password as a security measure. This is normal. Nothing is broken.
Enjoy.
oh,that worked i feel like a noob -_-

---

