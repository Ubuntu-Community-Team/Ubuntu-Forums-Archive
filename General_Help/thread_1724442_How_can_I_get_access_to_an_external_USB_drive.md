---
title: "How can I get access to an external USB drive?"
date: 2011-04-08
forum: General Help
---

### Post by cdysthe on 2011-04-08
Hi,

I have an external USB drive with one ext4 partition on it. When I plug it in it's mounted and a file manager window pops up. However, I am not able to create files/folders unless I'm root. I have to open Nautilus as root to put files on it. How do I set it so that I as a user can add files/folders to the drive having them end up with the same owner/permissions I have as a user? It's to cumbersome having to sudo every move with regards to the USB drive.

---

### Post by nothingspecial on 2011-04-08
```
sudo chown -R $USER:$USER /path/to/external/drive
```

---

### Post by seawolf167 on 2011-04-08
> **nothingspecial said:**
> ```
sudo chown -R $USER:$USER /path/to/external/drive
```

+1, if you have a specific user in mind (and you have more than one user on your machine) you can replace the $USER variables with 'username:groupname'

Additionally, if you dislike having to mount it all the time, you can add an entry in /etc/fstab to have it automount on boot (we can help you with this if you want to add this entry)

---

### Post by tredegar on 2011-04-08
> sudo chown -R $USER:$USER /path/to/external/drive
That makes all the files on that drive belong to $USER, you may not want that on an ext4 partition, and it may upset other users.

Another approach is to change the *permissions* of the mounted drive
```
sudo chmod 777 /media/whatever
```
That means anybody can read and write it, but if they wish they can set their own permissions on their own data (so other people cannot read or delete their files, for example).

---

### Post by cdysthe on 2011-04-08
> **nothingspecial said:**
> ```
sudo chown -R $USER:$USER /path/to/external/drive
```

Thanks. So I have to do every time I plug it in? There's no way to have external drives mount accessible to users? This is a one user laptop. Would it maybe work to change the permissions for /media permanently or even to configure whatever automounts the drive to mount it accessible to users?

---

### Post by wolfen69 on 2011-04-08
> **cdysthe said:**
> Thanks. So I have to do every time I plug it in? 

No.

---

### Post by nothingspecial on 2011-04-08
It's permanent until you chown to some other user.

---

### Post by tredegar on 2011-04-08
Please try changing the *permissions* not the *owner*, as at post #4

---

### Post by nothingspecial on 2011-04-08
> **tredegar said:**
> Please try changing the *permissions* not the *owner*, as at post #4

If it is a single user laptop, changing the owner, rather than giving anybody  freedom, is more secure........

.....no?

---

### Post by tredegar on 2011-04-08
> If it is a single user laptop, changing the owner, rather than giving anybody freedom, is more secure........
You are making *_assumptions_* that it is a single user laptop.

Changing the ownership of all the files on the drive is not appropriate.

It might work in this instance, but it is not the "right way" of doing it.

The "right way" of doing it is to grant permissions to users to use the drive as they, and root, see fit.

The solution is at post #4.

May I sugest you try it: 
Create another user. 
Can they save files to the drive that you have recursively **chown**'d to $USER, and preserve their permissions (Eg "nobody else can delete or modify **newuser**'s files") ?

Unless $USER has set the permissions to default to 777, it will not work. This is correct behaviour for linux.

---

### Post by nothingspecial on 2011-04-09
> **tredegar said:**
> You are making *_assumptions_* that it is a single user laptop.



Am I?



> **cdysthe said:**
>  This is a one user laptop. 

---

### Post by cdysthe on 2011-04-09
> **tredegar said:**
> You are making *_assumptions_* that it is a single user laptop.

Changing the ownership of all the files on the drive is not appropriate.

It might work in this instance, but it is not the "right way" of doing it.

The "right way" of doing it is to grant permissions to users to use the drive as they, and root, see fit.

The solution is at post #4.

May I sugest you try it: 
Create another user. 
Can they save files to the drive that you have recursively **chown**'d to $USER, and preserve their permissions (Eg "nobody else can delete or modify **newuser**'s files") ?

Unless $USER has set the permissions to default to 777, it will not work. This is correct behaviour for linux.

I did say above that this is a single user latop. However, it's good to learn concerns in this regard for multi user systems also where different users plug in their USB drives. I've got a machine like that also on my network.

---

### Post by cdysthe on 2011-04-09
Hi,

Thanks all for your insights. I chose the user approach on the laptop. Easier for me to understand and work with than permissions which are confusing at times. I just needed my rsync backup done :)

---

