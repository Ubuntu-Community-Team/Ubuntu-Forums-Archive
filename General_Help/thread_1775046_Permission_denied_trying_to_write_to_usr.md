---
title: "Permission denied trying to write to /usr"
date: 2011-06-04
forum: General Help
---

### Post by griffsterb on 2011-06-04
Hello all, I am getting started with Python, and I am very inexperienced with Linux. I have used the terminal to create a file: /usr/**mystuff**. Next I open gedit and attempt to save a test.txt file into **mystuff**, but I receive the error message:

*You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.*

I have done some research, but most of what I found involves attempts to alter files in other locations or with other versions of Ubuntu. I am running 11.04 and I want to make sure I don't mess anything up. 

Can someone provide some assistance? I would greatly appreciate it.

---

### Post by griffsterb on 2011-06-04
Can't save text files into my home directory either

---

### Post by Baumbart on 2011-06-04
That you can't write to /home/yourname is strange. I don't know why.
Did you try to write to *your* home folder or just to *the* home folder

For writing to /usr/mystuff open your editor as root, for example 'gksudo gedit'.

_But whatever you do as root you should be sure you don't mess up something._

---

### Post by griffsterb on 2011-06-04
K I figured out that I can type

gksudo gedit 

and then I have admin privileges. But this bothers me because I am on the admin on my computer. I want to have admin privileges any time I open gedit, whether it's through the gui or through the terminal. Is there a way I can do this?

---

### Post by griffsterb on 2011-06-04
I believe it is my home folder. If I right click>properties>permissions it says "You are not the owner, so you cannot change these permissions."

Really weird.

---

### Post by Baumbart on 2011-06-04
> **griffsterb said:**
>  But this bothers me because I am on the admin on my computer. I want to have admin privileges any time I open gedit, whether it's through the gui or through the terminal. Is there a way I can do this?

No, you don't want that, atleast not without having to type your password in.
Contrary to windows ,root in Linux really can do everything, so its highly insecure to just open it to everyone and everything which happens to be in your session.

Who is owner of your home folder, root?
is that folder /home or /home/yourname?

---

### Post by griffsterb on 2011-06-04
> **Baumbart said:**
> No, you don't want that, atleast not without having to type your password in.
Contrary to windows ,root in Linux really can do everything, so its highly insecure to just open it to everyone and everything which happens to be in your session.

Who is owner of your home folder, root?
is that folder /home or /home/yourname?

i stopped messing around in /usr and changed my cd to /home/spacelord

spacelord is my name on the pc. i then use

sudo mkdir pythonfiles

then /home/spacelord/pythonfiles has a lock symbol in the gui, lists the owner as 'root' and says 'you are not the owner, so you cannot change these permissions.'

---

### Post by Baumbart on 2011-06-04
> **griffsterb said:**
> i stopped messing around in /usr and changed my cd to /home/spacelord

spacelord is my name on the pc. i then use

sudo mkdir pythonfiles

then /home/spacelord/pythonfiles has a lock symbol in the gui, lists the owner as 'root' and says 'you are not the owner, so you cannot change these permissions.'

That's because root created that folder (through sudo)

These two sites may interest you.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by griffsterb on 2011-06-04
> **Baumbart said:**
> That's because root created that folder (through sudo)

These two sites my interest you.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

thanks for the help. this now begs the question, where is a suitable place to store my files for easy use? somewhere that i don't have to go through all these permissions to save text files and such?

---

### Post by Topsiho on 2011-06-04
Hello,

The directory /usr is NOT for saving your personal stuff, you should use your personal home directory for this, in the /home/<yourname)  directory.

In your /home/<yourname> you may create a directory for your python stuff, (great that you are learning this programming language!) such as /home/<yourname>/python/mystuff and work in that directory. You OWN that, and it's contents, and can edit the privileges there the way you want, without administrator (root) rights.

As for your idea that you always want to be the administrator, this is a very bad idea. You ONLY should be the administrator when you NEED to. So that you should have to use sudo or gksudo and TEMPORARILY have administrator rights. That way eventual hackers into your system have no more rights than an ordinary user, and can not wreck your system.

I think you have to read a lot of how Linux, and Ubuntu, are organized :), to avoid catastrophes such as using Windows. And putting files where they are not supposed to be.

Topsiho

---

### Post by Baumbart on 2011-06-04
In your home folder /home/spacelord but without sudo. 

I too am a new convert from windows, so I know all this is a pain in the ... at the beginning. But you get used to it within a week.

Note that I left windows because of a backdoor worm which messed up everything. I#m talking about webhoster contacting me because s.o. loaded malmare on their server through my access.
Including a bunch of my customers I had to call to change their ftp passwords.
I know how sony feels.

This sudo stuff is exactly what will save your day when someone tries to corrupt your system.
I highly recommend not to let your best defense down.

---

### Post by griffsterb on 2011-06-04
Awesome! Thanks for the help baumbart and Topsiho. I've learned a lot just from this thread. Gonna mark this as solved. Thanks again guys.

---

### Post by jespdj on 2011-06-04
If you want to change the owner of a file or directory, you can use the **chown** command. For example, suppose that you created a directory in your own home directory as root, but now you want to be the owner yourself:
```

# Make a directory as root; root will be the owner
sudo mkdir newdir

# Make yourself the owner of the directory
sudo chown spacelord:spacelord newdir

```
As already said, don't mess with files and directories outside of your home folder (don't make yourself the owner of directories outside your home folder - that might mess up the system in such a way that it will not work anymore).

---

### Post by Topsiho on 2011-06-04
Thanks for reacting like this to my remarks.

To help you further, you might have a look here:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

and download the Ubuntu manual. It is perfect for starters,

Topsiho

---

