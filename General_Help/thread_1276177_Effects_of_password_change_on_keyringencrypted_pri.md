---
title: "Effects of password change on keyring/encrypted private directory"
date: 2009-09-26
forum: General Help
---

### Post by J V on 2009-09-26
Just what are they?

My private directory I just found out, is still using my old password... How do I change it to my new one?

Also, The same appears for my keyring, and I (Ooh, how embarissing) don't know where the settings for the keyrings are xD

This appears also to be using my old password (when I tried to log in to an ftp server through nautilus)

Know where I can change these?

---

### Post by J V on 2009-09-27
My private folder won't unlock on login because the password is different (Now I have to unlock it before I can use my keyrings or firefox cause they are linked there)

---

### Post by wojox on 2009-09-27
This is a site from one of the mods here that should help: [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by J V on 2009-09-27
Thanks, know how to get the nautilus keyring password working again?

Edit: Found it, thanks

---

### Post by J V on 2009-09-27
Unsolving this, I just realised that seahorse does not save its data in .gnupg...

I need to know where it saves its data so I can stick it into my encrypted private directory...

Also, do I need to escape passphrases for the epd? I just spent an hour fighting with (I gave up) the non-intelligable system that apparently tells you exactly the wrong things (its a 6 character password ive been using for years, how the hell could it be wrong all of a sudden?)

---

### Post by Shujah on 2009-09-27
The first password you select at the time of installation is automatically made the default password, so once the login password is changed this problem arises. I had this problem with evolution might be the same case here.

you can change the password via Menu > Accessories > Passwords & Encryption keys > Passwords (Password Default)

---

### Post by J V on 2009-09-27
Yes I realise that, my next problem is, where is that?

I just found out that everything other than the password (All the passwords it stores) are stored unencrypted, in the ~/.gnome2/keyrings folder... This can't be secure...

Ahh yes, I disabled the password because I thought they were saved in .gnupg...

Right so create a shortcut in the ~/.gnome2 leading to the epd and it should be secure... lets hope...

By the way, if I create a new user, will they be using the same default keyring, or will they have a different one? (I presume a different one)

---

