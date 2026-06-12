---
title: "How do I know what I've downloaded? For backup"
date: 2010-05-29
forum: General Help
---

### Post by UDon on 2010-05-29
I back up my personal files regularly, including my bookmarks. What I would like to do is get a list of software applications that I've downloaded from Synaptic Package Manager.

The reason I want to do this is that I plan to do a fresh install of the latest Ubuntu 10.4. I've found things work better to do a fresh install of everything with the new OS (I currently have Ubuntu 9.10)

There is "History" in Synaptic, but I don't want to have to do a lot of copying and pasting. Is there an easy way I can do this?

Also, what else do you think I should backup if I am doing a fresh install?

---

### Post by wojox on 2010-05-29
Sounds like you're looking for something like this [Package installation after re/new install (Ubuntu)]("http://stringofthoughts.wordpress.com/2009/04/29/package-installation-after-renew-install-ubuntu/")

---

### Post by krishnandu.sarkar on 2010-05-29
Your can Backup your installed applications with APTonCD. I hope this will come handy for you.
You can again re-installed your backedup apps from APTonCD without the need of Internet Connection. All dependencies are backedup also.

---

### Post by ajgreeny on 2010-05-29
You can also get a simple text file with the following three commands, used one by one:-
```
sudo -i
cd /root/.synaptic/log
cat /root/.synaptic/log/*.log > /home/username/dpkg-$(date +%F).log
```
which will produce file called dpkg-2010-05-29.log (dpkg-year-month-day.log).

It will not list anything you have installed using dpkg or apt-get in terminal, only those using synaptic or update-manager.

---

### Post by oldfred on 2010-05-29
I have used the dpkg get & set per wojox's link and it works well. The only issue I had was when I did it from my system that I had used for 3 years to a new install. I had not housecleaned well and it installed some old stuff that I really did not want. Also some packages were totally obsolete and it does not install those (correctly). So you may want to houseclean before saving the file.

If you have added sources like medibutu
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.

The dpkg get is just a list of names and it will reinstall with the latest version. If you want to see more description of what you have installed this version (but not for reinstall) gives extra info.

List with explanations/version of programs
dpkg -l > ~/Desktop/installed_programs.txt

---

### Post by UDon on 2010-05-30
Perfect! Just what I wanted. Thanks guys for the responses!

---

