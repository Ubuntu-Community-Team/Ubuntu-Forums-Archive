---
title: "How do i upgrade Thunderbird??"
date: 2006-04-23
forum: General Help
---

### Post by morbid_bean on 2006-04-23
How do i upgrade my thunderbird from 1.0.7 to the newest version??!!!!please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by aysiu on 2006-04-23
Download [this script](http://www.ubuntuforums.org/showpost.php?p=950010&postcount=21) to your desktop and then go to Applications > Accessories > Terminal and copy and paste these commands: ```
cd ~/Desktop
mv installnewthunderbird.sh.txt installnewthunderbird.sh
chmod +x installnewthunderbird.sh
./installnewthunderbird.sh
```

---

### Post by FLeiXiuS on 2006-04-23
I thought thunderbird auto-updated it's self.  Hmm, I guess it's a parameter in the configuration some where..

---

### Post by morbid_bean on 2006-04-23
Ok cool, and ive noticed in most of my threads you have been the biggest help amost every time.   THANKS! For this   and thanks for all the other support :) ..............we all start somewhere so.... lol

---

### Post by aysiu on 2006-04-24
[QUOTE=FLeiXiuS]I thought thunderbird auto-updated it's self.  Hmm, I guess it's a parameter in the configuration some where..[/QUOTE] Well, this is one of those little gaps. If Ubuntu manages Thunderbird, it'll auto-update to the latest Ubuntu version, but that latest Ubuntu version is 1.0.7 in Breezy. Then, starting with 1.5, Thunderbird (the application itself--not Ubuntu) auto-updates itself.

[quote=morbid_bean]Ok cool, and ive noticed in most of my threads you have been the biggest help amost every time. THANKS! For this and thanks for all the other support  ..............we all start somewhere so.... lol[/quote] In all fairness, I modified the Thunderbird script slightly to update it to 1.5.0.2, but it was originally written by Ensnared, based off my Firefox script, which itself was based on the [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) entry, which was written by someone else (I don't know who).

So... we're all in it together.

---

### Post by mlissner on 2006-04-27
Beautiful. Thanks!

---

### Post by Hoffmann on 2006-04-28
[QUOTE=aysiu]Download [this script](http://www.ubuntuforums.org/showpost.php?p=950010&postcount=21) to your desktop and then go to Applications > Accessories > Terminal and copy and paste these commands: ```
cd ~/Desktop
mv installnewthunderbird.sh.txt installnewthunderbird.sh
chmod +x installnewthunderbird.sh
./installnewthunderbird.sh
```[/QUOTE]

aysiu:

If I upgrade Thunderbird by following your approach, what will happen when I upgrade to Ubuntu Dapper? I mean, is this new Thunderbird going to bee keeped? 
I already upgraded Firefox to the lattest version (by following another approach). Would  you have any comment about that too?
Thanks!
Hoffmann

---

### Post by aysiu on 2006-04-28
The script "installs" Mozilla's Thunderbird next to Ubuntu's Thunderbird. They co-exist, and there's a pointer from the Thunderbird launcher to the Mozilla version.

---

### Post by Hoffmann on 2006-04-28
[QUOTE=aysiu]The script "installs" Mozilla's Thunderbird next to Ubuntu's Thunderbird. They co-exist, and there's a pointer from the Thunderbird launcher to the Mozilla version.[/QUOTE]

Just one more question:

After upgrading the new Thunderbird, I can remove the script. Is that correct?

Thanks,
Hoffmann

---

### Post by aysiu on 2006-04-28
[QUOTE=Hoffmann]Just one more question:

After upgrading the new Thunderbird, I can remove the script. Is that correct?

Thanks,
Hoffmann[/QUOTE] Yes.

---

### Post by 4ebees on 2006-04-29
Hi Aysiu,

May I ask a quick question on the end here?

I have a fresh install of 5.10 and have not installed Thunderbird. Do I have to install T'bird for this to work... or should I merely install 1.5 and not install the version from the repos?

PS. I can understand morbid-bean's sentiment :)

Many Regards.

---

### Post by aysiu on 2006-04-29
[QUOTE=4ebees]Hi Aysiu,

May I ask a quick question on the end here?

I have a fresh install of 5.10 and have not installed Thunderbird. Do I have to install T'bird for this to work... or should I merely install 1.5 and not install the version from the repos?

PS. I can understand morbid-bean's sentiment :)

Many Regards.[/QUOTE] Well, no.

1. You don't need to have Ubuntu's Thunderbird in order to use Mozilla's Thunderbird.

2. Ensnared's script makes sure you have Ubuntu's Thunderbird installed anyway, just in case.

---

### Post by 4ebees on 2006-04-30
Hiya,

I installed the script and let it run it's course... but I cannot run T'bird without being root?

I have to open konqueror as a superuser and then click on the 'thunderbird' file... if I try the same as ME nothing happens ????

It will not launch in any other fashion. 'Natch if I start is as root it will install .thunderbird in /root/

Can you help me work out what the problem may be please?

I have changed permissions on the folder and files in T'bird in /opt and I have firefox 1.5 installed in the same directory (so I know something works from there). I'm afraid I'm at a bit of a loss. It has me buggered.

---

### Post by aysiu on 2006-04-30
Can you try typing this in the terminal and then posting back here the output? ```
sudo chmod -R 755 /opt/thunderbird
cd /opt/thunderbird
./thunderbird
```

---

### Post by 4ebees on 2006-04-30
I uninstalled Thunderbird completely (the old one) and then re-ran it:
I ran the script and got:
Backing up old Thunderbird preferences
cp: cannot stat `/home/patrick/.mozilla-thunderbird': No such file or directory
Creating symlink to new version data-dir ~/.thunderbird
ln: `/home/patrick/.thunderbird': File exists
Changing to home directory
Downloading Thunderbird from the Mozilla site
--01:59:05--  [http://mozilla.mirrors.tds.net/pub/mozilla.org/thunderbird/releases/1.5.0.2/linux-i686/en-US/thunderbird-1.5.0.2.tar.gz](http://mozilla.mirrors.tds.net/pub/mozilla.org/thunderbird/releases/1.5.0.2/linux-i686/en-US/thunderbird-1.5.0.2.tar.gz)
           => `thunderbird-1.5.0.2.tar.gz'
Resolving mozilla.mirrors.tds.net... 216.165.129.134
Connecting to mozilla.mirrors.tds.net|216.165.129.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,600,318 (10M) [application/x-gzip]

100%[=========================================>] 10,600,318   155.82K/s    ETA 00:00
02:00:12 (156.03 KB/s) - `thunderbird-1.5.0.2.tar.gz' saved [10600318/10600318]
Unzipping the .tar.gz file
Removing the unzipped .tar.gz
rm: cannot remove `thunderbird-1.5.tar.gz': No such file or directory
Linking launcher to new Thunderbird
Leaving `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'
The new Thunderbird is installed.

Where is says:
ln: `/home/patrick/.thunderbird': File exists
this file point to /home/patrick/.mozilla-thunderbird
which doesn't exist(?)

so I go:
sudo chmod -R 755 /opt/thunderbird
cd /opt/thunderbird
./thunderbird

and...

nothing happens.

Again, if I try to click on a root user... it works(?)

I know it's weird... again, and sorry for the pestering, but I'm at a loss.

---

### Post by aysiu on 2006-04-30
I'm at a loss, too.

*chmod 755* means everyone can read and execute and only the owner can write to it.

That thing about the .thunderbird file already existing and .mozilla-thunderbird not existing shouldn't affect the application launching, as those are just preference files.

What if we changed the ownership? ```
sudo chown -R 4ebees:4ebees /opt/thunderbird
cd /opt/thunderbird
./thunderbird
```

---

### Post by 4ebees on 2006-04-30
[QUOTE=aysiu]I'm at a loss, too.

*chmod 755* means everyone can read and execute and only the owner can write to it.

That thing about the .thunderbird file already existing and .mozilla-thunderbird not existing shouldn't affect the application launching, as those are just preference files.

What if we changed the ownership? ```
sudo chown -R 4ebees:4ebees /opt/thunderbird
cd /opt/thunderbird
./thunderbird
```[/QUOTE]

Do you mean
What if we changed the ownership? [code]sudo chown -R patrick:patrick

---

### Post by 4ebees on 2006-04-30
[QUOTE=4ebees]Do you mean
What if we changed the ownership? [code]sudo chown -R patrick:patrick[/QUOTE]

just did 
sudo chown -R patrick(with colon)patrick /opt/thunderbird

./thunderbird

nothing

?????

---

### Post by 4ebees on 2006-04-30
[QUOTE=4ebees]just did 
sudo chown -R patrick(with colon)patrick /opt/thunderbird

./thunderbird

nothing

?????[/QUOTE]


Hmmmmmm... I've never used evolution or Kmail :)
](*,)

