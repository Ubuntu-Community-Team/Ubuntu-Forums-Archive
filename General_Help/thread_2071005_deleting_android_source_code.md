---
title: "deleting android source code"
date: 2012-10-14
forum: General Help
---

### Post by unibroker on 2012-10-14
I am using Ubuntu 12.04 on a 6 year old computer.  Yesterday I tried to download the above source code.  While the download was proceeding I read that I wouldn't be able to compile this on my 32 bit machine.  At the very least I would like to delete all files downloaded yesterday. Can I delete by download date?  Can I delete by a range?

Thanks in advance.

---

### Post by Cheesemill on 2012-10-14
How did you download the source code?

What commands/application did you use?

---

### Post by unibroker on 2012-10-14
> **Cheesemill said:**
> How did you download the source code?

What commands/application did you use?

I downloaded the Android SDK and then
```
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
chmod a+x ~/bin/repo


cd ~/android/system/
repo init -u git://github.com/CyanogenMod/android.git -b gingerbread
repo sync -j4
```

---

### Post by Cheesemill on 2012-10-14
Deleting the ~/bin/repo and ~/android/system directories will get rid of everything.

---

### Post by unibroker on 2012-10-14
> **Cheesemill said:**
> Deleting the ~/bin/repo and ~/android/system directories will get rid of everything.
Thanks for your help.  I just want to delete everything associated with android, upgrade my system and start over.

---

