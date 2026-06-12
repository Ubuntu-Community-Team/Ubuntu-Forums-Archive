---
title: "New to linux/Ubuntu/GNOME"
date: 2006-04-06
forum: General Help
---

### Post by jdm2 on 2006-04-06
I'm new to all of the things metioned in the title and I need some help getting started.  Here are the things I want to do with my linux box:
Learn Linux
Samba server"getting access to printers and windows shared folders"
Apache server"basicly a forum"
Mysql server"Somebody said I needed it"
ssh server"windows to linux"aka remote login
getting wireless card working
Change the login background
and have fun

I don't have my computer with me or my wireless card either so I can't tell you what they are but I think my wireless card is the right type that works automately or with ndiswrapper.  My whole house is wireless except for my dad's computer.  We have WEP encryption.  I'm using the Ubuntu 5.10.  

Can anybody help me out?  Thanks

P.S.  Do I need to know any lanauge for the apache server?  

Thanks

---

### Post by Herman on 2006-04-06
Welcome, jdm2, 
The good people who are busy edititng the Official Ubuntu Wiki are doing a wonderful job, and that would be the best place to begin.
There is a link to the 'FrontPage' of the Wiki at the top of every Ubuntu Forum page, but they should make it brighter or blinking or something so it will attract more attention.
[LEFT]From the FrontPage you can either scroll down to links or click[LIST]
[*]User documentation[/LIST]or use the the search box in the top left corner. The Wiki is gettting better every day and even well seasoned Ubuntu users might find something new in it if they go and check it again, I know I did yesterday.

