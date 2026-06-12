---
title: "hostname: invalid option -- 'f'"
date: 2009-07-09
forum: General Help
---

### Post by Xzan on 2009-07-09
Hi everyone,

Since yesterday, i'm having a mistake with hostname. When i use "hostname -f" it returns :

```
hostname: invalid option -- 'f'
```

I tried to reinstall hostname and coreutils (apt-get install --reinstall) but it didn't fix my problem. I searched on google/yahoo/bing and i only found Japanese websites and even with translation from google i didn't manage to understand something.

The only thing i've made on my system before i noticed the problem was to add a repository in my /etc/apt/sources.list which is :

```
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
```

This repository is for VLC so i don't think it may be the source of the problem but i prefer tell it.

I have to say that i don't really use this option usually but phpmyadmin's installation and upgrade do and so it returns an error and break my system.

I really don't have a clue so if anyone can help me or give me a lead, it would be really nice.

Thanks a lot ;)

PS : I speak french so if you don't understand something i've said because of my english, feel free to ask me to clarify ;)

---

### Post by michy99 on 2009-07-09
Have you tried these?```
hostname --fqdn
hostname --long
```

---

### Post by Xzan on 2009-07-09
When i try these it returns :

```
[benjamin@Pal:~]$ hostname --fqdn
hostname: invalid option -- '-'

[benjamin@Pal:~]$ hostname --long
hostname: invalid option -- '-'
```

so i tried hostname -d

```
[benjamin@Pal:~]$ hostname -d
hostname: invalid option -- 'd'
```

Apparently, i have a bigger problem with hostname than i taught :s

---

### Post by michy99 on 2009-07-09
What happens if you enter hostname without any option?

---

### Post by Xzan on 2009-07-09
It works correctly :

```
[benjamin@Pal:~]$ hostname
Pal
```

---

### Post by Xzan on 2009-07-11
I've solved my problem thanks to the bug-coreutils mailinglist. I'm posting my fix here to help others that may have the same problem one day.

**A big thanks to Bob Proulx for his help.**

There is different version of hostname. The coreutils version of hostname does not accept options, it just give you your hostname and set it. The version in Ubuntu does more with options.

Apparently, i have once installed the coreutils version in my /usr/local/bin directory by compiling coreutils by myself. You can see if you have that version by entering the following command and it gives you the same answer :

```
type -a hostname
> hostname is /usr/local/bin/hostname
> hostname is /bin/hostname
```

To solve the problem, you just have to move or delete the /usr/local/bin/hostname :

```
sudo mv /usr/local/bin/hostname{,.bak}
```

If you close and open a new shell, it will be ok ! If you don't want to close your shell, just type :

```
hash -r
```

That's all.

---

