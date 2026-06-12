---
title: "No alien command + cant install .deb files"
date: 2006-04-14
forum: General Help
---

### Post by 999.michael on 2006-04-14
I am trying to install my lexmark printer driver, and in the instructions i have been given it says:

```
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
```

However, when i type `alien` the terminal tells me that there is no command called alien. I found some instructions to install alien that say:

```
sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
```

It then tells me that i dont have the libstdc++2.10-glibc2.2 library. i have downloaded this and typed

```
dpkg -i libstdc++2.10-glibc2.2.deb
```

but it says that i need superuser priveliges to run dpkg. i am guessing that i have to log on as 'root' to get superuser priveliges, but if i type root into the login screen and then the password which i set, it tells me that i cant log on from that screen.

Can somebody please tell me how to log on as root and therefore how to install .deb files! thanx in advance. :confused:

---

### Post by oscar on 2006-04-14
you dont need to log in as root, just use sudo as with the other commands:
```
sudo dpkg -i libstdc++2.10-glibc2.2.deb
```

Also you shouldn't have to specify other dependencies, just:
```
sudo apt-get install alien
```

---

### Post by vruum on 2006-04-14
edit: oscar was faster

---

### Post by 999.michael on 2006-04-25
yeah i just logged on as root in the end but that looks a lot faster, thanks

(also i didnt know about specifying dependencies, because i just got it off another post)

---

### Post by Anduu on 2006-04-25
Word of warning..

***Do Not*** attempt to use this method for lexmark drivers with Dapper Beta.

Hosed my install twice trying :rolleyes: 

Works great in Breezy 8)

---

### Post by stanthecaddy22 on 2006-04-26
another note -- alien -t creates a .tgz file but if you want to create a .deb file use the alien -d command

---

### Post by Jott on 2006-04-27
ok - I've got a lexmark and I just installed dapper - I read your word of warning - any suggestions?

---

### Post by Anduu on 2006-05-02
[QUOTE=Jott]ok - I've got a lexmark and I just installed dapper - I read your word of warning - any suggestions?[/QUOTE]

As of yet I am not able to get my printer working ](*,)

---

