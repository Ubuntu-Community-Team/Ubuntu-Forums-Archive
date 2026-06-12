---
title: "Deleting FIle's As Root?"
date: 2012-07-24
forum: General Help
---

### Post by Yayoushiko on 2012-07-24
Ok so i am trying to install Metasploit and i had to install it with Root.And i messed up and i am trying to delete the file's.But it is not letting me delete them since it was done with root.So how do i remove them?

---

### Post by QIII on 2012-07-24
What do you mean when you say you did this with root?

---

### Post by Yayoushiko on 2012-07-24
> **QIII said:**
> What do you mean when you say you did this with root?

I had to Install the Program as Root.Sudo Bash
And now i wan't to know how to delete it has Root user

---

### Post by QIII on 2012-07-24
How did you accomplish this?

What commands did you use?

---

### Post by HiImTye on 2012-07-24
you could have 'installed' it by a number of ways, first, what program were you installing and what instructions were you using?

---

### Post by Yayoushiko on 2012-07-24
> **QIII said:**
> How did you accomplish this?

What commands did you use?

Hum well i went into the Terminal and typed Sudo Bash to set my user as root/superuser,Then i went to cd /home/dillon/Downloads then i typed ./metasploit-latest-linux-x64-installer.run 
And then i installed it.Now i don't know how to delete the folder since it was created with root.

---

### Post by QIII on 2012-07-24
Did the instructions say to use sudo bash, or would sudo have worked on the .run?

---

### Post by UltimateCat on 2012-07-24
> **Yayoushiko said:**
> Ok so i am trying to install Metasploit and i had to install it with Root.And i messed up and i am trying to delete the file's.But it is not letting me delete them since it was done with root.So how do i remove them?

There are very powerful commands and should be used very carefully.
If you don't know what your doing you could compromise your operating system and at worse make it inoperatable-

Are your getting the message:
" You are not the Owner so you can not change these permission " ?

If so you have a few options but I strongly advise you to read this documentation first and discuss it with other members before doing anything.
[http://help.ubuntucom/community/ROOTSUDO](http://help.ubuntucom/community/ROOTSUDO)

You can change permissions by using:
 sudo chown
but you must know exactly the path to that file/folder
yourusername:Yourusername filename.xyz
Another way is to use nautilus but this is the command that you should use carefully and again; if you don't know what you are doing you could cause havoc to your system.  Please read the documentaton.
And; you could remove the file but I will caution you as I recently removed a file myself and am terrible sorry that I did because I'm having hardware issues.

---

### Post by QIII on 2012-07-24
Without researching exactly what that .run file does or where it puts things (I hope the installation gave you the chance to decide where to install it, therwise you will have to figure out where it went), you might be able to navigate to the directory where it is installed and run something like 

```
sudo ./uninstall
```

Even that may take a chmod to make the file executable.

I did read the installation instructions, and they call for sudo rather than sudo bash.

---

### Post by Yayoushiko on 2012-07-24
> **UltimateCat said:**
> There are very powerful commands and should be used very carefully.
If you don't know what your doing you could compromise your operating system and at worse make it inoperatable-

Are your getting the message:
" You are not the Owner so you can not change these permission " ?

If so you have a few options but I strongly advise you to read this documentation first and discuss it with other members before doing anything.
[http://help.ubuntucom/community/ROOTSUDO](http://help.ubuntucom/community/ROOTSUDO)

You can change permissions by using:
 sudo chown
but you must know exactly the path to that file/folder
yourusername:Yourusername filename.xyz
Another way is to use nautilus but this is the command that you should use carefully and again; if you don't know what you are doing you could cause havoc to your system.  Please read the documentaton.
And; you could remove the file but I will caution you as I recently removed a file myself and am terrible sorry that I did because I'm having hardware issues.

[@]("http://ubuntuforums.org/member.php?u=628170")[QIII No it said i must be root to install the program that's why i installed it as root.]("http://ubuntuforums.org/member.php?u=628170")

And thank you Cat i will try this :)

---

### Post by QIII on 2012-07-24
I am looking at the instructions right now.

```
chmod +x desktop/metasploit-latest-linux-x64-installer.run

``````
sudo desktop/metasploit-latest-linux-x64-installer.run

```"Note: If you do not have root privileges, you need to use sudo. For example, sudo
./metasploit-latest-linux-x64-installer.run."

In other words, sudo was all that was needed.

In any case, navigating to the directory where it was installed and running

```
sudo ./uninstall
```may work depending on permissions/executability -- in which case you may need to chmod or change ownership.

Just deleting the file, according to the documentation, will not delete any of the data that may have been gathered.  Uninstalling should give you the option to remove data as well.

---

### Post by Yayoushiko on 2012-07-25
Thank you everyone.I will let you know if the thing's you posted do not work :).

---

