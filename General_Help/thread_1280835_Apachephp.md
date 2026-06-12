---
title: "Apache/php"
date: 2009-10-02
forum: General Help
---

### Post by whathaveugot on 2009-10-02
hi folks,

this is my first post so a big HELLO to all linux geeks :)

I was just wondering whether there's a way to set up apache web server with php support in ubuntu netbook remix 9.04.

You reckon u can help?

Cheers.

---

### Post by mac9416 on 2009-10-03
```
$ sudo tasksel install lamp-server
```

That installs a server with PHP support.

---

### Post by whathaveugot on 2009-10-06
> **mac9416 said:**
> ```
$ sudo tasksel lamp-server
```

That installs a server with PHP support.
i did that and after a really long package installation and even after setting the mysql administrative passwd (after which the process eventually completed)....i got the following message in the terminal window: "aptitude failed (100)"

what does that mean and how do i fix it!!!??

cheers

---

### Post by mac9416 on 2009-10-07
Run this command:

```
$ sudo dpkg --configure -a
```

Then this one again just to be sure everything went OK:

```
$ sudo tasksel install lamp-server
```

---

### Post by whathaveugot on 2009-10-07
> **mac9416 said:**
> Run this command:

```
$ sudo dpkg --configure -a
```

Then this one again just to be sure everything went OK:

```
$ sudo tasksel lamp-server
```
firstly, to let you knw, the command that worked here was "sudo tasksel install lamp-server"....I dnt knw why but it was asking for a verbose and I thought 'install' would be best, 

anywayz I did what you told man but after hitting the second code the blue package configuration screen appeared in the terminal and went away in few seconds..leavin me with the terminal prompt....

u got any other idea?

Cheers.

---

### Post by bubblehead74 on 2009-10-07
This works for me:
```
sudo aptitude install apache2 php5
```

---

### Post by mac9416 on 2009-10-07
Oh yeah, my bad. I've edited all my other posts to have the right command. The correct command is this:

```
$ sudo tasksel install lamp-server
```

Have you tried that again? I bet it's already installed properly, but that's just to make sure.

---

### Post by whathaveugot on 2009-10-08
@[bubblehead74]("http://ubuntuforums.org/member.php?u=810873")....i tried using the command but first I got a message after the general reading/building dependency tree etc etc stuff....it was "directory '/var/log/apt' missing"...so I created a directory in /var/log/ and then hit the command once again...this time everything went without any disruption....my question is how do know for sure that apache/php is installed and ready to run in my system?

@[mac9416]("http://ubuntuforums.org/member.php?u=506161").....i tried firing the command once again....it was same again....the blue screen appeared and went off [without saying goodbye...just kiddin' :)]....

to both of you....HOW DO I CONFIRM THT APACHE WITH PHP SUPPORT IS INSTALLED IN MY NETBOOK??? PLZ HELP...:(

Cheers.

---

### Post by mac9416 on 2009-10-08
I can't claim to know much about servers or PHP, but here's my suggestion...

Delete index.html:

```
$ sudo rm /var/www/index.html
```

Create a file called index.php:

```
$ sudo gedit /var/www/index.php
```

Paste this line into index.php:

> <php?
print("<h1>Hello, world!</h1>");
?>

Save the file. Then type in your browser's location bar "localhost". If that doesn't work, try "localhost/index.php".

If "[SIZE="4"]Hello, world![/SIZE]" shows up in your browser, you have Apache installed with PHP support. :)

---

### Post by bubblehead74 on 2009-10-08
The previous post should help you. For more detailed explanation, read this article:

[Easy installation of LASP (Linux, Apache, SQLite and PHP) on Ubuntu]("http://www.bioinformatics.org/librarian/blog/2009/09/11/easy-installation-of-lasp-linux-apache-sqlite-and-php-on-ubuntu/")

---

### Post by whathaveugot on 2009-10-09
@[mac9416]("http://ubuntuforums.org/member.php?u=506161").....I'm getting a Page Load Error in firefox so I reckon apache is not installed...i'll try [bubblehead74]("http://ubuntuforums.org/member.php?u=810873")'s link.

@[bubblehead74]("http://ubuntuforums.org/member.php?u=810873")....think this should work or else I'll dwnld the sources and install it....

Cheers

---

### Post by whathaveugot on 2009-10-09
@[bubblehead74]("http://ubuntuforums.org/member.php?u=810873").....i tried the tutorial in the link u provided....everything went fine until the unpacking of php5-sqlite was goin....the following is what occured:
>
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  php5-sqlite 
0 packages upgraded, 1 newly installed, 0 to remove and 254 not upgraded.
Need to get 34.8kB of archives. After unpacking 152kB will be used.
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main php5-sqlite 5.2.6.dfsg.1-3ubuntu4.2 [34.8kB]
Fetched 34.8kB in 5s (6063B/s)      
Selecting previously deselected package php5-sqlite.
(Reading database ... 105657 files and directories currently installed.)
Unpacking php5-sqlite (from .../php5-sqlite_5.2.6.dfsg.1-3ubuntu4.2_i386.deb) ...
Setting up php5-sqlite (5.2.6.dfsg.1-3ubuntu4.2) ...

E: Directory '/var/log/apt/' missing
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

I tried checking in the browser as told in the tut but I got the same oage load error...
__

---

### Post by mac9416 on 2009-10-09
Found this fix here: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239)

