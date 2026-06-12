---
title: "Install FreeNX in Ubuntu 10.4 Lucid"
date: 2010-05-03
forum: General Help
---

### Post by NeddyDownUnder on 2010-05-03
Hi,

Anyone know if it's possible to install FreeNX in Lucid.

I've tried but get an error. 

These are the steps I followed:

```
sudo add-apt-repository ppa:freenx-team
```No error.

Then:
```
sudo apt-get update
```No error.

Then:
```
neddyo@Linux-Mac:~$ sudo aptitude install freenx-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for freenx-server
No candidate version found for freenx-server
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```[LEFT]Is there anyway to get this installed? Do I need to wait for FreeNX to be updated for Lucid or something? Or does anyone have any suggestion for a RDP server and client? I don't want to use VNC it's too laggy... 

Any advice would be appreciated.

Thanks.
[/LEFT]

---

### Post by srivo on 2010-05-03
Easy,

Go into synaptic package manager -> Settings -> Repositories -> Other Software (tab) and click on the freenx repositories. Edit and replace distribution Lucid by Karmic and you will be able to install freenx from the Karmic repositories.

---

### Post by stever62 on 2010-05-03
Having the same issues getting freenx to work on Lucid.
The Karmic repositories for freenx-server will install but I could not get it to generate custom keys.  NeatX will work in place of freenx (and is available for lucid) but I cannot find any documentation to see if there is a way to generate a custom keys.

---

### Post by stever62 on 2010-05-04
Finally got it to work.  Thought I'd post back.  Gave up on the karmic repository and added the jaunty ones which worked and allowed me to create custom keys.

---

### Post by NeddyDownUnder on 2010-05-04
Thank you for the replies. I'll give both of the suggestions a try tonight, and I'll mark the thread solved after I get it working.

Cheers

---

### Post by razor7 on 2010-05-05
Hi, i discovered that freenx team has now two PPAs, one for stable an other for testing.

In the stable, there is no freenx-server, but in the testing there is it...

By installing through testing PPA, i get freenx-server, but since lucid uses upstart instead of init, i really dont know if it is working.

Is there any suggestion on how to install freenx from lucid PPAs?

Thanks a lot!

---

### Post by razor7 on 2010-05-06
Well, I finally managed to get it working using Lucid repo.

For custom keys:
```
$ sudo apt-get install freenx
$ sudo /usr/lib/nx/nxkeygen
$ sudo /usr/lib/nx/nxsetup --install 
$ sudo dpkg-reconfigure freenx-server (select custom keys)
$ use key located in /var/lib/nxserver/home/.ssh/client.id_dsa.key

```

If you dont have "nxsetup" script, just download it above and extract it with 
```
tar xzvf nxsetup.tar.gz
```


Best regards

---

### Post by GavinP on 2010-05-09
Thanks for posting that - I was beginning to pull my hair out... :)

---

### Post by psypher on 2010-05-12
changing to the karmic ppa worked for me, just worked, no tweaking

---

### Post by NeddyDownUnder on 2010-05-12
Thank you for all the replies. 


I've actually gone a different route now and I have installed the server edition and Webmin...

I'm going to mark this thread as solved as it appears the solutions in this thread have worked for a few other people...

Thanks again for all the replies.

:)

---

### Post by ghepeath on 2010-05-18
> **NeddyDownUnder said:**
> Thank you for all the replies. 


I've actually gone a different route now and I have installed the server edition and Webmin...

I'm going to mark this thread as solved as it appears the solutions in this thread have worked for a few other people...

Thanks again for all the replies.

:)
Hey i try the Neatx server but i dont' find a way for a custom configuartion
any one know where i can create custom keys and user and password DB?

---

### Post by Zarok on 2010-05-22
> **razor7 said:**
> Well, I finally managed to get it working using Lucid repo.

For custom keys:
```
$ sudo apt-get install freenx
$ sudo /usr/lib/nx/nxkeygen
$ sudo /usr/lib/nx/nxsetup --install 
$ sudo dpkg-reconfigure freenx-server (select custom keys)
$ use key located in /var/lib/nxserver/home/.ssh/client.id_dsa.key

```

If you dont have "nxsetup" script, just download it above and extract it with 
```
tar xzvf nxsetup.tar.gz
```


Best regards
Hey

I tried doing this, and the keys worked after I downloaded that custom script, but the server doesn't start.

