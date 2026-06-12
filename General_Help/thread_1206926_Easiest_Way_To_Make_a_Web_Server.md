---
title: "Easiest Way To Make a Web Server?"
date: 2009-07-07
forum: General Help
---

### Post by antdgar on 2009-07-07
Hi,  I have just got a life-time unlimited 100mbit server, and I have no idea what to use it for. Slow processor though, Intel celeron D, 1GB RAM. Not the power house :P   ||||||||||||||||||||||||||||||||||||||||||||||| So, I want to make a website, and host in on there. Just a small one..  nginx seems too difficult and lacks documentation. I'm a linux noob.  Any simple way to create my own webserver and build a website onto it? GUI please :P

---

### Post by sshannin on 2009-07-07
I would very strongly recommend the Apache webserver.  Although it does not have any gui support that I know of, apache is by far the most common web server and is very easy to set up.

The link below explains how to install and set it up in a very straightforward manner.
[http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html)

---

### Post by sedawk on 2009-07-07
If you install apache2 package ("sudo apt-get install apache2")
and start apache2 (once manually with "sudo apache2ctl start")
you have a running web server with a simple default start page.

The next (optional) step would be to make ssh connection to
your server work from your laptop or desktop. Then you
can create and test web pages locally and if they work you
transfer changes from you local web directory to the web
server (rsync over ssh)

There are different ways to design your web pages:
* learn html and then use a text editor (vi,emacs) or a
  web designer like quanta plus.
* I do not know of a non-commercial web design tool that 
  works without learning html.
* Some tools (like your word processor, latex, ...) can export html, so
  you can try to create web pages by creating a non-web document and 
  then export it to html.
* Many people like wordpress - many blogs are created with
  wordpress. Have a look at wordpress (doesn't require html knowledge
  but needs some time for setup).

---

### Post by rbishop on 2009-07-07
Best guides are found all over the web....but I like to use [http://www.howtoforge.com](http://www.howtoforge.com).   They have a good wealth of information to pull from.

---

### Post by Jebtrix on 2009-07-07
> **rbishop said:**
> Best guides are found all over the web....but I like to use [http://www.howtoforge.com](http://www.howtoforge.com).   They have a good wealth of information to pull from.

+1

[http://www.howtoforge.com/set-up-ubuntu-server-with-ehcp-lamp-dns-ftp-mail](http://www.howtoforge.com/set-up-ubuntu-server-with-ehcp-lamp-dns-ftp-mail)

---

### Post by antdgar on 2009-07-08
But how do I put my domain name in there? When I try to open httpd.conf it seems to be a blank document.

Very tempted to install Windows on this server. Could probably have a web server up in 20 mins...

---

### Post by georgerobbo on 2009-07-08
It very much depends. If your looking for just the simple website, no advanced serverside scripting etc then you can just go for a version of linux such as Ubuntu Server, install LAMP (Linux Apache MySQL PHP) and then a publishing tool such as WordPress.
 
But if you want to make something really advanced, I would recommend getting hold of a copy of Windows Server with IIS (Internet Information Services), ASP.net and MS SQL and really pull out all the stops. 
 
ASP.net is light years ahead of PHP.

---

### Post by degarb on 2010-12-11
This thread really did not answer question, so I must revive.  I think he wants a package that installs with a click, and just point it to a directory to serve.  Done, and go about other business.  1 minute or less.  

The perfect example of a well done server is downstairs.dnsalias.net , except windows only.  I googled it, installed it, and up in running, all in about 1 to 5 minutes or less.  I did need to port forward on router, which took more time, since I had a hard time finding someone that could describe the meaning of port forwarding in a sentence until I found it logically explained in one sentence by a user in yahoo answers.  

So, if there is a good 1 minute server not available for current version of Ubuntu, then let me use the apache what is the htdocs folder to change, how do you open up the port?  (Just pray we don't have to configure anything in apache, cause I, and probably most readers here, lack any ability to read that file)

---

### Post by drdos2006 on 2010-12-11
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood



This is how my web server runs at home....
regards

---

### Post by degarb on 2010-12-11
> **drdos2006 said:**
> Here is a HOWTO which I found comprehensive and invaluable.


This is how my web server runs at home....
regards

Looks like this is pro approach.

I quit reading after realizing this was an entire OS install. I have an OS running and took two days getting belkin card to work; I know it would take same time to reproduce and install on another UBU. I just have online business card and get 4 legit hits per month,  so senseless to run anything other than a program that serves web pages.  

I installed lamp but no idea where it went.  I installed abyssws, but not working serving pages and no good trouble shoot.  I installed apache a while back but can make no head nor tails from the pages or config, so uninstalled it. 

We are looking for a straight forward few hundred k product that works without hours of manuals.

---

### Post by tekkidd on 2010-12-11
Firstly i would use Debian Lenny or Lucid Server. Then on top of that I would install Apache web server and Webmin for system administration. A desktop is up to you but i run my servers headless. Lastly if you want to host the site to computers outside your network you will need to forward the port that apache is on. All in all its nothing to hard.

---

### Post by degarb on 2010-12-12
> **tekkidd said:**
> Firstly i would use Debian Lenny or Lucid Server. Then on top of that I would install Apache web server and Webmin for system administration. A desktop is up to you but i run my servers headless. Lastly if you want to host the site to computers outside your network you will need to forward the port that apache is on. All in all its nothing to hard.

I figured out that the problem was with Ubuntu.  It closes off ports below 1024 or so, if the program isn't run in superuser mode.  

Of course, I must now manually start it, and enter the password each reboot, which sucks.  Since, wife and kid won't do this if I am not home.  I am a noob and have yet to figure out how to auto start something in super user mode.  In fact, I have no clue what noob means or its origin.

Again, apache refuses to download and I am really turned off by the ini.  I tried it before with no luck, and feel strongly that it had a really too complicated ini file to mess with.  Well, designed programs are designed to obviate support requests.  There are ways to hide the power, while making things just work for the noobs.  Whatever the hell that word means.

---

### Post by HermanAB on 2010-12-12
OK, so you want to know what is the Easiest way to make a web server:  Install OpenSuse and click LAMP Server in the installation wizard.

Ubuntu is not the easiest Linux.  It is the most fun Linux.

---

### Post by degarb on 2010-12-13
> **HermanAB said:**
> OK, so you want to know what is the Easiest way to make a web server:  Install OpenSuse and click LAMP Server in the installation wizard.

Ubuntu is not the easiest Linux.  It is the most fun Linux.

I love the community here too much.  The core philosophy also resonates with me too much

I installed lamp from the repo, but couldn't find it in any of the menus.  I ran lamp from the terminal, but nothing graphical or configurable.  So, I uninstalled it.  Obviously, I would need to research it more to use it.  Still, it would need to be run sudo style.

Abyss failed to mention sudo in manual, so it took overnight and a few hours to crack. Abyss, is easy and straight forward.  I haven't found stats, like on my xp server, yet.

---

