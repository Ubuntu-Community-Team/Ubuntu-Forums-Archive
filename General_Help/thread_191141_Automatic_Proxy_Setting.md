---
title: "Automatic Proxy Setting"
date: 2006-06-07
forum: General Help
---

### Post by t0mc4t on 2006-06-07
First, sorry for double posting.. but I really need this help.. ](*,) 

My university using automatic proxy script to access its network.
How do I configure ubuntu to work with it? I have configured firefox successfuly, but I don't know how to configure the system. For example for synaptic to access the update, lynx (text browser), and GAIM, etc...
I have tried to put the script on Network Proxy from System Preferences on GNome but it didn't work.

Thanks...

---

### Post by Lunar_Lamp on 2006-06-07
NOTE: don't take what is written here as a walkthrough, but as some pointers - I bumbled my way through setting this up twice.  The first time it worked simply, the second time it didn't.  You will want to try changing settings in synaptic itself before messing around with exporting http_proxy.  

My unversity does the same - and it's a little bit tricky.

My university used the script: [http://www-addresss-in-here/proxyall.pac](http://www-addresss-in-here/proxyall.pac)

This is not possible to use in many circumstances.  You need to know the ports that your proxy uses - I think 8080 is often a default, but my uni uses something different (3128).

Test out whether this works when you type it in a terminal: export http_proxy="http://PROXY:PORT/"

Then sudo synaptic on the command line.  If it does then you want to keep that setting (currently you have set your proxy in bash just for the terminal you are using and until you close it - good for testing, but not good for a permanent change!):

"sudo nano ~/.bashrc"

and add the line (obviously edit to your needs):
[code]
# export proxy so that synaptic can be used from command line
export http_proxy="http://wwwcache.nottingham.ac.uk:3128/"
[code]

remember the / after the port!!

I am not sure, but you MAY need to do this as root user also (I had a lot of trouble setting this up and so tried many things, so cannot be certain which are required in the end).  When I say root user, I mean that you have to "su" and then edit it as root also - two different bash profiles.  I don't see why you should have to do this though.

Then you need to open a new terminal (bashrc is only read when opening up a new terminal).  Try "sudo synaptic", which should open a command line version - hopefully this should work.  If not try fiddling with your proxy settings in synaptic (proxy and port number again - if you haven't tried this at all - try this before anything else, you may be lukcy).

If this works, i.e. you can run synaptic from the command line - try editing the synaptic command that runs on the menu (using alacarte menu editor) to be: gksudo synaptic.

---

### Post by t0mc4t on 2006-06-07
I don't really understand your "how to" step.. But I will try it..
Thanks...

---

### Post by Lunar_Lamp on 2006-06-07
Basically, your problem is that synaptic needs to be setup to use your proxy.  For some reason it doesn't seem to pick up the default settings.

Your first port of call should be to open synaptic manager then, settings>preferences>network.

Choose manual proxy configuration, and input the details in.

If you are having problems working out what port you need to use - try searching your uni's website for details.

---

### Post by izhar81 on 2007-11-30
> **Lunar_Lamp said:**
> Basically, your problem is that synaptic needs to be setup to use your proxy.  For some reason it doesn't seem to pick up the default settings.

Your first port of call should be to open synaptic manager then, settings>preferences>network.

Choose manual proxy configuration, and input the details in.

If you are having problems working out what port you need to use - try searching your uni's website for details.

I'm using Feisty,

but the main problem is i dont know what to put in Synaptic Manager > Manual Proxy Configuration...

the only data i have is Automactic Procy Configuration.pac url. Can i extract the info of .pac by typing it at browser address?

---

