---
title: "Apt Cache files been deleted"
date: 2009-07-03
forum: General Help
---

### Post by ario on 2009-07-03
Hi
I want to install a new fresh installation of ubuntu on my PC for some reason. I decided to backup my Apt Archive. I've downloaded and installed a large amount of packages via synaptic since I've installed my ubuntu. But theres only 100MB of files in my "/var/cache/apt/archives". It's not belivable.
For example i've installled FileZilla FTP Client and I can see it's checked in my synaptic list of installed packages. But can't find its package in my apt folder. Where are my downloads gone?
Why Synaptic Deleted its cache without asking me?
Do you have any Idea?
Thanks for your attention guys.
I'm tired of downloading a large amount of data whenever I need to install a new ubuntu system.:-k

---

### Post by ario on 2010-10-02
I even set my synaptic to keep all archvie files. But it will still delete some packages automatically.
Bump!

---

### Post by gmargo on 2010-10-02
Recommend you install an **apt** package caching daemon, such as **approx** (which I use) or **apt-cacher** or **apt-cacher-ng**.

[http://packages.ubuntu.com/lucid/approx](http://packages.ubuntu.com/lucid/approx)
[http://packages.ubuntu.com/lucid/apt-cacher](http://packages.ubuntu.com/lucid/apt-cacher)
[http://packages.ubuntu.com/lucid/apt-cacher-ng](http://packages.ubuntu.com/lucid/apt-cacher-ng)

---

### Post by drs305 on 2010-10-02
You can take a look at */etc/apt/apt.confd/20archive* to see how long APT will keep packages and how large a cache it will maintain. Other files in this folder may also be changed to suit your preferences. You can edit these settings as 'root'.

Although it may be a bit much, you can check the APT settings with:
```
apt-config dump
```

---

### Post by ario on 2010-11-01
> **drs305 said:**
> You can take a look at */etc/apt/apt.confd/20archive* to see how long APT will keep packages and how large a cache it will maintain. Other files in this folder may also be changed to suit your preferences. You can edit these settings as 'root'.

Although it may be a bit much, you can check the APT settings with:
```
apt-config dump
```

You mean I cant do it in GUI way? 'Cause I said "I even set my synaptic to keep all archvie files. But it will still delete some packages automatically". So the settings must be to not let apt delete packages. But it is still deleting things.
I decided to forget about this BUG and try to archive my apt cache by copying its content somewhere else every time I update my system! Which is annoying but no other solutions. Are there any?

---

### Post by drs305 on 2010-11-01
> **ario said:**
> You mean I cant do it in GUI way? 'Cause I said "I even set my synaptic to keep all archvie files. But it will still delete some packages automatically". So the settings must be to not let apt delete packages. But it is still deleting things.
I decided to forget about this BUG and try to archive my apt cache by copying its content somewhere else every time I update my system! Which is annoying but no other solutions. Are there any?

We'll have to wait for someone who has more depth of knowledge on the subject to provide the definitive answer. 

What I found in playing with settings is that if I 'hold' a package in Synaptic then APT doesn't necessarily respect it, and vice versa. I have to 'pin' the package in both to make sure the package isn't updated. 

The same may be true regarding saving packages. Until someone can offer more details, my suggestion would be to 'protect' your cache by both methods.

---

### Post by ario on 2010-11-02
> **drs305 said:**
> We'll have to wait for someone who has more depth of knowledge on the subject to provide the definitive answer. 

What I found in playing with settings is that if I 'hold' a package in Synaptic then APT doesn't necessarily respect it, and vice versa. I have to 'pin' the package in both to make sure the package isn't updated. 

The same may be true regarding saving packages. Until someone can offer more details, my suggestion would be to 'protect' your cache by both methods.

Very thanks.:)

---

### Post by cottfcfan on 2010-11-02
Can't help you with your current problem, but for future try using aptoncd.
 save all your cached downloads, then when you install a new system, just restore them, before installing your programs.
 Saves a lot of GB usage.

---

### Post by ario on 2010-11-03
> **cottfcfan said:**
> Can't help you with your current problem, but for future try using aptoncd.
 save all your cached downloads, then when you install a new system, just restore them, before installing your programs.
 Saves a lot of GB usage.

Thanks. Yes, that is another solution. But you should first have all your packages exist on your hard drive before archiving them with apt-cache, and synaptic/apt will suddenly purge them without ask!

---

### Post by Mike_tn on 2010-12-01
Same here. When I get an Update Manager update, the var/cache/apt/archives get hacked down.  Packages I use all the time are gone from archives. Still installed but no original downloaded package saved. AptOnCD only lists the packages in these same archives.  Missing ones are not available for that. The archives have some recently uninstalled packages that end up on AptOnCD results, another problem with AptOnCD. You would think UpdateManager would delete the ones you uninstall. So it matches the list generated with 
```
dpkg --get-selections > ~/my-packages
```This (above code) makes a list of all your installed packages and the list can be used for reinstallation.
Someone said you can download and install the list generated by the above code using
```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```**Question: [SIZE=2]Does anyone know how to download that same list and not install?[/SIZE]**

---

