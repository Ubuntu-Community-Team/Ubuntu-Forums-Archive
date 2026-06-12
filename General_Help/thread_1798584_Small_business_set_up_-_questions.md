---
title: "Small business set up - questions"
date: 2011-07-06
forum: General Help
---

### Post by Berduchwal on 2011-07-06
I run small accountancy firm and use Ubuntu for it.

There are few improvements to our systems I would like to make and I need some advice.

1) I want to have central list of users that is applicable for all office PCs with common passwords privileges and user names 

2) Common email folders (so if on my PC I file and email into folder some else can access this email)

3) Common hard drive

Preferably I would like to avoid setting up separate server at first. 
One office PC which is a main PC could potentially play a role of a server and desktop at the same time.

Number of concurrent users will be no greater then 4. 

Can you please let me know if this is possible and where can I find info about such things.

---

### Post by perspectoff on 2011-07-06
LDAP (OpenLDAP for Linux) is what you'll likely want for the database of users/passwords.

It is Windows-compliant so any Windows (Outlook, etc.) users can use it.

An alternative is to use a database such as MySQL or PostgreSQL to contain the users/passwords, but in the long run OpenLDAP will be the most universally-compliant and expandable.

You might want groupware. (cf. [http://www.kubuntuguide.info/index.php/Natty#Groupware](http://www.kubuntuguide.info/index.php/Natty#Groupware) or [http://ubuntuguide.org/wiki/Ubuntu:Natty#Groupware](http://ubuntuguide.org/wiki/Ubuntu:Natty#Groupware) ). Right now, Zimbra is one of my favorites (even though it is owned by Yahoo, and therefore, by proxy, Microsoft). It is what Yahoo itself now uses (in order to compete with Google), I believe.

Zimbra is largely Java-based and there is a good community edition. It started out as a college project and has the mentality of an open source system, even though it is now proprietary. It is probably one of the easier ones to set up.

If you don't need a full groupware solution, though, you can easily set up a mail server (dovecot-postfix) in house for your own usage. Ubuntu has a fairly nice mail server 

 sudo apt-get install dovecot-postfix

that will install everything (the basics, anyway) in about 20 minutes. It's then up to you to integrate the mailserver with LDAP or another database scheme like MySQL or PostgreSQL. If you only have a few users, you don't even need to do that, however. I only have 8 users on one installation and don't even bother with a database with that one. (cf. [http://www.kubuntuguide.info/index.php/Natty#Mail_servers](http://www.kubuntuguide.info/index.php/Natty#Mail_servers) or [http://ubuntuguide.org/wiki/Ubuntu:Natty#Mail_servers](http://ubuntuguide.org/wiki/Ubuntu:Natty#Mail_servers) ).

There is a fully integrated email solution with LDAP already integrated called iRedMail. I haven't tried it, but some people love it.

I happen to like DAViCal as a groupware calendaring server, using Thunderbird with the Lightning extension (or the standalone client Sunbird) to access it.

Lastly, if you need more than Skype for teleconferencing, look into BigBlueButton from Google. It's a lot of work to set up (and if used regularly should be on its own server), but it's pretty nice to have if you are a far-flung business concern.

A central hard drive is trivial. Just go buy a network-enabled hard drive. If you want something big, robust, expandable, and hot-pluggable, get a NAS (network-attached storage).

The Netgear ReadyNAS is a pretty good one, although there are lots of options these days. Having hot-swappable RAID capability means that if one of the multiple hard drives fails in the NAS, you can plug in another and keep on going without too much stress (since the data is redundantly stored on multiple hard drives for security). It's more expensive, but more reliable for a business. (If money is no object, get a Synology, which is the best, IMO).

If you want shared folders for web access, you can set up some WebDAV folders someplace (but I would never expose a central hard drive to the Internet using WebDAV). (cf. [http://ubuntuguide.org/wiki/Ubuntu:Natty#WebDAV](http://ubuntuguide.org/wiki/Ubuntu:Natty#WebDAV) or [http://www.kubuntuguide.info/index.php/Natty#WebDAV](http://www.kubuntuguide.info/index.php/Natty#WebDAV) ).

---

### Post by grahammechanical on 2011-07-06
May I turn your mind in a different direction?

Imagine a school administrator needing to centrally control the students access to the school computers. I have been checking out Edubuntu. I think that there are programs in that bundle that do what you are looking for in number 2. I am not suggesting you go over to Edubuntu but to look at how the people putting that bundle together cover the matter of administrating the network.

Regards.

---

### Post by perspectoff on 2011-07-06
> **grahammechanical said:**
> May I turn your mind in a different direction?

Imagine a school administrator needing to centrally control the students access to the school computers. I have been checking out Edubuntu. I think that there are programs in that bundle that do what you are looking for in number 2. I am not suggesting you go over to Edubuntu but to look at how the people putting that bundle together cover the matter of administrating the network.

Regards.

Are you talking a school-related groupware solution like School Tool (SchoolTool.org) ? That might have a lot of stuff (grading, attendance, etc.) that an accountant might not be interested in.

( sudo apt-get install schooltool )

Or a thin-client solution like LTSP?

 ( sudo apt-get install ltsp-server ltsp-manager ltsp-client )

Or a little of both, like iTalc?

Or like OutKafe, OpenKiosk, CafePilot, Untangle, monoWall, or ClearOS?

Edubuntu is pretty top heavy with extra stuff if one only wants a thin-client solution.

Perhaps a customer-relationship management system? SugarCRM Community Edition ( [http://www.sugarcrm.com/crm/download](http://www.sugarcrm.com/crm/download) ) ?

---

### Post by Berduchwal on 2011-07-06
Thank you very much.
This is a bit of information overload :) but I tried to make sens of it.

I only have ubuntu machines so windows compliance is not needed.
I run one instance of XP via virutal machine.

Ok so this groupwere software runs on server and clients connect to it. 
I have external provided that hosts my webserver and where my email accounts are hosted is this going to interfere?
So this groupwere is mainly for email, contacts, calendar and email folders?

So for common login I need something seperate? 
Like the openLDAP.
So openLDAP will override standard login screen somehow with one that connects to the server?

I have a NAS driver currently it is equiped with linux server of some sort as I use it for seeding torrents :)
So are you saying I can also use it for primary file storage with directory access?

Will then NAS need to check user permissions with openLDAP server?

---

### Post by perspectoff on 2011-07-06
There are many ways to store lists of users and passwords.

The Linux system itself stores a list of users and passwords for logon, doesn't it? That is stored in a small database (pamdb, I think).

It is possible to have a mail server that only allows the system users of the computer that the mail server is installed on to have email accounts. That is the most basic method.

(You could use the same user authentication method for any other server the lives on the same computer, as well.)

It is when you expect your user base to grow that you need a more robust method to manage users and passwords. That's where databases such as MySQL, PostgreSQL, and OpenLDAP come in.

You can have a central list of users and passwords, and additionally can assign them privileges to access different systems/servers at different security levels. That can add quite an order of complexity.

The central database ought to be accessible by the web if you intend to use it as a "single sign-on" information repository for multiple servers. To implement this, the database should then also be accessible as its own server.

That is a way that OpenLDAP is used, for example. You can have an OpenLDAP server that can provide a database of users/passwords/servers and can provide an independent referee service between users and services. It is often (but not always) accessed through the network. Both a user and a net-based service would both log in to the OpenLDAP server to find out about permissions. It's an ordeal to set this up for a small business owner, and is probably overkill. (Then again, small businesses can eventually become big businesses, can't they?)

I suspect you will be happiest with one of three groupware solutions: Zimbra, Citadel, or iRedMail (the last one for email only, though).

I would read about each and then make a decision. All have automated installers.

---

### Post by SeijiSensei on 2011-07-06
OpenLDAP is, to put it bluntly, a pain in the a** to configure.  I'd recommend using **NIS** since all the clients are running Ubuntu.  You just set up ordinary user accounts on the server, then run the NIS utilities to configure network authentication.  See this:  [http://tldp.org/HOWTO/NIS-HOWTO/index.html](http://tldp.org/HOWTO/NIS-HOWTO/index.html)  (Don't worry about the 2003 date on this document; NIS hasn't changed much in a long time now.)

Again if the clients all run Ubuntu, use **NFS** to share any common resources.  The alternative is to use Samba, but that's only of value in a mixed Linux/Windows environment.

You will need a server to manage things.  It doesn't need to be all that "heavy" though.  A decent older machine with a 1GB of memory will work fine.  Otherwise just buy a low-end server from Dell like this [T110]("http://www.dell.com/us/business/p/poweredge-t110/pd?oc=becwlk1&model_id=poweredge-t110").

As for the shared email folder, you'll want to be using IMAP on your server.  Then you can set up the shared folder either via **dovecot**, the IMAP server software, or by simply creating the shared folder somewhere and adding symbolic links to it in each user's /home/user/mail directory.  Make sure it has world-writable permissions.  You can make this automatic by editing /etc/skel before creating users.  Whatever files and directories appear in /etc/skel automatically become the files and directories of each new user.

Oh, and since your email is hosted externally, you should take a look at **fetchmail**.  It will routinely poll the remote mailbox(es) and download their contents to the local machine.  Here's a [write-up]("https://help.ubuntu.com/community/GmailPostfixFetchmail") on using fetchmail to get messages on a Google Mail account.

Out of curiosity, what programs are you using to run an accounting practice on Ubuntu?  I was of the belief that there is no decent professional accounting software that runs on Linux.  My last encounter with accounting software was at a manufacturing client's site; they used Sage which is what their accountants installed and maintained.

Eventually you should make the acquaintance of **rsync** to set up automated backups.

---

### Post by drdos2006 on 2011-07-06
Have a look at Citadel groupware, it may suit your needs.

[http://www.citadel.org/doku.php/start](http://www.citadel.org/doku.php/start)

regards

---

### Post by Berduchwal on 2011-07-07
I am based in the UK.
I use variety of packages for accountancy.
The only semi decent is kMyMoney but I also use gnuCash. There is nothing like sage or quickbooks but since now tax offices enables you to do onlinie filling for accounts and they provide PDF to submit any package is fine.

kMyMoney is a pain to set up and sometimes it drives me crazy but works.

I will get some sort of PC to run server and see what I can achieve.

Thank you

---

