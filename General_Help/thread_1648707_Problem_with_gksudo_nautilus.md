---
title: "Problem with gksudo nautilus"
date: 2010-12-19
forum: General Help
---

### Post by kanishkdudeja on 2010-12-19
Whenever i perform any file operations with gksudo nautilus..
for example i copy files from 1 place to another..the files get protected..and a cross appears on them and im not able to manipulate them using the normal file manager..how can i overcome this ?

---

### Post by cipherboy_loc on 2010-12-19
> **kanishkdudeja said:**
> Whenever i perform any file operations with gksudo nautilus..
for example i copy files from 1 place to another..the files get protected..and a cross appears on them and im not able to manipulate them using the normal file manager..how can i overcome this ?

Before I tell you how to fix it, we should understand what is going on. You are opening up nautilus with the gksudo command. The gksudo command is just a graphical sudo. Sudo is used to escalate your privileges from a basic user to root, for one command. Thus, if you run gksudo nautilus, you are modifying files as root, so root's permissions, "rub off" on them. Thus, when you go back to your regular file browser not being run as root, your browser sees that they have special permissions and ownership, and gives you those nice graphics. ;) 

To overcome this, open up a terminal (Applications -> Accessories -> Terminal) and, assuming all the files reside in your /home/username directory:

```

sudo chown [username] ~/* -R
sudo chmod 773 ~/* -R

```

Make sure you replace [username] with who you are. If you are not sure of who you are then run:
```
whoami
```


Note, if only YOU want noone else to be able to read your files, the second command should be:
```
sudo chmod 770 ~/* -R
```

Does anyone else have any suggestions for the chmod octal permission bits?

Cipherboy

---

### Post by kanishkdudeja on 2010-12-19
this thing i know.

But i want an alternative so that files dont get write protected when i manipulate them using gksudo nautilus..

mayb some command like gksudo nautilus or any extension of it ?

---

### Post by 3Miro on 2010-12-19
It sounds like you are using gksudo nautilus quite often, which is not intended. gksudo nautilus should be a very rare event for you. Can you please tell us exactly why do you need to use that so often, perhaps we can help you get things done the "normal" way.

Other than that, you can take a look at umask:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

However, I don't think there is a way to get Nautilus to not change ownership of files when they get copied. (you may be able to do that with a terminal command, but this is a security risk)

---

### Post by kanishkdudeja on 2010-12-19
im into webdevelopment. i use xampp. so i need to backup the htdocs folder located in /opt/lampp/. thats why.

---

### Post by 3Miro on 2010-12-19
> **kanishkdudeja said:**
> im into webdevelopment. i use xampp. so i need to backup the htdocs folder located in /opt/lampp/. thats why.

So why can't you just copy/paste that somewhere in your /home/username folder? Files in /opt are usually 644, meaning anyone can read them.

Another way to do this would be to just periodically tar everything in /opt/lampp and move the resulting file somewhere else. You can use all the chown and chmod in a script that you can call with a single command.

---

### Post by kanishkdudeja on 2010-12-19
when i copy the htdocs folder in /opt/lampp.. and go to some other location..

the option for paste is not highlighted..

n i cant tar htdocs folder..

it says permission denied

---

### Post by 3Miro on 2010-12-19
If paste is not available, that means that you don't have permission to write into the new folder. You should write things into /home/your_user_name/Make_some_backup_folder. Same place as Places -> Home.

Same goes for making a tar out of the folder. The destination for the tar file must be writable by whatever user is making the tar. You can also use sudo tar ..., in which case you can write almost anywhere and then you have to move only one file.

Try this, but change YOUR_USERNAME with your username on your computer. This should create a tar file in your home folder with the correct permissions.

```

tar -cjf /home/YOUR_USERNAME/lampp.tar.bz2 /opt/lampp 

```

---

### Post by kanishkdudeja on 2010-12-19
okay thanks mate..:)

---

### Post by 3Miro on 2010-12-19
> **kanishkdudeja said:**
> okay thanks mate..:)

If this solves your problem, please mark the thread as "solved". (otherwise, ask for more help)

---

### Post by gandaran on 2010-12-19
> **kanishkdudeja said:**
> Whenever i perform any file operations with gksudo nautilus..
for example i copy files from 1 place to another..the files get protected..and a cross appears on them and im not able to manipulate them using the normal file manager..how can i overcome this ?
this is a problem with ubuntu permissions since 9.10! gksu nautilus used to work nicely with files before!
use the terminal command line to copy (sudo cp) or move (sudo mv) files to root, you wont have this problem.

---

