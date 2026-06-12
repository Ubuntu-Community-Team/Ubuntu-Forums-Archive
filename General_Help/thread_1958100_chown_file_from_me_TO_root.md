---
title: "chown file from me TO root"
date: 2012-04-13
forum: General Help
---

### Post by ukchris on 2012-04-13
I wanted to permanently add some environmental variables to my system by adding them to /etc/environment.

I used:

```

sudo chown $USER /etc/environment

```

To be able to edit the file and now want to chown it back to root.

Is this the correct syntax:

```

sudo chown root /etc/environment

```

Thanks.  :)

---

### Post by 0011235813 on 2012-04-13
> **ukchris said:**
> I wanted to permanently add some environmental variables to my system by adding them to /etc/environment.

I used:

```

sudo chown $USER /etc/environment

```To be able to edit the file and now want to chown it back to root.

Is this the correct syntax:

```

sudo chown root /etc/environment

```Thanks.  :)
Short answer, yes.

---

### Post by ukchris on 2012-04-13
Short thanks, thanks.

:D

[edit - curious about the long answer :)]

---

### Post by enkay009 on 2012-04-13
Just my 2 cents but you don't need to change ownership of a file to edit it when you have sudo. 

Sudo gives you temporary superuser (read root) privileges for whatever command you want to run.

Instead of changing the ownership of the file, you could've instead used sudo to invoke an editor to edit the file. For example...
```
sudo nano /etc/environment
```

---

### Post by ukchris on 2012-04-13
Thanks enkay, that's great.  

I'm pretty new to Linux so all these tips are very useful.

---

### Post by 0011235813 on 2012-04-13
> **ukchris said:**
> Short thanks, thanks.

:D

[edit - curious about the long answer :)]
Well there isn't really a long answer, just that in another system, root might be called something else, though probably not.
> **enkay009 said:**
> Just my 2 cents but you don't need to change ownership of a file to edit it when you have sudo. 

Sudo gives you temporary superuser (read root) privileges for whatever command you want to run.

Instead of changing the ownership of the file, you could've instead used sudo to invoke an editor to edit the file. For example...
```
sudo nano /etc/environment
```
I agree. But if you want to use a graphical program, use: ```
gksudo gedit <location>
```
or kate or leafpead instead of gedit. <location> is obviously replaced with the location of the file like /home/username/Downloads/file.something.

---

### Post by enkay009 on 2012-04-13
gksudo is just a frontend for sudo where it presents you with a dialog box for the password instead of entering it from a terminal. You don't have to use gksudo to invoke graphical applications.

---

### Post by ukchris on 2012-04-13
Thanks enkay and 001*.  That's a much cleaner and easier method than my long winded way.

I suppose if you were setting up some kind of install shell script you could add these lines via a script or something you want to run in multiple environments. 

Would this work:

```

sudo (echo 'GTSB=~/sandbox/my-test-scripts'; echo 'CSUMVAL=$GTSB/csumval') >> /etc/environment

```

---

### Post by 0011235813 on 2012-04-13
> **enkay009 said:**
> gksudo is just a frontend for sudo where it presents you with a dialog box for the password instead of entering it from a terminal. You don't have to use gksudo to invoke graphical applications.

No, but it's the *recommended* method. See man sudo and man gksudo for details.

---

### Post by haqking on 2012-04-13
> **enkay009 said:**
> gksudo is just a frontend for sudo where it presents you with a dialog box for the password instead of entering it from a terminal. You don't have to use gksudo to invoke graphical applications.

actually gksudo should be used for graphical applications and is best practice to prevent permission and file ownership errors.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lisati on 2012-04-13
Some further reading about sudo and some of its variants can be found at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by enkay009 on 2012-04-16
> **0011235813 said:**
> No, but it's the *recommended* method. See man sudo and man gksudo for details.

> **haqking said:**
> actually gksudo should be used for graphical applications and is best practice to prevent permission and file ownership errors.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **lisati said:**
> Some further reading about sudo and some of its variants can be found at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the input. I didn't know about this caveat.

I don't normally use gksudo and in the last 6 years I never ran into any of the problems mentioned in the blog and wiki page. However I must note that I use <i>sudo -i</i>. Which among other things resets a bunch of user specifc environment variables (like $HOME). Which means no root owned files creep up in my home directory.

---

