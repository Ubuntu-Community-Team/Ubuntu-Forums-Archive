---
title: "web server"
date: 2010-01-18
forum: General Help
---

### Post by willazilla on 2010-01-18
I have inadvertantly enabled a different web server than Apache. And, have no idea how I did that or how to undo. Now I cannot access my localhost.:(

---

### Post by junapp on 2010-01-18
how do you know you enabled a different web server? which one? what happens when you 
```

sudo /etc/init.d/apache2 restart

```

---

### Post by willazilla on 2010-01-18
I enter 
root@willa-laptop:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
root@willa-laptop:~# 

When I enter your suggestion, I get:

root@willa-laptop:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@willa-laptop:~#

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> I enter 
root@willa-laptop:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
root@willa-laptop:~# 

When I enter your suggestion, I get:

root@willa-laptop:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@willa-laptop:~#

this does not indicate that you have a different web server running.

add 
```

ServerName "yourserverhostnamehere"

```

to /etc/apache2/httpd.conf

then the message will go away about the FQDN

---

### Post by lisati on 2010-01-18
> **willazilla said:**
> 
When I enter your suggestion, I get:
> 
root@willa-laptop:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@willa-laptop:~#

As I understand it, this isn't a serious "error". Let us know how you get on with pirateghost's suggestion.

---

### Post by willazilla on 2010-01-18
I'm really sorry (yes really) for being such a dummy. But, this can't be correct:

root@willa-laptop:~# /etc/apache2/httpd.conf ServerName localhost

because I'm getting: bash: /etc/apache2/httpd.conf: Permission denied

---

### Post by junapp on 2010-01-18
and if you browse to [http://localhost](http://localhost) what happens. It looks like apache is starting up, and nothing else is listening on its configured port (or you should see an error saying something else is listening on its port).

---

### Post by lisati on 2010-01-18
> **willazilla said:**
> I'm really sorry (yes really) for being such a dummy. But, this can't be correct:

root@willa-laptop:~# /etc/apache2/httpd.conf ServerName localhost

because I'm getting: bash: /etc/apache2/httpd.conf: Permission denied

You need to edit the file, e.g. ```
sudo nano /etc/apache2/httpd.conf
``` and then add the line about the server name

---

### Post by junapp on 2010-01-18
you probably want to edit /etc/apache2/sites-enabled/default, and amend the ServerName directive there instead of httpd.conf. There is a bit of difference in the way debian sets stuff up. Look to the 
/usr/share/doc/apache2/README.Debian.gz
file for the documentation and file structure.

---

### Post by willazilla on 2010-01-18
Actually, You are right Junapp! The path to localhost says "It Works!" Yay. I think. So, does that mean I've hosed something else?

---

### Post by junapp on 2010-01-18
I doubt it. I'd suspect that the XAMPP script is just telling you that apache is already running. Bit of a guess there - I've always set up everything individually, not all all that familar with the scripts that do it all for you in a single go.

---

### Post by willazilla on 2010-01-18
The way that I accidently hosed whatever it is I hosed was because I was trying to fix the fact that my ability to extract files mysteriously went away Saturday morning. So, I am unable to go to the link you suggest, the one ending in .gz.

---

### Post by junapp on 2010-01-18
you could go to a terminal and type
vi /usr/share/doc/apache2/README.Debian.gz

vi is a bit of thing to get used to. Use your arrow keys to go up and down to scroll through the file. To exit, hit the escape key and type 
:q!

---

### Post by junapp on 2010-01-18
that file
[http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz](http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz)

---

### Post by pirateghost on 2010-01-18
> **junapp said:**
> you probably want to edit /etc/apache2/sites-enabled/default, and amend the ServerName directive there instead of httpd.conf. There is a bit of difference in the way debian sets stuff up. Look to the 
/usr/share/doc/apache2/README.Debian.gz
file for the documentation and file structure.


editing the httpd.conf is the debian way to resolve this exact issue.

---

### Post by willazilla on 2010-01-18
> **lisati said:**
> You need to edit the file, e.g. ```
sudo nano /etc/apache2/httpd.conf
``` and then add the line about the server name

I found this file and edited it at:

# Include all the user configurations:
Include /etc/apache2/httpd.conf ServerName localhost

But still no localhost.

---

### Post by lisati on 2010-01-18
> **pirateghost said:**
> editing the httpd.conf is the debian way to resolve this exact issue.

I'd seen something about that somewhere but couldn't remember the link.

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> I found this file and edited it at:

# Include all the user configurations:
Include /etc/apache2/httpd.conf ServerName localhost

But still no localhost.

no, you are editing the apache2.conf file there.....

edit the /etc/apache2/httpd.conf FILE directly...if it isnt there then XAMPP does something different with its filestructures, which does NOT follow Debian standards....

---

### Post by willazilla on 2010-01-18
Did I mention how wonderful you all are? Thank you so very much for staying with me on this. I am on the edge of a launch and having this issue with my localhost is a huge bad. So, please know that you are very appreciated by me. :D

---

### Post by junapp on 2010-01-18
> **pirateghost said:**
> editing the httpd.conf is the debian way to resolve this exact issue.
Oh. I was following the documentation provided in the path referenced. 
Also, I was using the section titled "Debian, Ubuntu (Apache 2):" at:
[http://wiki.apache.org/httpd/DistrosDefaultLayout#Apache_2.2_default_layout_.28apache.org_source_package.29:](http://wiki.apache.org/httpd/DistrosDefaultLayout#Apache_2.2_default_layout_.28apache.org_source_package.29:)

Well for what it is worth willazilla, it might be worthwhile seeing where it is already set, then changing the default value. I would do that with 
```

grep -ir servername /etc/apache2/*

```This should list the files where servername is used. I suspect it will be in the places you tried, which I think you should undo, then change it in the 
/etc/apache2/sites-available/default

It should be on a line by itself in order to set the directive correctly.

---

### Post by pirateghost on 2010-01-18
> **junapp said:**
> Oh. I was following the documentation provided in the path referenced. 
Also, I was using the section titled "Debian, Ubuntu (Apache 2):" at:
[http://wiki.apache.org/httpd/DistrosDefaultLayout#Apache_2.2_default_layout_.28apache.org_source_package.29:](http://wiki.apache.org/httpd/DistrosDefaultLayout#Apache_2.2_default_layout_.28apache.org_source_package.29:)

Well for what it is worth willazilla, it might be worthwhile seeing where it is already set, then changing the default value. I would do that with 
```

grep -ir servername /etc/apache2/*

```This should list the files where servername is used. I suspect it will be in the places you tried, which I think you should undo, then change it in the 
/etc/apache2/sites-available/default

It should be on a line by itself in order to set the directive correctly.


i understand you reading those docs and thinking so, but on every single debian system i have, and the few ubuntu systems i have, on a default apache2 install, there is a file located in /etc/apache2 called httpd.conf

when i first ran into that same exact error the OP was getting, all the debian documentation i found stated exactly what i suggested to the OP.  just sharing my experiences.  i have been running debian webservers for years....

---

### Post by willazilla on 2010-01-18
Terrific! Here's the list:

~# grep -ir servername /etc/apache2/*
/etc/apache2/apache2.conf:Include /etc/apache2/httpd.conf ServerName localhost
/etc/apache2/mods-available/info.conf:#  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
/etc/apache2/mods-available/status.conf:# with the URL of [http://servername/server-status](http://servername/server-status)
/etc/apache2/mods-enabled/status.conf:# with the URL of [http://servername/server-status](http://servername/server-status)

I found the httpd.conf file in 2 locations, and changed it in both as: 

#ServerName [www.example.com:80](www.example.com:80)
# XAMPP
ServerName localhost

So it's odd that only one is being listed - the one in the root as opposed to /opt/lampp .... Then again, this is all odd to me.

Adding the server name did not bring back my local host. So, I will revert that change.

---

### Post by junapp on 2010-01-18
yes, that httpd.conf file exists, but by default it is empty (and I think back around breezy it actually had a notice that it was best to leave it empty), and it is my understanding that it is there for historical reasons so that all that documentation for other distros will work.

The thing to note is that httpd.conf is included by apache2.conf so it really makes no difference where you set it (apache2.conf/httpd.conf/default), except if you get into using virtual hosts (as I understand it) in which case I think setting it in the virtual host files makes sense.  Then again, if you don't like the multiple files for virtual hosts, you can have all your virtual hosts right inline with apache2.conf (or httpd.conf for that matter).

---

### Post by junapp on 2010-01-18
> **willazilla said:**
> 
/etc/apache2/apache2.conf:Include /etc/apache2/httpd.conf ServerName localhost

I think pirateghost will agree that that line in /etc/apache2/apache2.conf needs to be changed to:
```
Include /etc/apache2/httpd.conf 
```

and place
```
ServerName localhost
```

either on the line after that include, or in /etc/apache2/httpd.conf.

---

### Post by pirateghost on 2010-01-18
> **junapp said:**
> yes, that httpd.conf file exists, but by default it is empty (and I think back around breezy it actually had a notice that it was best to leave it empty), and it is my understanding that it is there for historical reasons so that all that documentation for other distros will work.

The thing to note is that httpd.conf is included by apache2.conf so it really makes no difference where you set it (apache2.conf/httpd.conf/default), except if you get into using virtual hosts (as I understand it) in which case I think setting it in the virtual host files makes sense.  Then again, if you don't like the multiple files for virtual hosts, you can have all your virtual hosts right inline with apache2.conf (or httpd.conf for that matter).


true, but i actually prefer to keep all my virtual hosts in one file /etc/apache2/vhosts.conf and have the apache.conf file call on it.  adding more to the already cluttered apache2.conf file seems ridiculous to me.  i prefer to keep my .conf files separated for ease of use.  i typically edit the apache2.conf file to suit a generic need of mine, and have it call on other conf files for the remainder of the configurations.  when something breaks, i can very easily go in and edit the small config files i have set up.  i would rather have 10 conf files with set directives (and labeled as to their function) than to have one big config to have to sift through every time i need to change something

---

### Post by pirateghost on 2010-01-18
> **junapp said:**
> I think pirateghost will agree that that line in /etc/apache2/apache2.conf needs to be changed to:
```
Include /etc/apache2/httpd.conf 
```and place
```
ServerName localhost
```either on the line after that include, or in /etc/apache2/httpd.conf.


absolutely  :D

---

### Post by junapp on 2010-01-18
> **willazilla said:**
> 
I found the httpd.conf file in 2 locations, and changed it in both as: 
...
So it's odd that only one is being listed - the one in the root as opposed to /opt/lampp .... 

try 
```

grep -ir servername /opt/lampp/*

```

---

### Post by junapp on 2010-01-18
> **pirateghost said:**
> ... would rather have 10 conf files with set directives (and labeled as to their function) than to have one big config to have to sift through every time i need to change something
I believe that's why sites-available/sites-enabled, mods-available/mods-enabled and a2ensite, a2dissite, a2enmod, a2dismod were created.

---

### Post by pirateghost on 2010-01-18
> **junapp said:**
> I believe that's why sites-available/sites-enabled, mods-available/mods-enabled and a2ensite, a2dissite, a2enmod, a2dismod were created.
yep.  but when you run 10 different virtual hosts on one server, editing each and every file in sites-available gets to be a pain in the ****.  if i were running one site, i would just modify the default listed in sites-available

the beauty of linux=we can all have our own way of getting the same task accomplished
the downfall of linux=we can all have our own way of getting the same task accomplished

---

### Post by willazilla on 2010-01-18
The file at etc/apache2/httpd.conf is indeed completely empty. But, placing the directive in apache2.conf (as below) did not bring back my local host. 

# Include all the user configurations:

Include /etc/apache2/httpd.conf 

ServerName localhost

# Include ports listing
Include /etc/apache2/ports.conf

#

---

### Post by junapp on 2010-01-18
okay. back to your question. when you 
```

sudo /etc/init.d/apache2 restart

```
what happens - what errors if any do you see?

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> The file at etc/apache2/httpd.conf is indeed completely empty. But, placing the directive in apache2.conf (as below) did not bring back my local host. 

# Include all the user configurations:

Include /etc/apache2/httpd.conf 

ServerName localhost

# Include ports listing
Include /etc/apache2/ports.conf

#


i think you are getting confused.

the file httpd.conf is where you would put the servername - edit THAT file, get rid of it from your apache2.conf.  your apache2.conf file is referencing the httpd.conf file from the line 
```
Include /etc/apache2/httpd.conf
```
leave that line in there and delete the servername line

after you have saved it, run:

sudo /etc/init.d/apache2 force-reload

---

### Post by willazilla on 2010-01-18
> **junapp said:**
> okay. back to your question. when you 
```

sudo /etc/init.d/apache2 restart

```what happens - what errors if any do you see?

No errors, but clearing my browser cache and refreshing, I still do not get my web site.

The requested URL /bcm_drupal/ was not found on this server.
  Apache/2.2.11 (Ubuntu) Server at localhost Port 80

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> No errors, but clearing my browser cache and refreshing, I still do not get my web site.

The requested URL /bcm_drupal/ was not found on this server.
  Apache/2.2.11 (Ubuntu) Server at localhost Port 80
that sounds like a drupal configuration issue.  if you are getting an error from apache, then apache is running properly and you need to have a look at your drupal config

---

### Post by willazilla on 2010-01-18
> **pirateghost said:**
> i think you are getting confused.

the file httpd.conf is where you would put the servername - edit THAT file, get rid of it from your apache2.conf.  your apache2.conf file is referencing the httpd.conf file from the line 
```
Include /etc/apache2/httpd.conf
```leave that line in there and delete the servername line

after you have saved it, run:

sudo /etc/init.d/apache2 force-reload

Totally confused! The httpf.conf file is completely empty. You are suggesting to remove the directive : 

ServerName localhost 

from the apache2.conf (as you suggested I place it there a post or so back) and place it in a completely empty file?

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> Totally confused! The httpf.conf file is completely empty. You are suggesting to remove the directive : 

ServerName localhost 

from the apache2.conf (as you suggested I place it there a post or so back) and place it in a completely empty file?
i told you to put that directive IN httpd.conf which is empty already (this would make your servername directive the only one in that file).  if you are not getting any errors with it in apache2.conf then leave it there.  from your previous posts it seems that you were just appending the line in apache2.conf
```
Include /etc/apache2/httpd.conf
```
with
```
Include /etc/apache2/httpd.conf ServerName "localhost"
```
which makes a HUGE difference

i was asking you to add the servername directive TO httpd.conf, not added to the line in apache2.conf that contains the filename...big difference.

like i said, if there are no errors with the directive currently located in apache2.conf, then leave it alone there.  your problems stem from a bad drupal configuration at this point.

---

### Post by willazilla on 2010-01-18
Is a localhost in the same category as virtual host? And, again, please forgive my lack of expertise in this area. I really appreciate the help you are providing.

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> Is a localhost in the same category as virtual host? And, again, please forgive my lack of expertise in this area. I really appreciate the help you are providing.
[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)
[http://en.wikipedia.org/wiki/Virtual_hosting](http://en.wikipedia.org/wiki/Virtual_hosting)

in terminal type
```
hostname
```

the hostname that it spits out at you should be used as your servername directive

basically localhost is 'this computer', so essentially you are not using IP addresses, or real hostnames at this point, this takes possible DNS issues out of the way since you are connecting to 'this computer'
localhost is the same as using the IP 127.0.0.1


you can have as many virtualhosts as you want in your apache setup

dont confuse the 2, localhost and virtualhosts are in different leagues altogether....

---

### Post by willazilla on 2010-01-18
After all of the help I received, and advice I've followed, I am still getting the message:

root@willa-laptop:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
root@willa-laptop:~# 

I have started and restarted my server a zillion times over the past few months, and if Apache were still running, it would say "XAMPP: Apache is already running. ..."

So, I can't help but wonder if that is at the root of this problem. How do I get the answer to the question "what server or service is running?" on my computer at the moment from the terminal window?

---

### Post by pirateghost on 2010-01-18
```
sudo apt-get install htop
```
after it is installed
```
htop
```

you should see user www-data listed and command /usr/sbin/apache2 -k start listed.  that would indicate it is running.

it seems to me that regular apache is running instead of the version that XAMPP is using

i have to ask, though, why run XAMPP?  it would be more beneficial to you to learn how to set up apache, mysql, and php by hand....

---

### Post by willazilla on 2010-01-18
None of the things you say should be listed are listed. As I mentioned earlier, I am trying to launch a web site for a non-profit that is really patient, but ... To resolve my immediate issue, I need to understand how to fix XAMPP. Given that scenario, should I re-install XAMPP?  Thank you!


  1  [|||                                                             3.3%]     Tasks: 242 total, 1 running
  2  [||||||                                                          6.8%]     Load average: 1.34 1.23 1.14 
  Mem[||||||||||||||||||||||||||||||||||||||||||||||||||||||||||624/2894MB]     Uptime: 04:37:08
  Swp[|                                                           0/1499MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 4359 root      20   0  462M  102M 22968 S  5.0  3.5 14:35.61 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
13354 root      20   0  2604  1308   964 R  2.0  0.0  0:04.75 htop
 5886 root      20   0 34900 15480  9700 S  1.0  0.5  0:08.69 gnome-terminal
 4838 root      20   0 16652  2952  1784 S  1.0  0.1  1:01.59 gnome-screensaver
 2615 root      20   0  5180  1912  1696 D  0.0  0.1  0:02.15 hald-addon-storage: polling /dev/sr0 (every 2 sec)
 4631 root      20   0 28976 20868  8028 S  0.0  0.7  0:46.63 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id 1036a
10154 nobody    39  19  264M 27640  4328 S  0.0  0.9  0:00.42 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-
 4722 root      20   0 22000  8876  7336 S  0.0  0.3  1:18.06 /usr/lib/gnome-applets/geyes_applet2 --oaf-activate-iid=OAFIID:GNOME_GeyesApplet_Factory --oaf-
 5467 root      20   0  198M 80008 25120 S  0.0  2.7  0:17.76 /usr/lib/firefox-3.0.17/firefox
 2473 haldaemo  20   0  6668  4664  3876 S  0.0  0.2  0:04.33 /usr/sbin/hald
 2698 root      20   0 16428  2848  2292 S  0.0  0.1  0:05.33 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
10150 nobody    20   0  264M 27640  4328 S  0.0  0.9  0:01.81 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-
10148 nobody    20   0  264M 27640  4328 S  0.0  0.9  0:01.15 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-
 2434 messageb  20   0  3080  1496   832 S  0.0  0.1  0:06.35 /bin/dbus-daemon --system
10152 nobody    39  19  264M 27640  4328 S  0.0  0.9  0:00.36 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-
 4632 root      20   0 74188 23784 14032 S  0.0  0.8  0:37.95 gnome-panel
 4764 root      20   0 20260 10612  7716 S  0.0  0.4  0:09.88 /usr/bin/gtk-window-decorator
 4534 root      20   0  7772  4644  2156 S  0.0  0.2  0:03.55 /usr/lib/libgconf2-4/gconfd-2
 4659 root      20   0 25320  9164  6264 S  0.0  0.3  0:00.64 gnome-power-manager
10147 nobody    20   0  264M 27640  4328 S  0.0  0.9  0:00.85 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-
 4649 root      20   0 23840 12800  8344 S  0.0  0.4  0:03.15 nm-applet --sm-disable
 5464 root      20   0  198M 80008 25120 S  0.0  2.7  7:38.86 /usr/lib/firefox-3.0.17/firefox
    1 root      20   0  3084  1860   564 S  0.0  0.1  0:01.29 /sbin/init
  873 root      16  -4  2224   584   316 S  0.0  0.0  0:00.08 /sbin/udevd --daemon
 2021 root      20   0 21168 18408   668 S  0.0  0.6  1:52.72 /sbin/mount.ntfs /dev/sda2 /windows -o rw,nls=utf8,umask=007,gid=46
 2267 root      20   0  1808   532   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty4
 2268 root      20   0  1808   524   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty5
 2274 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty2
 2275 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty3
 2276 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty6
 2341 root      20   0  2204  1076   556 S  0.0  0.0  0:00.00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 2386 syslog    20   0  2040   696   540 S  0.0  0.0  0:00.08 /sbin/syslogd -u syslog
 2409 root      20   0  1968   536   440 S  0.0  0.0  0:00.06 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

---

### Post by junapp on 2010-01-18
I'm sure you are getting tired of this, but hopefully learning while you go.

If you run a command like:
```

sudo netstat --tcp --udp --listening --program
```you should get a list of programs listening on particular parts. No need to post the entire output, but you may want to post the one that contains :www or :80 

For one of my machines it looks like:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:rsync                 *:*                     LISTEN      6851/rsync      
tcp        0      0 *:mysql                 *:*                     LISTEN      6526/mysqld     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      6871/smbd       
**tcp        0      0 *:www                   *:*                     LISTEN      5508/apache2  **  
tcp        0      0 *:domain                *:*                     LISTEN      5659/dnsmasq    
tcp        0      0 *:5910                  *:*                     LISTEN      6667/kvm        
tcp        0      0 *:ipp                   *:*                     LISTEN      6631/cupsd      
tcp        0      0 *:smtp                  *:*                     LISTEN      6814/master     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      6871/smbd       

```You see the www line, indicating apache is the server? What does your output look like from that command? 

As a complete aside, something like google apps might be an alternative if you are open to using something non drupal. It is pretty much free web hosting, email addresses for up to 50 or 100 people (I'm not sure what the offer is now) and a shared calendar, etc etc. Might be worth looking into.
[http://www.google.com/apps/intl/en/nonprofit/index.html](http://www.google.com/apps/intl/en/nonprofit/index.html)
[http://www.google.com/apps/intl/en/business/sites.html](http://www.google.com/apps/intl/en/business/sites.html)

[http://www.google.com/apps/intl/en/group/index.html](http://www.google.com/apps/intl/en/group/index.html)    (the free one)
use google sites to create the site once you are signed up. It is free.

---

### Post by willazilla on 2010-01-18
On the contrary, as long as I am making progress I love learning. And I do capture and retain the tidbits I pick up along the way. So, many thanks to you and this entire forum.

I hope you don't mind, my list isn't that long now, so here it is.

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:mysql                 *:*                     LISTEN      10140/mysqld    
tcp        0      0 *:www                   *:*                     LISTEN      12474/apache2   
tcp        0      0 localhost:ipp           *:*                     LISTEN      2750/cupsd      
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      10168/proftpd: (acc
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      2750/cupsd      
udp        0      0 *:bootpc                *:*                                 4770/dhclient   
udp        0      0 *:41813                 *:*                                 2722/avahi-daemon: 
udp        0      0 *:mdns                  *:*                                 2722/avahi-daemon: 

And, Apache is there! 

Can you tell me what the avahi is? I don't recall seeing that before. It is only as of Friday afternoon that I have been experiencing problems. Some have been resolved, but couldn't fit them all in one forum. Still wondering about my big picture, though.

---

### Post by junapp on 2010-01-18
I believe it is an auto discovery tool of some sort - looks for scanners/printers/remote desktops nearby - I could be completely wrong.  I believe ubuntu-desktop depends on it, so don't remove it, but according to:
[http://ubuntuforums.org/showpost.php?p=4596393&postcount=2](http://ubuntuforums.org/showpost.php?p=4596393&postcount=2)
you can disable it easily enough.
> **TenPlus1 said:**
> You don't really have to remove it, simply goto System -> Administration -> Services and untick Multicast DNS service discovery .. and this disables Avahi-daemon...

---

### Post by junapp on 2010-01-18
duplicate post

---

### Post by willazilla on 2010-01-18
Thanks to everyone who tried to help me today! And especially for your patience and kindness.

I am heading down the path of re-installation, though, since my issue is still looming. It is one of several that I can't nail down easily. So, off with the head of Jaunty and on to Karmic, and then on to a new XAMPP installation. Oh, and thank you for the link to [http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz](http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz) . I checked it out, and I'm sure it will come in handy at some point, just not this one.

---

### Post by pirateghost on 2010-01-18
> **willazilla said:**
> Thanks to everyone who tried to help me today! And especially for your patience and kindness.

I am heading down the path of re-installation, though, since my issue is still looming. It is one of several that I can't nail down easily. So, off with the head of Jaunty and on to Karmic, and then on to a new XAMPP installation. Oh, and thank you for the link to [http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz](http://vmlinux.org/cgi-bin/dwww/usr/share/doc/apache2/README.Debian.gz) . I checked it out, and I'm sure it will come in handy at some point, just not this one.

i definitely suspect some of the issues is XAMPP itself since it does not adhere to the same packages (apache, mysql, php) that ubuntu and debian use.  its obviously not running the daemons from the default locations and i can imagine that updates COULD cause issues when it updates apache but doesnt know that its running from another location instead

---

### Post by willazilla on 2010-01-18
Just curious, and this is way off point. 

But :) why would my archive manager stop extracting properly all of a sudden?

---

