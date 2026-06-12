---
title: "Ubuntu Tweak and Iron Web Browser"
date: 2011-04-20
forum: General Help
---

### Post by ClientAlive on 2011-04-20
Hi,

There are two apps I am interested in and was hoping I could get some direction on.

The first is Ubuntu Tweak. I definitely want this one. I don't see this in Synaptic at all. I wonder if I just don't have the repo installed that it comes from? Or is there some other way I should get it? Just did an update so synaptic should be up to date with what repos it has.

The other app I (think) I would like to try out is the Iron Web Browser. I only say "I think" because if it is know to be all buggy and have all kinds of problems - I don't want to deal with that. I've been on the internet for a couple hours now about this one and am getting limited and odd information. I see posts from a year or two ago asking the same question as I am (getting Iron) but no real closure/ solution. (Maybe I'm just not finding it).

Also, with Iron, I'm a little confused as to which is the latest version (assuming I could even get it on my system and run it). I did see a request submitted in 2010 for Iron to be included in Ubuntu repo; and, as you follow the comments through that page, it says it was added (that was quite a while back now). I d0 not get Iron in Synaptic either though. Wonder again if I just don't have the right repo installed for that one or what the deal is?

Does anyone have any information about this?

Here's the link to that bug report where they say they added it:  [https://bugs.launchpad.net/ubuntu/+bug/483473](https://bugs.launchpad.net/ubuntu/+bug/483473)

Well I think that's what they are saying.

By the way, I am running Ubuntu 11.04 (Natty Nahrwal) and the repos I have in Synaptic are for it. I also have the repos for medibuntu (both source and regular) but they are the ones for natty and I don't think anything is available for them yet. That's why they don't work/ get me anything.

I'm sorry I couldn't just figure this out better on my own. I don't know very much about Linux yet and a lot of the information I find is so over my head that I end up spending hours upon hours trying to figure out what they are talking about and end up side tracked and everything. I can hardly just accomplish what I set out to do. I just wanted to ask someone about it and maybe get some direction at least so I know where/ what to even look for or try to do.

If anyone can advise me on this I would sure be grateful.

Thanks

---

### Post by Frogs Hair on 2011-04-20
Ubuntu Tweak is a very handy application , just down load it , save it and double click the package . If you want the testing version with the newest features enable the source in the stable version once installed. I have not tried the Iron browser.

Here is the PPA for Ubuntu Tweak , enter commands in the terminal on at a time 

sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak




[http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

### Post by ClientAlive on 2011-04-20
> **Frogs Hair said:**
> Ubuntu Tweak is a very handy application ,  just down load it , save it and double click the package . If you want  the testing version with the newest features enable the source in the  stable version once installed. I have not tried the Iron browser.

[http://ubuntu-tweak.com]("http://ubuntu-tweak.com/")




Thanks Frogs Hair. I'm sitting here right now just chomping at the bit for both of these. I think Ubuntu Tweak will be easy enough to find and download. Iron seems to be a little more elusive though.

I wonder if I need to pay attention to what file type I'm downloading or something like that? If I get the wrong one - like the (tarball?) of it, would I be complicating matters for myself?


Thanks
:)

-------------------------------

Add: Oops! Didn't see the link till after I wrote that. Guess I got a little too excited.

:popcorn:

---

### Post by ClientAlive on 2011-04-20
When I double click the file for Ubuntu Tweak I think Synaptic is telling me there's a dependency it has that it can't get for me?

The picture attached shows what I get when I double click the file.

---

### Post by Frogs Hair on 2011-04-20
> **ClientAlive said:**
> When I double click the file for Ubuntu Tweak I think Synaptic is telling me there's a dependency it has that it can't get for me?

The picture attached shows what I get when I double click the file.

Use the ppa instruction , the package may not be ready for 11.04 . The PPA is supposed to work for 11.04.

Here is a link for Iron , but it is a tar ball .
[http://www.srware.net/en/software_srware_iron_download.php](http://www.srware.net/en/software_srware_iron_download.php)

---

### Post by ImDougy on 2011-04-20
[ubuntu-tweak.com]("http://ubuntuforums.org/ubuntu-tweak.com") .....nuff said

---

### Post by ClientAlive on 2011-04-20
> **Frogs Hair said:**
> Ubuntu Tweak is a very handy application , just down load it , save it and double click the package . If you want the testing version with the newest features enable the source in the stable version once installed. I have not tried the Iron browser.

Here is the PPA for Ubuntu Tweak , enter commands in the terminal on at a time 

sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak




[http://ubuntu-tweak.com](http://ubuntu-tweak.com)



Right on. I did a search on Google Linux and found a download for Python something. The file is "Python-2.7.1.tgz" but I don't really know what to do with it.


> **ImDougy said:**
> [ubuntu-tweak.com]("http://ubuntuforums.org/ubuntu-tweak.com") .....nuff said



Dude! I don't know anything about this stuff. That's the thing. I just sit here and not do anything when I don't know what's gonna happen or how to do something with Linux. I'm afraid to do something that will cause me problems.

I don't understand what a tar is or how to deal with it. I don't know what tgz is or what it would do if I started messing with it. I do spend _hours_ and _hours_ researching things to learn more about Linux and even reading about and practicing cammand line right now. Sometimes I just want to be able to do something though.

Sorry I'm so stupid about this. When you get into things about Linux though it just goes on and on and on. What do I do when I just want to enjoy my computer and not have to go crazy trying to learn a million things? I spend a lot of time learning right now but I can't learn everything at once.

:rolleyes:

---

### Post by Frogs Hair on 2011-04-20
> **ImDougy said:**
> [ubuntu-tweak.com]("http://ubuntuforums.org/ubuntu-tweak.com") .....nuff said

The Package from the site does not work on 11.04

---

### Post by ClientAlive on 2011-04-20
> **Frogs Hair said:**
> The Package from the site does not work on 11.04


I understand now. Sorry. I didn't really get what you were saying in your prev post.

I opened a terminal to run what you were instructing but it says something about no trusted keys found and I'm not sure if it will actually be able to use that repo then.

Here's the result terminal spit back out at me:

```

~$ sudo add-apt-repository ppa:tualatrix/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv FE85409EEAB40ECCB65740816AF0E1940624A220
gpg: requesting key 0624A220 from hkp server keyserver.ubuntu.com
gpg: key 0624A220: public key "Launchpad PPA for TualatriX" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```Do I need to get a key before I can proceed to try install (the next lines of code you gave me)?


Thanks
--------------------------------

I think I get what it's telling me. I think its saying it got the key but it happens to be one that is not trusted.

---

### Post by ClientAlive on 2011-04-20
Right on. I got it. Got Ubuntu Tweak. Learned a couple new commands too. Thanks a lot Frogs Hair! I think I can learn what to do with a tar. That shouldn't be too bad. I'll mark this one as solved.

Jake
:)

---

### Post by ClientAlive on 2011-04-20
I'm having a really hard time finding a way to get Iron. Frogs Hair - I followed that link you gave and the download is an exe file for windows. I looked all around on their web site and not finding it for Linux. The best information I've been able to find on the internet about getting it is a thread in another forum:

[http://forum.tinycorelinux.net/index.php?topic=8854.0]("http://www.google.com/linux?hl=en&q=download+iron+for+linux&btnG=Search")

It's only a couple mos old so I'm sure the info is pretty relevant. They mention it being in some repo; but, searching the internet to get that information, I can't find any.

I'm gonna keep looking though.

If anyone knows anything about this - please, please let me know.

From what I see it seems like there are a lot of people asking about this but very little solid information.

Thanks in advance.

Jake

-------------------------------

I'm a dumbass. I finally found it from the website. It's this tiny little link near the bottom of the page and it takes you to another page where you can dl the tar for either the 64 or 32 bit version. 

That page is here: [http://www.srware.net/forum/viewtopic.php?f=18&t=2293](http://www.srware.net/forum/viewtopic.php?f=18&t=2293)

Now just to figure out how to install from a tar. Hmmm . . .

Thanks Frogs Hair

---

