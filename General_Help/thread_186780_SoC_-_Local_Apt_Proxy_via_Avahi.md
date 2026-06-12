---
title: "SoC - Local Apt Proxy via Avahi"
date: 2006-06-02
forum: General Help
---

### Post by DaveH on 2006-06-02
Howdy,

I'm doing a Summer of Code project - the simple apt repository. Keeping in mind that this is *very* Pre-Alpha - those with strong hearts are welcome to try it out... Oh, and though this looks really big - I'm pretty verbose so it's really only a few commands...

[B]
What Does it do?[/B]

The proxy has two parts... a host and a client. The host will automatically turn your cache into a repository, and (for the moment) share it via http. The client will detect the share and add it to the repo list. Then if Ubuntu needs a package that has already been downloaded on the host, it will come over the local network. Phew...
[B]
How do I install?[/B]

Caveats - this is pre-alpha. Be prepared for it hose your system. It *shouldn't* but that doesn't mean it *won't*... All care, no responsibility :) If you are not a command line kind of person, then it'll be better to wait till this is tested a bit more. At the moment - wireless is odd (see below) and it's only built for i386... though if avahi runs on other platforms, then this should too.

********* **If you have a mixed environment of Breezy / Dapper etc. and not planning on updating them all to Dapper, think twice about using this - I'm not sure how that will behave yet**. ************
[B]
No really, how do I install?[/B]

Right - first, dependancies. I think these are right, but just post a message if more are req'd. I'm running Dapper, so this may or may not work on Breezy.

```
sudo apt-get install python2.4 avahi-daemon python2.4-avahi python2.4-gamin
```

This isn't quite a dependancy, but we need a web server. If you have you're own already installed, that's fine. I'm using Apache, to install it - 
```
sudo apt-get install apache
```
(I've found I have to run that a second time to start the server)

If you are using Apache, you'll need to disable a module for signing to work correctly...
```
sudo gedit /etc/apache/modules.conf
```

now put a '#' at the start of mime_magic_module, it should look like this...
```
#LoadModule mime_magic_module /usr/lib/apache/1.3/mod_mime_magic.so
```

Now to create the neccesary directories... everything will end up in /var/www/local_mirror by default. Feel free to dig into the code if you want to change it. 

Download the file at the bottom of the page and unzip it. Order of running these is important.
```
unzip apt-avahi.zip
chmod +x makedirs.sh
sudo ./makedirs.sh
sudo dpkg -i aptavahi_prealpha0.1_i386.deb
```

The Gnupg version in Dapper is borked for batch installs, so you'll have to answer some questions to generate a key. The important parts are the name => apt-avahi ; and don't enter a passphrase. If this goes wrong, removing the files in /var/run/apt-avahi/ will let you reinstall.

The host and client should work now - they'll happily detect each other on the same machine for the moment, so 
```
sudo apt-avahi-mdns-client&
```
then
```
sudo apt-avahi-mdns-host&
```

will start them. Look in ```
 /etc/apt/sources.list.d/apt-avahi.sources.list 
``` and your IP should be there. Take a note of it, you'll need it for the next step.

**Signing**

In order for apt to prefer the local source, you'll need to register the key of the host. On the client fill in the IP and run
```
 wget http://$IPofHOST/local_mirror/apt-avahi.pub 
sudo apt-key add apt-avahi.pub
```

And you're done :)

**More technically, what's going on...**

The code documents itself ;)
Seriously though - the repository is created by apt-ftparchive which keeps it's own database. Gamin watches for changes in /var/cache/apt/archives, and if the lock is released (e.g. apt-get is finished) it will update. This stops it continually refreshing in an upgrade. Avahi advertises the share over _aptproxy._tcp, where the client should create/update the file /etc/apt/sources.d/apt-avahi.sources.list ; if the host dissapears the link should too. Apt silently prefers signed repos over unsigned - so we also sign our repository to ensure it has top priority.

**Riiiight**
Obviously there is still lots to be done - but I thought a functioning prealpha might help people with the Dapper update. 
Bugs I know of - 

- the thing with the Apache Module - dunno, nmp.

- Gnupg - the next version has batch working, so hopefully that'll be in soon and I won't have to worry.

- Wireless - mmm, not sure about this one. If you can't see from wireless to wired on your Avahi network, I'm not sure. I have that issue too. If someone can shed some light, that'd be great.

Please post any suggestions, bugs, etc... below. I can't say I'll get to bugs straightaway, but I'll give it a shot :)

Cheers
Dave

Edit: The wireless thing looks like it is to do with Multicast. If anyone can shed any further light, I'd love to hear.

---

### Post by GameGod on 2006-06-02
Unfortunately, I don't have enough PCs laying around right now to test this, but this is a REALLY REALLY REALLY good idea, and a top-notch application of Avahi!

I can't wait to see how it turns out at the end of the summer...

---

### Post by ketsugi on 2006-06-03
[quote="DaveH"]```
chmod +x makedirs.sh aptavahi_prealpha0.1.deb
```[/quote]

Why do you need execute permissions on the deb file?

---

### Post by DaveH on 2006-06-04
I was just checking you were reading thoroughly ;)

You don't need to enable execution - edited...

---

### Post by tonic on 2006-06-06
Are you using ndiswrapper? Avahi doesn't work properly with it, or more likely ndiswrapper is missing some functionality. Honestly it all does seem to be pointing towards multicast.

Currently the behaviour seems to be this - to put it simply. With ndiswrapper you can publish to the interface but you can not discover from it.

---

### Post by DaveH on 2006-06-06
[QUOTE=tonic]Are you using ndiswrapper? Avahi doesn't work properly with it, or more likely ndiswrapper is missing some functionality. Honestly it all does seem to be pointing towards multicast.

Currently the behaviour seems to be this - to put it simply. With ndiswrapper you can publish to the interface but you can not discover from it.[/QUOTE]

I'm not using ndiswrapper - but I'm positive the problem lies with my router... pings to multicast make it to the wired network, but don't go backwards. It's niggly, but not much Ubuntu can do about it.

---

### Post by kvonb on 2006-08-03
Hello (if you're still there),

I tried all this last night on my server (Dapper 6.06) and several problems cropped up:

1) The gpg asks which type of key to generate, something about options 1, 2, or 3 I think (can't remember exactly now).  I just pressed enter for default.

2) These utils don't exist anywhere on my system:

                apt-avahi-mdns-client
                apt-avahi-mdns-host

I checked in synaptic, and apt-proxy-mdns-client, and apt-proxy-mdns-host do exist but don't work!

3) "/etc/apt/sources.list.d/apt-avahi.sources.list" doesn't exist either.

After several uninstalls and re-installs I gave up and went to bed!

Any ideas?

Regards,  Kev

---

