---
title: "Unable to update [11.10]"
date: 2012-01-17
forum: General Help
---

### Post by Gitominoti on 2012-01-17
I haven't used Ubuntu in a while, and I booted it up today to be greeted with 204 updates. I ran them, and it gave me an error, telling me to check my internet connection. My internet is working fine; I've restarted and reconnected several times. I tried switching from the Server from Canada to Main Server, and I managed to install the GRUB Customizer. Now there is still 203 updates. 

Can someone help me out? Thanks

---

### Post by fantab on 2012-01-17
Post the output after running ***sudo apt-get update***.

Meanwhile try the following:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

and then use UPDATE MANAGER to check for updates.

---

### Post by grahammechanical on 2012-01-17
Do you have any PPAs listed as software sources? Uncheck them and try again. It used to be that Ubuntu would ask the user to confirm an update from what it calls untrusted sources and then the update would go ahead but now when we click OK the update cancels. So, do not try to run an update with a PPA program also wanting to update.

Regards.

---

### Post by Scott Baker on 2012-01-17
Quick question. regarding your internet connection, are you using a wired connection, or are you trying to do this through a wireless connection? If it's wireless, have you got an unrestricted access point. I've had clients that have tried to update through a wireless connection, only to be stopped in their tracks by the access points (some libraries, coffee shops, etc. place certain limits on uploads and downloads.) Have you got an unrestricted shot at your internet?? :-k

---

### Post by Iceman404 on 2012-01-27
I just started having the same issue within the past few weeks. I've tried restarting, switching to wired from wireless, using apt-get via the command line, also, switching servers. Switching servers has kind of a curious quirk. depending on the server sometimes it won't complete loading the cache, others it does. Also, in the "software sources" tab, when I try to search for the "ideal server" i also get the connection error.

honestly I feel a little better knowing that this isn't just me :-)

---

### Post by Iceman404 on 2012-01-27
so after poking around with search a bit more apparently some guys over here [http://ubuntuforums.org/showthread.php?t=1772228&highlight=update+can%27t+find+internet+connection]("http://ubuntuforums.org/showthread.php?t=1772228&highlight=update+can%27t+find+internet+connection")

found that if they did:
```
sudo apt-get update
```

followed by 
```
sudo apt-get upgrade
```

they actually got their updates. I just tried this and noticed that the server that it was failing to connect with was actually google's (i'm running chrome). I went to software sources, unchecked the google servers, tried again and it's currently installing the rest of the packages! worth a look/hope this helps!

---

