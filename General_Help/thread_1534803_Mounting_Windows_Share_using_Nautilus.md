---
title: "Mounting Windows Share using Nautilus"
date: 2010-07-20
forum: General Help
---

### Post by Jackson Tan on 2010-07-20
Hi all,

I need some help on mounting a Windows share on my Ubuntu 9.10 laptop.

In Nautilus, I can find the share under Network which I want to mount. When I double-click on the desired folder, I was prompted for a username, domain and password. However, I could not log in; there was no error messages, but Nautilus kept prompting me for my username etc..

It would seem like I've entered the wrong details, but I've used a Mac OS to access the share using the same wired network and I had no problems doing so.

So what could be the problem? Am I missing some setting? Or is the Windows share setting denying access to Linux systems?

---

### Post by robsoles on 2010-07-20
I haven't had a problem mounting shares from Samba using both windows and Linux hosts.

Assuming by "Windows share" you mean from a windows OS - are you using the 'workgroup' the windows host is in, in the domain box (in nautilus password prompt) if you haven't set up a domain controller?


If nothing in my post so far has gotten you access to the share, please supply a bit more info.

What is the host OS that has the share you are trying to access? What kind of sharing is defined on that host?

---

### Post by theozzlives on 2010-07-20
Make sure you set your smbpasswd to the same password you have in Windows:
```
sudo smbpasswd -a <your_user_name>
```

---