> Putting this in "/etc/gdm/Init/Default" seems to have the right effect for me:
```
### Fix that bloody apt error! ###
mkdir -p /var/log/apt/
exit 0
```


And another from the same place:

> 
Confirm this bug when using /var/log as tmpfs on asus eee pc:
tmpfs /var/log tmpfs defaults 0 0

adding the line at end of /etc/fstab
tmpfs /var/log/apt tmpfs defaults 0 0
helps me.


Someone also wrote a patch and gives instructions on how to install it at that link, but it seems like too much monkeying around to recommend you try it. :)

---

### Post by bubblehead74 on 2009-10-09
I think your aptitude does not work. I found the following to your issue. The var/log error may prevent Apache from starting. I am afraid I cannot help you with this, sorry:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239")

---

### Post by whathaveugot on 2009-10-09
> **mac9416 said:**
> Found this fix here: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/220239)



And another from the same place:



Someone also wrote a patch and gives instructions on how to install it at that link, but it seems like too much monkeying around to recommend you try it. :)

I did this, then fired up all the commands that have popped up in this discussion....

sudo aptitude install apache2 php5sudo aptitude install apache2 php5 php5-sqlite

sudo tasksel install lamp-server

sudo dpkg --configure -a

but...everything just showing "....Done" and tht's it....I just cant get an output in firefox....reckon I've to downld those damn sources from the apache n php website and then compile and install them....now, I dont know how do I remove whatever is installed...:(

---

### Post by bubblehead74 on 2009-10-09
Try to start Apache manually:
```
sudo /etc/init.d/apache2 start
```

Also clear Firefox Cache, close it and start it again. Go to [http://localhost](http://localhost) again.

---

### Post by whathaveugot on 2009-10-10
> **bubblehead74 said:**
> Try to start Apache manually:
```
sudo /etc/init.d/apache2 start
```Also clear Firefox Cache, close it and start it again. Go to [http://localhost](http://localhost) again.

@[bubblehead74]("http://ubuntuforums.org/member.php?u=810873")...this wont work...the message is: 

__ [B]* Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

(2)No such file or directory: apache2: could not open error log file /var/log/apache2/error.log.

Unable to open logs

[/B]anyways, could you tell me how can I remove whatever has been installed in my system, coz I got a way around from a book about APACHE/PHP/MYSQL....just lemme knw how it works...

I'll try that way and post the method here if it works.

Cheers

---

### Post by mac9416 on 2009-10-10
Sorry it didn't work. This should remove what you've installed in this process...

```
$ sudo tasksel remove lamp-server
$ sudo aptitude remove apache2 php5 php5sudo php5-sqlite
```

It appears that you've encountered a somewhat rare /var/logs/ problem that no one has a good solution to yet. I hope you're able to get LAMP installed and working. Good luck!

---

### Post by fourbit on 2009-10-11
Whathaveyougot,

I am trying to install lamp through tasksel and came up with that same error. I found that I still had my synaptic package running. I closed that and ran the command 
sudo dpkg --configure -a (not sure if I needed too)

But, then I tried the tasksel command again and it's downloading as we speak.

Paul

Installed and running. But, doesn't know what to do with php file. :(

---

### Post by metvsmet on 2009-10-11
> **whathaveugot said:**
> hi folks,

this is my first post so a big HELLO to all linux geeks :)

I was just wondering whether there's a way to set up apache web server with php support in ubuntu netbook remix 9.04.

You reckon u can help?

Cheers.

Installing Lamp on Ubuntu, best tutorial:
[http://rslinux.wordpress.com/2009/10/11/installing-lamp-on-ubuntu/](http://rslinux.wordpress.com/2009/10/11/installing-lamp-on-ubuntu/)

---

### Post by whathaveugot on 2009-10-12
@fourbit...I got Apache/PHP with SQLite installed finally and it's working wonder! :) 

I got this way out from the book "Beginning PHP 5 and MySQL 5 From Novice to Pro" (2nd Ed) by W. Jason Gilmore.

Downloaded the sources from Apache and PHP's websites and followed the steps given by Jason to compile them followed by installation. It worked like cream!!!!! you can download it from this esnips link:[http://www.esnips.com/web/aj-pub](http://www.esnips.com/web/aj-pub)

@metvsmet....thanks heaps (anyways ;)) dude!!!

Cheers.

---

### Post by maxadocious on 2009-10-28
OMG!

This is the perfect thread for me. I've been looking for something just like this as I've been going through hell getting LAMP going on my netbook. I'm making a database for local access for my work, and I've been using a free webhost up to now.

Hopefully I can get it to work following the advice presented in here.

I do have a question though:

would it be better for me to un-install all of the stuff I've downloaded already for LAMP and start again following one of these guides?

thx

---

### Post by whathaveugot on 2009-10-30
> **maxadocious said:**
> OMG!

This is the perfect thread for me. I've been looking for something just like this as I've been going through hell getting LAMP going on my netbook. I'm making a database for local access for my work, and I've been using a free webhost up to now.

Hopefully I can get it to work following the advice presented in here.

I do have a question though:

would it be better for me to un-install all of the stuff I've downloaded already for LAMP and start again following one of these guides?

thx

tht's really upto you mate.

---

