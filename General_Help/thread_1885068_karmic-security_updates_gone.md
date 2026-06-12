---
title: "karmic-security updates gone?"
date: 2011-11-22
forum: General Help
---

### Post by LuniTux on 2011-11-22
Hello,

I have some computers running Ubuntu 9.10 with a vbox windows os. until today, the computers were working ok. today, I tried to install ssh on one of the computers. I got the following:

```
...
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.177 80]

...
```

I went to [http://security.ubuntu.com/ubuntu/dists/]("http://security.ubuntu.com/ubuntu/dists/") and noticed that the "karmic-security" folder is no longer there. Am I no longer allowed to update or install new programs from the repository on ubuntu 9.10 computers? If I can not download from "http://security.ubuntu.com/ubuntu/", is there an alternative mirror I can use?

Thanks,

---

### Post by snowpine on 2011-11-22
Karmic went "end of life" in April and won't have any more security updates.

But you can change your mirrors in /etc/apt/sources.list to "http://old-releases.ubuntu.com" for purposes of installing ssh.

---

### Post by LuniTux on 2011-11-22
Thanks

That was exactly what I needed!

---

