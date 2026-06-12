---
title: "Proxy server issue causing inability to install software"
date: 2009-12-17
forum: General Help
---

### Post by labrat256 on 2009-12-17
As I still consider myself a beginner with Ubuntu, I thought that I may just be having basic problems with setting my proxy server, but after posting the same problem in the beginners forum ([http://ubuntuforums.org/showthread.php?t=1323761](http://ubuntuforums.org/showthread.php?t=1323761)), I had no luck.

Every time I try to install something, either from Synaptic, the software centre or the terminal, it always wants to go through a proxy server I have to use on my university campus (which I am no longer on), despite me setting all of my proxy settings to connect directly to the internet. I've set the proxy settings in the Synaptic Package Manager, Preferences/Network Proxy and Firefox, I've also looked in .bashrc which didn't have anything. I'm running Ubuntu 9.10 on a Toshiba Equium P200. 


 Firefox works, all of my internet based apps work, but I can't install anything, its still convinced it wants to go through my proxy server despite me being unable to find any settings to change it anywhere. Am I missing something elementary, or is there a problem here?

---

### Post by Darael on 2009-12-17
I've run into this before. What you'll need to do is press alt+f2 and type "gconf-editor" (no quotes). Then you need to select system->http-proxy in the left-hand pane, and clear the checkbox for "use_http_proxy" and the content of "host". You'll be prompted for authentication the first time you do this. Finally, to stop it happening again, in the normal proxy configuration box create a new location with no proxy set, and one with your Uni proxy. The "Default" setting is, annoyingly, inadequate for resetting the proxy settings. Anyway, you can then switch to the appropriate location and "apply system-wide" at any time.

---

### Post by labrat256 on 2009-12-17
Thanks for your help, it is something I hadn't tried, but when I got to the http_proxy folder, both "host" was empty and "use_http_proxy" was unticked. 

I re-checked that the problem was still occuring, and it is, as shown by Synaptic returning:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/aa3d/aa3d_1.0-8_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/aa3d/aa3d_1.0-8_i386.deb)
  Could not connect to wwwcache.lancs.ac.uk:8080 (194.80.32.10), connection timed out [IP: 194.80.32.10 8080]

when I try to install something.

Are there any more places to set this?

---

### Post by Darael on 2009-12-17
Umm... there's an environment variable or two, I think...
You could try running "export http_proxy=" to ensure that apt (shich functions as a backend for synaptic) isn't trying to use a proxy, and check /etc/apt/apt.conf and any files in /etc/apt/apt.conf.d to make sure nothing's setting a proxy there, but beyond that I don't know...

---

### Post by dcstar on 2009-12-17
> **labrat256 said:**
> 
.......
Every time I try to install something, either from Synaptic, the software centre or the terminal, it always wants to go through a proxy server I have to use on my university campus (which I am no longer on), despite me setting all of my proxy settings to connect directly to the internet. I've set the proxy settings in the Synaptic Package Manager, Preferences/Network Proxy and Firefox, I've also looked in .bashrc which didn't have anything. I'm running Ubuntu 9.10 on a Toshiba Equium P200. 


Go into Synaptic and set some other proxy setting (invent one), and then see if it tries to use it.

Then set it back to direct connect and try again.

---

### Post by labrat256 on 2009-12-22
I've looked in all config files I can, nothing.

Also, if I change the proxy server, and then back to direct connection, it works just for that instance of Synaptic. I can download and install new packages with Synaptic after doing that, but as soon as I close it, and reopen it, I have the same problem. Doing this doesn't change the terminal though, it still tries to go through the proxy server.

Something is definitely going wrong here :P

---

### Post by labrat256 on 2010-01-02
Any further thoughts? Or is it worth launching a bug report?

---

### Post by joachimrs on 2010-01-03
I have exactly the same behavior.

I searched a lot of places for my universities proxy but did not find it. If I change the setting in Synaptic it temporarily works. The same is true for the use of the terminal.

I _didi_ change the proxy with apply system wide when I was at university and I changed it back at home.

There is _no_ http_proxy variable set and none are in .bashrc for my user.

When Firefox comes across flash content, he just tried to install and failed downloading. The same is true for update-manager. He happens to find updates, shows them to me but as soon as I want to install the updates he claims he cannot verify the sources and fails consistently on downloading each and every package.

If I switch to the terminal then and run a sudo apt-get update; sudo apt-get upgrade everything is fine.

I suspect it's somewhere in my user's desktop settings, but it's very well hidden.

---

