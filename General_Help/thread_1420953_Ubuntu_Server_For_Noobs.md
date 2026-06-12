---
title: "Ubuntu Server For Noobs"
date: 2010-03-03
forum: General Help
---

### Post by ally_uk on 2010-03-03
Hello People I am at my wits end I want to learn about more about Ubuntu Server mainly in a small home networking environment. I am becoming really frustrated with Linux in general, sure I like Linux prefer it to Microsoft am keen to get to grips with Linux and have this huge desire to learn about Ubuntu Server, so I spend ages trawling the web about Linux Tutorials, Server tutorials how to do this and how to do that and the end result is a giant headache. I end up frustrated with myself as I get p**sed off that I am getting nowhere.  

I have numerous books at home which clearly state they are designed for beginners but they all produce the same result, endless jargon, overcomplicated config files, and a assumption that you are a Linux genius. 

I'll explain my layout and what I actually want to achieve

PC running Windows 7 with Ubuntu Server running in vmware
2 Windows 7 clients.

The Goal

Server Setup as a Domain Controller
Shares created and served up with Samba
DNS Running on Server
Backups setup on server
Virtulisation running on server
DHCP running on server

Now what I need is plain english, Non-Geek instructions or guides on how to achieve this goal. I havent got a clue where to start.

My goal is to set this allup learn some stuff and document it cleary and concise so that fellow noobs can learn.

Please aid my own personal development and help introduce more user's to Linux by helping me understand the process of configuring a server.


Many Thanks

---

### Post by bodhi.zazen on 2010-03-03
> **ally_uk said:**
> Now what I need is plain english, Non-Geek instructions or guides on how to achieve this goal. I havent got a clue where to start.

Well, that is a tall order =)

You need to start by understanding how to us a terminal and terminal commands.

Next learn how to look up commands, and read about commands you do not understand. Typically this means reading the man pages.

Linux is not a drop in replacement for windows and you need to be willing to learn new tricks. If the command line is all geek to you, time to learn bash:

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

Should be able to work through the first half of that site in 2-3 hours.

The pick one of those tasks and work your way through a tutorial.

VMWare Server should run, for example, and comes with a web interface.

So what tutorial are you following ? Where are you getting stuck ?

If you want a graphical interface, take a look at webmin.

As a server guide see:

