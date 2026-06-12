---
title: "User leftovers"
date: 2010-05-29
forum: General Help
---

### Post by komitaltrade on 2010-05-29
I removed users and home directories, but when I again add user with same name (different or same UID - result is same), Ubuntu Lucid don't let me in the session because of some collision with old user (I also have old icon immediatelly in GDM).

It is obvious how some leftovers are present in system after user deletion, but what and where?

---

### Post by linfidel on 2010-05-29
Did you remove the users from the "Users and Groups" utility in the Administration section?  Did it succeed?  If it succeeded, you won't see the users there any more.  If they are deleted, you could check in /user to see if their directories are still there, and delete them. 

The other option would be to edit /etc/passwd (as root), and delete any lines with the user names in it.  I'd make a backup first, though.

---

### Post by komitaltrade on 2010-05-29
Please read first my post.

It is no user directory and user is deleted from /etc/passwd (otherwise he will appear in GDM even if directory and user is deleted and I wrote how system have some leftovers because Nautilus want to enter in /home/user what don't exist anymore with same UID, same is the name and xsassion don't start, it is broken).

---

### Post by linfidel on 2010-05-30
> **komitaltrade said:**
> Please read first my post.

It is no user directory and user is deleted from /etc/passwd (otherwise he will appear in GDM even if directory and user is deleted and I wrote how system have some leftovers because Nautilus want to enter in /home/user what don't exist anymore with same UID, same is the name and xsassion don't start, it is broken).Instead of telling me to read your post, perhaps you should read mine and answer the question I asked instead.  

I assume English is not your first language (at least I hope not), but your post is very hard to understand so if you want to solve problems, you will need to try to answer questions from people who try to help.

I have no more suggestions.

---

### Post by finlost on 2010-05-30
:popcorn:

---

### Post by JustinR on 2010-05-30
> **finlost said:**
> :popcorn:

+1 lol

To the OP: What do you mean there is a collision with the old user? What error, if it gives one, does it say?

---

### Post by komitaltrade on 2010-05-30
Correct, English is my sixt language (from 14), but as it is your first language, you should to understand "_***I removed users and home directories***_" and not to ask/suggest "*you could check in /user to see **_if their directories are still there_**,  and delete them*". Maybe is more appropriate delete than remove, but the fact is how I really removed them in external hard drive (to turned them back - to restore them, if thats not the problem). But result is same, directories are not in the system (they are out).

Despite my clear sentence (in English), I also answered again on your question "*It is no user directory and user is deleted from /etc/passwd*".

And what is wrong than if I wrote "_***I removed users and home directories***_" and if I just pointed on the material fact (by definition it cant be offensive, because I just pointed the fact how you should first to read again "_***I removed users and home directories***_").

P.S. After over 20 years on Linux, I really don't need answers (in fact - questions) from beginners in situation with serious problem. I located cause of the problem and I will solve it in day or two. You know, problem is how Linux is not anymore like before and he start to look and act more and more like Windows (registry philosophy is practically already implemented in Linux and it is truth how applications are with lot of leftovers in file system and it is not registry files like in Windows, it is ...).

---

### Post by linfidel on 2010-06-01
.
> **komitaltrade said:**
> P.S. After over 20 years on Linux, I really don't need answers  ...).Then you're certainly in the wrong place.

Pretty sad that after over 20 years on Linux, you can't figure out how to remove a user.  I wouldn't brag.  But then, it only seems like over 20 years - considering Linux has only been around for less than 20 years. :p

---

### Post by komitaltrade on 2010-06-01
First Linux kernel is developed 1991, ... so, ... I guess how I missed something vs. 20 years (but, you missed the point).

You also missed the point of question (it is not how to remove a user).

---

