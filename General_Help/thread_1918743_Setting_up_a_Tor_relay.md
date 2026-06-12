---
title: "Setting up a Tor relay?"
date: 2012-02-01
forum: General Help
---

### Post by matthewh3 on 2012-02-01
Hi I keep getting the following error messages when I try to set up a Tor relay

Feb 01 20:27:42.400 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 01 20:27:42.404 [Notice] Renaming old configuration file to "/etc/tor/torrc.orig.1"
Feb 01 20:27:42.404 [Warning] Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1": Permission denied
Feb 01 20:27:42.406 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 01 20:27:42.407 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 01 20:27:42.407 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 01 20:27:42.407 [Notice] Renaming old configuration file to "/etc/tor/torrc.orig.1"
Feb 01 20:27:42.407 [Warning] Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1": Permission denied

I have downloaded Tor from the repository.  I didn't have any problems setting up a relay when I used the browser package.  I have tried starting Vidalia using sudo.  Any ideas?

---

### Post by scarleo on 2012-02-07
So you need to fix permissions on /etc/tor folder, I'm not sure to what, but try
```
chmod -R +x /etc/tor
```

---

### Post by matthewh3 on 2012-02-12
> **scarleo said:**
> So you need to fix permissions on /etc/tor folder, I'm not sure to what, but try
```
chmod -R +x /etc/tor
```

I entered


sudo chmod -R +x /etc/tor


Into the command line and I'm still getting the following error when I try to set up relying even after starting Vidalia with sudo?


Feb 12 14:42:08.567 [Notice] Renaming old configuration file to "/home/matt/.vidalia/torrc.orig.1"
Feb 12 14:42:08.567 [Warning] Couldn't rename configuration file "/home/matt/.vidalia/torrc" to "/home/matt/.vidalia/torrc.orig.1": Permission denied

---

### Post by ottosykora on 2012-02-12
>I have downloaded Tor from the repository. I didn't have any problems setting up a relay when I used the browser package. I have tried starting Vidalia using sudo. Any ideas?<

you definitely should not do that, as what ever version of tor is in the repository it is ages old.

Go to the website of torproject and follow the procedure there.

To run just simple relay is easy, you can use the vidalia to complete few things there like some kind of contact etc.

so I recommend you to unistall what ever you got from the repo and install the ppa of torproject.

---

### Post by matthewh3 on 2012-02-12
> **ottosykora said:**
> >I have downloaded Tor from the repository. I didn't have any problems setting up a relay when I used the browser package. I have tried starting Vidalia using sudo. Any ideas?<

you definitely should not do that, as what ever version of tor is in the repository it is ages old.

Go to the website of torproject and follow the procedure there.

To run just simple relay is easy, you can use the vidalia to complete few things there like some kind of contact etc.

so I recommend you to unistall what ever you got from the repo and install the ppa of torproject.


