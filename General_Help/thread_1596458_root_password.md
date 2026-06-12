---
title: "root password"
date: 2010-10-14
forum: General Help
---

### Post by woopud on 2010-10-14
I'm trying to install the Lexmark printer driver package for my PRO205 but when it asks for my root password it wont accept it?  It keeps saying password is incorrect?  Ubuntu 10.10

Bert

---

### Post by CharlesA on 2010-10-14
Are you running this with sudo or something else?

@TheAnachron: I've removed yer post. See [here]("http://ubuntuforums.org/showthread.php?t=1486138").

---

### Post by sisco311 on 2010-10-14
> **woopud said:**
> I'm trying to install the Lexmark printer driver package for my PRO205 but when it asks for my root password it wont accept it?  It keeps saying password is incorrect?  Ubuntu 10.10

Bert

[uhelp]community/RootSudo[/uhelp]

Run the installer as root:
```
sudo path/to/file.sh
```

To get the exact path to the file simply drag & drop it in the terminal window.

---

### Post by TheAnachron on 2010-10-14
[[COLOR=#D40000]**CharlesA**[/COLOR]]("http://ubuntuforums.org/member.php?u=923868"),

Thanks! 
Tbh I haven't read that thread.

@woopud: Are you still having troubles?

---

### Post by woopud on 2010-10-14
So, the file is in my home folder what do I type in the terminal?

Bert

---

### Post by lloyd_b on 2010-10-14
> **woopud said:**
> So, the file is in my home folder what do I type in the terminal?

Bert

Have you tried the command Sisco311 gave you above?

Lloyd B.

---

### Post by woopud on 2010-10-14
> oopud@WOOPUD-PC:~$ sudo bash
root@WOOPUD-PC:~# /lexmark-inkjet-09-driver-1.5-1.i386.deb.sh
bash: /lexmark-inkjet-09-driver-1.5-1.i386.deb.sh: No such file or directory
root@WOOPUD-PC:~# install //lexmark-inkjet-09-driver-1.5-1.i386.deb.sh
install: missing destination file operand after `//lexmark-inkjet-09-driver-1.5-1.i386.deb.sh'
Try `install --help' for more information.
root@WOOPUD-PC:~# 




So, what am I doing wrong?

---

### Post by sisco311 on 2010-10-14
Try:
```
sudo ~/lexmark-inkjet-09-driver-1.5-1.i386.deb.sh
```

---

### Post by woopud on 2010-10-14
Thank you very much!  that did the trick.

Bert

---

### Post by CharlesA on 2010-10-14
Glad you got it working. Don't forget to mark the thread as solved. :)

---

### Post by sisco311 on 2010-10-14
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

### Post by trueathenianblue on 2010-11-01
I just want to say thank you to everyone who gets on these forums and helps us newbies - it took me several hours to figure out what was going on with the password issue and installing the printer. However, after reading several posts on the matter I finally have a working printer. Yeah! Also, I appreciate the clear and easy explanations a lot of you offer because when you switch over to Ubuntu from Windows and start reading these posts - it can sometimes be overwhelming.
Thanks again! :)

---