---

### Post by cooldudejz on 2006-04-30
what are the differences between 1.07 and 1.5. and if i upgrade to 1.5 will it use all my accounts and addresses from 1.07.thanx

---

### Post by aysiu on 2006-04-30
[QUOTE=4ebees]Hmmmmmm... I've never used evolution or Kmail :)
](*,)[/QUOTE] This is really baffling me.

Apparently it's a common problem. I've seen at least four people on these forums complain about Thunderbid 1.5 not working for them.

At the same time, I've personally used both the Wiki instructions *and* Ensnared's script (separately, of course), and have never had any problem with it. I wonder if there's some step you're missing, but I can't think of what it might be.

I guess... until we get this sussed out, you may want to try Evolution or KMail.

[quote=cooldudejz]what are the differences between 1.07 and 1.5. and if i upgrade to 1.5 will it use all my accounts and addresses from 1.07.thanx[/quote] 1.5 is the more up-to-date version. For the differences, read the release notes: > What's New in Thunderbird 1.5.0.2

Thunderbird 1.5.0.2 provides stability and security enhancements that are part of our ongoing program to provide a safer email experience for our users. We recommend that all Thunderbird users upgrade to this latest version.

Here's what's new in Thunderbird 1.5.0.2:

    * Improvements to product stability.
    * Several security fixes.
    * 1.5.0.2 does not include Universal Binary support for Mac OS X. We hope to have this ready for 1.5.0.3.

