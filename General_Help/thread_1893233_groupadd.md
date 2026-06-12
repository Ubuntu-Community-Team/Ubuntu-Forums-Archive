---
title: "groupadd"
date: 2011-12-09
forum: General Help
---

### Post by Jaybo2179 on 2011-12-09
when I search my /home directory with ls -l  I can't see the added projectX group the users are a part of.  

drwxr-xr-x 34 jason   4096 2011-12-09 18:07 jason
drwxr-xr-x  2 mark    4096 2011-12-09 17:41 mark
drwxr-xr-x  2 melissa 4096 2011-12-08 20:54 melissa
drwxr-xr-x  2 mike    4096 2011-12-09 17:39 mike

I know they are there though 

cat /etc/group

outputs 

projectX:x:1006:mike,mark,melissa

is that the only way I can find out what groups users are apart of? 

I'm a newbie to linux please be kind

---

### Post by WorMzy on 2011-12-09
You can find out group membership by either using "groupmems" to list the member of a group

e.g.

```
sudo groupmems -g audio -l
Password: 
wormzy  mpd 

```

or by using "groups" to list the groups a user is a member of:

```
wormzy@sakura[pts/2]:~$ groups root
root bin daemon sys adm disk wheel log

```

I find it strange that the output of your ls command has failed to specify which group each of the folders belong to. That's not something that I've ever seen before. If each one of those folders is supposed to be owned by the projectX group, try the following:

```
sudo chgrp projectX /home/*
```

If you want the folders and their contents to be owned by that group, add the -R flag:


```
sudo chgrp -R projectX /home/*
```

Be very careful with chgrp when paired with sudo, one mistake, and your entire system could be rendered unusable.

---

### Post by Jaybo2179 on 2011-12-09
thank you for the quick response!! Those methods work for me.  thank you again for you help!

---