### Post by Morbius1 on 2010-07-20
> In Nautilus, I can find the share under Network which I want to mount.  When I double-click on the desired folder, I was prompted for a  username, domain and password. However, I could not log in; there was no  error messages, but Nautilus kept prompting me for my username etc..The first question I guess is did you create the share on Windows to require a username and password? Or was it created as a simple share accessible to guests?
>  So what could be the problem? Am I missing some setting? Or is the  Windows share setting denying access to Linux systems?     Oddly enough if could be if you have "Windows Live Sign-In Assistant installed" : [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
Although I would think that would have affected the Mac as well.

Post the output of the following command from the Linux box to see if it gives us any useful error messages:
```
smbtree
```And just in case there is something misconfigured in the client Linux box post the output of this command as well:
```
testparm -s
```It could be something simple like the client is passing an unencrypted password to the server.

---

### Post by Jackson Tan on 2010-07-20
Hi all!

Thanks for your time and replies. I appreciate that greatly!


**[SIZE=2]robsoles[/SIZE]**:

> Assuming by "Windows share" you mean from a windows OS - are you using the 'workgroup' the windows host is in, in the domain box (in nautilus password prompt) if you haven't set up a domain controller?Honestly, I'm somewhat confused with the workgroup/domain thing, since I'm new to SMB and I'm using it only as an end-user. But I've used exactly the same details in Nautilus as I have for the login from Mac OS (which was successful), and it doesn't work.

> If nothing in my post so far has gotten you access to the share, please supply a bit more info.

What is the host OS that has the share you are trying to access? What kind of sharing is defined on that host?I'm not sure of the host OS, since it is a shared server for everyone in the lab to use. It appears as a Windows share under the Places > Network, but it could be a Mac since the lab uses primarily Apple computers.

As for the type of sharing, I'm not sure either, but I know I have write access to the directory assigned to me, as tested on the Mac OS.


**[SIZE=2]theozzlives[/SIZE]**:

I've tried the command but it returned "Failed to add entry for user <username>". Not sure if this is a problem, but the username for my Ubuntu is not the same as the one that I'm using for the share.


[SIZE=2]**Morbius1**[/SIZE]:

> The first question I guess is did you create the share on Windows to require a username and password? Or was it created as a simple share accessible to guests?I'm pretty sure that is the case. When I tried to access from Nautilus, I get a prompt for username/domain/password. Remember also that I could access the share through Mac OS without any problems.

As for the smbtree output, the relevant share was:

```

RSES
    \\SPACE1                 RSES Backup Server
        \\SPACE1\gfd                RSES GFD-SPACE Users
        \\SPACE1\IPC$               IPC Service (RSES Backup Server)

```I was allocated a folder by my supervisor under the folder gfd.

There were no error messages associated to the share SPACE1 that I was trying to login to, but there were other shares under RSES which complained of NT_STATUS_BAD_NETWORK_NAME and NT_STATUS_UNSUCCESSFUL.

As for testparm -s:

```

[global]
    workgroup = RSES
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    wins support = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /media/samba/
    force user = <username>
    force group = <username>
    read only = No
    create mask = 0644

```The username under [MyFiles] did show the username I was supposed to log in to the share.

Does anything appear wrong?

---

### Post by robsoles on 2010-07-21
I am used to testparm and smbpasswd only being necessary to run if you are setting up samba as a server and not just trying to use the client features of it. That is to say, where you enable a host to allow shares from it - not where you are trying to access shares from another host.

If the local machine doesn't need to share folders then you shouldn't need to refer to terminal - if you are running a desktop using nautilus and you can 'see' the share in 'network' by using nautilus then you have appropriate packages installed and now all you need to do is get your credentials right.

<snip> - just tried opposite of what this bit was about and seem to have proved myself wrong (LOL) - must be down to allowed hosts or similar kind of blocking - maybe I am wrong about being wrong but I can't leave it here as I had it a minute ago! </snip>

You might have to ask the laboratory/network administrator more about the network (ie, domain name or workgroup) and whether or not just any PC can be used to authenticate or if it is restricted to PCs that have been allowed - pretty sure I saw functionality to define 'allowed hosts' using samba last time I set up a domain controller using it for anyone.

---

### Post by Morbius1 on 2010-07-21
You have multiple issues here. One is the subject of this thread which is using an Ubuntu samba client to access a Windows share. This didn't make any sense to me:
> [SIZE=2]**Morbius1**[/SIZE]:

[QUOTE]The first question I guess is did you create the share on Windows to  require a username and password? Or was it created as a simple share  accessible to guests?  I'm pretty sure that is the case. When I tried to access from  Nautilus, I get a prompt for username/domain/password. Remember also  that I could access the share through Mac OS without any problems.[/QUOTE]Until I read this:
> I was allocated a folder by my supervisor under the folder gfd.Follow robsoles advice and find out what username and password ( if one is required ) the server expects from you. You mention the Mac as having access. Do you supply a username and password when using the Mac or do you have free access without authentication. The bigger issue here is how the server is set up. Is it part of a domain or Active Directory? There may be a separate authentication server that controls access to the domain. This is a little beyond my pay grade I'm afraid.

The other issue you have is really another post and that's using the Samba server on your Ubuntu machine:

(1) Your smb.conf ( output of testparm ) is a mess and I'm guessing it's because your using a HowTo that's 4 years old: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605). Quite a few things have changed in 4 years. I can show you how to reset your smb.conf to the factory fresh settings when you post your other thread.

(2) > 
I've tried the command but it returned "Failed to add entry for user  <username>". Not sure if this is a problem, but the username for  my Ubuntu is not the same as the one that I'm using for the share.That's the best practice. It's never a good idea to create a samba user that matches your own ubuntu login user name. But you can only create a samba password for a local ubuntu user. You need to create a separate local user first then create a samba password for that user. Again this is for another post.

---

### Post by robsoles on 2010-07-21
> **Morbius1 said:**
> 

(2) That's the best practice. It's never a good idea to create a samba user that matches your own ubuntu login user name. But you can only create a samba password for a local ubuntu user. You need to create a separate local user first then create a samba password for that user. Again this is for another post.

I can't disagree with morbius1 about best practice but I feel concerned to point out that in two samba 'domain controller' setups I am responsible for right now (work & home) that I have assigned samba users using the same passwords as their Linux counterparts - of course I mean that the usernames are the same where I know how I could associate a different username under samba than they have in Linux and still make their home-directoriies workout/equate the same (I happen to have set their passwords the same as much effort as that was - had to make a Linux user, set their password and then make a samba user equating to the Linux user and set their password as well!)

I could fill pages with the crap I have learnt about this stuff but I would feel like I was ranting really - what I was hiding in my previous post is that I don't think you have told the "lab's admin" that you are trying to get to the shares you are talking about (from your laptop), please tell [COLOR=Red]everybody[/COLOR] if I am wrong.

---

### Post by Morbius1 on 2010-07-21
> **robsoles said:**
> I can't disagree with morbius1 about best practice but I feel concerned to point out that in two samba 'domain controller' setups I am responsible for right now (work & home) that I have assigned samba users using the same passwords as their Linux counterparts - of course I mean that the usernames are the same where I know how I could associate a different username under samba than they have in Linux and still make their home-directoriies workout/equate the same (I happen to have set their passwords the same as much effort as that was - had to make a Linux user, set their password and then make a samba user equating to the Linux user and set their password as well!)
As it turn out I'm not going to disagree with you either ;). But in a typical home network samba sharing is more peer-to-peer. 

Let's say John creates a share and wants Mary to provide authentication to gain access. Most Samba HowTo's insist that John set up a samba user named mary that has a username and password that matches Mary's local login username and password. At that point John knows how to login to Mary's local machine. If Mary set's up a share for John to access and follows the same advice, Mary can now log into John's local machine. You can either set up a different set of usernames and passwords, same username but different passwords, or don't authenticate at all - just create a share that allows guest access and limit access by "hosts allow" to preserve privacy.

What you're talking about in setting up a domain controller is different. You are the  master of your network and you are controlling everyone's access within  it. If you want to set it up so that usernames and passwords match that's your prerogative since you've become the System Administrator but at least only one person knows everyones username and password.

---

### Post by Jackson Tan on 2010-07-22
Hi robsoles and Morbius1,

Thanks for the help! Sorry if I'm confusing matters up, since this is my first time using smb.

> now all you need to do is get your credentials right.> Follow robsoles advice and find out what username and password ( if one is required ) the server expects from you. You mention the Mac as having access. Do you supply a username and password when using the Mac or do you have free access without authentication.I need to supply a username and password when using the Mac, and I'm pretty sure I got it right since it is the same as my username and password for my University account. The prompt for logging in in both Mac and Ubuntu appears when I try to access anything deeper than the folder gfd.


> Is it part of a domain or Active Directory? There may be a separate authentication server that controls accesxs to the domain. This is a little beyond my pay grade I'm afraid.I'm not too sure of the difference between the domain and Active Directory, but I think the domain name I'm using is correct since the Mac can get in with it.

By the way, the domain is an interesting one. Most people I've spoken to, including my supervisor and one IT staff, knew nothing about the domain. It was something they did not encounter. Apparently, what happens is that Mac (which is the standard for the lab) identifies the correct domain automatically. That was what Nautilus did not do (it gave the domain of "WORKGROUP" instead).


> You might have to ask the laboratory/network administrator more about the network (ie, domain name or workgroup) and whether or not just any PC can be used to authenticate or if it is restricted to PCs that have been allowed - pretty sure I saw functionality to define 'allowed hosts' using samba last time I set up a domain controller using it for anyone.I can ask the IT support if any PCs can access the share, or only the machines issued. I'm pretty sure all would be able to access since people may want to use their own laptops (like me), but that's one thing I can find out.

But they did tell me that I'm quite on my own if I use Linux, since they only lend support for Macs and (to a small extent) PCs. And after all, I could log in with a Mac... 


> Your smb.conf ( output of testparm ) is a mess and I'm guessing it's because your using a HowTo that's 4 years old: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605). Quite a few things have changed in 4 years. I can show you how to reset your smb.conf to the factory fresh settings when you post your other thread.I guess that probably comes about when I was Googling ways to get the share to mount, prior to posting my problem here. If it is not essential, I suppose it can wait until the main problem is resolved (especially if it takes some effort to clean out the smb.conf).

---

### Post by robsoles on 2010-07-22
When you open 'network' from 'places' the first "level" within is "Windows Network" - when you double click that to open it the name of local area workgroup or domain is usually the contents of it...

You should be able to use the name of the workgroup/domain, that you enter (by double-clicking) to find the machine that you want the share off, in the 'domain' text box in the password prompt! :)

