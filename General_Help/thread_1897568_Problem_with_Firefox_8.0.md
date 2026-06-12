---
title: "Problem with Firefox 8.0"
date: 2011-12-19
forum: General Help
---

### Post by arroy_0209 on 2011-12-19
I recently reinstalled ubuntu 10.04LTS-2 and upgraded firefox to 8.0. Now I notice there is one problem with this version of firefox. Suppose I want to save some page by clicking ctrl+S (or choosing menu from "file") and a window opens where I am supposed to choose the directory where I want to save the file. By default, the directory shown is "Download". Problem occurs if I choose to create a new directory where I wish to save. To do this I need to click on "Create Folder" button which upon clicking, a blank new folder is shown where I am supposed to write the name of my choice. The problem is this newly opened folder vanishes fast even before I complete writing name of the new folder. Somehow firefox dislikes creating new directories by me. 
Are other users of firefox facing the same problem? What should I do? 

I had used the following commands to upgrade firefox:
```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by lovinglinux on 2011-12-19
I just tested and it worked. Are you using an AppArmor profile with Firefox? Are you trying to create the folder on a shared ntfs partition?

---

### Post by arroy_0209 on 2011-12-23
Thanks for your attention.
I am using apparmor profile for firefox but that one is supplied by ubuntu (actually updated automatically after installation) and this is probably not the problem since I had used the same apparmor profile with previous version of firefox I had.

I think I am not trying to create folder on a shared ntfs partition since there is only ubutu 10.04 LTS in the harddisk, as it was earlier.

The problem is somewhere else perhaps.

---

### Post by lovinglinux on 2011-12-23
Please try Firefox in safe mode:

```
firefox -safe-mode
```

---

### Post by arroy_0209 on 2011-12-23
I have tried to run firefox in safe mode using the command but the same problem takes place.

Meanwhile I had messed up things a bit. Can anybody please check whether what I had done is right. I tried to create a new profile for firefox and found that the same problem was present with this new profile. The problem got worse because then I deleted the second (new) profile and after that firefox refused to open; when I tried, a comment like "firefox is already running in the background, first kill that.." etc appeared. I had no way so I used 
```

sudo apt-get purge firefox
sudo apt-get purge firefox-locale-en

```I deleted everything inside ./mozilla/firefox using rm -rf. I was forced to install firefox (this time an older version since the current version was unavailable, the idea being to upgrade it after installation)
```

sudo apt-get install firefox-3.6

```After this as usual, I used the commands to upgrade:
```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get dist-upgrade

```I have noticed the problem remains without any add-on, with no-script add-on and also when run in safe-mode. Now what should I do?

I should mention, apparmor is running and is in fact in enforce mode all the time.

---

### Post by lovinglinux on 2011-12-23
Put firefox apparmor profile in complain mode and test.

---

