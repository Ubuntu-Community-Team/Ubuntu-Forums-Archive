---
title: "How to choose a password for a folder?"
date: 2012-01-11
forum: General Help
---

### Post by sinaphysics on 2012-01-11
Hi,
I want to lock one of my folders which isn't in my Home.
I want to choose a password for lock it and unlock it!
I use ubuntu 11.10.

---

### Post by cortman on 2012-01-11
All the folders that aren't in your home are locked by default, and can't be edited by any but root user. What do you mean by "locking" them?

---

### Post by sinaphysics on 2012-01-11
for example when I'm not near my laptop and my friends use it I want prevent them to access some folders by locking them.

---

### Post by cortman on 2012-01-11
So you're wanting them to not be able to view the folder contents?
You can set the folder to no read permissions quite easily-

```
sudo chmod uog-r /folder_name
```

---

### Post by pr3zident on 2012-01-11
Yea you can use chmod 

```
sudo chmod 700 /home/.../your folder 
```

I haven't tried the command cortman suggested probably works the same .....

---

### Post by Kslawdog on 2012-01-11
Or you can just right-click the folder, go to properties, select permissions, and under owners folder access select list files only.  Maybe just do this before your friends use your computer then after they are done just change it back.  But I'd have to say if your worried about your friends snooping through your computer I wouldn't let them use it at all.

---

### Post by Mariane on 2012-01-11
Considering you can recover the root password... I think the best way would be to transfer your folder on a pen drive and delete it from your computer altogether.

---

### Post by cortman on 2012-01-12
> **Mariane said:**
> Considering you can recover the root password... I think the best way would be to transfer your folder on a pen drive and delete it from your computer altogether.

It's true that a Linux-savvy and determined snoop could get around the chmod thing. It's like we used to say about locks on toolboxes, at the mechanic shop I used to work at- they're to keep honest people out. You can force open any locked toolbox or folder if you have enough determination, but for most honest people just a slight roadblock is plenty to deter them.

---

### Post by cortman on 2012-01-12
> **Mariane said:**
> Considering you can recover the root password... I think the best way would be to transfer your folder on a pen drive and delete it from your computer altogether.

It's true that a Linux-savvy and determined snoop could get around the chmod thing. It's like we used to say about locks on toolboxes, at the mechanic shop I used to work at- they're to keep honest people out. You can force open any locked toolbox or folder if you have enough determination, but for most honest people just a slight roadblock is plenty to deter them.

I guess it's the OP's job to decide whether his friends are "honest" or not...

---

