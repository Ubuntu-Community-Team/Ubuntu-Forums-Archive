---
title: "emacs 23 Install"
date: 2012-03-25
forum: General Help
---

### Post by Zzarkc-20 on 2012-03-25
I'm intending on installing emacs 23.4 via building through source code. I am running 11.10 64-bit. In one of the steps of this site:[http://www.yilmazhuseyin.com/blog/dev/basic-emacs-setup/](http://www.yilmazhuseyin.com/blog/dev/basic-emacs-setup/)
I am supposed to use: ```
sudo apt-get build-dep emacs
```The issue is, when I do this, I continually get the following error: 
```
E: Unable to find a source package for emacs23
```

I have done sudo apt-get clean and sudo apt-get update.

Any ideas? Also, there is an issue when I try running ./configure:```
configure: error: crt*.o not found.  Use --with-crt-dir to specify the location.
``` 

I have tried running:
```
 ./configure --with-crt-dir=/usr/lib/x86_64-linux-gnu

```

to no avail. 

Thanks for any help on this!!!

---

### Post by brainwash on 2012-03-25
Hey, 

what output does

```
./configure --with-crt-dir=/usr/lib/x86_64-linux-gnu
```

generate?

---

### Post by idoitprone on 2012-03-25
> **Zzarkc-20 said:**
> I'm intending on installing emacs 23.4 via building through source code. I am running 11.10 64-bit. In one of the steps of this site:[http://www.yilmazhuseyin.com/blog/dev/basic-emacs-setup/](http://www.yilmazhuseyin.com/blog/dev/basic-emacs-setup/)
I am supposed to use: ```
sudo apt-get build-dep emacs
```The issue is, when I do this, I continually get the following error: 
```
E: Unable to find a source package for emacs23
```I have done sudo apt-get clean and sudo apt-get update.

Any ideas? Also, there is an issue when I try running ./configure:```
configure: error: crt*.o not found.  Use --with-crt-dir to specify the location.
```I have tried running:
```
 ./configure --with-crt-dir=/usr/lib/x86_64-linux-gnu

```to no avail. 

Thanks for any help on this!!!

```
cat /etc/apt/sources.list
```

did you enable the sources repo and update it?

---

### Post by Zzarkc-20 on 2012-03-25
Ah! Including the sources fixed it! Thank you so much. I feel like an idiot for not checking that setting.

Thanks again!

---

