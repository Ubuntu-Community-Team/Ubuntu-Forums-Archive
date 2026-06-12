---
title: "Software Center crashed because of Platinum arts sandbox"
date: 2011-11-06
forum: General Help
---

### Post by Stawl on 2011-11-06
Hello everyone,
I did my search on the forum, and found that many people have had the same problem as I, but mine is a little different. I installed Platinum Arts Sandbox GameMaker from Ubuntu Software center and it crashed in the middle, now after several reboots and attempts at trying to remove it it still doesn't let me install/uninstall anything. I want to install other packages and it goes just fine until 75%(example) says "applying changes" and shows a dpkg gui with no content and just freezes there.

apt-get remove sandboxgamemaker does not work 
Error -> "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

apt-get update/upgrade doesn't work
Update Error -> Does the update but in the end shoes the above error.
Upgrade Error -> Exactly the same error as the above above.

If i do run the command line dpkg --configure -a it starts downloading the package which i no longer want plus, it freezes at 3% all the time.

I also run the update manager but it does exactly the same, says that some packages are not completely installed and starts downloading. (Freezing in the 3%) 

I seriously do not want to install xubuntu again... Can anyone help me out? I believe i did everything that came up in the search, still not working...

P.S: I'm using Xubuntu 11.04 fresh installation. This is kinda urgent to me.

Best regards,
Stawl

---

### Post by TeoBigusGeekus on 2011-11-06
Try
```
sudo apt-get install -f
```

---

### Post by Stawl on 2011-11-06
> **TeoBigusGeekus said:**
> Try
```
sudo apt-get install -f
```

:( Exactly the same error: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

This is what i get: 
```

sudo dpkg --configure -a
Setting up sandboxgamemaker (2.6.1+dfsg-7) ...
Cleaned old data
--2011-11-06 18:48:42--  http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.6.1Multiplatform.zip
Resolving sandboxgamemaker.com... 69.163.252.177
Connecting to sandboxgamemaker.com|69.163.252.177|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.6.1Multiplatform.zip [following]
--2011-11-06 18:48:50--  http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.6.1Multiplatform.zip
Resolving www.sandboxgamemaker.com... 69.163.252.177
Connecting to www.sandboxgamemaker.com|69.163.252.177|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 300469867 (287M), 300288588 (286M) remaining [application/zip]
Saving to: `PlatinumArtsSandbox2.6.1Multiplatform.zip'

 0% [                                       ] 191,071     --.-K/s  eta 6d 21h  ^

```

---

### Post by TeoBigusGeekus on 2011-11-06
Ok, try with these
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Stawl on 2011-11-06
> **TeoBigusGeekus said:**
> Ok, try with these
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
sudo apt-get upgrade
```

Still the same error... :(
I just removed /var/cache/sandboxgamemaker (read that it might work in the search)
But still doesn't.

Thanks in advance TeoBigusGeekus

---

### Post by TeoBigusGeekus on 2011-11-06
> **Stawl said:**
> Still the same error... :(
I just removed /var/cache/sandboxgamemaker (read that it might work in the search)
But still doesn't.

Thanks in advance TeoBigusGeekus

Don't thank me, I run out of ideas :(
Anyone else?

---

### Post by Stawl on 2011-11-06
Well, I installed xubuntu in 3 laptops and Platinum in all of them thats why i didn't want to reinstall xubuntu =) but seems like i have no other choice. Thanks for the very fast reply.

I'll just eat some :popcorn: while i watch them install.

Keep up the good work forum =)
Best regards,
Stawl

---

### Post by crunchy_chicken on 2011-11-30
apparently this issue with platinum arts sandbox wasn't resolved 100% because i had the same thing happen, however, it is downloading using the dpkg method. if it does install properly, who knows, i might try it.

---

### Post by Soup127 on 2012-09-23
I am having this same problem except the "applying changes" freeze occurred during an installation of Adobe Flash Player. Now it pretty much freezes when I install anything, and freezes when the Update Manager tries to do a download to correct the Adobe Flash Player installation. I've used Ubuntu before, but I'm pretty much clueless when it comes to Linux. I'm software savvy, and I'm sure I could get the simple code down, if someone could break it down for me really slowly. I had one buddy who turned my onto Ubuntu originally and he told me to run some sudo command for a problem I was having way back, and yeah basically, I got nowhere and his brief responses to my troubles were further frustrating. So yeah, I'll try anything, but please translate what the variables refer to, maybe plug in the variables for me... I would really like to learn but don't have a lot of time to study this right now. But I installed Ubuntu on my desktop to fix this ARP Spoofing problem I was getting in Windows (I used to have it on my laptop before that crashed). I'm running Ubuntu 12.04 LTS. My graphics card may be why the problems were difficult to install... it sometimes makes a little clicking noise. I got it at a recycled computer parts DIY fix-it store and it actually works, as opposed to my last one, so I'm stoked, don't mind the occasional noise. I just checked and it says my Graphics Driver is unknown?? OK, well... I think that's all the info.


> **Stawl said:**
> Hello everyone,
I did my search on the forum, and found that many people have had the same problem as I, but mine is a little different. I installed Platinum Arts Sandbox GameMaker from Ubuntu Software center and it crashed in the middle, now after several reboots and attempts at trying to remove it it still doesn't let me install/uninstall anything. I want to install other packages and it goes just fine until 75%(example) says "applying changes" and shows a dpkg gui with no content and just freezes there.

apt-get remove sandboxgamemaker does not work 
Error -> "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

apt-get update/upgrade doesn't work
Update Error -> Does the update but in the end shoes the above error.
Upgrade Error -> Exactly the same error as the above above.

If i do run the command line dpkg --configure -a it starts downloading the package which i no longer want plus, it freezes at 3% all the time.

I also run the update manager but it does exactly the same, says that some packages are not completely installed and starts downloading. (Freezing in the 3%) 

I seriously do not want to install xubuntu again... Can anyone help me out? I believe i did everything that came up in the search, still not working...

P.S: I'm using Xubuntu 11.04 fresh installation. This is kinda urgent to me.

Best regards,
Stawl

---

### Post by Soup127 on 2012-09-23
Also, I was looking at some other strings and there is mention of Adobe Flash having difficulty with playback on NVidia drivers. Not sure if this is related at all, but my motherboard is NVidia... possibly my video card too... I cracked the case and peeked at it, it is a TNT2 M64 32 MB PCI, PV-T03B-B4... which when I do a Google search for it says could quite possibly be at an NVidia, either that or Riva or Pine Technology... I'm not sure. But it is probably the NVidia, I suspect, since Adobe Flash has had problems with that company's card in other ways.

---

### Post by Soup127 on 2012-09-23
Here is the message it gives me when Update Manager tries to fix it:

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

-Then I click it and it says "flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.238.orig.tar.gz" but then doesn't do anything else after that.

---