Lemme know just how wrong I am when you try it!

---

### Post by Jackson Tan on 2010-07-22
> When you open 'network' from 'places' the first "level" within is "Windows Network" - when you double click that to open it the name of local area workgroup or domain is usually the contents of it...

You should be able to use the name of the workgroup/domain, that you enter (by double-clicking) to find the machine that you want the share off, in the 'domain' text box in the password prompt! :)

Alright, so are you saying that under Places > Network, I have Windows Network > DOMAIN, and that is the domain name I should be using?

That's precisely the domain I used (which also appeared on the Mac). But the prompt for password only came when I tried double-clicking on Windows Network > DOMAIN > (?)SERVER NAME > gfd.

---

### Post by robsoles on 2010-07-22
so what I am saying is to put whatever that DOMAIN is into the box in the middle of that password prompt in nautilus

Username: [robsoles            ]
Domain:   [ubuntuforums.org    ]
Password: [*********           ]

Whatever that 'group' is that you have to double click on to see the server with that share named 'gfd' needs to replace 'ubuntuforums.org' in my example block above along with your username and password.

Does that make it work for you if you do that?

---

### Post by Jackson Tan on 2010-07-22
> so what I am saying is to put whatever that DOMAIN is into the box in the middle of that password prompt in nautilus

Username: [robsoles            ]
Domain:   [ubuntuforums.org    ]
Password: [*********           ]

Whatever that 'group' is that you have to double click on to see the server with that share named 'gfd' needs to replace 'ubuntuforums.org' in my example block above along with your username and password.

Does that make it work for you if you do that?No, I'm afraid it doesn't. That was what I've been trying all the time (and with other possible domain names). And yes, the Mac can log in with *that* domain name. That's what's really confusing me...

