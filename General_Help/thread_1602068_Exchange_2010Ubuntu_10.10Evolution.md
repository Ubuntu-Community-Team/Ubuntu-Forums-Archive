---
title: "Exchange 2010/Ubuntu 10.10/Evolution"
date: 2010-10-20
forum: General Help
---

### Post by Sickpuppy87 on 2010-10-20
Hi guys 

so we recently updated our exchange from 2003 to 2010.  

Since then we have been having issues with Evolution connecting.  I have been googling most of the day but i have seen very little on this.  I have tried the evolution-mapi plugin with no luck.  I have also seen articals going both ways saying 2010 is supported then the next thing i read says there is no support for 2010. 
 
Just looking for some clearification here if anyone cant point me in the right dirrection it would be much appreciated. Let me know if i can give any more info. 

Thanks.

---

### Post by P4man on 2010-10-21
AFAIK, it only works using IMAP, so only for email, and even that  requires the server has IMAP4 enabled. The old trick evolution used by accessing exchange by (ab)using outlook web access no longer works, since MS canned WebDav.

There might be some server side apps you can install to make exchange  more standard compliant, but that may not be an option for you and I am not even sure there are any good ones out yet.

---

### Post by dcstar on 2010-10-21
> **Sickpuppy87 said:**
> Hi guys 

so we recently updated our exchange from 2003 to 2010.  

Since then we have been having issues with Evolution connecting.  I have been googling most of the day but i have seen very little on this.  I have tried the evolution-mapi plugin with no luck.  I have also seen articals going both ways saying 2010 is supported then the next thing i read says there is no support for 2010. 
 
Just looking for some clearification here if anyone cant point me in the right dirrection it would be much appreciated. Let me know if i can give any more info. 

Thanks.

I have been trawling for days trying to find a solution for Evolution to connect to Exchange 2007, there is a guy that has patched the MAPI code that he says works with 2007 & 2010 but I use 64-bit and he only has made 32-bit available:

[http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange](http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange)

---

### Post by Sickpuppy87 on 2010-10-21
> **dcstar said:**
> I have been trawling for days trying to find a solution for Evolution to connect to Exchange 2007, there is a guy that has patched the MAPI code that he says works with 2007 & 2010 but I use 64-bit and he only has made 32-bit available:

[http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange](http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange)


Sadly i dont know this is going to work.

when i try to run the install he has list (sudo apt-get -t sid install evolution evolution-common \)

i get 

```

The following packages have unmet dependencies:
 evolution : Depends: libevolution (>= 2.31.1) but 2.30.3-1ubuntu6 is to be installed
             Depends: libgtkhtml-editor0 (< 3.31) but 1:3.30.3-1ubuntu1 is to be installed
             Depends: libgtkhtml3.14-19 (< 3.31) but 1:3.30.3-1ubuntu1 is to be installed
E: Broken packages

```

i also just tried to install just the evolution-common package but that seems to have removed evolution.

---

### Post by OpenMinded on 2010-12-02
this kinda sucks.
That guy just posts and accepts no feedback.
Did not work on 10.04 for me either, upgrading to 10.10 to try.

