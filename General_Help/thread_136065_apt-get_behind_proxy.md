---
title: "apt-get behind proxy"
date: 2006-02-25
forum: General Help
---

### Post by angst_nu on 2006-02-25
hello,

i am new to linux its my 3 days of journey in ubunto 5.10 need help how to configure my linux box to update using apt-get.

my connection is behind proxy server

---

### Post by astoltz on 2006-02-25
Is your internet connection working at all?  If so, apt-get ought to work also.  What happens when you give the command ```
sudo apt-get update
```The proxy info is under System -> Preferences -> Network Proxy.

---

### Post by cilynx on 2006-02-25
Edit:

What he said...

---

### Post by dcstar on 2006-02-25
[QUOTE=angst_nu]hello,

i am new to linux its my 3 days of journey in ubunto 5.10 need help how to configure my linux box to update using apt-get.

my connection is behind proxy server[/QUOTE]
Synaptic-Settings-Preferences-Network and fill in the Proxy settings.

You may have to restart X (or reboot) to have them work.

---

### Post by angst_nu on 2006-02-27
[QUOTE=dcstar]Synaptic-Settings-Preferences-Network and fill in the Proxy settings.

You may have to restart X (or reboot) to have them work.[/QUOTE]
i set my proxy settings to 
Synaptic-Settings-Preferences-Network and fill in the Proxy settings and put my username and passowrd still the error encountered  407 Proxy Authentication Required.

my /etc/apt/apt.conf settings

ACQUIRE {
http::proxy "http://proxyon.com:8081/"
} 

linuxuser@abing:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  407 Proxy Authentication Required

---

### Post by claes on 2006-02-27
Try and add your username and password for the proxy in /etc/apt/apt.conf
Like this:

[http://username:password@proxyon.com:8081](http://username:password@proxyon.com:8081)

Claes

---

### Post by lamego on 2006-02-27
You can also use the generic environment variable to setup the proxy, before executing the apt related commands just type:
```
export http_proxy=http://user:pass@proxyserver:port
```

---

### Post by zagor on 2006-02-27
hi

I've had several issues with my proxy settings ([http://www.ubuntuforums.org/showthread.php?t=96115&highlight=proxy](http://www.ubuntuforums.org/showthread.php?t=96115&highlight=proxy)) but found two interesting posts through which I could solve my problems:

to set up **Synaptic**:
[http://ubuntuforums.org/archive/index.php/t-1575.html](http://ubuntuforums.org/archive/index.php/t-1575.html)
fill the fields with something like 
user name:passw@host
(no http:// in front, no :8080 at the end)
then fill the port field with the correct prot number (8080, in my case)

to set up **apt-get**:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

sudo gedit /etc/apt/apt.conf

add the following:

ACQUIRE {
http::proxy "http://user name:passw@host:port/"
} 

to set up **wget**:
sudo gedit /etc/wgetrc

uncomment the line with the http_proxy like this:

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
#ftp_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
# If you do not want to use proxy at all, set this to off.
use_proxy = on

The above three things made the trick for me.

Good luck
F.

---

### Post by angst_nu on 2006-02-27
[QUOTE=zagor]hi

I've had several issues with my proxy settings ([http://www.ubuntuforums.org/showthread.php?t=96115&highlight=proxy](http://www.ubuntuforums.org/showthread.php?t=96115&highlight=proxy)) but found two interesting posts through which I could solve my problems:

to set up **Synaptic**:
[http://ubuntuforums.org/archive/index.php/t-1575.html](http://ubuntuforums.org/archive/index.php/t-1575.html)
fill the fields with something like 
user name:passw@host
(no http:// in front, no :8080 at the end)
then fill the port field with the correct prot number (8080, in my case)

to set up **apt-get**:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

sudo gedit /etc/apt/apt.conf

add the following:

ACQUIRE {
http::proxy "http://user name:passw@host:port/"
} 

to set up **wget**:
sudo gedit /etc/wgetrc

uncomment the line with the http_proxy like this:

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
#ftp_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
# If you do not want to use proxy at all, set this to off.
use_proxy = on

The above three things made the trick for me.

Good luck
F.[/QUOTE]
hello,

thanks for the replys its so very helpful to me, i am now able to use apt-get 

i used his settings

ACQUIRE {
http::proxy "http://user name:passw@host:port/"
}

---

### Post by pcrage69 on 2006-03-09
I have tried all the suggestions, but nothing seems to work for me.  I think it's because I need to enter a domain name as part of my username for our proxy here at work.  Such as domain\username:password@proxy:port

For some reason, it's just not working correctly.  Any suggestions?

---

### Post by recover82 on 2006-03-12
At my work we tunnel through a proxy server and I can't do apt-get unless I point the sources.list file to the ftp:// addresses of the repositories.  It is http:// by default and doesn't want to work.  No system proxy settings are changed when I run apt-get...just point to the ftp:// addresses for each.

---

### Post by gusjones on 2006-12-15
> **pcrage69 said:**
> I have tried all the suggestions, but nothing seems to work for me.  I think it's because I need to enter a domain name as part of my username for our proxy here at work.  Such as domain\username:password@proxy:port

For some reason, it's just not working correctly.  Any suggestions?

If I were you I would try omitting your domain name as part of your user name for your proxy, I found that windows needs it for me but ubuntu did not.

Open  a command prompt and try:

export http_proxy=http://username:password@proxy:port

Now try synaptic or apt-get. Basically I've found that what you do at the command prompt overrides all the other network settings.

Something weird I did find though was that I had to on occassion renew my proxy access at the command prompt after a period of  inactivity.

Don't know if this will work for you, but it does save messing about with editing files, etc. and allows you to try out different proxy settings quickly and easily.

For those that are interested I write this post at work behind my proxy and using ubuntu installed on virtual PC running on winblows XP. cool or what? :D

---

### Post by gusjones on 2006-12-15
I hate replying to my own post, but this is necessary.

What I say above may stand but I need to add something I just noticed. When I  tried synaptic this morning it kept coming up with a 407 error (proxy access failed), however, when I then laucnched firefox and authenticated my web browser for access to the net (a dialogue box  comes up prompting for user name and password), and then tried synaptic I then was  able to get through fine. :o 

This is a strange one, perhaps requires a bit of research as to what is really going on underneath it all.

So try web browser first and if you get through with that then try synaptic or apt-get straight afterwards.

---

### Post by cilynx on 2006-12-15
This is a feature of the LAN that you're on.  My school uses the same idea.  When you force authentication before access, you don't have to track your users by physical means such as switch port or MAC address, you can simply track as authenticated users.

---

### Post by gusjones on 2007-03-27
I'm resurrecting this old thread as I'm running into problems, and have tried what has gone before.

Basically I'm running Ubuntu Dapper in VirtualBox (virtualisation software similar to VMware), on an XP host at work - now the problem is in getting apt-get / repositary access using NAT networking from Ubuntu running virtually through my XP host and past my company firewall. I have managed to configure everything fine for the internet but access to apt-get is flaky at best and synaptic just refuses to do anything.

Please see earlier posts as I have done the export_http thing which works fine for the ubuntu box sitting under my desk but doesn't seem to be working properly on my virtual ubuntu (I had this all working fine with VMware Server but unfortunately it had a bug which caused me to trash my company network by sending out DHCP server broadcasts and now I don't use it, the other option VirtualPC, owned by m$ has no linux support and I got nowhere with it). Again internet is mostly fine although access does seem to keep timing out every so often.

If I can't get a solution to this then I am going to chuck an extra network card into my host PC since VirtualBox allows the virtual operating system (in this case ubuntu) to grab the network card and I should hopefully be able to see through the proxy properly from there.

Also what I love about VirtualBox is that it is the only virtualisation software which has full USB support.

So has anyone come across similar problems, perhaps with solutions????

---

### Post by salubrium on 2007-11-22
For domain based authentication, there's two methods you can use depending if it's a windows 2000 domain or Windows 2003 domain.

export http_proxy="domain\\user:password@proxy:port"

Note: the double back slash is required..

or

export http_proxy="use@domainr:password@proxy:port"

---

### Post by charbo on 2007-12-06
Our network uses Windows2003 as proxy server, and it is a Active Directory domain.

export http_proxy="domain\\username:passwd@proxy-server-name:port"

is not working, with the apt-get giving error saying that it cannot resolve

'passwd@proxy-server-name'


Any thoughts?

Thanks in advance.

---

### Post by zagor on 2008-02-15
> **gusjones said:**
>  have managed to configure everything fine for the internet but access to apt-get is flaky at best and synaptic just refuses to do anything.

Please see earlier posts as I have done the export_http thing which works fine for the ubuntu box sitting under my desk but doesn't seem to be working properly on my virtual ubuntu 
[...]
So has anyone come across similar problems, perhaps with solutions????

Could you find a solution to this?
I'm in a quite similar environment: using linux (several distros) in virtualbox (and VMWare sometimes) running on a WinXP, using NAT networking.
In my company, proxy access is needed to reach the internet. I've solved my issues as written in my earlier post (note that synaptic has no final "/", while apt-get has: at least once this has been important for me, for the lack of "/" in the apt-get proxy line was blocking it).
For me it works either in virtualbox and in VMWare. 
In synaptic I need to select only http sources, for the ftp protocol does not go through the proxy.

The only odd thing here, is that sometimes net in virtualbox simply doesn't do everything: I receive an ip but I don't see anything net-related (intranet or internet).

Now, I know it sounds really (REALLY) stupid, but my solution to this is pretty much microsoft-style: after setting up synaptic and apt-get proxies as described in the other post, I simply reboot the virtualmachine and it works...
Don't know how, don't know why.

Possibly you have a smarter and more repeatable solution?

---

