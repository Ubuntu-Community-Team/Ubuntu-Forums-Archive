---
title: "Error Message and I can't get around it! Have no idea what to do...."
date: 2010-09-22
forum: General Help
---

### Post by msbug206 on 2010-09-22
I am trying to upgrade, get my wireless working, and install other programs...but for the past few weeks I continue to get this same error message whenever I try to do anything when it comes to changing things within the system. This is the error message I get:

[B]Error: Opening the cache
(E: Malformed line 55 in source list/etc/apt/sources.list (dist), E: The list of sources could not be read.)
This usually means that your installed packages have unmet dependencies.[/B]

I have no idea what to do....Please help. I am an extreme newbie. I've been looking for a solution for a while now....

Thanks in advance.:(

---

### Post by CharlesA on 2010-09-22
Did you mess with the sources.list file?

What version of Ubuntu are you using?

---

### Post by msbug206 on 2010-09-22
I haven't done anything with the sources list. I found a previous solved thread with my same problem, but it didn't work. I'm getting the same error message.

10.04 LTS: Lucid Lynx

---

### Post by CharlesA on 2010-09-22
What does your sources.list look like?

Post it here in [noparse]```

```[/noparse] tags.

---

### Post by msbug206 on 2010-09-22
I don't know what to enter in order to get that information.

---

### Post by plucky on 2010-09-23
> **msbug206 said:**
> I don't know what to enter in order to get that information.

Open a terminal (Applications > Accessories > Terminal)  and post output of ```
cat /etc/apt/sources.list
```

---

### Post by msbug206 on 2010-09-26
Here is what I got when I put the code in.


# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
 

 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 

 # newer versions of the distribution.
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
 

 ## Major bug fix updates produced after the final release of the
 

 ## distribution.
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 

 ## team. Also, please note that software in universe WILL NOT receive any
 

 ## review or updates from the Ubuntu security team.
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 

 ## team, and may not be under a free licence. Please satisfy yourself as to  
 

 ## your rights to use the software. Also, please note that software in  
 

 ## multiverse WILL NOT receive any review or updates from the Ubuntu
 

 ## security team.
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
 

 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

---

### Post by coffeecat on 2010-09-26
> **msbug206 said:**
> Here is what I got when I put the code in.

That cannot be the whole file - there are less than 30 lines there and your problem is in line 55. And how did you manage to triple-space it?

Try this:

```
cat /etc/apt/sources.list > $HOME/Desktop/mysources
```That will write  a file called mysources onto your desktop. There's a reason for changing the name in the desktop copy. Now copy and paste the contents of that file into your reply, and **please** enclose it in [noparse]```

```[/noparse] tags. You can click on the # button in the toolbar above the message field to do that.

---

