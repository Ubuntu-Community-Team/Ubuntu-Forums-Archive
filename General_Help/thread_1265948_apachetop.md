---
title: "apachetop"
date: 2009-09-14
forum: General Help
---

### Post by xpinx2pin on 2009-09-14
Hi, does anyone know how to install apachetop on ubuntu 9.04?

i had install on repository using apt-get, but still didn't worked.

---

### Post by BUSHYBOB on 2009-09-14
I installed it on hardy and it's working fine, but after rereading your post I tried it with jaunty.

It installed ok, but when I tried to run it I got this error

** buffer overflow detected ***: apachetop terminated.

I have attached the complete output

---

### Post by xpinx2pin on 2009-09-29
Same prob with me. Its buffer overflow error.

Does anyone have success install apachetop on ubuntu 9.04 ?

---

### Post by karlwilbur on 2009-09-29
There seems to be a bug with apachetop 0.12.6-9 (the version in Jaunty)

I have been using 0.12.6-7 from Hardy just fine.

To install 0.12.6-7 on:
-- Jaunty x86_64
```

sudo aptitude remove apachetop
wget http://mirrors.kernel.org/ubuntu/pool/universe/a/apachetop/apachetop_0.12.6-7_amd64.deb
sudo dpkg -i apachetop_0.12.6-7_amd64.deb
rm apachetop_0.12.6-7_amd64.deb
sudo aptitude hold apachetop

```

-- Jaunty i686
```

sudo aptitude remove apachetop
wget http://mirrors.kernel.org/ubuntu/pool/universe/a/apachetop/apachetop_0.12.6-7_i386.deb
sudo dpkg -i apachetop_0.12.6-7_i386.deb
rm apachetop_0.12.6-7_i386.deb
sudo aptitude hold apachetop

```

---

