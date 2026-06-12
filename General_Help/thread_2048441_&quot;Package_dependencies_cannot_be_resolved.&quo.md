---
title: "&quot;Package dependencies cannot be resolved.&quot; when trying to install OpenJDK 6 Runtime."
date: 2012-08-26
forum: General Help
---

### Post by bub166 on 2012-08-26
As the title says, I was trying to install OpenJDK 6 Runtime on Ubuntu 12.04, but I'm getting this error:

"Package dependencies cannot be resolved.

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b24-1.11.1-4ubuntu2) but 6b24-1.11.1-4ubuntu2 is to be installed
               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is to be installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.1 is to be installed"

I'm rather new to Ubuntu (I have used it a bit in the past, and successfully installed this before, but have never come across this error), and I am not sure how to proceed here. I searched for help, but suggestions seemed varied and confusing, so some basic tips on how to fix this issue would be nice. I do know how to use the Terminal.

Thank you in advance.

---

### Post by user333 on 2012-08-26
Try this:
```

~# apt-get update
~# apt-get libjpeg8 libpulse0 openjdk-6-jre-headless

```

If you don't get any errors try installing openjdk-6-jre again from the terminal. That way you can post all the terminal output. (By the way, please use [CODE] tags to format terminal output to make things easier to read. You can add it manually or by using the advanced posting mode)

---

### Post by bub166 on 2012-08-26
Thanks for the suggestion, I'll make sure to keep that in mind from now on.

As for the instruction you gave, this is what appeared after apt-get update:

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```I'm not really sure what it is saying here. Thanks again.

---

### Post by user333 on 2012-08-26
Oh, sorry. You need to be root (that's what the ~# means). So just type sudo before each of the commands, or enter bash as root and then run the commands:

```

~$ sudo bash
~# apt-get update
~# apt-get libjpeg8 libpulse0 openjdk-6-jre-headless
~# exit #This exits from the root terminal to get back to normal bash
~$

```

---

### Post by bub166 on 2012-08-26
Oh, of course, I knew that. It's just been a while since I've used it, and I didn't think to do that.

Anyway, the update worked fine, but when I entered the second part, I got:
```

E: Invalid operation libjpeg8
```
Is there another thing that was implied by the second command that I just didn't enter, or am I doing something else wrong here?

---

### Post by MrGiedi on 2012-08-26
It wont work trough apt-get i guess
 Not 100% sure bout it but u can try dowload each  packet separetely and install it.
Search`em right here [http://packages.ubuntu.com/](http://packages.ubuntu.com/). I mean search for libjpeg8 and so on.
and here`s how to install deb packages [http://everyjoe.com/technology/howto-use-dpkg-to-install-deb-files/](http://everyjoe.com/technology/howto-use-dpkg-to-install-deb-files/).
Then you should be able to install OpenJDK.

---

### Post by bub166 on 2012-08-26
As it turns out, updating seems to have made it possible to install it. Thank you both for your help! I can tell there is a great community here already.

---

### Post by user333 on 2012-08-26
Glad you got it working ;)

---

### Post by MrGiedi on 2012-08-27
May I ask u what did u update? Askin since I dont get fully and wanted to be sure what was the solution in ur case and most importantly for satisfaing curosity. :P Thanks in advance for the answer.

---

