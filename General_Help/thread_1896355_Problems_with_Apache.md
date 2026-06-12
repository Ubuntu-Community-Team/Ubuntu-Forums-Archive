---
title: "Problems with Apache"
date: 2011-12-16
forum: General Help
---

### Post by adamantasaurus on 2011-12-16
Hello, 

I am trying to setup a server using an old desktop to host my own website. I am following this tutorial ...........

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments)

I get to the part where it tells me to back up the apache files by entering 

sudo cp /etc/apache2/apache2.conf/etc/apache2/apache2.conf.bak

I enter it and I get this error message (this is for the files he tells me to back up after that also)

cp: missing destination file operan after '/etc/apache2/apache2.conf/etc/apache2/apache2.conf.bak
try 'cp --help' for more information.


My next problem is in that tutorial it tells me to change some lines of code...

in the apache2.conf file and he tells me to change...

Scroll down (down arrow) to where it says “ServerTokens Full” and change it to read “ServerTokens Prod”
Now, scroll down a little further and change “ServerSignature On” to “ServerSignature Off”

But there is no 'ServerTokens' or 'ServerSignature'.

So I decided to write the code in myself. My question is is that ok to do??

And also I got to the part where it tells me to restart apache2 I enter the command sudo /etc/init.d/apache2 restart

And it gives me this message

Apache2:could not reliably determine the servers fully qualified domain name, using 127.0.1.1 for ServerName
..... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName.

What do I do/What am I doing wrong?

Many Thanks In Advance.

Joey

---

### Post by yetiman64 on 2011-12-16
> cp: missing destination file operan after '/etc/apache2/apache2.conf/etc/apache2/apache2.conf.bak
try 'cp --help' for more information.For the copy command try it with a space between the source and the destination like,
```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
```Not sure about the rest sorry.

---

### Post by adamantasaurus on 2011-12-16
> **yetiman64 said:**
> For the copy command try it with a space between the source and the destination like,
```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
```Not sure about the rest sorry.

I did that an it didn't say anything at all all I saw was the normal UserName@computername:~$_

Does that mean it worked?

---

### Post by yetiman64 on 2011-12-16
> **adamantasaurus said:**
> I did that an it didn't say anything at all all I saw was the normal UserName@computername:~$_

Does that mean it worked?
Most likely yes, a way to check is to navigate in Nautilus to the address /etc/apache2 and look for a file "apache2.conf.bak", if it exists the copy worked. Though the terminal not giving an error output is a good sign usually for most terminal commands (will only give an output on an error in most cases).

---

### Post by fdrake on 2011-12-16
> **adamantasaurus said:**
> I did that an it didn't say anything at all all I saw was the normal UserName@computername:~$_

Does that mean it worked?

post output of:
```

ls /etc/apache2/apache2.conf*

```

> And it gives me this message

Apache2:could not reliably determine the servers fully qualified domain name, using 127.0.1.1 for ServerName
..... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName.

What do I do/What am I doing wrong?
this tutorial is pretty outdated! what ubuntu server version are you using?
```

less /etc/lsb-release

```

---

### Post by fetal on 2011-12-16
What  version of apache are you running? That website you linked was posted in 08. More than likely a different version of a apache. So you may not find those two lines of code. Did you read line by line? Or did you search for them?

---

### Post by mörgæs on 2011-12-16
Please stop adding NEED HELP PLEASE!!! to your thread titles. It is annoying and does not help you getting a faster answer.

---

### Post by adamantasaurus on 2011-12-16
> **fdrake said:**
> post output of:
```

ls /etc/apache2/apache2.conf*

```


this tutorial is pretty outdated! what ubuntu server version are you using?
```

less /etc/lsb-release

```

Is there a more recent tutorial you can direct me to?

I'm using the latest version I guess I downloaded it off of the ubuntu website.

---

### Post by adamantasaurus on 2011-12-16
> **fetal said:**
> What  version of apache are you running? That website you linked was posted in 08. More than likely a different version of a apache. So you may not find those two lines of code. Did you read line by line? Or did you search for them?

