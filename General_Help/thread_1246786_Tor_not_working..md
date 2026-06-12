---
title: "Tor not working."
date: 2009-08-22
forum: General Help
---

### Post by serpantman on 2009-08-22
Hey everyone.

  Installed tor and edited privoxy's config file adding

forward-socks4a / localhost:9050.

and disabling logs.

I've made sure both services are started but tor isn't masking my ip. I checked the tor button settings. Is their a graphical version for operating privoxy like their is for windows? It's not working, but i dont know what the problem is.

---

### Post by P4man on 2009-08-22
Torbutton ?

[https://addons.mozilla.org/en-US/firefox/addon/2275](https://addons.mozilla.org/en-US/firefox/addon/2275)

If you want to filter on URLs, you can combine it with foxyproxy:

[http://foxyproxy.mozdev.org/](http://foxyproxy.mozdev.org/)

---

### Post by serpantman on 2009-08-22
Yes that was the torbutton i was refering to in my first post. I used to use tor all the time in windows, but never got it working on ubuntu. And now i just installed jaunty over both OS's. So i really need to get it working if i wanna use it. I'll check out foxy proxy, maybe its out-of-the-box support for tor will fix it for me lol.

Is their any interfaces/displays for privoxy/tor? Like in the windows version, or even a text based one? How are you supposed to switch up your proxy chain while using the linux version?

---

### Post by P4man on 2009-08-22
For tor there is vidalia (its in the repo's) but afaik, it does little else than starting/stopping tor.

---

### Post by P4man on 2009-08-22
oh and there is TorK for KDE, but it works on gnome as well.

---

### Post by Bezmotivnik on 2009-08-22
I installed the Ubuntu TorButton for Firefox.

It doesn't work.

I installed the Vidalia package with Synaptic (which **should** install Tor, Privoxy and TorButton, or it's not Vidalia). 

Torbutton still doesn't work. :confused:

Get this error:

**You need to toggle Tor or restart for your settings to take effect.**

"Restarting" or rebooting does nothing.

TorButton's test in Preferences shows a failure.

Privoxy settings are as default in the TorButton preferences.

Thoughts?

As always, thanks for any good advice!

---

### Post by michy99 on 2009-08-22
```
forward-socks4a / localhost:9050.
```Should be```
forward-socks4a / localhost:9050 .
```Notice the space before the dot.

---

### Post by Bezmotivnik on 2009-08-22
> **michy99 said:**
> ```
forward-socks4a / localhost:9050.
```Should be```
forward-socks4a / localhost:9050 .
```Notice the space before the dot.
Brilliant! :rolleyes:

Where is this code?

Here?:

2. Run the command: sudo gedit /etc/privoxy/config
3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .

Thanks!

I'm also getting this error:

*Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.*

I'd swear Tor wasn't installed...but it's part of Vidalia.

---

### Post by Bezmotivnik on 2009-08-22
Where** IS** Tor, anyway?:

anonymous@X:~$ sudo apt-get install tor privoxy
[sudo] password for anonymous: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

---

### Post by michy99 on 2009-08-23
Tor was dropped from the repositories in Jaunty. You need to add these lines to /etc/apt/sources.list:```
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty  main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
```Then run this to get the key:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AFA44BDD
```

---

### Post by serpantman on 2009-08-23
Well it looks like Tor is working. When i turn on the tor button, firefox's proxy settings get changed to 127.0.0.1 port 8118. So it looks like privoxy is the problem? I'm sure i configured it right.

I just add this 

forward-socks4a / localhost:9050.

then diable logging? 

When i browse with it on, i cant refresh because tor stops me, but my internet isn't slow, and my true ip is dectected by web servers.

Any ideas?

EDIT: I didint refresh this page, i missed all the other post. Adding the space.

---

### Post by serpantman on 2009-08-23
Success!!! Thank you very much.

---

### Post by Bezmotivnik on 2009-08-23
> **michy99 said:**
> Tor was dropped from the repositories in Jaunty. 
That's what it looked like to me, but I couldn't imagine this, so I assumed I was wrong.

**Why?** :confused:

Is there some fatal problem with the current program that makes it hazardous to use, or what?  Tor's been in the Ubuntu repositories ever since 2005, to my knowledge.

Thanks for your help...

---

### Post by michy99 on 2009-08-23
> **Bezmotivnik said:**
> That's what it looked like to me, but I couldn't imagine this, so I assumed I was wrong.

**Why?** :confused:

Is there some fatal problem with the current program that makes it hazardous to use, or what?  Tor's been in the Ubuntu repositories ever since 2005, to my knowledge.

Thanks for your help...

I found a discussion here:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/jaunty/+source/tor/+bug/328442)

It seems that Tor released a major version change due to some security problems with the previous version. Apparently, no one has volunteered to test and maintain the package for Ubuntu, so it was dropped.

I have used the version from the [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) repository for several months with no problems.

---

### Post by sky5564 on 2009-10-08
> **michy99 said:**
> Tor was dropped from the repositories in Jaunty. You need to add these lines to /etc/apt/sources.list:```
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty  main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
```Then run this to get the key:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AFA44BDD
```

in installed vidalia but when i try to start tor i get "vidalia is unable to locate tor executable check your settings"

i have vidalia and privoxy installed and i assumed vidalia installed tor but i guess it didn't.

when i run sudo apt-get install tor i get "couldent find package tor but it is reffered to by another package"

i added those lines to the repository but it still says the same thing.

lol i dont know why it isint working??????????

---

### Post by husunzi on 2009-11-11
Tor is still not available in the repositories for Karmic (9.10), although Vidalia is, but I'm still getting the same "Vidalia was unable to start Tor" message. Either the Vidalia in the repositories doesn't include Tor (strange, since Tor is the central component), or there's another problem. I had tried [this Jaunty fix]("http://ubuntuforums.org/showpost.php?p=7832839&postcount=10") before, but it still didn't work (after it apparently installed, Vidalia continued to say "unable to start Tor), same as several other people on these threads. Any suggestions? Will Tor or a working Vidalia ever be returned to the Ubuntu repositories? This is essential for people living in countries where important websites are blocked (regular proxies don't work for a lot of things).

---

### Post by Bezmotivnik on 2009-11-16
> **husunzi said:**
> Tor is still not available in the repositories for Karmic (9.10)...

Considering the stuff that *is* supported, I find this amazing.

Not going to fight it, back to XP.

---

