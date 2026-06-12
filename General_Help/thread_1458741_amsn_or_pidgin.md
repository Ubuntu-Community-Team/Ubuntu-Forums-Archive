---
title: "amsn or pidgin"
date: 2010-04-20
forum: General Help
---

### Post by croaken on 2010-04-20
Hi! :)
I have this problem, that i doesnt have pidgin installed on my computer. 
I thought it would be there from the beginning? I guess I was wrong
Anyways, i have tried to install both pidgin and amsn through packages
from internet, but one time the package couldnt be found when i tried to install and
the other time there were nothing else than the package on the site, and no 
description how to install it. As a beginner i think those things are very useful :)

So can anybody give me a helping hand to get through these problems?
Give me an instruction of what to do and I'll tell everything that comes in the way. :)
(it doesnt matter if its pidgin or amsn)

(I think i have the version before the latest of ubuntu. I'm not sure how to check but i think that's the case!)

Thank you!

croaken

---

### Post by jaco223 on 2010-04-20
> **croaken said:**
> Hi! :)
I have this problem, that i doesnt have pidgin installed on my computer. 
I thought it would be there from the beginning? I guess I was wrong
Anyways, i have tried to install both pidgin and amsn through packages
from internet, but one time the package couldnt be found when i tried to install and
the other time there were nothing else than the package on the site, and no 
description how to install it. As a beginner i think those things are very useful :)

So can anybody give me a helping hand to get through these problems?
Give me an instruction of what to do and I'll tell everything that comes in the way. :)
(it doesnt matter if its pidgin or amsn)

(I think i have the version before the latest of ubuntu. I'm not sure how to check but i think that's the case!)

Thank you!

croaken

Try this:
Open a terminal window and type
```

sudo apt-get update

sudo apt-get install pidgin
```
Or 

```
sudo apt-get install amsn
```
You should be able to install one or both of them. i just tried and there was
no problem.
Hope this helps.

Jaco

---

### Post by jaco223 on 2010-04-20
To check your version of Ubuntu open a terminal and type

```
lsb_release -a
```


Jaco

---

### Post by croaken on 2010-04-20
> **jaco223 said:**
> Try this:
Open a terminal window and type
```

sudo apt-get update

sudo apt-get install pidgin
```Or 

```
sudo apt-get install amsn
```You should be able to install one or both of them. i just tried and there was
no problem.
Hope this helps.

Jaco

I just tried this and when i typed sudo apt-get update, 
in the beginning most files is "ign" and some "hit"
then ther is about 12 error-files (404 not found)
and another ten that is "failed to fetch"

and then i  typed sudo apt-get install pidgin and it says
"Package pidgin is not aviable, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. However the following packages replace it: libpurple-bin libpurlple0

when i wrote sudo apt-get install amsn it only said "couldn't find package amsn"

Do i have to download a package from the net? 
thank you for helping me !

---

### Post by jaco223 on 2010-04-20
Croaken try this link to install pidgin

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

And this link for amsn

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1)

Select which version of Ubuntu you're using, scroll down the page to where it says Download amsn.
Hope this helps.

Jaco

---

### Post by _0R10N on 2010-04-20
Well, it looks like you're having a conflict in your sources.list. That could be the cause of why packages are not being installed. Post it please!

Kind regards!

_0R10N >>

---

### Post by croaken on 2010-04-20
> **jaco223 said:**
> Croaken try this link to install pidgin

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

And this link for amsn

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1)

Select which version of Ubuntu you're using, scroll down the page to where it says Download amsn.
Hope this helps.

Jaco

It's strange how things can be so difficult :/ When i clicked "install this now" at the link for pidgin you gave me, a window came up and said
"[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/I]"

and this is the files that were listed:
"[I]Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz](http://ubuntu.gnu.gen.tr/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/I]"

I dont know if it helps i i copy everything but to be sure, i do it anyways :)

And then, when i tried downloadning amsn, i could choose either to just save file or to open it with GDebi Package Installer. And when i open with the package installer, it says "Error: Wrong architecture 'i386'"

please help 
thank you jaco for your support and help :)!!

---

### Post by nitstorm on 2010-04-20
> **croaken said:**
> And when i open with the package installer, it says "Error: Wrong architecture 'i386'"


Are u using 64-bit ???? or 32-bit?

---

### Post by croaken on 2010-04-20
> **nitstorm said:**
> Are u using 64-bit ???? or 32-bit?

Tell me how i check that and i'll do it!

---

### Post by jaco223 on 2010-04-20
> **nitstorm said:**
> Are u using 64-bit ???? or 32-bit?

+1. Check if you have a 32bit or 64bit system installed. Open a terminal and type:

```
cat /proc/version
```

Post the output of that please.

Thanks.

---

### Post by croaken on 2010-04-20
> **jaco223 said:**
> +1. Check if you have a 32bit or 64bit system installed. Open a terminal and type:

```
cat /proc/version
```

i cant see if i have a 32bit or 64bit system out of this but i guess you can :)
this is what it says:
"Linux version 2.6.31-16-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009"

---

### Post by nitstorm on 2010-04-20
actually the code is 
```
 uname -m
```

Please post the output of this please :)

---

### Post by jaco223 on 2010-04-20
Try this link and see if you can get Pidgin installed.

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

Follow the instructions there, and you should be able to get it installed.

Jaco

---

### Post by croaken on 2010-04-20
> **jaco223 said:**
> Try this link and see if you can get Pidgin installed.

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

Follow the instructions there, and you should be able to get it installed.

Jaco

thank you it works now, finally! :)
i wish amsn had something like this too

thanks for all your help, jaco!

---

### Post by jaco223 on 2010-04-20
> **croaken said:**
> thank you it works now, finally! :)
i wish amsn had something like this too

thanks for all your help, jaco!


Glad you got one installed! 

Not sure if you're using 32bit or 64bit, but here's the link for amsn.

[http://packages.ubuntu.com/lucid/amd64/amsn/download](http://packages.ubuntu.com/lucid/amd64/amsn/download)

---

### Post by jaco223 on 2010-04-20
> **croaken said:**
> thank you it works now, finally! :)
i wish amsn had something like this too

thanks for all your help, jaco!


Glad you got one installed! 

Not sure if you're using 32bit or 64bit, but here's the link for amsn.

[http://packages.ubuntu.com/lucid/amd64/amsn/download](http://packages.ubuntu.com/lucid/amd64/amsn/download)

[http://packages.ubuntu.com/lucid/i386/amsn/download](http://packages.ubuntu.com/lucid/i386/amsn/download)

---

### Post by trig on 2010-04-20
Or go into synaptic and type pidgin, that is hoe i installed it.

---

### Post by trig on 2010-04-20
image of synaptic

---

