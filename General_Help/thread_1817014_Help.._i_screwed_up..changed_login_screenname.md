---
title: "Help.. i screwed up..changed login screenname"
date: 2011-08-02
forum: General Help
---

### Post by macminiuser on 2011-08-02
I recently used ubuntu tweak and changed the login screen name to something different.Now I cannot login, I mean it logs me in ,but loops back out to the login.
Help????? please?

---

### Post by macminiuser on 2011-08-02
I am writing this from a different computer, and I am using ubuntu 10.10

---

### Post by macminiuser on 2011-08-02
Ok What I did was change my hostname under ubuntu tweak

---

### Post by Brushstroke on 2011-08-02
Hmm. Have you enabled the root account so you can login as root? If you have, login as root and edit these two files: 
```
/etc/hosts
```and...
```
/etc/hostname
```You should see your hostname in those two files. Change it in both files so it matches Ubuntu Tweak's changes if it doesn't match already.

If you can't login to root, insert your Live CD for Ubuntu and mount the hard drive from the Live CD, and try to edit these two files from the hard drive.

---

### Post by macminiuser on 2011-08-02
> **Brushstroke said:**
> Hmm. Have you enabled the root account so you can login as root? If you have, login as root and edit these two files: 
```
/etc/hosts
```and...
```
/etc/hostname
```You should see your hostname in those two files. Change it in both files so it matches Ubuntu Tweak's changes if it doesn't match already.

If you can't login to root, insert your Live CD for Ubuntu and mount the hard drive from the Live CD, and try to edit these two files from the hard drive.

Thank you very much.
That did the trick

---

