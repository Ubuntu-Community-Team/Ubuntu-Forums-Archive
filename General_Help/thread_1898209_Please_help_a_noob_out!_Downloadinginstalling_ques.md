---
title: "Please help a noob out! Downloading/installing questions!"
date: 2011-12-20
forum: General Help
---

### Post by aponia on 2011-12-20
First off, I'm running Ubuntu 11.10. 

Alright, here is my problem-- and you are allowed to laugh, I'm sure it sounds really dumb: when I download a program (such as the Opera browser, Flash player, Safari, etc), how on Earth do I install it? I can't double click on most .deb files because then it opens in the software manager, and usually the program I'm trying to download isn't there. I'm also having just as many problems with .tar, .tar.gz, etc. They're pretty much like zip files in windows, right? Well, if I extract the folders, where do I put them? ...and how do I even find where to put them? There's no address bar like in windows! 

Feel free to talk to me like I'm a mentally incompetent five-year-old, because I've been running windows since I can remember and I have zero experience with Linux. 

I'd really appreciate any help!

---

### Post by wildmanne39 on 2011-12-20
Hi, here is a link that tells you how to install software, some of it is through sofhtware manager but it also talks about debs and tar as well.
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Thanks

---

### Post by Rubi1200 on 2011-12-20
Hi and welcome to the forums aponia :)

Most software can be downloaded and installed using the Ubuntu Software Center.

There is really little need to be downloading files in the format you have done unless there is a specific version you need or an application that is not available via official repositories.

And, on that point, please be very careful what you download and which source it comes from.

The best security policy is to only install packages from the official repositories and use the in-built package managers to handle the rest.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/UbuntuSoftwareCenter?action=show&redirect=SoftwareCenterFAQ](https://help.ubuntu.com/community/UbuntuSoftwareCenter?action=show&redirect=SoftwareCenterFAQ)

---

### Post by Quantumlicht on 2011-12-20
Hello,

This is my first post on this forum. I am a noob myself but I just want to point out 2 simple commands you will always use.

You need to type these in the console which you can acces by typing ctrl+t.

```
sudo apt-get install _package_name
```
```
sudo apt-cache search keyword
```

sudo gives you root priviledge and the apt-get install will install the package with the given name. You should always look up with apt-cache search to find the correct name for the package you want to install.

Hope this helps.

---

### Post by critin on 2011-12-20
>  I can't double click on most .deb files because then it opens in the  software manager, and usually the program I'm trying to download isn't  there.Yes--deb files are **supposed** to be opened and installed by software center.  It's doing what its supposed to do.   You need to choose 'install by software center' in the pop-up menu.

You should be able to find most things through the software center and they will install along with all dependencies, use it whenever possible.  If you must find something outside of the software center, be sure and look for the .deb file download and let SC do the work for you.

---

### Post by aponia on 2011-12-21
> **Quantumlicht said:**
> Hello,

This is my first post on this forum. I am a noob myself but I just want to point out 2 simple commands you will always use.

You need to type these in the console which you can acces by typing ctrl+t.

```
sudo apt-get install _package_name
``````
sudo apt-cache search keyword
```sudo gives you root priviledge and the apt-get install will install the package with the given name. You should always look up with apt-cache search to find the correct name for the package you want to install.

Hope this helps.

Thank you for that information! I'm sure this will really come in handy!

---

### Post by aponia on 2011-12-21
> **critin said:**
> Yes--deb files are **supposed** to be opened and installed by software center.  It's doing what its supposed to do.   You need to choose 'install by software center' in the pop-up menu.

You should be able to find most things through the software center and they will install along with all dependencies, use it whenever possible.  If you must find something outside of the software center, be sure and look for the .deb file download and let SC do the work for you.

I will be sure to search for the .deb files as an alternative, but what if the application I'm trying to install doesn't come with .deb but only .tar, etc? I'm aware that .deb files open in the software center but a couple of times I've received the notice that it does not exist in the software center... that's where I'm a bit confused! 

I do appreciate your answer, though!

---

### Post by aponia on 2011-12-21
> **wildmanne39 said:**
> Hi, here is a link that tells you how to install software, some of it is through sofhtware manager but it also talks about debs and tar as well.
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Thanks
Thank you!

---

### Post by aponia on 2011-12-21
> **Rubi1200 said:**
> Hi and welcome to the forums aponia :)

Most software can be downloaded and installed using the Ubuntu Software Center.

There is really little need to be downloading files in the format you have done unless there is a specific version you need or an application that is not available via official repositories.

And, on that point, please be very careful what you download and which source it comes from.

The best security policy is to only install packages from the official repositories and use the in-built package managers to handle the rest.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/UbuntuSoftwareCenter?action=show&redirect=SoftwareCenterFAQ](https://help.ubuntu.com/community/UbuntuSoftwareCenter?action=show&redirect=SoftwareCenterFAQ)
I will keep this in mind! Thank you very much for the information.

---

### Post by critin on 2011-12-21
> I'm aware that .deb files open in the software center but a couple of  times I've received the notice that it does not exist in the software  center... that's where I'm a bit confused! 

Correct--they do not exist **in** the center, but the center will install them after you download the .deb--nice huh?  :)

But I like keeping it simple and safe, and I've been able to find everything I need there.  It may not be the Brand Name, but it works just as well if not better.

---

### Post by grahammechanical on 2011-12-21
You are still in the windows frame of mind. In Linux and Ubuntu in particular you do not need to run a setup.exe or an install.exe file in order to install a program.

If the program you want is not in the Software Centre and you are downloading it as a deb or tar file then it should automatically be downloaded into the Download folder. From there you can put it in its own folder that you have created.

If it is a .deb file then right click on it and select Open with Ubuntu Software Centre and then Software Centre will install it for you and if you need to remove that program you will find in now in the software Centre with a button that says Remove.

If it is a tar or tar.gz file then right click and select Open with Archive Manager and you can extract the file right into the folder it is already in. Now, you can open the deb file with Software Centre.

It is just a different way of working. You get used to it. I find it simpler. I like the way that the software Centre does all the work.

Regards.

---

### Post by oldos2er on 2011-12-22
> **Quantumlicht said:**
> ```
sudo apt-cache search keyword
```


No need to use 'sudo' with 'apt-cache search'.

---

