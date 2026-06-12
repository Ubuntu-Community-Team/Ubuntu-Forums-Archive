---
title: "How do I delete Locked Files?"
date: 2010-11-10
forum: General Help
---

### Post by SINNISTER on 2010-11-10
Hey all

I have a few files on my desktop that have a lock on the top right corner of the Icon like this....
[IMG]http://img507.imageshack.us/img507/6091/screenshotwh.jpg[/IMG]

How do i delete it? it tells me that i do not have sufficient permission to delete this file....

thanks for your help :)

---

### Post by 3Miro on 2010-11-10
1. If you don't have sufficient permissions to delete a file, then you should really consider if you want to delete it. If you don't have permission, this means that it is a system file and it may mess your system.

2. How did such file get on your Desktop in the first place. Something here is going very wrong.

3. You can open terminal (Apps -> Access -> Terminal) and run:
```
 gksudo nautilus 
```
This will open file manager with superuser privileges, which means that you can do anything INCLUDING COMPLETELY DESTROY YOUR SYSTEM. Be very very very careful about what you are doing.

4. You should carefully consider 1 and especially 2 before you go to 3. Post more information here so that we can help you.

---

### Post by Taak on 2010-11-10
If you are **SURE** that they are not important files, you have to remove them as root user (admin).
 
Star opening a terminal. Then type:
 
sudo rm /your/files/path/file_name.ext 
 
It could ask for you root password. Just type it and press enter.
 
sudo means "exec the next command as root"
rm is "remove". Be careful because no one will never ask you a confirm before deleting a file.

---

### Post by Amente on 2010-11-10
If what Taak said doesn't help the first you have to change the (attributes) permissions of the files by writing on the terminal

```

sudo chmod +rw  /the file paths
#You may also need to change the owner ship,since you want to delete the files you can fill in all the possible owner ship attributes by typing
sudo chown 777 /the file path

# Now you can delete them using your file manager or from the terminal



```

---

### Post by SINNISTER on 2010-11-11
I my mistake unziped Joomla onto my desktop and for some reason it just locked its self there but i already have a copy of Joomla in another dir.

So i have no clue why it will want to lock its self but the files are useless and Ima delete them...

---

### Post by SINNISTER on 2010-11-11
> **3Miro said:**
> 1. If you don't have sufficient permissions to delete a file, then you should really consider if you want to delete it. If you don't have permission, this means that it is a system file and it may mess your system.

2. How did such file get on your Desktop in the first place. Something here is going very wrong.

3. You can open terminal (Apps -> Access -> Terminal) and run:
```
 gksudo nautilus 
```
This will open file manager with superuser privileges, which means that you can do anything INCLUDING COMPLETELY DESTROY YOUR SYSTEM. Be very very very careful about what you are doing.

4. You should carefully consider 1 and especially 2 before you go to 3. Post more information here so that we can help you.

Awesome this worked :) thanks alot guys

---

### Post by 3Miro on 2010-11-11
If all that you did was unzip a file, then those would have probably been "read-only" files. You can delete read only files without sudo or gksudo, you an open the regular file manager (Places -> Home or Desktop) and then right-click on files -> properties -> permissions and change the access for the owner to "Read Write". The gksudo and sudo are the nuclear options, those will delete everything.

Glad you resolved this issue. If you don't have any more questions, you can mark the thread as "Solved"

---

### Post by SINNISTER on 2010-11-11
Hey yeah its resolved, how so mark the thread as "Solved"?

thanks

---

