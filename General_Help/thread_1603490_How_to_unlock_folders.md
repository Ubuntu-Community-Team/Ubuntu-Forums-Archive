---
title: "How to unlock folders?"
date: 2010-10-22
forum: General Help
---

### Post by TheNerdAL on 2010-10-22
I'm trying to unlock certain folders that I'm trying to delete but can't. How do I do this? It looks like this: 
[IMG]http://i.imgur.com/4kpd4.png[/IMG]

---

### Post by JustinR on 2010-10-22
> **TheNerdAL said:**
> I'm trying to unlock certain folders that I'm trying to delete but can't. How do I do this? It looks like this: 
[IMG]http://i.imgur.com/4kpd4.png[/IMG]

It means it's owned by someone else - so you don't have the permissions to view it. If you want to get into it press ALT + F2 and type 'gksudo nautilus' and navigate to the folder.

You can change the folder permissions to your user if you want to view it normally - navigate to the folder using the procedure I posted above, right click it, go to permissions, and change 'Owner' to your username. to answer your question.

---

### Post by TheNerdAL on 2010-10-22
> **JustinR said:**
> It means it's owned by someone else - so you don't have the permissions to view it. If you want to get into it press ALT + F2 and type 'gksudo nautilus' and navigate to the folder.

You can change the folder permissions to your user if you want to view it normally - navigate to the folder using the procedure I posted above, right click it, go to permissions, and change 'Owner' to your username. to answer your question.

I don't see any folders in that directory where the folders are at.

---

### Post by JustinR on 2010-10-22
> **TheNerdAL said:**
> I don't see any folders in that directory where the folders are at.

Where is the folder located? For example, if it's at /home/USER/Desktop/FOLDER you could just do this:

Press ALT + F2 and type 'gksudo nautilus /home/USER/Desktop/FOLDER'.

---

### Post by TheNerdAL on 2010-10-22
> **JustinR said:**
> Where is the folder located? For example, if it's at /home/USER/Desktop/FOLDER you could just do this:

Press ALT + F2 and type 'gksudo nautilus /home/USER/Desktop/FOLDER'.

Ahhh, there is what I was missing. No one told me to do that part. Thanks! :D

---

### Post by JustinR on 2010-10-22
> **TheNerdAL said:**
> Ahhh, there is what I was missing. No one told me to do that part. Thanks! :D

Well that's what the 'navigate to folder' meant! :P Just use nautilus and browse through until you find the folder!

---

### Post by ibuclaw on 2010-10-22
> **TheNerdAL said:**
> I'm trying to unlock certain folders that I'm trying to delete but can't. How do I do this? It looks like this: 
[IMG]http://i.imgur.com/4kpd4.png[/IMG]

You unlock folders by "levelling up", :-)

As what has already been echoed here, it is an indicator that the directory is owned by someone else (ie: root), and you can only change the attributes of a folder if you are the owner.

---

