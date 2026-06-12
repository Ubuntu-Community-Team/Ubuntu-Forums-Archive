---
title: "Crash between 10.04 to 11.04 upgrade. Need access to files from LiveCD"
date: 2011-08-17
forum: General Help
---

### Post by Pedro Abrantes on 2011-08-17
Hi!

Yesterday, while upgrading from Ubuntu 10.04 to 11.04, the computer crashed. For this reason, when I reboot, Ubuntu doesn't recognize any longer the root folder and so on... and halts execution in a blank screen (well before the login screen).
I'm currently running LiveCD and I can see the Filesystem with the root folder, the bin folder, home folder and so on....
My question is How can I access the files I had in my desktop from LiveCD? I know the user and password so how can I access it? Please tell me there is a way!!! I'm so desperate! 

Thank you for your time!
P.S. I'm a newbie...

---

### Post by hansdown on 2011-08-17
Welcome to the forum, Pedro Abrantes.

Open a terminal, and enter this....

gksudo nautilus

You should be able to save your files to a thumb drive, etc.

I'm having trouble getting the quote tags to work.

---

### Post by Pedro Abrantes on 2011-08-17
> **hansdown said:**
> Welcome to the forum, Pedro Abrantes.

Open a terminal, and enter this....

gksudo nautilus

You should be able to save your files to a thumb drive, etc.

I'm having trouble getting the quote tags to work.


Thanks for the quick reply Hansdown,

  Unfortunately when I run in the terminal gksudo nautilus the desktop folder opens with nothing in it an in the terminal the following message appears

ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Moreover, shouldn't it ask me at least my password? Is it that simple? Just run that command and have access to my files?

Thank you for your time!!

---

### Post by JC Cheloven on 2011-08-17
Hi Pedro, 

-> Yes it is that simple! No password required unless you encrypted your partition or something similar.

You only have to know in which partition your ubuntu is. Sould be one of the few listed in nautulus in the left column. Go to that (click it in nautilus) and navigate INSIDE IT to home/pedro (replace "pedro" with whatever your username is). 

You should see all your folders and files, an be abke to copy to an external media.

---

### Post by westie457 on 2011-08-17
> Unffortunatly When I run in the terminal gksudo nautilus the desktop folder opens with nothing in it an in the terminal the following message appears



That is what normally happens.

> ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


These errors messages in the terminal usually can be ignored.


> Moreover, shouldn't it ask me at least my password? Is it that simple? Just run that command and have access to my files?

When using a LiveCD a password is not normally required. It is that simple. All your files are located in File System/home/<your name here>.

Be very careful what you do while running Nautilus as /root. It is very easy to accidentally destroy your system especially if you start to delete things. Usually there is no way to get them back.

---

