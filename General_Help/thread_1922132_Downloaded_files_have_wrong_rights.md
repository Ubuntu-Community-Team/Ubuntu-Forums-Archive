---
title: "Downloaded files have wrong rights"
date: 2012-02-08
forum: General Help
---

### Post by Exterminator13 on 2012-02-08
Hi, everybody!

I'm using firefox. When I download any file, its rights are
```

-rw------- 1 oleg oleg 452456448 2012-02-07 23:58 video.avi

```And I cann't open it remotely. So, I should change its permissions to:
```

-rw-r--r-- 1 oleg oleg 452456448 2012-02-07 23:58 video.avi

```e.g. add read option to all users. Only after that files read without any problem.

I investigated problems occur only when to download from firefox. I tried different browser - rights of downloaded files are correct!

Can anyone tell me, how can I make all the downloaded files created with correct permissions?

---

### Post by painejake on 2012-02-08
Have to tried started firefox from the command line as you and saving then saving files?

```
$ firefox
```

---

### Post by Exterminator13 on 2012-02-20
After recent update problem dissappeared!

---