[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

If there is something you do not understand, read and ask questions.

---

### Post by ally_uk on 2010-03-03
Thanks for the reply I am pretty good with the terminal, that part I have no problem with, it's the getting the server actually doing something which is proving to be a challenge I read documentation on stuff like LDAP, SAMBA and it is just to overwhelming for the Linux newbie or anyone making the transition from Windows to Linux.

I just need clear concise steps on getting the server off the ground I really do not want to use Webmin prefer the CLI.

---

### Post by Iowan on 2010-03-03
=D> CLI is a good thing! (Couldn't find a "thumb's up smilie). The server guide has already been referenced - [http://help.ubuntu.com]("http://help.ubuntu.com") has more good help pages. [http://howtoforge.com]("http://howtoforge.com") has some good projects - but lacks the follow-up configuration. Unfortunately, configuration continues to be a way of life...

---

### Post by gumpish on 2010-03-03
When you're trying to bend a Linux server into being a domain controller you need to appreciate that this is a bit like trying to force a VHS VCR to play Betamax tapes. Active Directory is a Microsoft construct - the fact that Linux can do it at all (after hours of work) is amazing. It should be taken as given that it will not be as straightforward as configuring a STANDARD NON-PROPRIETARY internet service. (You'll find that DNS and DHCP are simpler.)

---

### Post by Letrazzrot on 2010-03-03
I am a noob who has just successfully set up a server that I'm mostly happy with.  It is a pretty simple affair, however:  samba file server (for both public and multiple private shares, both windows and linux), mail server with fetchmail and dovecot, were the main setups.  

But, I suppose I can understand your frustration somewhat -- it took many hours of following micro tutorials, reading man pages, and experimentation.  In hindsight, none of it was too complicated; just the information seems spread out, overly technical, and/or pertaining to old or different versions of the OS or applications.

Personally it wasn't too painful as I'm used to forcing myself to patiently work through problems slowly (it comes with my job), but I can see how it can frustrate.  Having tutorials that explain the various options and choices made behind putting them into a config file would be helpful.  

Something like this: [http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/)

It is short, and very specific, but I liked the extra explanations that were given here.  Perhaps you will find it useful on your quest.

Good luck!

---

### Post by ally_uk on 2010-03-04
Thank you for the replies, I will try the above link you posted tonight and report back on my progress. What servers do you guys use at home? and what do they do? how did you find the setup and configuration process was it easy? or longwinded what tools / tutorials / guides did you use?

This will help me get a better insight as to how to go about things.

---

### Post by Letrazzrot on 2010-03-04
> **ally_uk said:**
> What servers do you guys use at home? and what do they do?

I use a (headless) MSI Wind PC (atom processor) with the latest Ubuntu Server installed.  Installation went pretty easy, for the most part, considering I am completely new to *nix.  It file serves for two different accounts and a public share, spread out over a desktop (WinXP & Ubuntu), laptop (Ubuntu only, for now), and a netbook (WinXP).  And I also have it serving email for one of those accounts -- I will add this for the other account eventually.  Not too bad, I think, for just a week and a half of persistence.\\:D/

Right now I'm investigating automated backup solutions.  I'm leaning toward just trying to roll my own in Python, since I'm wanting to learn that language anyway.  A very simple bash script would work just as well, however, since I only need something simple.    In the meantime, I suppose I'll just do manual backups with dar.

> how did you find the setup and configuration process was it easy? or longwinded what tools / tutorials / guides did you use?Learning enough of the command line and operating system to understand enough to even get anywhere was definitely *not* easy for me. However, looking back, there isn't anything too complicated about the setup, it's just knowing the right commands, options, and locations of config files.

Mostly I read through the Ubuntu docs already linked above.  Lots of googling, searching these forums, and also:

[http://www.linux.com/archive/feature/146613](http://www.linux.com/archive/feature/146613)
[http://www.aboutdebian.com/lan.htm](http://www.aboutdebian.com/lan.htm)
[http://samba.netfirms.com/sambconf.htm](http://samba.netfirms.com/sambconf.htm)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

are from my bookmarks -- I can't attest to the validity or helpfulness of any of these, since I've since forgotten which pieces of information came from where.  As I said, it took culling from many different sources, along with lots of experimentation, before everything worked.  And, even now, I'm not absolutely positive about its stability, although it seems fine.  Also, I'm pretty sure it's not all that secure, but I'm not so concerned about that as it's a closed network behind a firewall.  The weakest part security-wise is probably the Windows netbook browsing the internet.

> This will help me get a better insight as to how to go about things.I'd advise with patience! ;)  Digging into the nuts and bolts of any operating system is going to be challenging/time-consuming; doing so on an entirely new OS, doubly so.

---

### Post by ally_uk on 2010-03-04
Thanks for the advice, It seems i'm going to have to get hands on and break some stuff lol, Somebody should really release a Linux in Plain English book :p 

As much as I love Linux, It is a bloody complicated system if you do not not what you are doing. I suppose in a way it puts alot of people off from using it, if something goes wrong and you have to start messing about with config files then it's going to really get on a average user's nerves.

And why hasn't anyone thought of centralising the information? why do I have to spend hours trawling through documentation hoping to get something to work only to end up with a massive headache lol, People have referred me to the official Ubuntu server ive gone over it a few times but I will be honest here from a user who wants to get a server up and running it is pretty crap.

I'm not moaning lol just venting a few thoughts, maybe if the doucmentation was a little bit easier to understand and Linux wasn't so cryptic to newbies then alot more people would adopt it.

Anyways enough of the ranting, 

I think basic Samba filesharing will be the first thing I shall tackle, I'm talking really basic here like my first goal is to share a folder with windows 7 if I can get that working I will be happy lol will let you know how I get on and of any disasters I encounter.

:)

---

### Post by FiveSidedPoly on 2010-03-04
Hey ally_uk, don't stress over it, take your time and I'm sure you'll be fine.
 
I recommend starting with the last link Letrazzrot gave you, it is old, but very good. It has helped me in the past finding issues and correcting them.
 
And also the Official server guide bodhi.zazen linked for you.
 
Here are a few others that should be helpful. A lot of the same material is covered, not all of it is useful in some instances, but every little bit can help. :)
 
[Fixing Samba Share Issues]("http://http://ubuntuforums.org/showthread.php?t=1169149")
 
[Ubuntu Hacks/Small Office/Home Office Server]("http://http://commons.oreilly.com/wiki/index.php/Ubuntu_Hacks/Small_Office/Home_Office_Server")
 
The last one is very similar to the one Letrazzrot gave you, but covers a lot more stuff in one bite.
 
I would suggest sticking with CLI for now, I've noticed some very strange things going on with my config files right after I install Webmin, which leads me to believe that there is a good reason it isn't in the repos anymore. I have yet to attempt eBox because at the moment the Samba file serving is working fine, which is what my server's main purpose is for, right now I don't want to take my chances.
 
BTW:  Following these guides I have two Windows7, 3 WinXP, and two Ubuntu boxes connected to the server without problems.  I didn't even have to change the "WINS" line in the smb.conf like is shown, I left it default.

---

