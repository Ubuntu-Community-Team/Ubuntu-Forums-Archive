---
title: "Growing usage of root directory because of updates"
date: 2012-06-30
forum: General Help
---

### Post by mathgen on 2012-06-30
Hi

I am  a relatively new user to Ubuntu. I have installed 11.10 and also recently  12.04. 

I  update  whenever new updates are available from  Update Manager.  I have observed that probably  because of these freqeuent updates,   The   /  directory  is occupying more and more space.

 I have not installed too many packages or apps.  I am only using default apps and maybe a handful of apps.  But Used space  of   '/' directory   is continuing to grow  without any new apps.

  Maybe a month or 20 days  ago,  Used space  was  around 6 GB and  now today it is  6.7  GB. Is there any way  we can  reduce this  "Used Space" by deleting  unnecessary, old  files ? 

It appears  the unnecessary files are not automatically deleted.   

Or is  it  normal and without any  solution in Ubuntu ?

---

### Post by jmfal on 2012-06-30
Welcome to Ubuntu

run this in a terminal:

```
 sudo apt-get autoclean    
```

It clean out files used to install apps and such

---

### Post by CatKiller on 2012-06-30
When you install a new kernel it doesn't remove the old ones, in case the new one doesn't work. Some of those can mount up. Removing the old linux packages (but not the latest one!) in Synaptic will free up some space.

---

### Post by southerngeek on 2012-06-30
```
sudo apt-get autoremove
```
will uninstall any unused dependencies/packages that your system no longer needs.

```
sudo apt-get clean
```
Will completely clean out your package cache, and will probably free up the most disk space. Check out the apt-get man page for more info. :)

---

### Post by Daniel Jones on 2012-07-02
Installing updates will always consume some memory on your mobile phone, but executing "sudo apt-get autoclean" in terminal will free some space from on your mobile memory that have been used while installing apps and updates.

---

### Post by Lyfang on 2012-07-02
Try BleachBit (removes old temporary files).

---

### Post by Zvlwab on 2012-07-02
This may also help to remove old config files:
```
dpkg -l | awk '/^rc/ {print $2}' | xargs sudo dpkg --purge
```

You can use localepurge to automatically remove unused locale files when installing or updating packages:
```
sudo apt-get install localepurge
```

And you can manually remove unused (mostly hidden) files from your home dir, but don't remove any files of which you don't know what they do.

---

### Post by vasa1 on 2012-07-02
And as "a relatively new user to Ubuntu", make it a point to understand commands or software suggested to you.
Be especially aware of what you tick or don't when using "cleaning" programs.

---