---

### Post by robsoles on 2010-07-22
Is laptop you are using powerful enough to run a VM of Windows XP?

You could test two things if so: (1) Can XP access this share? (2) Can Ubuntu host access a share on your VM of XP?


I'll look into possible solutions some more when I get home tonight - my lunch break is about to be finished, good thing I ate before I checked my subscriptions!

---

### Post by Jackson Tan on 2010-07-23
> **robsoles said:**
> Is laptop you are using powerful enough to run a VM of Windows XP?

You could test two things if so: (1) Can XP access this share? (2) Can Ubuntu host access a share on your VM of XP?

I suppose I can get a virtual XP running, but there's an easier way, I think. This laptop I'm using comes with Windows 7 (though I hardly use it nowadays), so I can try to access the share through it.

But now, here's the embarrassing part. How do I go about accessing the share through Windows 7? Is it under Networks in Windows Explorer? I tried that, but there are only a few items shown there, none of which contains the server/share that I want.

Is that an indication that the share in question is only accessible by Macs? Or is Windows 7 just trying to be difficult to me?

I'll probably try again later or tomorrow if I have the time.

---

### Post by robsoles on 2010-07-23
I killed my only chance to have win7 as soon as I looked at it - little laptop with no CD/DVD ROM tray and I went out of my way to make a USB installer of Ubuntu for it!

Having said that I have some dim memory of win7 and they do try harder and harder to make everything look like they make it happen by magic (MS that is) so - open 'my computer' and look at their simile of an address bar, by memory it isn't immediately apparent that you can type in it but just click it a couple of times and I think it turns "type-able".

Clear the address that is presented and type in an address like
```
\\the-server-name\the-share
```
and press enter - should prompt for password and probably annoy me a great deal by allowing you to access the share!

Actually, when you hit the recent version of the old 'start' button there is a box to type into - address of server/share should work in that box as well!

I am checking a couple of ideas and am about to refer you to either synaptic or terminal to refresh your copies of 'local samba' stuff on your laptop - just want to be pretty darn sure before I go telling you what to try next!

---

### Post by robsoles on 2010-07-23
Ok, didn't take much more checking after starting back on this again.

If you are not trying to share folders from your laptop then let's remove the samba server from your setup:
```
sudo apt-get purge samba
```
(I choose purge to get rid of your configuration that was never really worth having if you really didn't want to share any folders off your laptop)

Now let's reinstall all your 'client' networking stuff I have identified so far and retry what you are doing to connect to these shares
```
sudo aptitude -f reinstall samba-common samba-common-bin libwbclient0 winbind smbclient libsmbclient
```

Please post back the output of the 'reinstall' command if there is any error reported - lemme know if that enables you to access the share you are after!!

---

### Post by Jackson Tan on 2010-07-25
Hi!

Sorry for the delayed reply. I was occupied for the weekend so I cannot head down to my lab.

> Clear the address that is presented and type in an address like
```
\\the-server-name\the-share
```and press enter - should prompt for password and probably annoy me a great deal by allowing you to access the share!

That worked in the sense that I was prompted for a username and password. But it could not log in, and I think the problem is with the fixed domain name. Win7 does not allow me to change the domain which I'm logging in with. It used my laptops network name, which is obviously different from the domain which the share is on.

But at least the network is there to be accessed, since Windows said that I did not have the permission to access that share. However, the share is invisible to the list of items under network...


As for cleaning up the configuration file, there are no errors with the reinstall command, but the share is still not accessible. Just a note though: the purge command did nothing because samba was not installed. I probably installed and uninstalled it when I was trying to get the share to work.

---

### Post by robsoles on 2010-07-26
I'm able to post but not able to access my usual PCs nor VMs right now but when I get back to stuff I can 'mess up' in later today I will try to make myself a scenario like your problem and see how I can get your results - that'll give me better advice to give you I'm hoping.

in meantime:

Have you tried deleting contents of 'domain' box/field and just having username and passwords in the nautilus password prompt box?

Have you tried with the old MS chestnuts 'workgroup' and 'mshome'?

Just to eliminate them while I think about possible encryption 'gotchas' and the like which could be causing the problem.

---

### Post by Jackson Tan on 2010-07-26
> Have you tried deleting contents of 'domain' box/field and just having username and passwords in the nautilus password prompt box?

That won't work. The "Connect" button is greyed out if there is nothing under username and domain.

> Have you tried with the old MS chestnuts 'workgroup' and 'mshome'?

I'm not sure what you mean there. Do you mean putting those two as the domain? If so, it doesn't work.

---

