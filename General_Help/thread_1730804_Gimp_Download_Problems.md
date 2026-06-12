---
title: "Gimp Download Problems"
date: 2011-04-16
forum: General Help
---

### Post by billhay4 on 2011-04-16
I am trying to install GIMP from the Ubuntu Software Center and get a "Failed to Download Package Files" message. It asks me to check my internet connection which seems to be working fine. However, there is no option to re-try to download.
Any suggestions on how to get this download to work.
Thanks for helping a newbie.
Bill

---

### Post by Enigmapond on 2011-04-16
Open a terminal and try it from there. Please post any errors that occur:

```
sudo apt-get install gimp
```

PS Welcome to the forum.. :)

---

### Post by billhay4 on 2011-04-16
Typical newbie mistake. I am on a brand new system and Ubuntu hadn't updated itself. Once this occurred, the download went seamlessly.
I had tried the teminal install, but it failed, too.
Thanks,
Bill

---

### Post by Enigmapond on 2011-04-16
Good! Incidentally, if you want the latest version 2.7, just run this in the terminal. The main repos are sometimes slow at getting the cutting edge versions.

```
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update && sudo apt-get upgrade
```

Cheers!

---

