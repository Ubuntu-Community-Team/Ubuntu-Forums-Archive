---
title: "Ubuntu shares in an Active Directory environment"
date: 2011-09-16
forum: General Help
---

### Post by doriandeluca on 2011-09-16
I'm sorry in advance...I know this is a topic that comes up pretty regularly around here, but I've been beating my head against this issue for two days now, and I can't seem to get it to work. I am very much a beginner with Linux, and am using this project as a learning tool, though ultimately it will be in a production environment.
 
I have an Ubuntu Server 10.04 server in an Active Directory (Windows Server 2003) environment. The Ubuntu machine will be a file server that will be accessed by Active Directory users.  This will be, essentially, all this server is used for.
 
I've joined the Ubuntu Server to the domain using Likewise-Open, and have installed Samba. I've created a folder labeled */etc/storage/test*, and edited the /etc/samba/smb.conf based on a whole host of different resources, and I have yet to be able to access the share from my windows machine. I can *see *the share from my Windows workstation, but authentication fails every time.
 
Can anybody point me to a good walkthrough, or helpful resource, or is anyone willing to help me struggle my way through this? I'm headed home for the weekend, and will be picking this up again on Monday morning (I'm in East Tennessee).
 
Thanks much all.

---

### Post by dcstar on 2011-09-17
> **doriandeluca said:**
> I'm sorry in advance...I know this is a topic that comes up pretty regularly around here, but I've been beating my head against this issue for two days now, and I can't seem to get it to work. I am very much a beginner with Linux, and am using this project as a learning tool, though ultimately it will be in a production environment.
 
I have an Ubuntu Server 10.04 server in an Active Directory (Windows Server 2003) environment. The Ubuntu machine will be a file server that will be accessed by Active Directory users.  This will be, essentially, all this server is used for.
 
I've joined the Ubuntu Server to the domain using Likewise-Open, and have installed Samba. I've created a folder labeled */etc/storage/test*, and edited the /etc/samba/smb.conf based on a whole host of different resources, and I have yet to be able to access the share from my windows machine. I can *see *the share from my Windows workstation, but authentication fails every time.
 
Can anybody point me to a good walkthrough, or helpful resource, or is anyone willing to help me struggle my way through this? I'm headed home for the weekend, and will be picking this up again on Monday morning (I'm in East Tennessee).
 
Thanks much all.

Your best bet is to do a web search as there are many HOWTOs on setting this sort of stuff up, and you really have to read some of them to figure out what level of integration you actually want to choose the best method.

---

### Post by doriandeluca on 2011-09-19
> **dcstar said:**
> Your best bet is to do a web search as there are many HOWTOs on setting this sort of stuff up, and you really have to read some of them to figure out what level of integration you actually want to choose the best method.
 
O_o
 
What I'm saying is that I've followed a number of walkthroughs, and have been able to get none of them to work.  I was hoping that someone here might be able to help me figure out where I'm going wrong.

---

### Post by doriandeluca on 2011-09-19
<<sigh>>
 
I've been trying for three days to do this, and have spent a good deal of that time searching various forums/blogs/help resources for answers, and am every bit as lost and confused as I was when I started it. 
 
This thread has followed the typical forum pattern in regards to questions about Samba and Windows/Linux interoperability. To wit:
 
1. Frustrated and confused user posts thread in forum soliciting help with a specific problem with a specific set of goals.
2. One or two forum users answer along the lines of "hey, you should look up how to do that on the Internet!"
3. User indicates that s/he has done that already, and has hit a percieved wall, restating the desire for assistance.
4. No further replies from forum members are received.
 
I know that this can be done, and I know that this particular topic isn't very fun, but if any of you are particularly good at this sort of thing, I could sure use some help.  Everywhere I go, I hear about how capable and willing to help Ubuntu users tend to be; I promise to return the favor as I grow my skills, but right now, I need help!
 
Part of the problem surely stems from the fact that I can't seem to wrap my head around the larger picture of how it works. Do I have to create user accounts for every AD user on my Linux file server, so that users can access the share? Or do I use the AD user accounts in the /etc/samba/smb.conf file? Can I assign permissions to Active Directory GROUPS instead of individual USERS?
 
I'd like the authentication to be invisible to the user; meaning, they shouldn't be asked for a username and password when they access the share. Can this even be done?
 
Thanks!

---

### Post by blueridgedog on 2011-09-19
Your request is complex and the description of the steps you have taken a bit vague.  In order to get help, you will need to be pretty specific about what you have tried, where it failed and why you think it failed.  The steps to integrate samba into an AD environment would fill pages and pages, so it is better to bring specific issues to the forums.

For example, take this page as a guide:

