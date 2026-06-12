---
title: "Looking for web editor to use on Linux"
date: 2011-11-07
forum: General Help
---

### Post by glennbates on 2011-11-07
Looking for a web editor that will directly save files on my site.  Would prefer it save to my computer at the same time but really need it to save to my server.

What do you recommend?

---

### Post by haqking on 2011-11-07
> **glennbates said:**
> Looking for a web editor that will directly save files on my site.  Would prefer it save to my computer at the same time but really need it to save to my server.

What do you recommend?

[bluefish]("http://bluefish.openoffice.nl/index.html") or [kompozer]("http://kompozer.net/")

I believe will do as you want

---

### Post by glennbates on 2011-11-07
> **haqking said:**
> [bluefish]("http://bluefish.openoffice.nl/index.html") or [kompozer]("http://kompozer.net/")

I believe will do as you want
I have these installed.  Maybe I just don't know how to configure them.  Where can I learn?

---

### Post by haqking on 2011-11-07
> **glennbates said:**
> I have these installed.  Maybe I just don't know how to configure them.  Where can I learn?

by clicking on each of the links and reading ;-)

there is a manual on the bluefish page [http://bluefish.openoffice.nl/manual/](http://bluefish.openoffice.nl/manual/)

and kompozer user guides [http://kompozer.net/community.php](http://kompozer.net/community.php)

Both support remote site publishing as far as i know

---

### Post by satanselbow on 2011-11-07
There's a new kid on the block (built out of the ashes of Kompozer / NVu and the like) called BlueGriffon which I have just started to poke about with - seems pretty capable so far ;) Some of the addons are paid for but the base app is free.

[http://www.bluegriffon.com/](http://www.bluegriffon.com/)

Or my all time favourite (web) IDE of all time - Komodo Edit...

[http://www.activestate.com/komodo-edit](http://www.activestate.com/komodo-edit)

Neither are in the repos but are both come with simple install scripts :popcorn:

---

### Post by haqking on 2011-11-07
> **satanselbow said:**
> There's a new kid on the block (built out of the ashes of Kompozer / NVu and the like) called BlueGriffon which I have just started to poke about with - seems pretty capable so far ;) Some of the addons are paid for but the base app is free.

[http://www.bluegriffon.com/](http://www.bluegriffon.com/)

Or my all time favourite (web) IDE of all time - Komodo Edit...

[http://www.activestate.com/komodo-edit](http://www.activestate.com/komodo-edit)

Neither are in the repos but are both come with simple install scripts :popcorn:

I remember seeing a package for bluegriffon somewhere ?

---

### Post by glennbates on 2011-11-07
How do I configure KompoZer to directly edit my web pages?

---

### Post by drdos2006 on 2011-11-07
To the OP
Is your server on your local area network, or is it hosted ?

If on your LAN, I would install nfs-kernel-server and mount the web directory on my desktop. That is how I did it.

If your server is hosted, your hosting service may have software to install that can allow you to mount your web on your desktop. My host does.

regards

---

### Post by haqking on 2011-11-07
> **glennbates said:**
> How do I configure KompoZer to directly edit my web pages?

I referred you to the manuals in your other thread.

see here for site editing [http://www.charlescooke.me.uk/web/ugs08.htm](http://www.charlescooke.me.uk/web/ugs08.htm) which is a link from [http://kompozer.net/community.php](http://kompozer.net/community.php) the link i referred you to in your other thread here [http://ubuntuforums.org/showthread.php?t=1877149](http://ubuntuforums.org/showthread.php?t=1877149)

---

### Post by Elfy on 2011-11-07
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by haqking on 2011-11-07
> **drdos2006 said:**
> To the OP
Is your server on your local area network, or is it hosted ?

If on your LAN, I would install nfs-kernel-server and mount the web directory on my desktop. That is how I did it.

If your server is hosted, your hosting service may have software to install that can allow you to mount your web on your desktop. My host does.

regards

you can connect to the site from within the applications

[http://www.charlescooke.me.uk/web/ugs08.htm](http://www.charlescooke.me.uk/web/ugs08.htm) for site management in Kompozer

---

### Post by satanselbow on 2011-11-07
> **haqking said:**
> I remember seeing a package for bluegriffon somewhere ?

getdeb had one - but links were broken last time I looked ;)

---

### Post by glennbates on 2011-11-07
> **forestpiskie said:**
> Please do not post duplicates, it dilutes community effort. Threads merged
I didn't.  This was a new question.

---

### Post by haqking on 2011-11-07
> **satanselbow said:**
> getdeb had one - but links were broken last time I looked ;)

ahh gotcha, i knew i remember seeing one

edit: yeah getdeb2 for 11.10 [http://www.ubuntuupdates.org/packages/show/371905](http://www.ubuntuupdates.org/packages/show/371905)

---

### Post by glennbates on 2011-11-07
> **haqking said:**
> you can connect to the site from within the applications

[http://www.charlescooke.me.uk/web/ugs08.htm](http://www.charlescooke.me.uk/web/ugs08.htm) for site management in Kompozer
I believe that is what I need.  I'll give it a try.

Thanks!

---

### Post by drdos2006 on 2011-11-07
For more information, this is how my web hosting organisation provides desktop access through cPanel.

regards

---

### Post by haqking on 2011-11-07
> **drdos2006 said:**
> For more information, this is how my web hosting organisation provides desktop access through cPanel.

regards

yes most web hosts do pretty  much the same thing.

The OP wants to use an editor that connects directly to his site, the apps mentioned above do this.

Cheers

---

### Post by glennbates on 2011-11-07
After reading everything and thinking about it, I think what I need to do is work on it on my localhost and just upload it.  What I think I need to know to do is:

1) How do I install php on my system?

2) What is the easiest ftp to use if I do it this way?

---

### Post by drdos2006 on 2011-11-08
I am assuming that your server is on your LAN, or that you are running the server on your desktop through VirtualBox.

Set your server with a static IP.
From the server terminal, run     
     sudo apt-get install apache2
     sudo apt-get install php5
    sudo apt-get install libapache2-mod-php5
    sudo /etc/init.d/apache2 restart
You might also need php5-gd
     sudo apt-get install php5-gd

Use Kompozer to access your web files via your server's static IP address, use FileZilla to upload to your hosting ISP.

regards

---

