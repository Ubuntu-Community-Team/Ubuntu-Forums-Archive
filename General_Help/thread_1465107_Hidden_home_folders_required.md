---
title: "Hidden /home folders required?"
date: 2010-04-29
forum: General Help
---

### Post by AJH101 on 2010-04-29
I plan a fresh install of Lucid but will first copy my /home folder. Once I have installed Lucid and any extra software I have decided to keep I plan to copy back the contents of my /home folder.

My question is: do I need all of the .folders, or is it just the software I have decided to keep? My concern is that I might omit something I need, but at the same time I do not want to fill up my system with data no longer required.

Can anyone provide any guidance? Thanks!

---

### Post by madverb on 2010-04-29
The hidden folders and files are generally configuration files.
You don't really need them but you will have to reconfigure everything.

---

### Post by srs5694 on 2010-04-29
It may be you're misunderstanding something vital: Normally, software isn't installed in /home. The /home directory holds user data -- user (but not system) configuration files, user-created files, files downloaded from the Internet, etc. Software is installed in a variety of directories, but mostly in subdirectories of /usr, with system configuration files in /etc. Thus, copying the contents of /home will not affect what software is installed on either system. In Ubuntu, you normally use the Advanced Package Tools (APT) to install software, using command-line utilities like apt-get or GUI tools like Synaptic. (There are other ways to do it, but APT is the most common and easiest.) That said, it's possible to download software (in .deb packages or .tgz tarballs, for example), store those packages in /home, and then install them in one way or another. The .deb, .tgz, or whatever files stored in /home aren't installed and usable, though; they're just sitting there dormant until you install them.

---

