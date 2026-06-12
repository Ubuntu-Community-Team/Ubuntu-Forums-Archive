---
title: "help me in compiling vlc source code."
date: 2011-09-09
forum: General Help
---

### Post by vikash_chandola on 2011-09-09
I have downloaded vlc source code from videolan website. I want to compile and install it. I have installed checkinstall but something is wrong.
first i extract archive 
then cd to that folder and type ./configure  But it is not continuing as it should. see attachment.

---

### Post by ottosykora on 2011-09-09
is there a special reason why you do not take the ready made vlc from the repository?

---

### Post by vikash_chandola on 2011-09-09
> **ottosykora said:**
> is there a special reason why you do not take the ready made vlc from the repository?
Yeah i can download vlc via software center or from any other place. But here i want to know how to compile source code and make .deb.

---

### Post by ron999 on 2011-09-09
> **vikash_chandola said:**
> ... But here i want to know how to compile source code and make .deb.
Hi
Follow the tutorial here:- [http://ubuntuforums.org/showthread.php?t=1398119]("http://ubuntuforums.org/showthread.php?t=1398119")
But drop down to the section that says "**Building the release version 1.1.11...**"

---

### Post by vikash_chandola on 2011-09-09
> **ron999 said:**
> Hi
Follow the tutorial here:- [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)
But drop down to the section that says "**Building the release version 1.1.11...**"
what happen in my case.
why ./configure give that output. Imean failed to continue.
what am i doing wrong?

---

### Post by blueridgedog on 2011-09-09
> **vikash_chandola said:**
> I have downloaded vlc source code from videolan website. I want to compile and install it. I have installed checkinstall but something is wrong.
first i extract archive 
then cd to that folder and type ./configure  But it is not continuing as it should. see attachment.

What is the owner and permission details of the file?  

```
ls -al ~/Desktop/vlc-1.1.11/configure
```

The error is trying to tell you that your current user account lacks permission to run the ./configure file.  Lets see what those permissions are.

---

### Post by vikash_chandola on 2011-09-09
> **blueridgedog said:**
> What is the owner and permission details of the file?  

```
ls -al ~/Desktop/vlc-1.1.11/configure
```The error is trying to tell you that your current user account lacks permission to run the ./configure file.  Lets see what those permissions are.
that is it.
I am only user administrator on my computer.

---

### Post by blueridgedog on 2011-09-09
Based on your screen shot, the file is not executable:

```
chmod 700 ~/Desktop/vlc-1.1.11/configure
~/Desktop/vlc-1.1.11/configure
```

"chmod" means "change permissions for a file or directory", 700 means that the file "owner" (in this case your user account) should have read, write and execute permissions to the file.

---

### Post by vikash_chandola on 2011-09-09
> **blueridgedog said:**
> Based on your screen shot, the file is not executable:

```
chmod 700 ~/Desktop/vlc-1.1.11/configure
~/Desktop/vlc-1.1.11/configure
```"chmod" means "change permissions for a file or directory", 700 means that the file "owner" (in this case your user account) should have read, write and execute permissions to the file.
first of all thanks for taking interest in my post.

You mean this is incorrect source/ configure file is different or corrupted. If yes then it should only with vlc but it is happening with other sources also see this attachment.here i am try to compile valgrind. that is also giving same error.
Some days ago when i try to do so in UBUNTU 11.04 (with this valgrind source). it was working fine. I run ./configure command. It works finely.(However other commands make and install  were not working due to some reasons).
So what should i do?

---

### Post by blueridgedog on 2011-09-09
Many times you will download files (especially if working from source) that are not executable and you will have to make them executable prior to being able to run them.

---

### Post by vikash_chandola on 2011-09-09
> **blueridgedog said:**
> Many times you will download files (especially if working from source) that are not executable and you will have to make them executable prior to being able to run them.
can you please explain in simple language 
can i make their executable .deb or not?

---

### Post by oldos2er on 2011-09-09
That's a strange error, assuming you're "in" your home folder. You didn't use 'sudo' to extract the source code, did you?

---

### Post by vikash_chandola on 2011-09-09
> **oldos2er said:**
> That's a strange error, assuming you're "in" your home folder. You didn't use 'sudo' to extract the source code, did you?
I extract source code as i usually do right click and then extract here.
[B]How to extract archive using command (as administrator)?
[/B]**I** am back on my ubuntu 11.04 (not xubuntu). I was just trying xubuntu today.

---

### Post by oldos2er on 2011-09-10
You don't want to extract any archive as root when in your /home/user folder. 

I notice in your screen shot you're working in /media/main drive/software/Linux/*, the 'Permission denied' error would be explained by your not having read/write permission there.

---

### Post by Zill on 2011-09-10
> **vikash_chandola said:**
> ...can i make their executable .deb or not?
I think you are slightly confused on this.  Compiling an application from source code will *not* automatically produce a .deb package.  It will simply allow you to run the application on your PC.

However, please note that if you do this then the resulting application will not receive any automatic updates as these only apply to installed .deb packages.

Compiling from source is not the recommended method of installing software in Ubuntu as, unless you are very experienced, you are highly likely to experience problems, including the infamous "dependency hell"!

If you do wish to continue compiling then I suggest you should first learn more about the Linux file structure and permissions etc.

---

