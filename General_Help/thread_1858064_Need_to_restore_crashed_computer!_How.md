---
title: "Need to restore crashed computer! How?"
date: 2011-10-11
forum: General Help
---

### Post by Jelster64 on 2011-10-11
First, I' m sorry for possible bad English. I'm Dutch and my English can be really bad.

I installed Ubuntu (32-bit at a 64-bit computer -_-) 11.04 and used it for a while. There was something wrong with the partitionating I guess, but I was still able to use it. No prob. Then I became bored of the usual interface. So I installed the packages kubuntu-desktop and xubuntu-desktop to give it more looks. It worked fine, although it loaded xubuntu and xubuntu' s login screen, but everything still worked so I just used it. Worked fine.

Then it became bad. I tried to install GNOME 3, because I've heard lots of good things about it, so I went to this page ([http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html)) and started to install it. So I did this:

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

But at some point of the last step, I quit the installation. That was a bad idea, because the next time I started my computer, it crashed. So I went to install the 64-bit version of ubuntu. I "upgraded Ubuntu 11.04 to Ubuntu 11.04" and after it was installed, I restarted my computer. It crashed anyway. The command line restore version of linux (built-in) also crashed! Well this is what I want right now:

-I want to recover /home/jelle (jelle is my username).

Nothing more! I don't need to restore the applications, just that personal folder! I tried to do that by "trying Ubuntu" and navigating to my folder, but it's locked. I'm unauthorized. What should I do to fix it? How can I restore those files? BTW when I login, it fails to load xubuntu since that package was installed. Just saying.

Can anyone help? Please?

---

### Post by Jelster64 on 2011-10-12
BUMP

Please? Anyone?

---

### Post by cryptotheslow on 2011-10-12
Wow, that sounds like you have ended up with a very messy install!

So - boot up with the LiveCD / USB and take the "Try Ubuntu" option again. From a Terminal enter:

```
gksu nautilus
```

This will open the usual file explorer but running with root permissions.....  so be careful what you do with it! Hopefully that should do away with the padlock symbol and allow you to copy your files off.

Do you have an external drive or something to copy them off too?

---

### Post by TeoBigusGeekus on 2011-10-12
Boot from the live cd, choose "Try ubuntu" and once you're on a working desktop, open a terminal and give
```
gksu nautilus
```
to open nautilus with root priviledges. Try then to backup your home folder.

EDIT: Too late...

---

### Post by Jelster64 on 2011-10-13
Thanks for replying! I have another problem right now, and I have screenshots with it.

OK, I opened up terminal and used your command, which worked fine. Then I went to my real file system.
[IMG]http://www.afbeeldingenuploaden.nl/uploads/1886921.png[/IMG]

Then I found my home folder, and my user folder (which wasn't locked).:D
[IMG]http://www.afbeeldingenuploaden.nl/uploads/3152442.png[/IMG]

But the folder wasn't filled with files like I remembered it. In fact, there where only 2 files in there:
[IMG]http://www.afbeeldingenuploaden.nl/uploads/3738843.png[/IMG]

So there was a readme file in there, and I opened it. It said I had to use some command, so  I did that. But it gave an error. It was like this:
[IMG]http://www.afbeeldingenuploaden.nl/uploads/4449064.png[/IMG]

Do you guys know what I should do with it?

---

### Post by cryptotheslow on 2011-10-13
Ahhh....  your home partition is encrypted. It is possible to get it mounted from the LiveCD so you can access the files, but it involves chroot-ing into the previous install.

Have a read of the steps here (the "Access your encrypted data from a live CD" section):
[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)


Just look out for the last step where is states "You can not access the decrypted data, on the live CD, with nautilus as root:" - that should actually read "You can _***now***_ access the decrypted data, on the live CD, with nautilus as root:"  :D

---

### Post by Jelster64 on 2011-10-13
As before, this solution gives another problem.

I've did everything that guide said, and there was indeed a folder called mnt which was reachable by gksu nautilus. But all of the files had weird names. Check out this screenshot:
[IMG]http://www.afbeeldingenuploaden.nl/uploads/017934Screenshot.png[/IMG]

What should I do about it?

BTW Thanks a whole lot for the fast support:D

EDIT: I just found out that all of the files where just the same as the usual user folder, but they have different names. Did I do something wrong?

---

