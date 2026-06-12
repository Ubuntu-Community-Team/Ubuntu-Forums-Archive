---
title: "External Hard Drive help!"
date: 2010-12-16
forum: General Help
---

### Post by boblettoj99 on 2010-12-16
Hi, i borrowed an external hard drive from my friend to back up a load of stuff on my windows partition before reinstalling it. I am doing this through ubuntu.

I am trying to zip up folders like My Documents etc and chuck them on the external hard drive but it always comes up with errors to do with read/write permissions. In the permissions tab on the folder properties of the ext hard drive it says I am owner but i have no file access (only folder access is create and delete files). When i try to give myself read/write permission it just goes straight back to nothing when i look at it again...what is going on? How can i get this to work?

Thanks

---

### Post by dexjjohn on 2010-12-16
If you have files that are currently in use by the OS you will not be able to copy.  This includes a song that is in a playlist etc....  Just try dragging parts of the folder over at a time until the whole operation is complete....Just a workaround.

---

### Post by cariboo on 2010-12-16
There are two ways to solve your problem, the first and easiest is to run naultilus as root. Press Alt-F2 and type:

```
gksu nautilus
```

Or, manually mount the external drive, and change the ownership and permissions using the following commands:

```
sudo chmod -R 777 /media/mountpoint
```

and

```
sudo chown -R you:you /media/mountpoint
```

Where you = your username and mountpoint = where ever you have the disk mounted. This solution should only be considered temporary, until you have restored your Windows partition, as the above commands leave the external drive wide open for anyone to access it.

---