At the moment there is a Lucid-packaged freenx in the repositories, but installing it doesn't help. During running apt it says while installing the packages 
```

Tehdään asetuksia: freenx-server (0.7.3.git100327.e224628-0~ppa4~lucid1) ...
start: Unknown job: freenx-server

```
(the Tehdään asetuksia is a finnish message from APT when its installing the package)
so the server never starts up. I've tried the old way of running it form etc/init.d and it says the same thing, so does running service freenx-server start.

I tried checking manually with nxserver --start and it said its running, but it won't accept connections. Something is messed up here :I

Edit : A-HA! I got it working using the default keys that came with NXserver. The creation of custom SSH keys was a problem with it. NOw I just gotta manage to create those custom keys...

Edit2: NOw it works. Hooray. :) The upstream start/stop thing still fails though, someone needs to fix that at some point.

Edit3: Except resuming suspended sessions doesn't. :(

```

NX> 203 NXSSH running with pid: 3965
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.11.2 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mie
NX> 102 Password: 
NX> 103 Welcome to: eee701 user: mie
NX> 105 listsession --user="mie" --status="suspended,running" --geometry="1024x600x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'mie' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
2000    unix-gnome       532FBD0DC0B77544A89F28BABC48B8E5 -RD--PSA    24 1024x552       Suspended   701kotiverkko


NX> 148 Server capacity: not reached for user: mie
NX> 105 restoresession  --link="modem" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="701kotiverkko" --type="unix-gnome" --geometry="1024x552" --client="linux" --keyboard="pc102/fi" --id="532FBD0DC0B77544A89F28BABC48B8E5" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
/usr/bin/nxserver: rivi 1584: 10126 Päätetty              sleep $AGENT_STARTUP_TIMEOUT
NX> 105 NX> 596 Session startup failed.
NX> 280 Exiting on signal: 15

```
Any ideas? After I tried to reconnect after that error, it had killed the session I tried to resume on the first attempt, and created a new one instead.

Edit4: It seems it suspends the session correctly, since after suspending it and doing a nxserver --list, it shows a suspended session is available. However, when I try to reconnect, it just gives the same error as before, just with a different session ID, and terminates the session and removes it from the servers .nx/ folder. I tried reinstalling both the server and the client once again, but it didn't help. :/

---

### Post by ChristianSL on 2010-06-07
same here...
does anyone has an idea?

---

### Post by Steve1961 on 2010-06-07
> **razor7 said:**
> Well, I finally managed to get it working using Lucid repo.

For custom keys:
```
$ sudo apt-get install freenx
$ sudo /usr/lib/nx/nxkeygen
$ sudo /usr/lib/nx/nxsetup --install 
$ sudo dpkg-reconfigure freenx-server (select custom keys)
$ use key located in /var/lib/nxserver/home/.ssh/client.id_dsa.key

```

If you dont have "nxsetup" script, just download it above and extract it with 
```
tar xzvf nxsetup.tar.gz
```


Best regards

Thanks, works fine for me now

---

### Post by natnek on 2010-06-09
For Zarok and ChristianSL - further down in this thread we're also discussing the resuming session issue:

[http://ubuntuforums.org/showthread.php?t=1044659](http://ubuntuforums.org/showthread.php?t=1044659)

---

### Post by Zarok on 2010-06-19
I'm happy to report that the resume bug has been fixed on the latest Freenx-server build that came out on their PPA within the last few days. Hooray!!!

---

### Post by afrodeity on 2010-06-30
```

sudo /usr/lib/nx/nxsetup --install 
sudo: /usr/lib/nx/nxsetup: command not found

```

Thank you razer7 for providing the setup script.

```

sudo mv nxsetup /usr/lib/nx/nxsetup

```

Now any clue as to what the freenx server address should be? I am using the NoMachine client

---

### Post by HvanMidden on 2011-07-19
Hi there,
 
I have since a few months problems resuming sessions. Everything worked fine before and I did not make any changes except the suggested upgrades.
 
My system is Ubuntu 10.10 - the Maverick Meerkat 
I am using Lucid: 0.7.3.git110520.3884279-0ubuntu1ppa4 (freenx)
 
Since this version is higher than the vesrion mentioned above as the solution, I suspect that it was upgraded (how can I find my upgrade hiostory?) this newer version reintroduced the resume problem.
 
Has anyone similar problems or even better a solution, because it is very irritating to always have to restart the session.
 
Thanks
Herman

---

