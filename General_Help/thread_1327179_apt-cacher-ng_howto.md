---
title: "apt-cacher-ng howto"
date: 2009-11-15
forum: General Help
---

### Post by alanwalterthomas on 2009-11-15
This is how I set up apt-cacher-ng. I decided to write this out so I can remember how I did it, & because some other tutorials I tried to use had mistakes. It saves you from having to download the same package from repositories on different machines on a lan.

First install the package:
sudo apt-get install apt-cacher-ng
Then, if you need it, more documentation is available in your browser @:
file:///usr/share/doc/apt-cacher-ng/html/index.html

You'll need the server to have a static IP address on your lan. Mine's 192.168.1.100

Setup the Server:
Make a file: /etc/apt/apt.conf.d/02proxy
Put the following line in it:
Acquire::http { Proxy "http://localhost:3142"; };
Go to:
[http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html)
You should see: Apt-Cacher NG maintenance page for ~Your Desktop's Name Here~

Setup the Client:
sudo gedit /etc/apt/apt-conf.d/02proxy
Put the following line in it:
Acquire::http { Proxy "http://192.168.1.100:3142"; };

Now you should be able to download a package on the server, & once then clients will be able to get it from there.

If you want to import packages you downloaded prior to installing apt-cacher-ng so that they'll also be available, use sudo nautilus to copy everything in /var/cache/apt/archives to /var/cache/apt-cacher-ng/_import (you'll have to make _import)
Then run:
chown -R /var/cache/apt-cacher-ng /var/cache/apt-cacher-ng/_import
Go to:
[http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html) & click on the import button at the bottom of the page.
You need to configure the server and one client before doing the import. See above for instructions.
Run "apt-get update" on client(s) once to teach ACNG about remote locations of (volatile) index files.

Somehow this isn't perfect. I updated the server's packages, then a client's. The client downloaded some packages from the server, but not all. Anyway, I'm happy enough for now.

---

### Post by alanwalterthomas on 2009-11-15
Now I've turned off the server & found out my laptop isn't smart enough to try going to the Internet if the server doesn't respond.
I'd like to be able to travel with the laptop & download software/receive updates without having to get rid of the 02proxy file, then remember to put it back.

How can I teach the computer to first look for the files on the server & if they're not found, look online?

It would be even better if I could then have the laptop send it's downloaded packages to the central cache. Is there a better way to do that than manually importing?

---

### Post by wch on 2009-12-09
There seems to be a bug in your instructions. The path to the files should be: **/etc/apt/apt.conf.d/02proxy** instead of what you have listed.

Also, I have a question: is there a way to limit the access to the maintenance page? It seems that there's nothing stopping random people from running the expiration process and slowing down the system.

---

### Post by nardis_Miles1 on 2009-12-09
I'm already running apt-cacher, not apt-cacher-ng. I have tried using the apt-cacher-cleanup.pl script to remove packages from hardy. However, because the Package files still exist in my archive, the script will not clean these. Apparently there is a distkill.pl in apt-cacher-ng that would be useful. Is there any way to either 

1. move gracefully to apt-cacher-ng from apt-cacher (i. e. simple symbolic links between package directories) so that I can use distkill.pl

or

2. use distkill.pl from apt-cacher-ng within apt-cacher?

Art Edwards

---

### Post by alanwalterthomas on 2009-12-09
To save a bit of work, I made this script

#!/bin/sh
#This should start apt-cacher-ng
apt-cacher-ng
exit 0

& wrote /path/to/this/script in /etc/rc.local
Now apt-cacher-ng starts automatically.

I think you're right about my mistake. Edit apt.d to apt.conf.d

I still haven't found out anything re my questions & sorry, I don't know how to answer the others.

---

### Post by nardis_Miles1 on 2010-01-05
If apt-cacher is similar to apt-cacher, it does this automatically. That is, apt-cacher first looks in the local cache. If it doesn't find the package, it downloads the package from a repository found in /etc/apt/sources.list and caches it simulaneously.

---

### Post by nardis_Miles1 on 2010-01-06
I have just finished switching from apt-cacher to apt-cacher-ng. 

This is accomplised easily by:

1. moving /var/cache/apt-cacher/packages to your home directory (//home/me)
2. removing apt-cacher
3. installing apt-cacher-ng
4. executing 
*mkdir /var/apt-cacher-ng/_import*
*sudo mv /home/me/packages/*.deb /var/apt-cacher-ng/_import*
6. starting apt-cacher-ng (*sudo /etc/init.d/apt-cacher-ng start*) if it is not already started during installation
7. pointing a browser to 

[http://localhost:3143/acng-report.html](http://localhost:3143/acng-report.html)  

where 3143 is my chosen port (3142 is default)

8. clicking on **Start Import** button at the bottom of the page.

It's important to note that *_import* is the expected name of the directory. It appears to be hard wired on the apt-cacher management web- page

I would like to point out that the file *02proxy* under */etc/apt/apt.conf.d* is only required if you are using a proxy. I don't, so it was unnecessary. In fact, keeping 02proxy prevented the server from using its own apt-cacher cache. Also, I was unable to start apt-cacher-ng while apt-cacher was installed, even though I had changed the port from 3142. After removal of apt-cacher, apt-cacher-ng started and seems to work perfectly. The import was also completely successful.

---

### Post by davidshere on 2010-02-09
I've seen several people moving from apt-cacher to apt-cacher-ng, and the claim that apt-cacher is no longer supported.  Is this true?

I want to move my apt-cacher server from one machine to another, and I'm wondering if the directions for doing so are similar to your directions for switching from apt-cacher to apt-cacher-ng?

Also, 
> **alanwalterthomas said:**
> 
Setup the Client:
sudo gedit /etc/apt/apt-conf.d/02proxy
Put the following line in it:
Acquire::http { Proxy "http://192.168.1.100:3142"; };

Is this what's done in apt-cacher-ng on the clients instead of editing the /ect/apt/sources.list file to use your local URLs for the repository?

It seemes somewhat FreeBSD-needlessly-complicated to me.  But maybe that's just cause I'm used to the apt-cacher way.

---

### Post by SecretCode on 2010-02-10
I can't answer your question on migration since I started with -ng. But what I can say is that I tried setting up a proxy (as you quoted) and it didn't work for me - I had to edit the URLs in sources.list.

If it worked I'd say setting a proxy is much simpler - you only have one place to change instead of having to copy it into every new repository / ppa you add.

---

### Post by davidshere on 2010-02-17
> **nardis_Miles1 said:**
> 
4. executing 
*mkdir /var/apt-cacher-ng/_import*
*sudo mv /home/me/packages/*.deb /var/apt-cacher-ng/_import*
On my system, the path to apt-cacher-ng is 
```
/var/cache/apt-cacher-ng
```

---

### Post by davidshere on 2010-02-17
> **SecretCode said:**
> I had to edit the URLs in sources.list.
Here is a good single-line command for this, just change "thebone" to the name/ip of your machine.  The command makes a backup first, sources.list.bak
```
sudo perl -i.bak -pe 's/http:\/\//http:\/\/thebone:3142\//g' /etc/apt/sources.list
```

---

### Post by cong06 on 2010-02-18
I'm also looking for advice about apt-cacher vs apt-cacher-ng.

As far as the website is concerned it looks like apt-cacher is still supported:
[http://packages.qa.debian.org/a/apt-cacher.html](http://packages.qa.debian.org/a/apt-cacher.html)
last package upload ~ 2 months ago

While apt-cacher-ng does have a noticeable performance increase, the things I like about apt-cacher are:
1) It keeps one version of each package, and doesn't drop based on 'age'
2) It has command line commands for importing. I don't have to switch to a web interface.
3) The security.ubuntu.com and archive.ubuntu.com sometimes share packages. With apt-cacher-ng (as with apt-proxy) when you import you have to import to both trees. With apt-cacher it stores them all in a folder.

Although I'm looking forward to being persuaded that there are 'work-arounds' so that I can enjoy the speed increase.

---

### Post by cong06 on 2011-01-20
> **cong06 said:**
> I'm also looking for advice about apt-cacher vs apt-cacher-ng.

As far as the website is concerned it looks like apt-cacher is still supported:
[http://packages.qa.debian.org/a/apt-cacher.html](http://packages.qa.debian.org/a/apt-cacher.html)
last package upload ~ 2 months ago

While apt-cacher-ng does have a noticeable performance increase, the things I like about apt-cacher are:
1) It keeps one version of each package, and doesn't drop based on 'age'
2) It has command line commands for importing. I don't have to switch to a web interface.
3) The security.ubuntu.com and archive.ubuntu.com sometimes share packages. With apt-cacher-ng (as with apt-proxy) when you import you have to import to both trees. With apt-cacher it stores them all in a folder.

Although I'm looking forward to being persuaded that there are 'work-arounds' so that I can enjoy the speed increase.


Now using apt-cacher-ng:
1) works the same as apt-cacher
2) using elinks gives you a commandline program
3) if you mess around with backend files, you can move security.ubuntu.com to the uburep/ folder

---

### Post by kernst on 2011-04-21
Just one thing to add to your apt-cacher - to - apt-cacher-ng migration instructions (which were very helpful by the way):

> **nardis_Miles1 said:**
> 
*sudo mv /home/me/packages/*.deb /var/apt-cacher-ng/_import*
6. starting apt-cacher-ng (*sudo /etc/init.d/apt-cacher-ng start*) if it is not already started during installation
7. pointing a browser to 

[http://localhost:3143/acng-report.html](http://localhost:3143/acng-report.html)  

where 3143 is my chosen port (3142 is default)

8. clicking on **Start Import** button at the bottom of the page.


Works great except that apt-cacher-ng must have "valid index files in its cache" [according to the user guide]("http://www.unix-ag.uni-kl.de/~bloch/acng/html/howtos.html#imp"), or else you get an error at the import step. (I wish I'd copied the text of the error so I could put it here.)

The Apt-Cacher-NG user guide[[1]]("http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html") describes how to do this, but in plain terms, you configure one client to either use the apt-cacher-ng via either method above (proxy or modifying sources.list), then run 'apt-get update' from that client. Since my server is also its own apt-cacher client, I just ran 'sudo apt-get update' at the server after setting up apt-cacher-ng according to your instructions.

Also, I didn't seem to have any issues using apt-cacher-ng with the apt.conf proxy method, on the client or the server. My /etc/apt/apt.conf.d/02apt-cacher (the filename doesn't matter) looks like this:

```
Acquire::http::Proxy "http://aptcachernghost:3142/";
Acquire::http::Proxy::security.ubuntu.com "DIRECT";
```

**References:**
[1] [http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html](http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html)

---

### Post by xiangxing on 2011-04-21
Far away the birds of the air; eternal worrying is so Lin, The ship drifted always caring is bay; The hustle and bustle of travelers, whether in a hurry night returned home far away, the heart is ties, always miss place, or home.
<a href=http://www.ebuybus.com>wholesalers</a>

---

### Post by xiangxing on 2011-04-21
Spring breath filled with the whole world, you see the sky so that the glittering and translucent, grass and small animals to life as gay. I like to wear cute little baby puppies walk to the baby, looking at naughty births in the grass back and forth running, frolic; Looking at lightweight bird among the twigs jumping, singing; Smelling a mild scent in the air, curl up, the heart is always very touched, very pleased. I...
[ closeouts ](http://www.ebuybus.com)

---

### Post by Dis-appointed on 2011-04-29
Please help in my effort to make our laptop "wife-proof" :P

I found [this script]("https://help.ubuntu.com/community/AutomateAptCacheNgProxySettings?action=fullsearch&context=180&value=linkto%3A%22AutomateAptCacheNgProxySettings%22") in the Ubuntu Community Docs which pings the sever and then updates the apt.conf.d with the proxy info or "" if it can't find it.

(FYI: This is fine as far as it goes ... but since you can't ping a specific port it can't tell if apt-cacher-ng is running on the server.)


I'm looking to change the $SERVER bit to a fake, so that apt won't download anything if the sever isn't available.
```

echo "Acquire::http { Proxy \"http://$SERVER:3142\"; };" > /etc/apt/apt.conf.d/02proxy

```Would 0.0.0.0 work? I'm a noob, so I thought I ask before I try.
I don't want to use 127.0.0.1 or localhost because for other reasons (like an offline updating) I might have ACNG installed.


Why do this?
One reason: I don't want apt on my laptop to download anything if It's not on my home network and can't use my ACNG proxy. So on boot I'd like it to run the script and hobble apt. (or via the network hooks as per[ the doc]("https://help.ubuntu.com/community/AutomateAptCacheNgProxySettings?action=fullsearch&context=180&value=linkto%3A%22AutomateAptCacheNgProxySettings%22")) Thereby avoiding large bills when my wife unknowingly installs/updates something when connected via the mobile.

*Edit* Will use 192.0.2.200 as it's only supposed to be used in  documentation, and never on any network according to RFC 5737 and  reserved as such by iana. Therefor if should never be found.

---

### Post by SecretCode on 2011-04-29
In my setup, if my apt-cacher-ng server is unavailable, apt can't download anything - even on a laptop away from the house. It doesn't decide to bypass the acng server and go direct. So if you hard code your local acng server and leave it, you should get what you are looking for.

---

### Post by Dis-appointed on 2011-04-29
> **SecretCode said:**
> In my setup, if my apt-cacher-ng server is unavailable, apt can't download anything - even on a laptop away from the house. It doesn't decide to bypass the acng server and go direct. So if you hard code your local acng server and leave it, you should get what you are looking for.

I hear you, but hardcoding it isn't really an option for me. Since my next step is to add more/alternate APNG proxy's.
i.e allowing it to alternate with home and office proxy servers depending on who has it at the time, by adding a few more if statements.

*Edit* Just struck me that, someone might think I'm an idiot because if I left it set on any proxy it couldn't reach, it wouldn't download anyway, lol. Probably cos I was trying to simplify my question as much as possible without including the other things I plan to try and make it do :P So I want a way to make it look at a definitely fake proxy, but don't know enough yet about ubuntu to be sure I'm not going to make something else break.

*Edit* Will use 192.0.2.200 as it's only supposed to be used in documentation, and never on any network according to RFC 5737 and reserved as such by iana. Therefor if should never be found.

---

### Post by shane2peru on 2011-05-02
Thanks for this simple howto!  I followed the instructions and it worked fine for me.  Very simple, and saves me a bunch of time since my dsl is not very fast.  The import part was key for me since I don't bother setting up apt-cacher-ng until after I had did a large install, and wanted to copy that over to my laptop.  Thanks again!

Shane

---

### Post by shane2peru on 2011-05-06
Hmm, I ran into the problem that everyone else has had, when the server is off, no updates.  AS a temp fix, since I didn't really understand what everyone else was saying, I moved 02proxy to .02proxy to make it hidden, and updated.  Worked, probably not the best, but worked as a quick easy fix, then when server is running, I will just un-hide the file.  

Shane

---

### Post by lifeboy on 2012-03-18
So I'm still not clear on how to make ac-ng intelligent enough to survive and still download updated when I'm out of the office  and the ac-ng server is not available.

Could someone please break it down for us?

thanks

---

### Post by kernst on 2012-03-20
> **lifeboy said:**
> So I'm still not clear on how to make ac-ng intelligent enough to survive and still download updated when I'm out of the office  and the ac-ng server is not available.

Could someone please break it down for us?

thanks


It's not a built-in function of apt-cacher-ng, so you'll have to pick one of the solutions here, all of which involve writing scripts to or manually renaming config files to "hide" them from APT, then possibly running 'apt-get update' as root.

[Shane's solution]("http://ubuntuforums.org/showpost.php?p=10778931&postcount=19") seems pretty straightfoward, even if it's not automatic.

You could also [file a feature request]("https://alioth.debian.org/tracker/?atid=413110&group_id=100566&func=browse") for apt-cacher-ng if intelligently handling different networks is important to you. Seems worthy of one.

In the days before NetworkManager, I'd have suggested something like [this article on debian-administration.org]("http://www.debian-administration.org/article/Network_profiles_for_a_laptop"), which uses [guessnet]("http://guessnet.alioth.debian.org/"). Now, I don't know how to run arbitrary scripts when an interface comes up.

---