Here are some links that might help also:
Learn Linux: 
[CENTER][http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide]("http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User%27s_Guide")[/CENTER]
    [CENTER][http://www.linuxcommand.org]("http://www.linuxcommand.org/")[/CENTER]
    [CENTER][http://www.linux.org/lessons/]("http://www.linux.org/lessons/")[/CENTER]
   [CENTER][http://www.ee.surrey.ac.uk/Teaching/Unix/]("http://www.ee.surrey.ac.uk/Teaching/Unix/")
[LEFT]ssh server:         [http://www.users.bigpond.net.au/hermanzone/p11.htm]("http://www.users.bigpond.net.au/hermanzone/p11.htm")

I am not the best person to advise you on those other subjects, so I'll just leave those for somone else to answer. 
All the best, :D (Herman)
[/LEFT]
  [/CENTER]
  [/LEFT]

---

### Post by jdm2 on 2006-04-06
Thank you for the help and links.  I will check them out tonight or tommorrow.

---

### Post by cskeide on 2006-04-06
I'll just list what packages to install to get the different things working. You can install these packages through the terminal, or by using synaptic.

- Samba server"getting access to printers and windows shared folders"
samba
smbfs
After installing these packages you should be able to browse the windows network through "Places -> Network Servers".

- Apache server"basicly a forum"
apache or apache2
phpbb2

- Mysql server"Somebody said I needed it"
mysql-server

- ssh server"windows to linux"aka remote login
openssh-server

- Change the login background
to change the login background, go to:
System -> Administration -> Login Screen Setup

---

### Post by Jedeye on 2006-04-06
The Ubuntu guide was and still is very helpfull for me [http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by jdm2 on 2006-04-06
Thanks for the list of package and the links.  I have checked out the ones posted before and they look very helpful.  I will read them this weeken.

---

### Post by drberg1000 on 2006-04-07
[QUOTE=jdm2]Thanks for the list of package and the links.  I have checked out the ones posted before and they look very helpful.  I will read them this weeken.[/QUOTE]

There is also some very good documentation at [http://www.us.debian.org/doc/](http://www.us.debian.org/doc/) though most of it is geared towards a system administrator as opposed to an end user.  Since Ubuntu is derived from Debian most of the instructions can be applied with minimal or no changes.


--Dave

---

### Post by jdm2 on 2006-04-08
What do I need to know to run a web server.  I want to have 1-2 pages and I really want to start a message board.  Can you help me out.  Thanks

---

### Post by nanotube on 2006-04-08
for web serving and message board, you might be better off just getting some free webspace somewhere. it's not worth the trouble for just a coupla pages.
(unless you just want to learn how to do that stuff for its own sake).

---

### Post by adamkane on 2006-04-08
> Apache server"basicly a forum"
> Mysql server"Somebody said I needed it"

Install Apache2 + MySQL4 + PHP4 + phpmyadmin. See:
[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

> ssh server"windows to linux"aka remote login

Install ssh with Synaptic. SSH is very easy to use. Use Terminal to connect remotely in Linux. Use PuTTY to connect using Windows:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")
[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe")

> getting wireless card working

Dapper has significant better support for wireless.

> Change the login background
> and have fun.

Eye Candy:
[http://www.ubuntuforums.org/showthread.php?t=77694]("http://www.ubuntuforums.org/showthread.php?t=77694")

Gnome Art:
[http://art.gnome.org/]("http://art.gnome.org/")

Gnome Look:
[http://www.gnome-look.org/]("http://www.gnome-look.org/")

 Composite manager guide:
 [http://www.ubuntuforums.org/showthread.php?t=75527]("http://www.ubuntuforums.org/showthread.php?t=75527")

Knome guide:
[http://ubuntuforums.org/showthread.php?t=115974]("http://ubuntuforums.org/showthread.php?t=115974")

Gnome-ish QT guide:
 [http://ubuntuforums.org/showthread.php?t=76633]("http://ubuntuforums.org/showthread.php?t=76633")

---

### Post by jdm2 on 2006-04-09
I want to learn it.  What lanague do I need to know for I can do this?

---

### Post by adamkane on 2006-04-09
This is a controversial issue. Everyone has a different opinion.

Learn Bash scripting for Linux/Ubuntu. You can also learn Python or Perl scripting.

Learn PHP scripting for Apache/MySQL. You can also learn Ruby, Python and Java scripting.

Python is strongly promoted by Ubuntu enthusiasts.

---

### Post by trent dillman on 2006-04-09
Oh, and make sure to bone up on security before going public. You don't want to get hacked by some lame-o script kiddie!

---

### Post by jdm2 on 2006-04-09
Thanks for the tip.  So I really need to know PHP for apache.  Does anybody know of a site where I can read about PHP and message boards with apache?  Thanks

Also I'm kinda confused on the login splash screen.  I check out those links you gave me and saw some nice looking splashes but they only had a username in put.  When I  download them how will it work.  Will I just be downloading the picture or will they have it set up like the picture is?  Thanks

---

### Post by adamkane on 2006-04-09
PHP allows Apache to grab information from MySQL. PHP or another scripting language is essential to use Apache with MySQL.

Reading room:
[http://safari.oreilly.com/]("http://safari.oreilly.com/")

Read anything from O'Reilly. I find PHP Hacks very easy and useful.

---

### Post by Snocrash on 2006-04-09
phpbb is a great message board server for apache and Mysql. It requires a little setup to get working, but it is well worth the time to learn it. Themes, avatars, sigs, it's all there. I have used it alot in the past for gaming or group boards. And there is plenty of documentation on it.

[http://www.phpbb.com/]("http://www.phpbb.com/")

-Sno

---

### Post by jdm2 on 2006-04-09
Thanks
Do I need MySQL or not?

---

### Post by Snocrash on 2006-04-09
Yes....MySQL is the database that actually holds all the tables and threads etc. It needs to be installed, configured and running for phpbb to work. They have a pretty good howto for set it up. I also suggest mysqladmin for a graphical MySQL admin tool.

-Sno

---

### Post by jdm2 on 2006-04-09
Thanks

---

### Post by adamkane on 2006-04-09
How to install Apache + PHP + MySQL + phpmyadmin:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by jdm2 on 2006-04-10
Thanks for the link.

---

### Post by jdm2 on 2006-04-13
I'm going to try and go help the people that are working on my system tomorrow since I'm off tomorrow.  What are the commands I can use to gather info and ost it here for help.  They are having sound problems and I'm got a wireless card in there too.  Can you help me?  Thanks

---

### Post by jdm2 on 2006-04-18
I don't remeber if I told you this but I was think of doing wireless internet but I have talk my dad into letting me run a cable through the wall so it will be hook up as the following.  Hooked into the pc and then the other end will be hooked into my router.  Will that work out fine?  Thanks

---

