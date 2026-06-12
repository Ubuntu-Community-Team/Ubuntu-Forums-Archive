---
title: "Possibly (but probably not) a unique idea."
date: 2010-04-04
forum: General Help
---

### Post by teacher86314 on 2010-04-04
I'm a new school teacher.  There's questions on whether or not our computer lab is totally... ahem... legal.  Nobody really knows how many Windows CD keys we're using.  So, instead of spending possibly thousands of dollars in purchasing new cd keys (or millions in fines from Microsoft), I've decided to change the courseware and go 100% Linux.  I've chosen Ubuntu as my solution.

I need to know what to research, or if you already know of a link I could go to which will answer all of my questions, that would also be great!  Here's what I want to accomplish:

1. Each computer on the network will have their own installation of Ubuntu, as setting up a PXE server was crazy hard and I couldn't keep track of what I was doing to figure it out.

2. No matter which computer a student sits down at, I want them to have access to their own files.  It would be a huge benefit if they could work in their own environment, too.  That way they can customize their desktop, bookmarked pages in Firefox, etc. without messing-up someone else's desktop.

3. I'd like to have all of the computers go through my computer to access the internet.  I'd like to be able to globally block/allow specific sites from just my computer instead of having to go to each of their computers individually to make changes.  I'm sure I'll lose track trying to do it the hard way.

4. I want to be able to control all of their user accounts from my computer. That way when a student leaves, I can delete all of their files to free-up HDD space and remove their username.  Also, I'd like to be able to turn on/off network access permission from my computer as needed.

5. I want however this works not to draw too many resources from my computer.  I'll be using a laptop for most of my work on the network, but I want all of the STUDENT computers to be forced to log into the network.

6.  If it's possible - I'd like the ADMIN account to still be able to add/remove software on each of the computers.

So - is this possible?
If so, what should I look-up?

---

### Post by kblft on 2010-04-04
Though I've never experimented with it - there is an edubuntu version that is designed for such purposes and can achieve at least some of the goals you listed (if not all)

see [http://edubuntu.org/](http://edubuntu.org/) and [http://en.wikipedia.org/wiki/Edubuntu](http://en.wikipedia.org/wiki/Edubuntu) for more information

---

### Post by gzarkadas on 2010-04-04
You have done well, and you should IMHO stay in this route despite the expected initial difficulties, because there are even more to gain aside from money. The setup you want to achieve is rather complex, but definitely doable. I will try to answer some of the issues; hopefully the rest will be completed by others :).

> **teacher86314 said:**
>  1. Each computer on the network will have their own installation of Ubuntu, as setting up a PXE server was crazy hard and I couldn't keep track of what I was doing to figure it out.

You can simply setup the server (or servers) that are described below, then make all necessary changes to _one_ "template" client computer. After all work as wished, copy the template computer's configuration (this means all changed files in /etc and possibly some files in /var) in a usb stick and then make a default install + copy of changed config to all other clients.

> **teacher86314 said:**
> 2. No matter which computer a student sits down at, I want them to have access to their own files.  It would be a huge benefit if they could work in their own environment, too.  That way they can customize their desktop, bookmarked pages in Firefox, etc. without messing-up someone else's desktop.

The easiest way is to setup a shared folder in a file server (NFS or Samba) and setup all client computers to mount at startup, then use it as /home. Application settings files are stored as hidden files and directories inside each user's home folder, so I guess this will make users' environment portable also.

> **teacher86314 said:**
> 3. I'd like to have all of the computers go through my computer to access the internet.  I'd like to be able to globally block/allow specific sites from just my computer instead of having to go to each of their computers individually to make changes.  I'm sure I'll lose track trying to do it the hard way.

You will have to configure your network so that all computers are enforced to use yours as a proxy. This means that either:

[LIST]
[*]All connections go to a switch. The switch connects to your proxy. The proxy (through a 2nd network card) connects to the Internet router.
[*]You setup a rule in your router that only the proxy machine can access the Internet (and secure the router). This is best for your case (laptop machine).
[/LIST]
In your proxy server you set up the appropriate firewall and proxy access rules; in the client computers you setup their connection to use your proxy server. For firewall you can use ufw (ubuntu default), firestarter or whatever suits you. For proxy you will use squid.

> **teacher86314 said:**
>  4. I want to be able to control all of their user accounts from my computer. That way when a student leaves, I can delete all of their files to free-up HDD space and remove their username.  Also, I'd like to be able to turn on/off network access permission from my computer as needed.

You need to setup an LDAP server. I haven't done it before though, so I cannot be much of a help here.

 > **teacher86314 said:**
>  5. I want however this works not to draw too many resources from my computer.  I'll be using a laptop for most of my work on the network, but I want all of the STUDENT computers to be forced to log into the network.

The whole package of servers (Samba or NFS, proxy, LDAP) is not that demanding, if the number of served clients is not high. However, it would be better to have a dedicated computer for the file and LDAP servers that stays in class. That way, you can have the entire internal network usable when you take the laptop away, but no Internet since there will be no proxy.

> **teacher86314 said:**
>  6.  If it's possible - I'd like the ADMIN account to still be able to add/remove software on each of the computers.

This is definitely doable; I must though make some research for the best possible solution before I post an answer.

> **teacher86314 said:**
>  So - is this possible?
If so, what should I look-up?

Yes, but it will require some work, as all large scale projects do; you would need to go through it with all alternative platforms.

---

### Post by ugm6hr on 2010-04-04
gzarkadas has answered the specifics of your questions, which should point you in the right direction.

Nevertheless, I agree Edubuntu is worth looking at before pursuing alternatives aggressively, since it is designed for a similar purpose.

Otherwise, agree that an LDAP server and an NFS server will do most of what you want. The network control would be better off in a server too - maybe look at ebox (I haven't experimented with for a year or 2), but it also does a lot of what you need: [http://www.ebox-platform.com/](http://www.ebox-platform.com/)

Once you've decided what route to take, ask again if you get stuck.

---

### Post by srs5694 on 2010-04-04
Good answers below; just one point of elaboration....

> **gzarkadas said:**
> You need to setup an LDAP server. I haven't done it before though, so I cannot be much of a help here.

LDAP is actually just one of several tools that can do this. NIS is another one. Kerberos comes close, but is a bit awkward. Samba on the server, in conjunction with Winbind on the clients, can also do the job, although this could create issues with mismatched user IDs. Overall, LDAP is probably the best approach, although NIS might be as good. (I'm less familiar with NIS myself.)

---

### Post by patchwork on 2010-04-04
Networking with others who are doing things similar to this can be a big help.  From [this thread]("http://ubuntuforums.org/showthread.php?t=1432049&highlight=mentor"), frodo is another teacher setting up a linux network for the classroom.  I would suggest posting a question for frodo about the things learned in that experience.

---

