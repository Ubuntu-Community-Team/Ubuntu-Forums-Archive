---
title: "Really good question about the /home/user folder..."
date: 2010-06-27
forum: General Help
---

### Post by pepsifx357 on 2010-06-27
Inside the /home/user folder there are hidden folders with . suffixes, like /home/user/.firefox and so on.  However, when you do an ls inside the /user folder or look at it with nautilus, you can't see them.  What are these folders, what are they called, what do they do, and is there a way to view them all in a list in the terminal or in a file manager like nautilus?

---

### Post by Zimmer on 2010-06-27
In Nautilus, press ctrl +h
in terminal ls -a
They are user application data and settings...

---

### Post by pepsifx357 on 2010-06-27
Thank you!

---

### Post by Irony on 2010-06-27
Or hit the View in the Nautilus menu bar and click view hidden folders.

Note if you rename your .mozilla folder to say .mozilla1 and fire up firefox you will see that it is returned to its default state. To restore close firefox delete .mozilla and rename .mozilla1 back to .mozilla and on starting firefox your settings are back as they were.

---

### Post by pepsifx357 on 2010-06-27
Interesting...Can this method of hiding folder/files work outside of the /home/user folder?  such as /var/hidden/.hidden_folder  ?

Also, is there anyone working on a easy way to encrypt and password files and folders.  I've seen a lot of tutorials and it just seems to much trouble.

---

### Post by bobcollard on 2010-06-27
> **pepsifx357 said:**
> Interesting...Can this method of hiding folder/files work outside of the /home/user folder?  such as /var/hidden/.hidden_folder  ?

Also, is there anyone working on a easy way to encrypt and password files and folders.  I've seen a lot of tutorials and it just seems to much trouble.
I use Truecrypt, you can find it here:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
Don't encrypt a hidden folder.

---

### Post by pepsifx357 on 2010-06-28
> **bobcollard said:**
> I use Truecrypt, you can find it here:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
Don't encrypt a hidden folder.

Since my last post, I've been using gpg with hidden folders.  Would this be a bad idea too?

---

### Post by gadolinio on 2010-06-28
> **pepsifx357 said:**
> Interesting...Can this method of hiding folder/files work outside of the /home/user folder?  such as /var/hidden/.hidden_folder  ?


Yes.
A folder such as---------> /var/hidden/.hidden_folder
would behave like------> /home/user/.mozilla
regarding this hidden issue.

---

