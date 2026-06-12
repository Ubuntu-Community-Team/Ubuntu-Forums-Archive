---
title: "Can't Download Software"
date: 2010-06-10
forum: General Help
---

### Post by gooeysan on 2010-06-10
Recently I was trying to download some software from Ubuntu Software Center. I found the app I needed, pressed install, entered my password and then i got an error window with this written in it:
'The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.'
The problem is that I don't remember what I downloaded or when I did it.

P.S. Sorry for bad english-I'm from Lithuania

---

### Post by amite on 2010-06-10
first run $sudo apt-get autoclean
then try to install ur software.

---

### Post by Woody1987 on 2010-06-10
Also try

```
sudo apt-get -f install
```

---

### Post by gooeysan on 2010-06-10
@Woody1987 I did try that and the output was:
'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.'
@amite it's the same

---

### Post by Woody1987 on 2010-06-10
> **gooeysan said:**
> @Woody1987 I did try that and the output was:
'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.'
@amite it's the same

Yea, just run what it tells you.

---

### Post by gooeysan on 2010-06-10
That one was a bit obvious but i'm kind of sleepy  cuz' it's midnight so yeah... Thanks

---

