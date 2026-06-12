---
title: "simple questions by a newbie"
date: 2006-04-30
forum: General Help
---

### Post by fouadk on 2006-04-30
i have couple of simple questions...
1- i want to create a launcher that will appear on all desktop of users, in windows xp u create it in c:\documents and settings\all users\desktop 
is there is anything similiar in ubuntu or i have to create a launcher in each home folder of the users???
2- when i use synaptic manager or apt-get to install a new game (planetpenguin-racer for example) if i type in a terminal the name that i saw in synaptic the game might run or might not, how would i know the magic world that would run the game that i just installed...
3- in a newly opened terminal if i press TAB i get a list of all the possible word i could enter, lets suppose that we installed a new game or a new application , cant we in a terminal by pressing TAB filtering newly installed application???

Please elaborate coz im a newbie...

---

### Post by enopepsoo on 2006-04-30
2 in synaptic select the package, go to properties then installed files.  you should be typing in the nearest thing to the name of the pacage you installed that is in /usr/bin.
3 that should work too.

---

### Post by geek.de.nz on 2006-04-30
1 - create a directory "Desktop" in /etc/skel:
```

sudo -l
#enter password
cd /etc/skel
mkdir Desktop

```
and copy your link or whatever there:
```

cp /path/to/desktop/item /etc/skel/Desktop/

```


add a user with:
```

useradd -m -g group username

```

Have a look here [http://www.die.net/doc/linux/man/man8/adduser.8.html](http://www.die.net/doc/linux/man/man8/adduser.8.html) .

Hope that helps :-)

---

