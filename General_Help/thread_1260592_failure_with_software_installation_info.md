---
title: "failure with software installation info"
date: 2009-09-07
forum: General Help
---

### Post by rwarwarwa on 2009-09-07
Hi there,

I went to BBC to open iplayer. It said I needed realplayer installed. I went to install helix as it says it is the linux player that works as realplayer. 

After install I would try to launch helix from applications but it wouldn't launch.

I now go to add/remove to uninstall helix and I get this

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list'and reload the software information with 'sudo apt-get update' and 'sudo apt-get install -f'

I open synaptic and get this...

E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I know there is info here but could you please tell me what my next step should be. 

Thanks,

rwa

---

### Post by oldos2er on 2009-09-07
Open the file with
```
gksu gedit /etc/apt/sources.list
```
and add a comment mark # in front of line 54. Use Ctrl-I to quickly locate the line.

 Once that's done run
```
sudo apt-get update
```

---

### Post by rwarwarwa on 2009-09-08
Thanks for the reply.

I put in the first line and get...


(gksu:5027): gtk-warning**: cannot open display:

hmm,

thanks,

rwa

---

### Post by Niloc on 2009-09-08
[sudo] password for colin: 
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty Release.gpg
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/main Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/restricted Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/universe Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/multiverse Translation-en_US
Get:1 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates Release.gpg [189B]
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/main Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/restricted Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/universe Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/multiverse Translation-en_US
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security Release.gpg
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/main Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/restricted Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/universe Translation-en_US
Ign [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/multiverse Translation-en_US
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty Release
Get:2 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates Release [49.6kB]
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security Release
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/main Packages                           
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/restricted Packages
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/main Sources     
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/restricted Sources
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/universe Packages
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/universe Sources 
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/multiverse Packages
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty/multiverse Sources
Get:3 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/main Packages [165kB]
Get:4 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/restricted Packages [2589B]
Get:5 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/main Sources [46.7kB]
Get:6 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/restricted Sources [623B]
Get:7 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/universe Packages [54.4kB]
Get:8 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/universe Sources [14.9kB]
Get:9 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/multiverse Packages [6637B]
Get:10 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-updates/multiverse Sources [2117B]
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/main Packages
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/restricted Packages          
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/main Sources
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/restricted Sources
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/universe Packages                  
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/universe Sources                   
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/multiverse Packages                
Hit [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) jaunty-security/multiverse Sources                 
Fetched 343kB in 6s (51.6kB/s)                                                 
Reading package lists... Done
colin@colin-desktop:~$ 

This is all I get, apt-get update has no effect and I cannot find any packages at all!! Such as 'wvdial' or 'Thunderbird', I simply cannot find any packages.
Two laptop computers, same results on both...

Any assistance appreciated..

Colin

---

### Post by rwarwarwa on 2009-09-08
HI Colin,

I think this is not the thread you wanted to reply to.

thanks,

rwa

---

### Post by oldos2er on 2009-09-11
> **rwarwarwa said:**
> Thanks for the reply.

I put in the first line and get...


(gksu:5027): gtk-warning**: cannot open display:


 Which version of Ubuntu are you running?

 Try **sudo nano** in place of gksu gedit. To get to line 54, hit Ctrl-W then Ctrl-T (in nano, those commands are written as  ^W, ^T).

---

### Post by rwarwarwa on 2009-09-11
Hi Ann,

Thanks for the reply. I am running Jaunty Jackalope. I will be back at the computer on Monday and will try that then.

thanks,

rwa

---

### Post by rwarwarwa on 2009-09-14
Hi Ann,

I got somewhere using the sudo nano. I get to what I think is line 54. It says

"deb-http://mirror.noreply.org/pub/tor/jaunty main"
I tried the sudo apt-get update but nothing. I don't see the place to enter that text. 

Thanks much.

rwa

---

