---
title: "Starting XAMPP at boot"
date: 2011-09-03
forum: General Help
---

### Post by mcfc4eva on 2011-09-03
Hi,

I have installed [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html").

It works fine, however to start XAMPP I must type the following in Terminal;
```
sudo /opt/lampp/lampp start
*my password*
```

I was looking for an easier way to start XAMPP. Ideally a desktop shortcut would have been good but I couldn't find a solution to this. Anyway I did find a tutorial on [how to start XAMPP at boot]("http://cahbojonegoro.wordpress.com/2009/01/05/start-xampp-at-boot-ubuntu-way/") however it doesn't work.

Here's the problem;
In the first stage of that tutorial it asks me to type
```
cd /etc/init.d/
sudo vi lampp
```

This displays a screen like this;
[IMG]http://i54.tinypic.com/2ujm6wn.png[/IMG]

Next step is to copy the and paste this code;
```
#!/bin/bash
/opt/lampp/lampp start
```
And I am displayed with the error
```
E486: Pattern not found: opt
```
[IMG]http://i51.tinypic.com/5v0z8n.png[/IMG]
The only way I can get out of this is to physically click the red 'X', at which point a dialogue box tells me that a process is still running and asks me to confirm, so I did.

Anyway I tried the whole process again, and I think it's because a file is already created or something, but I am faced with this problem;
[IMG]http://i55.tinypic.com/dbocqa.png[/IMG]

I think I must have half a dozen 'lampp' files in the init.d directory now, but I cannot view them or delete them to start again. I'm really starting to miss the GUI from Windows :(

Does anybody know why the tutorial isn't working and how I can fix the 'swap files' error?

Thanks
--Mike

---

### Post by Valkyr333 on 2011-09-03
Hi,

It seems as though we have to very specific and different problems. Do you think you could start your own thread to address your problem, so as to avoid confusing either or both of us when instructions are given on this one?

---

### Post by mcfc4eva on 2011-09-03
> **Valkyr333 said:**
> Hi,

It seems as though we have to very specific and different problems. Do you think you could start your own thread to address your problem, so as to avoid confusing either or both of us when instructions are given on this one?

This is my thread...?

---

### Post by Valkyr333 on 2011-09-03
Oh you're right. I'm sorry, it looks as though my browser somehow randomly jumped onto your thread while I thought I was still looking at my own. My mistake.

---

### Post by WorMzy on 2011-09-03
You're using vi, which is an advanced text editor, and not "newbie friendly". If you want to learn how to use vi, I recommend running
```
vimtutor
``` which will teach you how to use vim, which is vi, but with a lot of extra functionality.

Otherwise, I suggest you use gedit.

```
gksudo gedit /etc/init.d/lampp
```


Honestly though, I don't see why you're using XAMPP in the first place. Ubuntu's repositories have all the components necessary for a native LAMPP, and all you need to do to install them is to run

```
sudo apt-get install lamp-server^
```

That will install LAMPP, and make it automatically start at boot-up.

However, if you'd prefer to continue down this XAMPP path, that's up to you.

---

### Post by ComputerLady on 2012-01-30
Thanks WorMzy for your post on this thread! 

I'm a new user to Ubuntu and am running in a virtual machine (VM) install within windows for developmental purposes. Trying to figure out how to create an optimal LAMPP environment inside Ubuntu has been driving me nuts! Only concern I have with this approach is if I can restrict outside access to that web server when I have it up and running as you can with XAMPP. 

Yeah, I'm new to using Apache and so forth in this kind of environment too so I'm shooting myself in my foot every time I turn around in sorting all of this out. My goal, in setting up this developmental install, is to emulate the same versions of everything found on the hosting web server so if I 'blow things up' I'm doing it on my test server! 

Ah well, learning new things is lots of fun.... And to think I bought a computer to reduce stress!

---