Kk will do soon as but at the moment the current Tor is the only way I can browse the Internet if you read thread - [http://ubuntuforums.org/showthread.php?p=11683329#post11683329](http://ubuntuforums.org/showthread.php?p=11683329#post11683329)

---

### Post by Prospero2006 on 2012-02-12
Compiling TOR from source is also a good way to learn about how it all works. Fun too.

---

### Post by scarleo on 2012-02-12
I just tested to set set up tor and when running it from Vidalia you need to own the /var/run/tor directory: chown user /var/run/tor

...and then set it to permissions 700: chmod 700 /var/run/tor

---

### Post by ottosykora on 2012-02-12
> **scarleo said:**
> I just tested to set set up tor and when running it from Vidalia you need to own the /var/run/tor directory: chown user /var/run/tor

...and then set it to permissions 700: chmod 700 /var/run/tor

yes, but then you need to have the configuration there and there is nothing there when it is fresh installed.

To make it more simple, one can use the tcp port 9051 , means tick the top tick box under advanced and all works straight away

I mever manged to get the socks really running, as the when the /tor directory is not present it says 'directory not found' and if I create it and give it finaly the right permissions it says:


```
Feb 13 01:46:00.970 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Feb 13 01:46:00.971 [Hinweis] Opening Control listener on 127.0.0.1:9051
Feb 13 01:46:00.971 [Hinweis] Opening Control listener on /var/run/tor/
Feb 13 01:46:00.984 [Warnung] Could not unlink /var/run/tor/: Is a directory
Feb 13 01:46:00.984 [Hinweis] Closing partially-constructed listener OR listener on 0.0.0.0:9001
```


Therefore I use the normal tcp port 9051 and all works.

---

### Post by hawthornso23 on 2012-02-12
```
sudo chmod -R +x /etc/tor
```

You probably don't want to do that. It will mark every file in the folder recursively as executable. That includes things you probably don't want to be executable like config files and documentation.

---

### Post by ottosykora on 2012-02-12
also note:

zhe installed tor will run on start and then it is confusing to change anything.

Best:
install

sudo apt-get sysv-rc-conf

then run it

sudo sysv-rc-conf

and scroll with arrow key to the line with tor and remove all x

reboot


now even if you have tor installed, you still can run the tor-browser-bundle, which I would recomend anyway as this takes care of many things in firefox that can bypass the tor

---

### Post by matthewh3 on 2012-02-13
> **hawthornso23 said:**
> ```
sudo chmod -R +x /etc/tor
```

You probably don't want to do that. It will mark every file in the folder recursively as executable. That includes things you probably don't want to be executable like config files and documentation.

Woops

---

### Post by matthewh3 on 2012-02-13
> **scarleo said:**
> I just tested to set set up tor and when running it from Vidalia you need to own the /var/run/tor directory: chown user /var/run/tor

...and then set it to permissions 700: chmod 700 /var/run/tor

Did that still getting this error message when I try to set up relying -


Feb 13 08:50:32.445 [Warning] Unable to open "/var/run/tor/tor.pid" for writing: Permission denied
Feb 13 08:50:32.445 [Notice] Renaming old configuration file to "/etc/tor/torrc.orig.1"
Feb 13 08:50:32.445 [Warning] Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1": Permission denied

---

### Post by ottosykora on 2012-02-13
when you open vidalia, go to advanced under configuration

what is ticked there? the socks or the tcp for the control port?

Select the tcp for the control port and port 9051, then all will work. Do not bother with the /var/run/tor it does not work in the current version properly so far.

But install to from the torproject site either or use torbrowser bundle.

---

### Post by matthewh3 on 2012-02-13
> **ottosykora said:**
> when you open vidalia, go to advanced under configuration

what is ticked there? the socks or the tcp for the control port?

Select the tcp for the control port and port 9051, then all will work. Do not bother with the /var/run/tor it does not work in the current version properly so far.

But install to from the torproject site either or use torbrowser bundle.

Tried that and get the following error messages -


Feb 13 11:54:26.121 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 13 11:54:26.160 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 13 11:54:26.160 [Warning] Unable to open "/var/run/tor/tor.pid" for writing: Permission denied
Feb 13 11:54:26.160 [Notice] Renaming old configuration file to "/etc/tor/torrc.orig.1"
Feb 13 11:54:26.160 [Warning] Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1": Permission denied
Feb 13 11:54:26.162 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 13 11:54:26.162 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 13 11:54:26.162 [Warning] Unable to open "/var/run/tor/tor.pid" for writing: Permission denied
Feb 13 11:54:26.163 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 13 11:54:26.163 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 13 11:54:26.163 [Warning] Unable to open "/var/run/tor/tor.pid" for writing: Permission denied
Feb 13 11:54:26.163 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Feb 13 11:54:26.163 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 13 11:54:26.163 [Warning] Unable to open "/var/run/tor/tor.pid" for writing: Permission denied
Feb 13 11:54:26.164 [Notice] Renaming old configuration file to "/etc/tor/torrc.orig.1"
Feb 13 11:54:26.164 [Warning] Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1": Permission denied


I have installed Tor from the ppa.  I had no problem setting up relying with the browser bundle.  Will Bitcoin still work with Tor using the browser bundle.

---

### Post by ottosykora on 2012-02-13
Did you remove the original tor you were installing from repository?
This should be done first.

Then get tor from the torproject.org and follow the instruction given there.

Then:
sudo apt-get sysv-rc-conf

then run it

sudo sysv-rc-conf

and scroll with arrow key to the line with tor and remove all x

reboot

first now you can make chnages to settings etc.

When all ready, you go to vidalia, check first if you can run just the client.
If working, then you have to set up the relay by going to relaing and complete the tabs there. E.g you still have  no contactinfo set etc.
When you run the current versin of tor, the /var/run/tor does not exist and if it does it is empty and you will not get any such messages.

Under advanced, select the top tickbox called tcp (controll port) and do not forget to click on OK down on the page!

Then you should be able to start tor from vidalia.

Uncheck also the tickbox on firts tab of vidalia: start tor with start of vuidalia, as you want start it by clicking on start first.

With the tor budle only the browser will work so far, one can try otherthigs, but most other programs simply break the tor and bypass it.



>ControlPort is open, but no authentication method has been configured. <

you have to set some authentication, best select automatic password creation.


You have to operate the browser in a way that it has no contact to any antivirus or adblok or what ever, as such things can bypass the tor.
Therefore it is best to use the bundle browser, where all plugins etc are disabled.


Thaat you had no problem with bundled browser is because there all is preconfigured more or less. Here you still seem to use some old version of tor.

---

### Post by matthewh3 on 2012-02-13
After trying all these different commands now it's totally knackered!  It won't start and it doesn't give any error messages.  I just installed the ppa then installed through synaptic.  I've tried doing a complete removal with synaptic but it's still no good.  Does anyone know I way I can completely remove every last trace of Tor so I can do a fresh clean install and start over.

---

### Post by ottosykora on 2012-02-14
you have to follow all step by step  and try this and that.

Stop first tor, the best done by the method I gave you with the tool sysv-rc-conf


see that I have small typo there in the instruction:

sudo apt-get install sysv-rc-conf

ithas to be, install is missing 


then again

sudo sysv-rc-conf

and remove any x from the line with tor.
Dis so? reboot now
Tor is stopped now and all removal and purging will work.


When done you can remove tor completely and vidalia too. 
If you have some polipo or privoxy from earlier installs , remove those as well.
But stop tor first and disable starting at boot.

From then you go to :
[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

and follow the exact procedure there

Then you have to configure some basic things. In your log from vidalia, it says that you did bot configure or tick any functions at all. Simply started tor with nothing.

---

### Post by matthewh3 on 2012-02-14
> **ottosykora said:**
> you have to follow all step by step  and try this and that.

Stop first tor, the best done by the method I gave you with the tool sysv-rc-conf


see that I have small typo there in the instruction:

sudo apt-get install sysv-rc-conf

ithas to be, install is missing 


then again

sudo sysv-rc-conf

and remove any x from the line with tor.
Dis so? reboot now
Tor is stopped now and all removal and purging will work.


When done you can remove tor completely and vidalia too. 
If you have some polipo or privoxy from earlier installs , remove those as well.
But stop tor first and disable starting at boot.

From then you go to :
[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

and follow the exact procedure there

Then you have to configure some basic things. In your log from vidalia, it says that you did bot configure or tick any functions at all. Simply started tor with nothing.


sudo apt-get sysv-rc-conf
E: Invalid operation sysv-rc-conf

---

### Post by yetiman64 on 2012-02-14
Try ```
sudo apt-get **install** sysv-rc-conf
```see ottosykora's last post you quoted ;)

---

### Post by matthewh3 on 2012-02-14
> **yetiman64 said:**
> Try ```
sudo apt-get **install** sysv-rc-conf
```see ottosykora's last post you quoted ;)

Thanks

So OK I completely removed Tor and associated packages.  Then reinstalled as per the Tor website then did the - sudo sysv-rc-conf - un-checking all boxes and restarted then I went settings > general - and un-ticked - Start the Tor Software when Vidalia starts- then ticked the box in - settings > advance - Use TCP Connection ( Control port ) [127.0.0.1:9051] -  Then restarted again and now I get the pop up error message -



Vidalia can't find out how to talk to Tor because it can't access this file: /var/lib/tor/port.conf
Here's the last error message:
Permission denied

And in Advanced error messages I get the following -



Feb 14 12:11:28.418 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Feb 14 12:11:28.418 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 14 12:11:28.419 [Notice] Initialized libevent version 2.0.12-stable using method epoll. Good.
Feb 14 12:11:28.419 [Notice] Opening Socks listener on 127.0.0.1:0
Feb 14 12:11:28.419 [Notice] Socks listener listening on port 59116.
Feb 14 12:11:28.419 [Notice] Opening Control listener on 127.0.0.1:0
Feb 14 12:11:28.419 [Notice] Control listener listening on port 48214.
Feb 14 12:11:28.419 [Warning] Directory /var/run/tor does not exist.
Feb 14 12:11:28.419 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user and group account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Feb 14 12:11:28.419 [Notice] Closing partially-constructed listener Socks listener on 127.0.0.1:59116
Feb 14 12:11:28.419 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:48214
Feb 14 12:11:28.419 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Feb 14 12:11:28.420 [Error] Reading config failed--see warnings above.


???

---

### Post by matthewh3 on 2012-02-14
> **matthewh3 said:**
> Thanks

So OK I completely removed Tor and associated packages.  Then reinstalled as per the Tor website then did the - sudo sysv-rc-conf - un-checking all boxes and restarted then I went settings > general - and un-ticked - Start the Tor Software when Vidalia starts- then ticked the box in - settings > advance - Use TCP Connection ( Control port ) [127.0.0.1:9051] -  Then restarted again and now I get the pop up error message -



Vidalia can't find out how to talk to Tor because it can't access this file: /var/lib/tor/port.conf
Here's the last error message:
Permission denied

And in Advanced error messages I get the following -



Feb 14 12:11:28.418 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Feb 14 12:11:28.418 [Warning] ControlPort is open, but no authentication method has been configured.  This means that any program on your computer can reconfigure your Tor.  That's bad!  You should upgrade your Tor controller as soon as possible.
Feb 14 12:11:28.419 [Notice] Initialized libevent version 2.0.12-stable using method epoll. Good.
Feb 14 12:11:28.419 [Notice] Opening Socks listener on 127.0.0.1:0
Feb 14 12:11:28.419 [Notice] Socks listener listening on port 59116.
Feb 14 12:11:28.419 [Notice] Opening Control listener on 127.0.0.1:0
Feb 14 12:11:28.419 [Notice] Control listener listening on port 48214.
Feb 14 12:11:28.419 [Warning] Directory /var/run/tor does not exist.
Feb 14 12:11:28.419 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user and group account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Feb 14 12:11:28.419 [Notice] Closing partially-constructed listener Socks listener on 127.0.0.1:59116
Feb 14 12:11:28.419 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:48214
Feb 14 12:11:28.419 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Feb 14 12:11:28.420 [Error] Reading config failed--see warnings above.


???



Think I may have deleted -  /var/lib/tor/port.conf - yesterday trying to remove Tor completely from my PC.  I thought it would just create it again when I reinstalled?  What do I do know.  Try to compile from source but I wanted the Tor ppa for updates.

---

### Post by Lauscher on 2012-06-07
The solution to the problem
> Couldn't rename configuration file "/etc/tor/torrc" to "/etc/tor/torrc.orig.1"is quite simple, whether you know it :)

The command
```
sudo chown debian-tor /etc/tor -R 
```allows Vidalia to change the config files, but not to the current user (except using sudo).

---

### Post by Mankano on 2012-12-16
Thank you, Lauscher, thank you very much :) I've been looking for the solution to that for quite a while..

---

