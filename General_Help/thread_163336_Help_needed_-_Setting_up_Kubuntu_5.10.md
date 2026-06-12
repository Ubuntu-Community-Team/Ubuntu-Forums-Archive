---
title: "Help needed - Setting up Kubuntu 5.10"
date: 2006-04-20
forum: General Help
---

### Post by manishsingh4u on 2006-04-20
Hi Friends,
       I have a dual boot PC with Windows 2000 and Kubuntu 5.10 all setup well with all packages I need and in a very good working state.
       For some reasons, now I wish to make it only Kubuntu now and remove windows 2000 as nowadays I rarely boot windows.
       The problem is if I do a fresh install again, I will need to download and install all the packages again which I would wish to skip if possible, I have aleady made a backup of all the packages which are located in my [COLOR="Red"]/var/cache/apt/archives/[/COLOR] directory.
So is it possible to install all these packages in an easy way on the new installation without pain?

---

### Post by Qrk on 2006-04-20
Yes, after you reinstall, just change to the directory where you backed up /var/cache/apt/archives. Since it is probably a CD, just do:

```
cd /media/cdrom0
sudo dpkg -i *.deb
```

You may think that this way is not as good as using apt-get, but I believe it is the same thing. Apt-get only tracks the dependencies of files and downloads them. It then calls upon dpkg to actually install them from /var/cache/apt/archives.

---

### Post by manishsingh4u on 2006-04-20
Thanks **Qrk**. You gave me a really straight way to do this. Thanks again.

---

