---
title: "deb-src: command not found"
date: 2009-08-16
forum: General Help
---

### Post by Tarkers on 2009-08-16
Hey guys, I'm just following a HOWTO on ntfs-3g
[http://ubuntuforums.org/showthread.php?p=1545618#post1545618](http://ubuntuforums.org/showthread.php?p=1545618#post1545618)

very first step is
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all
When i try this in terminal I'm getting a deb-src: command not found

Am I missing a necessary repository?

I'm not really sure what to do, I've tried a couple searches with no luck.

I'm still a total Ubuntu noob so any help would be great, thanks.

---

### Post by oldos2er on 2009-08-16
The instructions you're following are three years old. Try this instead:
```
sudo apt-get update && sudo apt-get install ntfs-3g
```

---

### Post by michy99 on 2009-08-16
I think ntfs-3g is installed in Jaunty by default. Of course, I could be wrong.

---

### Post by Tarkers on 2009-08-16
Oh, so it is, awesome thanks

---

