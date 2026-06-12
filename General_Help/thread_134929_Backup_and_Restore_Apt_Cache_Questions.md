---
title: "Backup and Restore Apt Cache Questions"
date: 2006-02-22
forum: General Help
---

### Post by ezsit on 2006-02-22
I have followed the instructions on the Ubuntu Guide to backup the contents of the apt cache (/var/cache/apt/archives) so I have all the updates and downloaded programs I have installed.  I see the instructions of the Ubuntu Guide give instructions how to restore the contents for the directory, but will this also reinstall the applications? My question is this -- If I reinstall Ubuntu 5.10 can I reinstall all the .deb files directly from by backup of the /var/cache/apt/archives directory? Is this a simple procedure?

---

### Post by ezsit on 2006-02-23
So, not one person knows the answer? Do I need to dpkg -i all the .debs in the /var/cache/apt/archives after restoring the contents of the folder? I assume so, but I would like some input. Thanks.

---

### Post by Sutekh on 2006-02-24
Ooh I was gonna answer this, but got side-tracked.

[QUOTE=ezsit]I have followed the instructions on the Ubuntu Guide to backup the contents of the apt cache (/var/cache/apt/archives) so I have all the updates and downloaded programs I have installed. I see the instructions of the Ubuntu Guide give instructions how to restore the contents for the directory, but will this also reinstall the applications?[/QUOTE]
Well as you've probably guessed, copying the contents of the cache back to /var/cache/apt/archives doesn't re-install them.

[QUOTE=ezsit]Do I need to dpkg -i all the .debs in the /var/cache/apt/archives after restoring the contents of the folder? I assume so, but I would like some input.[/QUOTE]
I think that this is so.  I was going to test whether or not using apt-get would work, but haven't had the chance, in any case I don't think that apt-get would look in the cache when trying to install a program.  

So its gonna be dpkg to re-install the .deb's unless someone else knows differently.

---

### Post by ezsit on 2006-02-24
Thanks for the response. I might get a chance to test this myself. I plan on installing Suse over the weekend. If I don't like Suse, I'll be going back to Ubuntu. I'll post back when I'm done with the results. Thanks.

---

### Post by LateNighter on 2006-02-24
They say that doing it this way SPEEDS up the process of ReInstall...

 Thats a Crock, I've tried it and it's a BIGGER Hassle then just reinstalling it from the Repositories to begin with...
 I've Never tried it with dpkg or in Ubuntu...

 But i use to run Linspire 5.0 and did this ONE TIME, It took me longer to do it this way then it did if I did a reinstall Straight from CNR.
 Which was agonizingly SLOW to say the Least.... Either Way U Did It....

 And I can tell you Downloading and Installing from Ubuntu's Repositories is A WHOLE LOT FASTER then Linspire's CNR ever thought about being....
 Among better Hardware Support, Both 32bit as well as 64bit....

 But thats another Story.  I don't want to Start a debate over OS's So I'll STOP there.  But thats just my Opinion...:twisted:

---

### Post by az on 2006-02-25
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

