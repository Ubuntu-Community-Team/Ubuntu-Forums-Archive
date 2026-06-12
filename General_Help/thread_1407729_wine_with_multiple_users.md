---
title: "wine with multiple users"
date: 2010-02-15
forum: General Help
---

### Post by tzg6sa on 2010-02-15
Hi All,

I have wine apps installed by user A. I wanted that user B will be able to run these apps. So I did what is posted here:
[http://ubuntuforums.org/showpost.php?p=3205534&postcount=14](http://ubuntuforums.org/showpost.php?p=3205534&postcount=14)

After that a made a symlink for user B:
```
B@B.PC:~$ ln -s /home/wine ~/.wine
```

I hoped B can run now the apps. But
```
wine: /home/B/.wine is not owned by you
```

The owner of /home/wine is user A, but B is part of the group with rwx rights.

How can I make the wine apps run from user account B?

Thanks.

---

### Post by gsmanners on 2010-02-15
That particular method is still problematic for some applications. I would suggest using this one:

[http://ubuntuforums.org/showthread.php?t=917422](http://ubuntuforums.org/showthread.php?t=917422)

---

