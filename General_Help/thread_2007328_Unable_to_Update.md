---
title: "Unable to Update"
date: 2012-06-20
forum: General Help
---

### Post by Sef on 2012-06-20
When I go to update my 12.04, I get this error: 

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

What's the best way to resolve this issue?

---

### Post by Arielxgbarton on 2012-06-20
Hi Sef, 

If you want to update, and update manager will not work for you, you can burn a liveCD on a CD-RW and use that to update

I have done this before, just pick UPDATE TO UBUNTU 12.04

From the Ubuntu website, there is a alternate install which involves downloading a .iso file, making a virtual CD and using that to update

Hope this helps 

Arielxgbarton

---

### Post by kanikilu on 2012-06-20
Someone correct me if I'm wrong, but I think the first thing to do is try deleting (or moving) the old lists and then running the update again: ```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
sudo apt-get update
```

---

### Post by kanikilu on 2012-06-20
If it's the dpkg status file, and not the lists, you can try replacing the status file with a backup. Someone detailed that here: [http://askubuntu.com/a/5175](http://askubuntu.com/a/5175)

---

### Post by CharlesA on 2012-06-20
> **kanikilu said:**
> Someone correct me if I'm wrong, but I think the first thing to do is try deleting (or moving) the old lists and then running the update again: ```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
sudo apt-get update
```
That would be the fix. Someone on IRC ran into that the other day.

---

### Post by Sef on 2012-06-20
> That would be the fix. Someone on IRC ran into that the other day.

It was. Thank you kanikilu.

---

### Post by 2burke on 2012-06-22
Have had probs with downloader the last couple of days.

  ran

 sudo greg@greg-HP-Compaq-dx2200-MT:~$ 
greg@greg-HP-Compaq-dx2200-MT:~$ sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
mv: cannot stat `/var/lib/apt/lists': No such file or directory
greg@greg-HP-Compaq-dx2200-MT:~$ sudo apt-get update
did a full update good
Some one must have fix the prob

---

