---
title: "apt-get installed from a non-existent source"
date: 2010-12-07
forum: General Help
---

### Post by COKEDUDE on 2010-12-07
My apt-get installed from a non-existent source. So I am wondering how this is possible. I installed pidgin with this command. 

```
sudo apt-get install pidgin
```

The package information says it is in: 
**deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main **

[http://packages.ubuntu.com/maverick/i386/pidgin/download](http://packages.ubuntu.com/maverick/i386/pidgin/download)

This is the only repository I have in my source.list from maverick. 
**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse **

Could anyone explain how this is possible?

---

### Post by HiImTye on 2010-12-07
am I missing something? those are identical

---

### Post by ubuntu27 on 2010-12-07
:D Either it is a typo, or he/she is joking.

---

### Post by sikander3786 on 2010-12-07
Let us see the complete output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by COKEDUDE on 2010-12-07
> **HiImTye said:**
> am I missing something? those are identical

Yes it was a typo. I only have this one in my source list. 

**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse**

> **ubuntu27 said:**
> :D Either it is a typo, or he/she is joking.

Yes you are right. 

> **sikander3786 said:**
> Let us see the complete output of this command.

```
cat /etc/apt/sources.list
```


I commented out all the lucid stuff so they didn't conflict with the maverick line. 

```
deb http://archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse

deb http://packages.linuxmint.com/ isadora main upstream import
#deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
#deb http://archive.canonical.com/ubuntu/ lucid partner
#deb http://packages.medibuntu.org/ lucid free non-free


# deb http://ftp.de.debian.org/debian squeeze main
# deb http://ftp.us.debian.org/debian squeeze main

# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb http://archive.getdeb.net/ubuntu lucid-getdeb games
```

---

### Post by sikander3786 on 2010-12-07
Ubuntu automatically saves the downloaded packages under var/cache/apt/archives so they don't need to be re-downloaded everytime. Might be you installed pidgin sometime earlier and then removed it but the package was still there ;-)

If you want to test, remove pidgin, clear your apt-get cache and try installation again.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by COKEDUDE on 2010-12-07
> **sikander3786 said:**
> Ubuntu automatically saves the downloaded packages under var/cache/apt/archives so they don't need to be re-downloaded everytime. Might be you installed pidgin sometime earlier and then removed it but the package was still there ;-)

If you want to test, remove pidgin, clear your apt-get cache and try installation again.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

Yes you are correct I had pidgin installed on my system. I never removed it though. I had this pidgin package installed on my system from the lucid repository. 

[http://packages.ubuntu.com/lucid/pidgin](http://packages.ubuntu.com/lucid/pidgin)

I don't have a var/cache/apt/archives in my distro. Is there a way to check where that file is? 


Any idea how I installed pidgin from maverick when I never had the correct repository in my sources.list?

---

### Post by sikander3786 on 2010-12-07
> I don't have a var/cache/apt/archives in my distro. Is there a way to check where that file is? 

Which distro is this?

---

### Post by COKEDUDE on 2010-12-07
> **sikander3786 said:**
> Which distro is this?

Linux Mint Isadora.

---

