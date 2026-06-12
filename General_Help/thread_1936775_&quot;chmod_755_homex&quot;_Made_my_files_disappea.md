---
title: "&quot;chmod 755 /home/x&quot; Made my files disappear"
date: 2012-03-06
forum: General Help
---

### Post by toseethefruit on 2012-03-06
Hello Everyone,

I have a question for which I've not been able to find an answer after several hours of searching. Last night, I did a fresh install of Ubuntu 10.04 LTS on my Dell Studio 15 laptop. I created a new user with an encrypted home folder (to do this, I simply checked "Encrypt Home Folder" in the Users and Groups GUI). This morning, I turned the computer on and was greeted with a message that read "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)". If I clicked "OK," I was given another message about how Nautilus could not create my Home directory and several other directories.

Using another computer, I found several websites that talked about the first message ("There is a problem with the configuration server..."). Following their instructions, I went into TTY1, logged in, and did

```
chmod 755 /home/x
```

(where "x" is my username).

I then logged in using the regular X server. When I did, however, all of the desktop configurations I had made to my computer (e.g., Compiz and Theme settings) were replaced with the defaults. In addition, none of my files showed up in Nautilus.

Can any of you tell me 1) Whether I should have done something differently, and 2) How I can restore my settings and access to my files?

Thank you very much!

My best,
J.L.

---

### Post by cryptotheslow on 2012-03-06
Hi,

It sounds like for whatever reason your encrypted home directory failed to mount.

Use Nautilus (default file explorer in Ubuntu) - and look in your home directory for a .Private directory - note the dot at the start. It will be hidden from view in Nautilus by default, so look in the menus for the option to show hidden files or simply press Ctrl H.

If the .Private directory is there see section 5 here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

or there is a good guide to recovering the contents using a LiveCD (or USB) if you have one to hand here:
[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

Oh - and chmoding everything to 755 in your home directory probably won't break anything but there are certain folders in there that are deliberately set to 700 e.g. the .gvfs  .ecryptfs directories to prevent other users of the PC reading them.

Good Luck :D

---

### Post by toseethefruit on 2012-03-06
Hi cryptotheslow,

Thanks so much! This is actually the second time that this has happened to me with Ubuntu 10.04 (which I'm required to use). Do you (or anyone else) have any recommendations for avoiding this problem in the future?

Again, thank you!

---

### Post by cryptotheslow on 2012-03-06
Hi,

I can't really suggest how to avoid it as the only time I have done manual recoveries was for testing purposes to make sure I know how to do it should some disaster occur - I've never had a genuine problem with ecryptfs on a live system - but I still keep those two pages bookmarked and noted down in my big black book of useful things *TM :D

The main thing to bear in mind when using encryption is to ensure you carry out regular backups of your files (also encrypted or otherwise). Even small corruptions in an encrypted container can render them completely inaccessible and alternative file recovery strategies such as Photorec simply cannot work due to the encryption.

That would be my only offered snippet of wisdom really :)

Let us know how you get on :)

---

