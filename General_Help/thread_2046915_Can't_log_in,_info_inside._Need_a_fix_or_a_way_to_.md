---
title: "Can't log in, info inside. Need a fix or a way to decrypt my home folder."
date: 2012-08-23
forum: General Help
---

### Post by Anonymau5 on 2012-08-23
Yesterday, my Xubuntu account was working as usual. As far as I know I didn't do anything that could change something.

However, when I tried to log in today, the screen would turn black, display a few things, then say "Plymouth disconnected from server." or some such. Logging in from other accounts is working.

I decrypted my home folder with the option provided in the service.

So I need either a fix for this or a way to retrieve my files from the home folder.

Thank you in advance.

---

### Post by Toz on 2012-08-23
Hello and welcome to the forums Anonymau5.

Have a look at the ownership of the .Xauthority and .ICEauthority files in your home directory (you can try logging in from the console via Ctrl+Alt+F1). If they are not owned by you, you can change the ownership:
```
sudo chown <usernname> .Xauthority .ICEauthority
```
...where <username> is your username.

Incorrect ownership of those files can prevent you from completing a successful login. This seems to be a common issue.

---

### Post by cryptotheslow on 2012-08-24
If you can't fix it using Toz's suggestion (or any other way), there are instructions here on how to recover the contents of your encrypted home using a LiveCD to boot from:

[http://bodhizazen.net/Tutorials/Ecryptfs/#Live](http://bodhizazen.net/Tutorials/Ecryptfs/#Live)

---

