---
title: "Error message after Sign in"
date: 2006-03-19
forum: General Help
---

### Post by chowyunpat on 2006-03-19
I have been using Breezy Badger 5.10 for about 2 weeks now and in the past week when I have logged in I get this error message:


*Your $Home ./drmc file has incorrect permissions and is being ignored.  This prevents the default session from being saved.  File should be owned by user and have 644 permissions.*


I click on the window and then the desktop starts up like normal.  What does this error mean and how do I fix it?

---

### Post by taurus on 2006-03-19
The file is .dmrc, not ./dmrc and the owner has read and write permission.  So, make sure you are the owner of that and it has the right permission...
```

sudo chown userid .dmrc
chmod 600 .dmrc

```

---

### Post by psychicdragon on 2006-03-19
I've never seen this error before. You could try running these two commands, it might work:

(You need to be in your home dir)
```
sudo chown **username** .dmrc
chmod 644 .dmrc
```

EDIT: Too slow T_T

---

### Post by chowyunpat on 2006-03-19
This has to be the 2 quickest responses I have ever seen on a message board, I had 2 answers in less that 5 minutes, and I appreciate the lighting fast responses, however I tried entering the data i, you guys gave me in your posts, but neither one worked..  I still get the message after I sign in.

---

### Post by psychicdragon on 2006-03-19
Did you chmod the file to 600 or 644? I told you 644 because that's what you mentioned in your original post, but my .dmrc file is chmod 600. I think tauros was right in telling you to chmod 600.

If that doesn't work, could you post the output of both:
```
cat .dmrc
stat .dmrc
```

---

### Post by tuxcantfly on 2006-03-19
sudo rm .drmc

will get rid of it, and it will recreate itself on the next login

---

