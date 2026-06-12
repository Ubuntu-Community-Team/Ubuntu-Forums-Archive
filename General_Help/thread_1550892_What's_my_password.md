---
title: "What's my password?"
date: 2010-08-11
forum: General Help
---

### Post by lwalper on 2010-08-11
I have downloaded the Apache web server so I can set up a local web server to test my PHP pages. The download automatically went into the default "Downloads" folder instead of the /opt folder where the Apache instructions said to download the file to. I have tried to move the file from the Downloads folder to the /opt folder but am denied access - says I don't have enough privileges (or some such thing?). Bummer.

So I tried to use the terminal to install the file that I downloaded from Apache (following their instructions - actually copied/pasted the command line so there would be no typo problem) - no joy.

The first thing I was instructed to do was to enter the su command, which I did, and was asked for a password. I have tried every password I have ever used on this system and I receive the following:

su: Authentication failure

and it returns me to the prompt. What is my password?

I checked the archives for similar problems and came up with zero relevant hits.

---

### Post by corrytonapple on 2010-08-11
Are you sure it isn't sudo? Your password is the one you created at installation. Remember, the password isn't visible when you use terminal.

---

### Post by bowens44 on 2010-08-11
Just out of curiosity, is there any reason you didn't just install it from the repositories?

---

### Post by WorMzy on 2010-08-11
Ubuntu doesn't set a root password by default, so su won't work. Use "sudo -i" instead. This command requires YOUR password, which you set when you installed Ubuntu.

But I, too, must ask why you're doing things the difficult way. To install apache, all you need to do is run (in a terminal) "sudo apt-get install apache2", or open up Synaptic (System -> Administration -> Synaptic Package Manager) and install it there.

If you want Apache, MySQL and PHP, then run "sudo tasksel install lamp-server".

---

### Post by lwalper on 2010-08-12
Just tried sudo -i and it worked. Thanks!

Why not install from the repositories? Well, just trying to follow the directions I was given at Apache. They must have forgotten about sudo -i. The command (su) they suggested did require a password, but it wasn't anything I had. Maybe it's for some upper level programmer or something? I'm a noob.

Before posting here I did try to install xampp from Synaptic, but it didn't seem to recognize that as an installable package. I also tried to look for lampp - again it did not locate the package, so thought I was pretty well stuck installing what I had downloaded from the prompt.

---

### Post by lwalper on 2010-08-12
In the terminal I just tried

sudo tasksel install lamp-server

and this is the reply I get.

leslie@leslie-laptop:~$ sudo tasksel install lamp-server
[sudo] password for leslie: 
tasksel: aptitude failed (100)

I'll try Synaptic again.

---

### Post by lwalper on 2010-08-12
Looking in Synaptic it appears that there is already quite a bit of Apache2 and MySQL server 5.1 stuff installed, though there is also a whole slew that is not installed, but no PHP. What PHP packages do I need? and do I need to install any more of the Apache or MySQL files as well? There's a PHP5-odbc package. Will that install all the necessary files?

---

### Post by WorMzy on 2010-08-12
You could try using apt-get to install the lamp-server packages, although I've never tried it myself, so I can't promise that it'll work

```
sudo apt-get install lamp-server^
```

If that doesn't work, then follow this tutorial: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by lwalper on 2010-08-12
OK! Thanks, that worked!! Doesn't look like anything new was installed in the process. I must already have everything I need. I'll check that link as well.

Thanks again.

---

### Post by lwalper on 2010-08-12
Went through the "Installing Apache 2" instructions and all seems to be working OK. Thanks again!:p

---