Maybe this helps:
[https://bbs.archlinux.org/viewtopic.php?pid=625367](https://bbs.archlinux.org/viewtopic.php?pid=625367)

Also, my collegue has lightning for Thunderbird combined with something else which works for the calendar in TB.
So that might be a nice alternative.

---

### Post by MrSkrimps on 2010-12-05
Hey guys, 

I read through the forums all the time looking for solutions and usually find them, except for this time.  I hope I'm in the right place for it.  So here is the deal, I use evolution and I (until recently) have been able to check my work email using exchange OWA.  Worked perfect in Ubuntu 10.10, however, ran into so many problem with 10.10 that i decided to backstep to 10.04 (battery indicator problems, system reporting battery dead and hibernating when fully charged, plymouth splash screen ugly and when i attempt to fix it, get stuck in a boot loop.etc), so I downgraded to ubuntu 10.04 and upgraded evolution to 2.30.3 which from what I can tell, is the most current version (packed with 10.10), installed evolution-mapi plugins etc.  I can create my exchange account, it validates me however, it doesn't sync my inbox folders, but it does sync my calendar...I've been going back and forth with 10.04 and 10.10, and i'm toying with the idea of upgrading to 10.10 again, but am skiddish to do so, because I don't want risk having to do a complete re-install of anything.  Any suggestions? ideas? could really use some help on this one.

---

### Post by OpenMinded on 2010-12-13
> **MrSkrimps said:**
> Hey guys, 

I read through the forums all the time looking for solutions and usually find them, except for this time.  I hope I'm in the right place for it.  So here is the deal, I use evolution and I (until recently) have been able to check my work email using exchange OWA.  Worked perfect in Ubuntu 10.10, however, ran into so many problem with 10.10 that i decided to backstep to 10.04 (battery indicator problems, system reporting battery dead and hibernating when fully charged, plymouth splash screen ugly and when i attempt to fix it, get stuck in a boot loop.etc), so I downgraded to ubuntu 10.04 and upgraded evolution to 2.30.3 which from what I can tell, is the most current version (packed with 10.10), installed evolution-mapi plugins etc.  I can create my exchange account, it validates me however, it doesn't sync my inbox folders, but it does sync my calendar...I've been going back and forth with 10.04 and 10.10, and i'm toying with the idea of upgrading to 10.10 again, but am skiddish to do so, because I don't want risk having to do a complete re-install of anything.  Any suggestions? ideas? could really use some help on this one.

I hope anyone posts here when there is a solution.
With previous links I ran into dependency problems and instable clients.
I was so far as to be able to Authethenticatie in Evolution and got a message back that authentication was succesful against Exchange 2010.
Unfortunately no mail was loaded and after a few times trying I got an error again.

So pretty much a work in process and what I really miss is a central spot on where to check for progress.
Anyone knows where we could redirect our issues?
Just file a bug for the current evolution for not being able to connect to Exchange 2010?

---

### Post by MrSkrimps on 2010-12-13
> **OpenMinded said:**
> I hope anyone posts here when there is a solution.
With previous links I ran into dependency problems and instable clients.
I was so far as to be able to Authethenticatie in Evolution and got a message back that authentication was succesful against Exchange 2010.
Unfortunately no mail was loaded and after a few times trying I got an error again.

So pretty much a work in process and what I really miss is a central spot on where to check for progress.
Anyone knows where we could redirect our issues?
Just file a bug for the current evolution for not being able to connect to Exchange 2010?

I FOUND A FIX!!!!!!!!  At least for my situation anyway.  I can't guarantee this will work for users checking a 2007 or 2010 exchange server because my company uses 2003, however, this worked for me.  Quick Run down of my problem:

Ubuntu 10.04 Lucid Lynx AMD64

i couldn't check my exchange email using Evolution 2.28 that is packaged with 10.04.  However, in 10.10 (evolution 2.30) i could check exchange all day long like its nobody's business.  The problem is, there are just too many things about 10.10 i just don't like and i prefer an LTS anyway. 

THE FIX---

So, initially I thought, "can't check in 10.04, but CAN in 10.10....hmmmm, eureka!!! I shall simply upgrade Evolution to the same version in 10.10 problem solved!!!"  wrong.  Problem was not solved in the slightest, again, I can sync my calendar, but not my email.  (this is evolution 2.30.3 btw), so I wrestle with this for a few days, make a post on this site, search the far ends of the internetz and nothing. No answer...other than upgrade to 10.10 and inherit bigger problems than my dislike of using OWA.  I was about to give up when the thought hit me...."Why not add 10.10 repo's to my source list in 10.04?"  (this came after I virtualized 10.10 to see if there were any differences in synaptic..which, to my surprise, there were...)..so, I added 10.10 repo's to my sources list for 10.04.  Fired up synaptic, reloaded sources and BAM!!  Evoltuion (along with its plugins for exchange) were all ready for an upgrade (upgrade to what is packaged with 10.10).  So, i upgraded...re-opened Evolution (still reports 2.30.3), added my exchange account and VOILA!!  I'm now checking email, sending email, syncing my calendars etc.  the plus side, is with this method, i could virtually upgrade to any software I wanted in 10.10 without upgrading TO 10.10.  Latest Transmission, Brasero, shotwell, FGLRX (which runs better than 10.04), Ubuntu 10.10 font family, even the calculator...ANYTHING.  So there you have it folks.  In a nutshell, if you can check your exchange accounts in 10.10, this work-around/backporting should work for you.

Words to the Wise-
DO NOT RUN UPGRADE while you have 10.10 repo's in your 10.04 source list...no telling what could break..or you might just accidentally upgrade your entire OS.

BE CAUTIOUS!!  Some things (which I learned almost the hard way, WILL BREAK 10.04 if you upgrade so be careful!!)  I learned the best method, is to decide what you want to upgrade/backport, and go ONE AT A TIME, so if something goes nutty, you KNOW what caused it and where to start on fixing it.  Below is a copy of my sources list to give an example of what I did (copy and paste under the lines MAVERICK MEERKAT REPOS, I put that line there so i could see them easily).  Enjoy, hope this helps someone!!! AND REMEMBER, WHEN YOU ARE FINISHED USING THE REPO's, COMMENT THEM OUT (like they currently are) WITH THE "#" BEFORE THE LINE...(without the "" of course)
----------------------------------------------------------------

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

#MAVERICK MEERKAT REPOS

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

#MAVERICK MEERKAT
## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

---

### Post by dcstar on 2010-12-13
> **MrSkrimps said:**
> I FOUND A FIX!!!!!!!!  At least for my situation anyway.  I can't guarantee this will work for users checking a 2007 or 2010 exchange server because my company uses 2003, however, this worked for me.
.........
Words to the Wise-
DO NOT RUN UPGRADE while you have 10.10 repo's in your 10.04 source list...no telling what could break..or you might just accidentally upgrade your entire OS.

BE CAUTIOUS!!  Some things (which I learned almost the hard way, WILL BREAK 10.04 if you upgrade so be careful!!)  I learned the best method, is to decide what you want to upgrade/backport, and go ONE AT A TIME, so if something goes nutty, you KNOW what caused it and where to start on fixing it.  Below is a copy of my sources list to give an example of what I did (copy and paste under the lines MAVERICK MEERKAT REPOS, I put that line there so i could see them easily).  Enjoy, hope this helps someone!!! AND REMEMBER, WHEN YOU ARE FINISHED USING THE REPO's, COMMENT THEM OUT (like they currently are) WITH THE "#" BEFORE THE LINE...(without the "" of course)
........

I am surprised that you were able to upgrade and run 10.10 Evolution on a 10.04 platform, in past releases the next version of Evolution had multiple dependencies that made it virtually impossible to Backport to earlier releases - so it was never done. If it works for you then good luck.

BTW, there is currently a later version of Evolution available in the Natty repositories, I don't know if you are game enough to try it....

Edit: I just tried this on a test 10.04 system, yes you can install the later Evolution but when I reverted the repositories back to Lucid I found that I could not install things like Postfix!

---

### Post by OpenMinded on 2010-12-15
[QUOTE=MrSkrimps;10235453]I FOUND A FIX!!!!!!!!  At least for my situation anyway.  I can't guarantee this will work for users checking a 2007 or 2010 exchange server because my company uses 2003, however, this worked for me.  Quick Run down of my problem:

Ubuntu 10.04 Lucid Lynx AMD64

i couldn't check my exchange email using Evolution 2.28 that is packaged with 10.04.  However, in 10.10 (evolution 2.30) i could check exchange all day long like its nobody's business.  The problem is, there are just too many things about 10.10 i just don't like and i prefer an LTS anyway. 

THE FIX---

Sorry, but this is really not a fix!
This thread is about Exchange 2010!
2003 has been working already for a long time.
I couldn't care less about people nagging about 10.10 over 10.04, I have upgraded to 10.10 and have no issues, it's running great.

Fiddling with packages from 10.10 on 10.04 is generally a bad idea and will break things.
I tried with 11.04 on 10.10 and all kinds of things broke.

Your post fits nice somewhere where people look for running 10.10 Evolution on 10.04, but please do not post that you fixed it before reading the title, because IT DID NOT.

I think we conclude from your post that people on 10.10 have no issues with Exchange 2003, which is already knows, because the OWA has been supported from Exchange.
Of course Microsoft has to **** things up for other parties connecting, so they changed in 2007 to Webdav i think and removed that again 2010, so that it changed again.

So the real issue here is connecting to Exchange 2010 with Evolution by using the MAPI protocol.
If any has this figured out reproducable on 10.04 or 10.10 please post!

---

### Post by s01o on 2011-01-05
Evolution 2.30.3 with Exchnage 2010.
I do not know exactly who package makes things work than those below because they installed the heap (along with those who are dependent).
Another important thing is that Server Type is not selected Microsoft Exchange, and Exchange MAPI.

The remaining options are:

Configuration
Server: mail.example.com
Username: example.user
Domain: example


evolution-mapi - 0.30.3-1ubuntu1
libexchangemapi-1.0-0 - 0.30.3-1ubuntu1
libmapi0 - 1:0.9 + svn2158-0ubuntu1
libmapiadmin0 - 1:0.9 + svn2158-0ubuntu1

---

### Post by Dokuganryu07 on 2011-01-17
For Outlook 2007 I did the following which made it (finally) work:


Server type:   IMAP (I know it is not IMAP but somehow, it worked.)

Server/server name:  Type the IP address of the mail server here.

Username:  your username, without the @blahblahblah


do the same for the sending server, as STMP.


Tested and worked with:  Outlook Web Access 2007, Outlook 2007, Outlook 2003.

It may just work with 2010 as well, but I have not been able to test it, as I do not have a server with outlook 2010.

---

### Post by rod40cool on 2011-01-19
> **Dokuganryu07 said:**
> For Outlook 2007 I did the following which made it (finally) work:


Server type:   IMAP (I know it is not IMAP but somehow, it worked.)

Server/server name:  Type the IP address of the mail server here.

Username:  your username, without the @blahblahblah


do the same for the sending server, as STMP.


Tested and worked with:  Outlook Web Access 2007, Outlook 2007, Outlook 2003.

It may just work with 2010 as well, but I have not been able to test it, as I do not have a server with outlook 2010.

This is a mail only alternative. Setting your email account in Evolution to IMAP will get you email from an Exchange 2003, 2007 and 2010 server provided your administrator has enabled IMAP on the Exchange server and enabled your Active Directory account for IMAP. However IMAP wont sync your Exchange calendar or contacts like the Exchange or Exchange MAPI connectors do.

My work recently upgraded from Exchange 2003 to an Exchange 2010 server. Neither the Microsoft Exchange nor the Exchange MAPI server types work with an Exchange 2010 server. 

My workaround is using CrossOver Linux (which uses Wine) with MS Office 2007 installed - I find Outlook 2007 running in CrossOver works well. The only drawbacks are you have to pay for CrossOver Linux - which I did - but without it I would have to run a VirtualBox VM of Windows to run Outlook natively, and for me the less Win stuff I have to run the better. So until Evolution gets 2010 support I'm sticking with Outlook running under CrossOver.

---

### Post by PeteLong on 2011-01-19
It appears to work out of the box with 2010 - I've had no problem?

[Connecting Evolution Mail Client to Exchange 2010]("http://www.petenetlive.com/KB/Article/0000378.htm")


Pete

---

### Post by dcstar on 2011-01-20
> **PeteLong said:**
> It appears to work out of the box with 2010 - I've had no problem?

[Connecting Evolution Mail Client to Exchange 2010]("http://www.petenetlive.com/KB/Article/0000378.htm")


I have not been able to get Evolution MAPI to work into Exchange 2007 sites behind NAT firewalls and using Self-Signed Certificates (although Outlook connections work)

I believe both these issues may be a factor in the Evolution problem as it may only work with "proper" SSL certificates and/or more unspecified port access into the server.

---

### Post by muiz on 2011-01-20
> **dcstar said:**
> I have not been able to get Evolution MAPI to work into Exchange 2007 sites behind NAT firewalls and using Self-Signed Certificates (although Outlook connections work)

I believe both these issues may be a factor in the Evolution problem as it may only work with "proper" SSL certificates and/or more unspecified port access into the server.

I have also not been able to get Evolution 2.30.3 to work using MAPI against Exchange 2010. I wiresharked the packets between Ubuntu and Exchange and found that Evolution is sending a NspiBind request to Exchange and Exchange replies back with MAPI_E_NO_SUPPORT. 

Does anybody know why this might happen or what this means?

---

### Post by Sickpuppy87 on 2011-03-15
Ha i forgot i posted this here and gave up.  Today i started looking for new solutions and found my own post. 


anyway.  my question is for PeteLong.  Are you on the same network as your exchange 2010 server?  Is SP1 installed?  Hosting Switch? 

What version of Ubuntu/ evolution are you using ..... JEALOUS !!!!!

> **PeteLong said:**
> It appears to work out of the box with 2010 - I've had no problem?

[Connecting Evolution Mail Client to Exchange 2010]("http://www.petenetlive.com/KB/Article/0000378.htm")


Pete

---

### Post by ibeardslee on 2011-03-20
I have the Evolution 2.30.3-1.ubuntu6 (Maverick 10.10) working nicely with Exchange 2010 (Version 14.1 Build 218.15) running on Windows Server 2008 R2 Standard (SP1).  It's using 'evolution-mapi' version 0.30.3-1ubuntu1.  All on the same virtualised (KVM) test network.

Seems that I had used the same process as posted by PeteLong earlier in this thread.  I had wanted to use Lucid 10.04 for this but was having not as much success, at this point Natty 11.04 even less.

Now going slightly off topic.  I'm vaguely assuming that some people trying to connect to Exchange are also trying to connect to Active Directory.  My issue is now if I want to provide authentication to the Ubuntu workstation via the same Active Directory that the Exchange server does.

I can get the AD authentication working nicely with 'likewise-open', but then I have the failure with Evolution segfaulting that is mentioned in numerous threads.

Any thoughts on connecting to AD (and Exchange 2010)?

---

### Post by ibeardslee on 2011-03-20
Sigh .. so it seems to work now.

I saw this .. [http://www.petenetlive.com/KB/Article/0000384.htm](http://www.petenetlive.com/KB/Article/0000384.htm) .. after following links from PeteLong's post.  So, I thought I'd try again.

Seems that using lower-case domain names and IP addresses of the mail servers was the trick I was missing.  Thanks for those tips Pete!

I'll go back and try that with Lucid now.

---

### Post by rschu68 on 2011-04-04
> **muiz said:**
> I have also not been able to get Evolution 2.30.3 to work using MAPI against Exchange 2010. I wiresharked the packets between Ubuntu and Exchange and found that Evolution is sending a NspiBind request to Exchange and Exchange replies back with MAPI_E_NO_SUPPORT. 

Does anybody know why this might happen or what this means?

-> look at this:
[http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange](http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange)

Grtz
~remke

---

### Post by dazman19 on 2011-04-04
it probably wont work the NTLM. Exchange 2010 uses that.

Just open up SMTP + POP3 or IMAP.

Personally i prefer thunderbird, and I have it connecting to our work exchange server it runs pop3/imap for incoming mail and authenticated  SSL/TLS SMTP for outgoing.

---

### Post by Rebootkid on 2011-05-02
Most places don't want to open IMAP or Pop3 protocols.
Remember that Linux users are still considered "Second Class" in many Windows shops.

Take a look at Davmail folks. I use it. It front ends the OWA interface, and I use IMAP+ on the back end to configure Evolution. Calendaring is a bit slow, but other than that, it seems to work fine.

---

### Post by guisar on 2011-06-01
Has anyone found a deb (pre-built) for natty or one which works with Evolution 3? The exchange-mapi in the repos I've found only works against Evolution 2.3.

---

### Post by dimago on 2011-08-18
hello all

I did the config to use the evolution MAPI with my exchange 2010.

I use the Secure Connection. If I dont use, dont ask me to authentication.

So, when I use the Secure Conection, ask me for auth, and I put my password, and it comes OK.

I can send e-mail, but I cant receive email. Dont download the folders.

Anyone has any idea about this?

Thanks anyway

---

### Post by subielover on 2011-09-24
Followed the guide in the link [http://www.petenetlive.com/KB/Article/0000378.htm](http://www.petenetlive.com/KB/Article/0000378.htm) and works perfectly for me.

---

### Post by PhilFox on 2011-09-28
A workaround for very slow autocomplete of mail addresses between Exchange 2003 and Evolution

I have...
Evolution 2.32.2
Ubuntu 11.04 (Natty)
All the evolution plugins I can find.
Outlook Exchange Server 2003 
1.2 MB RAM
1.6 GHz processor
Wireless connection can get 500kbs
Exchange is hosted on fasthosts


Edit/Preferences/Mail Accounts/exchange account/Edit/
    Receiving options: Guessed the LDAP address (not sure if it makes any difference)
    Receiving email: Server type selected = Microsoft Exchange
                      Limit number of GAL responses = 100 (out of about 2000)
                      Expand groups of contacts in GAL to contact lists = not selected

Edit/Preferences/Contacts
    Always show address of the completed contact = select
    then select the contact list to search from - keep it small if you can

Keep open all the time 2 evolution windows 
     1. = Mail
     2. = Contacts, with the mailing list populated

Then write your email, but when you type the recipient name into the mail address bar make sure you type the contact name as it is detailed in the contacts window. It should autocomplete quickly. You need to include the prefix if there is one. It will not autocomplete if the contact does not have an email address and only has a phone number.

It is much quicker if you type the name precisely with capital letters in the right place and in the order in which your contacts are displayed eg perhaps with Surname first

Do not press the "To" or "CC" button. They will hang.

Plug-ins include Automatic Contacts.

Mail and calendar work almost OK - except that calendar will not update from server, but will update the server. To update calendar from the server requires a reboot.

---

### Post by floorripper on 2011-10-03
Hello linux fans,

I have tried several guides but none of them works. I am working on this more than one month, and it seems to be useless.

[COLOR=Blue]http://www.petenetlive.com/KB/Article/0000378.htm[/COLOR]             
# did not solve my  problem but helped

[COLOR=Blue]http://www.jones.ec/blogs/a/entry/evolution_evolution_mapi_and_exchange[/COLOR]  
#some packadges are not in His repositories, I have also changed some lines in cfg as he requested but it does not make a difference

# Run ldbedit -H ~/.evolution/mapi_profiles.ldb
# Within the profile LDB entry, append:
seal: true

[COLOR=Blue]http://www.webupd8.org/2010/06/install-evolution-230-in-ubuntu-1004.html[/COLOR] 
#also some packages are missing, once I have installed version 2.30 form there evolution has completely crashed  and closed when I have opened it. So I was not able to see the status.
I had to revert back to the original version by commands ppa purge. Is there any another complete repo for 2.30 from which I can update my version to 2.30 once more also with dependences?

this case:
I am able to authenticate with the exchange server, first of all I have downloaded some of the directories, but later on I received errors in connections and seems to be that the evolution has problems with downloading mails and directories threes.
I am not able to send or receive e-mails. I am attaching the screenshot. [http://www.floorripper.com/download/evolution.png](http://www.floorripper.com/download/evolution.png)

By the way normal OWA settings is not working at all. My colleague is using MAC and Safari and he has no issues with owa settings. (but he might be on exchange2007). When we tried his account on mine ubuntu, It was not working either.

My system:

Ubuntu 10.04.3 LTS

dpkg -l | grep evolution
ii  evolution                            2.28.3-0ubuntu10.3  
ii  evolution-common                     2.28.3-0ubuntu10.3  
ii  evolution-data-server                2.28.3.1-0ubuntu5   
ii  evolution-data-server-common         2.28.3.1-0ubuntu5   
ii  evolution-exchange                   2.28.3-0ubuntu1     
ii  evolution-indicator                  0.2.8-0ubuntu1      
ii  evolution-mapi                       0.28.3-0ubuntu1     
ii  evolution-plugins                    2.28.3-0ubuntu10.3  
ii  evolution-webcal                     2.28.0-1            
ii  libebackend1.2-0                     2.28.3.1-0ubuntu5   
ii  libebook1.2-9                        2.28.3.1-0ubuntu5   
ii  libecal1.2-7                         2.28.3.1-0ubuntu5   
ii  libedata-book1.2-2                   2.28.3.1-0ubuntu5   
ii  libedata-cal1.2-6                    2.28.3.1-0ubuntu5   
rc  libedata-cal1.2-7                    2.30.3-0ubuntu1~ppa0
ii  libedataserver1.2-11                 2.28.3.1-0ubuntu5   
rc  libedataserver1.2-13                 2.30.3-0ubuntu1~ppa0
ii  libedataserverui1.2-8                2.28.3.1-0ubuntu5   

Evolution settings:
Server type: Exchange MAPI
server: 1.1.1.1
username: iamtheuser
domain name: thisdomain

Exchange is 2010 (according to the new webmail loook)

Do you have a clue what might be wrong? Revert back to windows is not the best way, only because of emails...windows sucks..are you with me?


Thanks a lot

Floorripper

---

### Post by hax3 on 2012-01-16
I just installed Evolution 3.2.1 using PeteNetLive walkthrough.

I got it working for receiving emails but I can't send emails.  It doesn't seem to be using the MAPI connection to exchange to send email as the email is stuck in the out box under the "On This Computer" folder tree instead of the Outbox under Exchange Email Account Tree on the main left navigation frame of Evolution.  

Anyone have any idea?  I did a google search and someone submitted the same issue in LaunchPad last week with no reply...

TIA

---

### Post by mebomechanicno1 on 2012-07-17
> **hax3 said:**
> I just installed Evolution 3.2.1 using PeteNetLive walkthrough.
 
I got it working for receiving emails but I can't send emails. It doesn't seem to be using the MAPI connection to exchange to send email as the email is stuck in the out box under the "On This Computer" folder tree instead of the Outbox under Exchange Email Account Tree on the main left navigation frame of Evolution. 
 
Anyone have any idea? I did a google search and someone submitted the same issue in LaunchPad last week with no reply...
 
TIA
 
I don't know HOW it works, or WHY it works BUT I noticed my outgoing messages were stuck in the Outbox under the "On This Computer" folder tree instead of the Outbox under Exchange Email Account Tree as indicated above.  I tried moving that Outbox into the Exchange Email Account Tree but it would not move, so I created another Outbox immediately below my Inbox and moved the contents of the first Outbox into the latter Outbox.  Everything went and when I tried sending another message that went out with no difficulty.  Like I say, I have no idea How or Why, and if somebody cleverer than I can explain it, please do.

---