I'm using apache2 (If that is what your asking). I hit cntrl. w and typed in some words to search for and nothing showed up.

---

### Post by adamantasaurus on 2011-12-16
> **mörgæs said:**
> Please stop adding NEED HELP PLEASE!!! to your thread titles. It is annoying and does not help you getting a faster answer.

Ok sry I didn't know it would annoy people

---

### Post by adamantasaurus on 2011-12-16
> **yetiman64 said:**
> Most likely yes, a way to check is to navigate in Nautilus to the address /etc/apache2 and look for a file "apache2.conf.bak", if it exists the copy worked. Though the terminal not giving an error output is a good sign usually for most terminal commands (will only give an output on an error in most cases).

Ok Thank You

What do you mean navigate in Nautilus? How do I do that?

---

### Post by fdrake on 2011-12-16
here:[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)

I suggest you to use for a server a LTS(long-time-support) release like 10.04. Next year( ?mid of 2012? - if the maya calendar permits :D) there will be another long release 12.(04?) and you will be able to upgrade directly from 10.04 to it.

---

### Post by yetiman64 on 2011-12-16
> **adamantasaurus said:**
> Ok Thank You

What do you mean navigate in Nautilus? How do I do that?
What I mean by "navigate in Nautilus" is to open any nautilus window (your home folder will do) > click on "Filesystem" > find and open the "etc" folder > find and open the "apache2" folder and look for the file inside it. 

Note that the much quicker (terminal) method for checking the backup file you created was shown in post No. 5 by fdrake. Cheers.

---

### Post by adamantasaurus on 2011-12-17
> **yetiman64 said:**
> What I mean by "navigate in Nautilus" is to open any nautilus window (your home folder will do) > click on "Filesystem" > find and open the "etc" folder > find and open the "apache2" folder and look for the file inside it. 

Note that the much quicker (terminal) method for checking the backup file you created was shown in post No. 5 by fdrake. Cheers.

How do I click on "filesystem" it is just a black screen with words I'm not using the desktop version (unless I am missing something). 

And I have another question how do you open a terminal I see on the unbuntu website they tell you to type in [COLOR=#150500][FONT=Verdana]Applications -> Accessories -> Terminal 

and when I do that I hit enter and it tells me command invalid or something like that. 

And another unrelated question 

I installed the 10.04 version and when I check to see what version I'm using I type in 

[/FONT][/COLOR][LEFT][COLOR=#150500][FONT=monospace]cat /etc/lsb-release

and it tells me I'm using version 11.10 (but I know I installed 10.04)??

Thanks for the advice though
[/FONT][/COLOR][/LEFT]

---

### Post by yetiman64 on 2011-12-17
Are you on a server install without a desktop environment ? If so, use the terminal method in post No. 5, as you won't have nautilus in such an install. **Edit**: just noted your last post states a server only install, apologies for missing the info.

```
ls /etc/apache2/apache2.conf*
``` as fdrake noted. Sorry for the confusion if you aren't running a desktop environment, my wrong assumption by the sound of it.

**Edit2**: the screen you log into is a tty terminal and commands are issued directly from it. No need to "call up" gnome-terminal (once again for desktop installs that info, same with the directions [COLOR=#150500][FONT=Verdana]"Applications -> Accessories -> Terminal" are for those on a desktop install) [/FONT][/COLOR]

---

### Post by adamantasaurus on 2011-12-17
> **fdrake said:**
> here:[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)

I suggest you to use for a server a LTS(long-time-support) release like 10.04. Next year( ?mid of 2012? - if the maya calendar permits :D) there will be another long release 12.(04?) and you will be able to upgrade directly from 10.04 to it.


I'm on the first step of the page 2

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2)

It's telling me to enter vi /var/www/info.php to insert that .php page into my website I enter that command and a black screen pops up with a bunch of blue lines on the left side and at the bottom it says "/var/www/info.php" [New File] what does that mean?

---