The Rumbling Edge has a more detailed list of notable bug fixes.

Release Date: April 21, 2006 If you use Mozilla's Thunderbird, the mail configuration files will be in /home/cooldudejz/.thunderbird, but if you use Ubuntu's Thunderbird, the mail config files will be in /home/cooldudejz/.mozilla-thunderbird, so you'd have to copy the folder over and rename it.

---

### Post by 4ebees on 2006-04-30
Yeah, I was wondering myself... but I went back and checked everything and ... well, it seems to work as root.. VERY weird.
I can't quite work it out.

I don't want to run it as root, natch.

I've included myself in the groups
patrick
users
mail

none of which has helped.

This may seem a little unrelated however...
I changed the root password to blahblah and my user password to blah.

Now I can use blah if I 

sudo

but need

blahblah 

if I

su

Unrelated (I'm new to Ubuntu as my main desktop distro. I've been using FC3 and 4 - but couldn't get my webcam going as I have hyperthreading on my chip - thus an SMP kernel, and FC4 and the pwc drivers with smp didn't mesh :(  My laptop has FC4 (standard P4 chip) and it's fine... my desktop... well, another story. The short version is that I found out by trial and error on a spare hdd that Ubu would run my webcam, scanner, and graphic tablet... and...well, here I am - this is my explanation for my confusion surrounding sudo/su and Ubu's oddities :) :)  - no flaming now, please :)

So, in summary, would this have ANY effect? :-k

---

### Post by 4ebees on 2006-05-14
Okay, here's what I did. I reinstalled (remember, this is a spare HDD so no harm) and then installed Thunderbird.

I tried out the script... no luck again.

I uninstalled anything relating - new and old, links etc.

I installed T'bird in /opt

Added the following to F'fox in about:config

network.protocol-handler.app.mailto

then set 'status' as 'userset', 'type' as 'string' and then added:

/opt/firefox/firefox

Now when I click on a mailto link in F'fox it opens T'bird.

Then in /home/patrick/.thunderbird/[defaultname].default/

I opened the pref.js file and added

user_pref("network.protocol-handler.app.http", "/opt/firefox/firefox");
user_pref("network.protocol-handler.app.https", "/opt/firefox/firefox");

This was all whilst Thunderbird was closed.

Now if I have a URL link inside an e-mail and click on it, it opens Firefox.

You can do the same with Opera if you wish 
(just change /opt/firefox/firefox to the relevant directory for Opera)

So, managed to sort out my problem and everything is "FAB, Virgil" :)

Disclaimer: None of the above is my creation. I have picked up all this from posts in Ubuntu, Opera, Fedora Core, Firefox and Thunderbird forums. Any credit due is to those people not me.

---

