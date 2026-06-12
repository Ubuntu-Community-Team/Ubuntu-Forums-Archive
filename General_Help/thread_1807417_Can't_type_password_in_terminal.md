---
title: "Can't type password in terminal"
date: 2011-07-19
forum: General Help
---

### Post by severityCONCEPT on 2011-07-19
Guys, i need to install the new firefox. I have allready downloaded the tar.bz2 package and extract it in a folder. I go to terminal, type 
**sudo make install **

and appear 
**[sudo] password for severityconcept: **

but i can't type any character. How to type my password in terminal when i run that command I mentioned above?

---

### Post by Bucky Ball on 2011-07-19
You *ARE* typing your password, you just can't actually see it in a terminal. This is completely normal. Just type in your password, even though you can't see what you're typing, and hit Enter. ;)

ps: I would run

```
sudo apt-get update
sudo apt-get upgrade
```... before bothering with untarring files. The second command will upgrade all packages that can be and there could be the Firefox update there already.

What Ubuntu release are you running and what Firefox are you upgrading to?

---

### Post by pommie on 2011-07-19
Typing in your password does not show in a terminal, just blindly type in your password and hit enter.
This is to stop anyone looking over your shoulder from seeing how many characters your password consists of.

Cheers David

Edit, I need to type faster :)

---

### Post by srisharan on 2011-07-19
password doesnt appear not even asterisks or dots.But rest assured your password is being typed

---

### Post by severityCONCEPT on 2011-07-19
> **Bucky Ball said:**
> You *ARE* typing your password, you just can't actually see it in a terminal. This is completely normal. Just type in your password, even though you can't see what you're typing, and hit Enter. ;)

ps: I would run

```
sudo apt-get update
sudo apt-get upgrade
```... before bothering with untarring files. The second command will upgrade all packages that can be and there could be the Firefox update there already.

What Ubuntu release are you running and what Firefox are you upgrading to?

I'm using the newest release of ubuntu (11.04). I want to upgrade Firefox 4 to 5.

---

### Post by Bucky Ball on 2011-07-19
Run the previous update and upgrade commands. Pretty sure it's in that repository already (from memory). ;)

---

### Post by linuxman94 on 2011-07-19
> **Bucky Ball said:**
> Run the previous update and upgrade commands. Pretty sure it's there already. I'll boot in and check after.

Yep firefox 5 is in the repos. The update commands will do it.

---

### Post by Swagman on 2011-07-19
I don't understand... Firefox 5 is installed by **default** in 11:04.

Unless you upgraded from an earlier distro or possibly installed 11:04 in April ?

---

### Post by severityCONCEPT on 2011-07-19
> **Swagman said:**
> I don't understand... Firefox 5 is installed by **default** in 11:04.

Unless you upgraded from an earlier distro or possibly installed 11:04 in April ?

I only got firefox 4 in my 11.04. It's probably because I downloaded the .iso long before firefox 5 is released.

---

### Post by plucky on 2011-07-19
> **severityCONCEPT said:**
> I only got firefox 4 in my 11.04. It's probably because I downloaded the .iso long before firefox 5 is released.

But if you do all the updates it will install Firefox 5.

Do you have an Internet connection?

---

### Post by Bucky Ball on 2011-07-19
As I keep saying, open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
```... should upgrade all packages to the latest in the repositories. That could possibly upgrade the kernel and a heap of other things also so might take awhile.

---

### Post by SoFl W on 2011-07-19
Can't he just add a PPA and simplify his life even more?  

(I don't know what the PPA is for Firefox, I am happy with 3.6.18. using 10.4)

---

### Post by severityCONCEPT on 2011-07-19
> **plucky said:**
> But if you do all the updates it will install Firefox 5.

Do you have an Internet connection?

Yes, I have. But I always got a problem when installing the updates because I'm using proxy. Especially when I use sudo app-get update or sudo app-get upgrade. Is there any solution? I've already change the proxy in network proxy preferences but it still not working.

---

### Post by Bucky Ball on 2011-07-19
apt, not app!

---

### Post by lovinglinux on 2011-07-19
> **severityCONCEPT said:**
> Yes, I have. But I always got a problem when installing the updates because I'm using proxy. Especially when I use sudo app-get update or sudo app-get upgrade. Is there any solution? I've already change the proxy in network proxy preferences but it still not working.

I have seen a solution for the proxy issue, but I don't remember it and I can't find the thread.

Meanwhile, download Firefox deb packages from the repository manually and install:

[http://packages.ubuntu.com/natty/firefox](http://packages.ubuntu.com/natty/firefox)

The download link is at the bottom of the screen. You will also need to download and update these packages:

[firefox-globalmenu]("http://packages.ubuntu.com/natty/firefox-globalmenu")
[xul-ext-ubufox]("http://packages.ubuntu.com/natty/xul-ext-ubufox")
[firefox-gnome-support]("http://packages.ubuntu.com/natty/firefox-gnome-support")

> **SoFl W said:**
> Can't he just add a PPA and simplify his life even more?  

(I don't know what the PPA is for Firefox, I am happy with 3.6.18. using 10.4)

There is no need to add a ppa on Natty and it will probably also don't work because of the proxy issue.

BTW, if you want, info about the ppa is at [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by Wim Sturkenboom on 2011-07-20
> **severityCONCEPT said:**
> Yes, I have. But I always got a problem when installing the updates because I'm using proxy. Especially when I use sudo app-get update or sudo app-get upgrade. Is there any solution? I've already change the proxy in network proxy preferences but it still not working.

Thanks for below goes to gmargo who posted it in [http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306)

> 
To configure the apt tools to use a proxy, create a file /etc/apt/apt.conf with the following content, substituting appropriately:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```


---

### Post by severityCONCEPT on 2011-07-21
> **lovinglinux said:**
> I have seen a solution for the proxy issue, but I don't remember it and I can't find the thread.

Meanwhile, download Firefox deb packages from the repository manually and install:

[http://packages.ubuntu.com/natty/firefox](http://packages.ubuntu.com/natty/firefox)

The download link is at the bottom of the screen. You will also need to download and update these packages:

[firefox-globalmenu]("http://packages.ubuntu.com/natty/firefox-globalmenu")
[xul-ext-ubufox]("http://packages.ubuntu.com/natty/xul-ext-ubufox")
[firefox-gnome-support]("http://packages.ubuntu.com/natty/firefox-gnome-support")



There is no need to add a ppa on Natty and it will probably also don't work because of the proxy issue.

BTW, if you want, info about the ppa is at [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

Deb package is really helpful. I'm new in linux and deb package is the easiest one to install. Thanks to lovinglinux for the links.

---

### Post by severityCONCEPT on 2011-07-21
> **Wim Sturkenboom said:**
> Thanks for below goes to gmargo who posted it in [http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306)

Is there any risk of losing data if I create that file?

---

