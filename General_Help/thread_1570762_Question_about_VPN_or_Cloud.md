---
title: "Question about VPN or Cloud?"
date: 2010-09-08
forum: General Help
---

### Post by rolandpish on 2010-09-08
Hi there.

We have a Ubuntu Server running in our small department.

There comes the time when we need to setup a kind of "private cloud" mainly to keep our files in sync and to store them in the ubuntu centralized server.

For example, sometimes I go to the office and work with the Ubuntu Lucid desktop, while sometimes I go to an alternate office and use a Windows XP box and need to work with the same files; and the same story with my home laptop with Linux Mint (one of my partners use a MAC computer).
Apart from having the files in the "cloud" server, we also need the files locally in each computer.
At this moment we are using a service called Dropbox but now we need to setup our own "cloud" as privacy for the documents we work with is crucial from now on.

After talking about this with my dept partners we thought about the possibility of installing and configuring a VPN and a Samba server, but the problem with this is that files reside in the server and not locally in each computer and I can't figure out a form of "syncing" files between the server and the workstations.

As cloud computing has been acquiring more importance and as we are thinking about setting up a "cloud storage" for us (as Dropbox service does), I started researching on this and found stuff like Eucalyptus, openQRM, OpenNebula, Ubuntu Enterprise Cloud, eyeOS and so on.

At this point, I would like to stop for a moment and ask you guys for recommendations for what we want to achieve.
Is the VPN with a special setup what we need?
Or
If VPN is discarded, which could be the tool/service/application/server to set up this "cloud" storage we want for our dept?

I really appreciate your opinions and help.

Thanks in advance

PS: I read a little about Ubuntu Enterprise Cloud, but this needs at least 2 computers, one for the cloud controller and another for the node controller. For the moment, we only have one box (ubuntu server) and we need everything installed in that computer. Is this possible with UEC?

Cheers,
Roland

---

### Post by harrismh777 on 2010-09-08
Please read:

[http://en.wikipedia.org/wiki/Revision_control](http://en.wikipedia.org/wiki/Revision_control)

8-[

Document control systems (sometimes called revision control systems) are usually used for software development where "parts" need to be kept in sync.

But they can be used anywhere. Really research this well. There are many of these systems to choose from (some open and free, some commercial, etc).

As for VPN, that is another matter having more to due with security. Basically, if you want your remote people to be able to access your work network (from home, hotel, convention center, etc) as though they were actually *at work* then you'll want to setup VPN. This is completely separate as a discussion point from how you decide to handle document control. 

Yes, the first thing you are going to want to accomplish is setting up VPN and making that work. 

Choose your document control system carefully. You will probably want to expand on your concept of just one server. There really needs to be redundancy, for backup capability if nothing else, but also for mirroring and possible load balancing. 

My two cents after working with this stuff at IBM for about 25 years. 

:popcorn:

---

### Post by rolandpish on 2010-09-08
Thanks a lot for your reply harrismh777. I really appreciate it.

Wow, you really hit the target :)
I've been using subversion for a couple of years in my every-day work and never came svn to my mind in order to solve this!

Now things are getting really clear for me (feel free to advice anything you want):

* I can set up a VPN (I did it once about 2 years ago and using TAP instead of TUN and not assigning a password to the users). Which one -between TUN and TAP- should I use as I will be adding/removing users frequently and sometimes resetting user passwords?

* Install subversion server (accesible only through the VPN) and install required software in client computers (Tortoise, RabbitVCS, etc.) to stay in "sync".

Is there something additional that needs to be considered in this setup?

Thanks in advance.

Roland

---