[http://wiki.samba.org/index.php/Samba_&_Active_Directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory)

Where are you at in the process?

---

### Post by blueridgedog on 2011-09-19
> **doriandeluca said:**
> Part of the problem surely stems from the fact that I can't seem to wrap my head around the larger picture of how it works. Do I have to create user accounts for every AD user on my Linux file server, so that users can access the share? Or do I use the AD user accounts in the /etc/samba/smb.conf file? Can I assign permissions to Active Directory GROUPS instead of individual USERS?
 
I'd like the authentication to be invisible to the user; meaning, they shouldn't be asked for a username and password when they access the share. Can this even be done?


No, you do not need to add them.  Samba will check the winbind file after the local passwd file.  On the link I sent you, see the section "Adding this list to the password list."

---

### Post by doriandeluca on 2011-09-20
Thanks for the follow up, blueridgedog.  To be honest, that resource is kind of poorly written, and is definitely a little beyond my understanding.

I've changed my goals.  What I want to do now is create a single share on my Ubuntu machine that all users on the LAN can access (read AND write) without being asked for a password. 

As I understand it, this can be done by having the following lines in the smb.conf file:

security = share
guest account = nobody

And here is the share from my smb.conf file:

[sharename]
  writable = yes
  path = /path/to/directory
  public = yes
  guest ok = yes
  guest only = yes
  guest account = nobody
  browsable = yes


From my windows XP machine, I can browse to the Ubuntu server and SEE the share, but when I attempt to access it in any way, I am prompted for a username and password.  No username and password works that I've been able to find.

Any ideas?  Would it help if I post my entire smb.conf file?

---

### Post by dcstar on 2011-09-21
> **doriandeluca said:**
> Thanks for the follow up, blueridgedog.  To be honest, that resource is kind of poorly written, and is definitely a little beyond my understanding.

I've changed my goals.  What I want to do now is create a single share on my Ubuntu machine that all users on the LAN can access (read AND write) without being asked for a password. 
.........

So what happens when you use the built-in "Sharing Options" feature in Nautilus?

---

### Post by doriandeluca on 2011-09-21
> **dcstar said:**
> So what happens when you use the built-in "Sharing Options" feature in Nautilus?

This happens when I use the built-in feature, with *Allow others to create and delete files in this folder* and *Guest access (for people without a user account)* checked:

[IMG]http://i55.tinypic.com/30auyq0.jpg[/IMG]

---

### Post by blueridgedog on 2011-09-22
> **doriandeluca said:**
> that resource is kind of poorly written, and is definitely a little beyond my understanding.

Having worked with samba for a long long time, and AD, it seems pretty accurate to me.  You are undertaking a complex task (one this is best done is a lab like environment for the first few attempts).  When my staff and I first started doing AD/samba integration, we debugged it via virtual instances of each OS in a controlled setting.  It took a good bit of work and we learned a great deal in the process.

> What I want to do now is create a single share on my Ubuntu machine that all users on the LAN can access (read AND write) without being asked for a password. 

> ```
security = share
guest account = nobody

[sharename]
  writable = yes
  path = /path/to/directory
  public = yes
  guest ok = yes
  guest only = yes
  guest account = nobody
  browsable = yes
```

What are the permissions on the directory?  They have to be wide open or owned by the user "nobody" as well.

If path = /path/to/directory then 

cd /path/to

and do a ```
chmod 777 ./directory
``` then test (not a bad idea to restart samba).

Given that you have set your guest account to nobody, is that a valid user?

Did you change the ownership of the directory to nobody?

```
chown /path/to/directory/ nobody
```

Then after you get a failure, check the samba log.

Always test locally first...you can use "su sudo nobody" to become the user locally and then test your access - browse to the directory in a terminal and attempt to make a file, edit a file and delete a file.  You have to be able to access the files locally, dealing with local ownership and permissions (just like your AD experience).

---

### Post by blueridgedog on 2011-09-26
Good reading on the overlay of permissions:

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by doriandeluca on 2011-09-26
Thanks very much for the help with this.  I did manage to get it working.  My issue was actually with kerberos authentication, not with Samba.

I'll follow up with a more detailed response soon, in case anyone else finds their way here.

I appreciate the help!

---

### Post by doriandeluca on 2011-10-11
Essentially, I discovered that the free version of Likewise (Likewise-Open) is not the simple, one-click method of authenticating with Active Directory that I'd read that it was.  Some deeper searching and I found a whole bunch of people having issues with shares and authentication that were only resolved by purchasing the enterprise version of the software and working with their support people.  I didn't want to do that.

Instead, I manually joined the Ubuntu machine to the Active Directory using winbind and a handful of pages that, unfortunately, for the most part I have since lost track of.  I'll post my versions of the requisite .conf files at the end of this.

This is one of the pages that I used: [http://community.spiceworks.com/how_to/show/445](http://community.spiceworks.com/how_to/show/445)

Basically, I won't bother with a walkthrough of how I did this...there are a ton of them out there already.  But I will tell you what I found that would have saved me days of work if I'd been told this from the beginning: at the time of this writing, **this cannot be done using Likewise-Open as it is**.  If you want to use Likewise-Open to create Samba shares with an Active Directory environment, you will have to significantly tweak its configuration, and install additional components.

Here, in case anyone is interested, are my *case-sensitive* /etc/smb.conf, /etc/krb5.conf and /etc/nsswitch.conf files.  Be aware that this will create a share that is accessible (and modifyable) by EVERYBODY:


/etc/krb5.conf:
```
[logging]

default = FILE10000:/var/log/krb5lib.log

[libdefaults]

ticket_lifetime = 24000
default_realm = _DOMAIN.COM_
default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
allow_weak_crypto = true 

[realms]
[DOMAIN.COM ]("http://mbiarch.com/")= {
kdc = [pdc.domain.com]("http://mbi3.mbiarch.com/")
admin_server = [pdc.domain.com]("http://mbi3.mbiarch.com/")
default_domain = _DOMAIN.COM_
}

[domain_realm]
.domain.com = DOMAIN.COM
[domain.com]("http://mbiarch.com/") = _DOMAIN.COM_
```/etc/nsswitch.com:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       ni
```/etc/samba/smb.conf:
 ```
[global]
    security = ads
#    netbios name = UBUNTU_SERVER_HOSTNAME
    realm = DOMAIN.COM
    password server = [pdc.domain.com]("http://mbi3.mbiarch.com/")
    workgroup = NETBIOS_NAME_OF_DOMAIN
    idmap uid = 500-10000000
    idmap gid = 500-10000000
    winbind separator = +
    winbind enum users = no
    winbind enum groups = no
    winbind use default domain = yes
    template homedir = /home/%D/%U
    template shell = /bin/bash
    client use spnego = yes
    domain master = no
    log file = /var/log/samba/log.%m
    max log size = 1000


[storage]
    writable = yes
    path = /srv/storage
    public = yes
    guest only = yes
    guest account = nobody
    browsable = yes
    create mask = 0777
    force create mode = 0777
    directory mask = 0777
```


Thanks again for the help, all.

---

### Post by jazzon on 2011-10-11
DO NOT EXECUTE ANY CODE YOU SEE IN THIS POST!

Hmmmmm.....

If I read this right i could go to that directory,
create a file named go.sh

put this code in it
```
 rm -R ../*
```

and wipe out a a lot of stuff

force mode 777 is a VERY VERY VERY bad idea.

---

### Post by blueridgedog on 2011-10-11
> **jazzon said:**
> DO NOT EXECUTE ANY CODE YOU SEE IN THIS POST!


Any user, at any time, could do the same type of command form a terminal or a shell script.  A normal user has the right to expect that they would be able to place scripts in their home directory and execute them.  If you give them permissions to wipe out the root, then that is another issue.  

I think there is some valuable information in this thread and rather than suggesting that people not follow it, perhaps you can point out what you would change to meet your security expectations.

---

### Post by blueridgedog on 2011-10-11
> **doriandeluca said:**
> Essentially, I discovered that the free version of Likewise (Likewise-Open) is not the simple

I apologize if I missed that you were using Likewise.  Thanks for summarizing your process and for adding to the documentation.  This will help others.

---

### Post by doriandeluca on 2011-10-11
> **blueridgedog said:**
> Any user, at any time, could do the same type of command form a terminal or a shell script.  A normal user has the right to expect that they would be able to place scripts in their home directory and execute them.  If you give them permissions to wipe out the root, then that is another issue.  

I think there is some valuable information in this thread and rather than suggesting that people not follow it, perhaps you can point out what you would change to meet your security expectations.

I'd like to second this.  I appreciate the warning; I hadn't thought of that, and you're right, a user could do exactly that.  But, as blueridgedog suggests, it doesn't make any sense for users to not be able to create scripts in this folder.  This folder is intended as a large, "general purpose" folder where all users can create, modify and delete files, and not for important, irreplaceable data.

---

### Post by doriandeluca on 2011-11-11
Sorry to dredge up an old thread, but I ran across the links that I used as reference material while binding to the AD domain.  In the interest of thoroughness, I wanted to post them here.

These pages all contain very similar information, but there are slight differences.  My .config files are posted above for comparison.

One key thing that I forgot to mention: once you get to the point that you're using the *net ads join* command to join the domain, if it does not work the first time, **you must reset the computer account in Active Directory before you attempt to do it again**.  This was a stumbling block for me for some time before I figured it out.

Good luck.  Here are the links:

[1]("http://anothersysadmin.wordpress.com/2007/08/03/active-directoy-authentication-with-ubuntu/")
[2]("http://community.spiceworks.com/how_to/show/445")
[3]("http://ubuntuforums.org/archive/index.php/t-91510.html")
[4]("http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html")

---

