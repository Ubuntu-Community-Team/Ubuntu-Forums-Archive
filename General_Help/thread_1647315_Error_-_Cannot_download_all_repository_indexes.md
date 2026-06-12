---
title: "Error - Cannot download all repository indexes"
date: 2010-12-17
forum: General Help
---

### Post by bhala on 2010-12-17
Hi ,

I am new to the ubuntu environment and have been using it only since Maverick has been realeased. All was going smooth, till i got this error while updating few days back.

I am attaching my sources.list & the error message i got in terminal while i tried 'sudo apt-get upgrade'
**Sources.list :**
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick universe
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse


```

**Error Msg :** 

```
W: Failed to fetch
http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg
Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch 
http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg 
Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch 
http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg 
Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Can anyone tell me , what should be done to get the updates running again ?

---

### Post by pellgarlic on 2010-12-17
hi. it sounds like your dns resolution isn't working ("No address associated with hostname").

can you try this in your terminal:

```
# ping archive.canonical.com
```

if it says:

```
# ping: unknown host archive.canonical.com
```

it means the "domain name" can't be resolved to an ip address.


paste the output of:

```
# cat /etc/resolv.conf
```

to see what nameservers your machine is using. if you're using a router, it will probably be the router's ip.

---

### Post by bhala on 2010-12-17
Hi, 

Thanks for the quick reply !
I am able to ping 'archive.canonical.com' 

**Output :**
```
PING archive.canonical.com (91.189.88.33) 56(84) bytes of data.
64 bytes from scandium.canonical.com (91.189.88.33): icmp_req=1 ttl=55 time=277 ms
64 bytes from scandium.canonical.com (91.189.88.33): icmp_req=2 ttl=55 time=286 ms
64 bytes from scandium.canonical.com (91.189.88.33): icmp_req=3 ttl=55 time=278 ms
64 bytes from scandium.canonical.com (91.189.88.33): icmp_req=4 ttl=55 time=284 ms
64 bytes from scandium.canonical.com (91.189.88.33): icmp_req=5 ttl=55 time=286 ms
^Z
[3]+  Stopped   
```

And i am using a router to connect to my home network in a different floor.
Also i have configured my router for OpenDNS if it helps.

**Output of 'cat /etc/resolv.conf' :**

```
bhala@NEO:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain Bunker
search Bunker
nameserver 10.8.16.1

```

---

### Post by pellgarlic on 2010-12-17
hi. it seems that this *may* be a bug:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

in that thread, there are a couple of things that are suggested.

one is to use "aptitude" instead of "apt-get". aptitude is newer, and better at many things, so i would recommend using it rather than apt-get anyway... so try an "aptitude update" and see if it's any better.

the other option mentioned, is to try manually changing your DNS server to 8.8.8.8 (or some other if you have a preference). you could try setting the opendns ip directly in your /etc/resolv.conf file (note - if this helps, you will need to do some more steps to make that change permanent...)

hope one of these helps...

---

### Post by bhala on 2010-12-17
Hey,

That did the trick !! Changing the DNS nameserver in resolv.conf got it working.
Thanks for the help.
 :) 
What you mentioned by making the changes permanent is to change the DNS manually in the router,right ?

Just to gain a little know how, if you don't mind, what exactly could have caused this conflict? I was using the same setup even before this problem arose. 
One more thing is should i install the aptitude package before using it?

Thanks for your time. Much appreciated.
Cheers,
Bhala.

---

### Post by pellgarlic on 2010-12-17
to be honest, i don't completely understand what causes the problem, but it seems to be related to the way apt-get resolves ip addresses, and the fact that resolv.conf points to a router, instead of directly to a nameserver, confusing apt-get. i could be wrong on that though.

to make the changes permanent, i meant to make the "resolv.conf" retain the new nameserver - that file is automatically written to by NetworkManager, so the entry you have added will be removed by the system at some point.

however, i would recommend trying "aptitude" first, (change the resolv.conf back to what it was, to make sure that using aptitude actually makes a difference). aptitude should be installed by default, if you're using a relatively recent release of ubuntu. it's used in the same way as apt-get. making a permanent change to resolv.conf would be a less preferable option. if it comes to that, i can show you how though.

---

### Post by bhala on 2010-12-17
Am using maverick but still, had to download aptitude using apt-get. 

But using aptitude update showed the same errors again !!

---

### Post by pellgarlic on 2010-12-17
=o i didn't actually realise that aptitude had been removed from ubuntu maverick... =\ i'm kind of stunned.

ok, to make the nameserver permanent in resolv.conf, you do this:

```
vim /etc/dhcp3/dhclient.conf
```

find this line:

```
#prepend domain-name-servers 127.0.0.1;
```

uncomment it, and replace "127.0.0.1" with your desired DNS server ip. next, in the line that starts like this:

```
request subnet-mask, broadcast-address...
```

remove the "domain-name-servers" entry. save and close the file (:wq).

---

### Post by bhala on 2010-12-17
Hey man,

Its done ! Thanks for the help :)

---

### Post by pellgarlic on 2010-12-17
glad to have helped =)

---

