---
title: "Windows 7 client to Samba Share authentication problem"
date: 2009-12-28
forum: General Help
---

### Post by HuaiDan on 2009-12-28
I'm stumped. 


I'm trying to use Windows 7 and Vista machines to connect to an Ubuntu share. With guest permissions turned on shareside, I am able to connect from the windows boxes with whatever share permissions I have set.

The problem arises when I want to password-protect those shares. When I turn off guest access for those shares and try to connect, I get prompted for a login, as expected. When I entered the share-owner login, windows kicked it back with a message saying something to the effect of, "windowsbox\username does not exist or password entered incorrectly".

I then created a user on the windows box to match the share-owner on the linux box, but this didn't seem to affect anything.


In summary, I can connect to shares as guest, but I really want to protect these shares with passwords, which I haven't figured out. 
Any clues, please?

---

### Post by QrK0 on 2009-12-28
Seems a domain problem.
On the windows side, try to put the domain/workgroup of the samba server before the user name, like:
```
workgroup/userName
```

---

### Post by HuaiDan on 2009-12-28
Windows shows it using a backslash, e.g.,

WORKGROUP\username


Where WORKGROUP is the workgroup name in smb.conf.

But I've tried it both ways. With  WORKGROUP\username it just kicks it back as unknown username, but as WORKGROUP/username I get a permissions error, so it seems the latter is correct.


I have all permissions set to owner full privileges, which is the login I'm trying to use.  Just a shot in the dark here, do I need to put share users in smb.conf?

---

### Post by capscrew on 2009-12-28
> **HuaiDan said:**
> Windows shows it using a backslash, e.g.,

WORKGROUP\username


Where WORKGROUP is the workgroup name in smb.conf.

But I've tried it both ways. With  WORKGROUP\username it just kicks it back as unknown username, but as WORKGROUP/username I get a permissions error, so it seems the latter is correct.


I have all permissions set to owner full privileges, which is the login I'm trying to use.  Just a shot in the dark here, do I need to put share users in smb.conf?

You need to add the user to the smbpasswd database and then activate it.

I am not near a Linux/Samba install, but if you look at the man pages or read this [**_[COLOR="DarkSlateGray"]google search[/COLOR]_**]("http://www.google.com/search?q=smbpasswd&btnG=Go!") on *"smbpasswd"* you will see.

---

### Post by HuaiDan on 2009-12-28
Thanks @ capscrew and QrK0. Both answers were a necessary piece of the puzzle.

I'm thinking about using smbpasswd to set up a read-only guest account with no password. I'm assuming there must be a corresponding user account, so would that be possible without setting up a guest account in users? Would the password need to be the same?

Must authenticate, full privileges for owner (got it), read-only for guest (still working on it).   Any ideas?

---

### Post by nailzuz on 2009-12-28
Hello guys,

Firstly i'd like to say that i'm newbie in Linux, Ubuntu, samba. 
but now i faces exactly the same problem as described here. 


After reading some how-to guides i decided to build up my home file server on Ubuntu server + Samba. I've installed Ubuntu server 9.10, samba and Webmin for easier samba share configuration. My aim was to share files on my FAT32 hard drive. I've mounted it using mount command and umask=000 property to give rw permissions for all users. 
After i shared my mounted directory using samba.conf file and WEBMIN appropriate samba GUI section. I imported my unix users to samba users via Webmin. I gave new passwords to my samba users. 

As a result if i'm connecting from XP machine, it asks me to enter user/pass, i enter ussr/passw and everything works fine - i can browse my share and do everything with files. 

But when i try to connect from win 7 machine i enter the same user/passw and win7 throws an error. 
How to fix it and what to do? Any special configurations are needed on samba linux or in win7???

..and, when i enable guest access in samba -> i can access shares even from win7 machine with guest account

It would be appreciative to receive help here

thx
(my firs post in Ubuntu forums)

[COLOR="Red"]S O L U T I O N[/COLOR]

Do followings manipulations in windows

[I]Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options

Network security: LAN Manager authentication level
Send LM & NTLM responses 

Minimum session security for NTLM SSP
Disable Require 128-bit encryption[/I]

or [here]("http://sourceperfect.wordpress.com/2009/05/06/access-samba-network-shares-from-vista-windows7/") with images

---

### Post by capscrew on 2009-12-28
> **HuaiDan said:**
> Thanks @ capscrew and QrK0. Both answers were a necessary piece of the puzzle.

I'm thinking about using smbpasswd to set up a read-only guest account with no password. I'm assuming there must be a corresponding user account, so would that be possible without setting up a guest account in users? Would the password need to be the same?

Must authenticate, full privileges for owner (got it), read-only for guest (still working on it).   Any ideas?

Yes you can have guests without setting up an explicit *"guest account"*.  No need to add anything to the smbpasswd database,  You should handle guests as anonymous users.

I have created an Ubuntu user called *smbguest *with limited user rights.  There is user like this on all Ubuntu systems.  This is the *nobody *user. This user is referenced in the [global] section of the smb.conf file with the ***baduser ***directive. 

The directive *baduser *refers to any user that has no smbpasswd entry.  In other words when someone on the system that is **not recognized by Samba **attempts to use the share, they have the rights of *baduser* (in my case smbguest). 

@nailzuz,

Not good form to hijack another users thread.  Webmin is not something I use so I wouldn't have a clue as to how to address your concerns.

Webmin alters the standard configuration of Ubuntu, therefore any solution I provide might not work in your case.  My suggestion is to start your own thread stating your specific problems.  There are plenty of Webmin users out there.

Edit: @nailzuz,  You solution is specific to Webmin.  No help to the OP's question.  At the least you should make that point clear for others viewing this in the future.

---

### Post by nailzuz on 2009-12-28
> **capscrew said:**
> 
Edit: @nailzuz,  You solution is specific to Webmin.  No help to the OP's question.  At the least you should make that point clear for others viewing this in the future.

I don't think so, my (not my) solution is not specific to webmin. Webmin samba module is just GUI for smb.conf, as i know no differences either you configure through Webmin or directly make corrections in conf file, isn't it? I've answered on my own question, which was seemed to me the same as OPs. And to fix it some changes should be made in windows 7.
sorry for offtop. i appreciate and hold in esteem older collegues

---

### Post by doas777 on 2009-12-28
> **nailzuz said:**
> 
[COLOR=Red]S O L U T I O N[/COLOR]

Do followings manipulations in windows

[I]Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options

Network security: LAN Manager authentication level
Send LM & NTLM responses 

Minimum session security for NTLM SSP
Disable Require 128-bit encryption[/I]

or [here]("http://sourceperfect.wordpress.com/2009/05/06/access-samba-network-shares-from-vista-windows7/") with images
better answer to your issue is instead of lowering windows security, instead, raise sambas'
```
client NTLMv2 auth = yes
```

yes this issue has the same symptoms as the ops (users had not had smbpasswd run for them), so it looks the same (credentials rejected), but the answer is completely different.

---

### Post by capscrew on 2009-12-28
> **nailzuz said:**
> I don't think so, my (not my) solution is not specific to webmin. Webmin samba module is just GUI for smb.conf, as i know no differences either you configure through Webmin or directly make corrections in conf file, isn't it? 

So sure...But then again, not.  You don't know what you don't know, eh.  Webmin has been rejected from the repos because it DOES change the way it interacts with the OS (and Samba).  > 

I've answered on my own question, which was seemed to me the same as OPs. And to fix it some changes should be made in windows 7.
Many times this is the root of many problems down the road.  Modifying something that already interacts with other software or OS because you don't know is not the answer and of no help to others.  Note doas777's response.> 

sorry for offtop. i appreciate and hold in esteem older collegues

Hmmmm, I wonder.

---

### Post by HuaiDan on 2009-12-28
Thanks to all.  I did create a guest account, because I couldn't find another way to prompt for auth in all cases. Important discoveries include finding that samba passwords do not need to match linux account passwords for a given account. Now I have access only permissions for "guest" and full permissions for owner. . Best practice? Not a clue, but it works.

Doas777 and Nailzuz, your suggestions might come in handy, as I have one Vista box that still won't log in. Think it might have something to do with what you suggested. I'll have to play with it after work. I'll keep you posted.

Again, thanks to everyone for your suggestions. More coming later.

---

### Post by HuaiDan on 2009-12-29
So here's what I did:

I started by right-click on the folder I wanted to share and went to sharing options. I had thought it would be a simple matter of leaving "allow others...." and "guest access" unchecked, but that didn't work; at that time I was still unaware of smbpasswd.

Here's what worked:

First, users must be created in system/administration/users and groups for any share users. 
For security reasons I gave any new users minimal permissions and complex passwords. This password is irrelevant and (hopefully) won't be used later. 
If you want more than one user to have the same permissions, say, read and write or full control, put them in a group and give that group appropriate permissions in the folder permissions. Give owner full permissions. In permissions, give 'others' access only permissions, which applies to the 'guest' account.
Then, 
sudo smbpasswd -a *username*
and enter the password desired for each share user. Remember, it doesn't have to match the corresponding linux user's password. I imagine it would be a good practice to keep it the same, though, except for 'guest'.  
sudo smbpasswd -a guest
and hit 'enter' twice to enter a null password for 'guest'.

Then, 

sudo gedit /etc/samba/smb.conf
 and personalize the following under "Share Definitions":

[*share name*]
path = *share path*
write list = *username1 username2 usernameEtc*

e.g. 

[Movies]
path = /media/80gb/movies
write list = BobH TomD


Finally I was able to log in to the different users with varying permissions, and log in as 'guest' with no password and access only permissions, on both linux and windows clients.


Almost ready to call this case closed, but for one hitch. I can only get read-only permissions on any user from a vista box. Two laptops, side-by-side, log in as owner on one, can create and delete files. Log out of that one, log in as owner from the vista (32 Ultimate) laptop, and I get read-only.


What's up with that?  Fix that one and I'll call this 'solved'.

---

### Post by doas777 on 2009-12-29
> **HuaiDan said:**
> So here's what I did:

I started by right-click on the folder I wanted to share and went to sharing options. I had thought it would be a simple matter of leaving "allow others...." and "guest access" unchecked, but that didn't work; at that time I was still unaware of smbpasswd.

Here's what worked:

First, users must be created in system/administration/users and groups for any share users. 
For security reasons I gave any new users minimal permissions and complex passwords. This password is irrelevant and (hopefully) won't be used later. 
If you want more than one user to have the same permissions, say, read and write or full control, put them in a group and give that group appropriate permissions in the folder permissions. Give owner full permissions. In permissions, give 'others' access only permissions, which applies to the 'guest' account.
Then, 
sudo smbpasswd -a *username*
and enter the password desired for each share user. Remember, it doesn't have to match the corresponding linux user's password. I imagine it would be a good practice to keep it the same, though, except for 'guest'.  
sudo smbpasswd -a guest
and hit 'enter' twice to enter a null password for 'guest'.

Then, 

sudo gedit /etc/samba/smb.conf
 and personalize the following under "Share Definitions":

[*share name*]
path = *share path*
write list = *username1 username2 usernameEtc*

e.g. 

[Movies]
path = /media/80gb/movies
write list = BobH TomD


Finally I was able to log in to the different users with varying permissions, and log in as 'guest' with no password and access only permissions, on both linux and windows clients.


Almost ready to call this case closed, but for one hitch. I can only get read-only permissions on any user from a vista box. Two laptops, side-by-side, log in as owner on one, can create and delete files. Log out of that one, log in as owner from the vista (32 Ultimate) laptop, and I get read-only.


What's up with that?  Fix that one and I'll call this 'solved'.

one thing that is somtimes confusing about network sharing, is that "sharing" permissions and folder permissions are different, and stack on top of eachother.
for instance on windows, MS recommends that you create your share permissions giving everyone full control, but on the permissions of the specific folder, (on the filesystem level, not the network) constrain the users to more specific rights. for instance if I create a share granting everyone full control, but share a folder that is readonly to the users group, then my network users will only be able to read it.

In linux they don;t stack quite so confusingly, but the base concept is the same. the user must have permissions to the physical folder, if they want to access it, regardless of whether samba says they should have access.

so now that i've spent 3 paragraphs explaining stuff you already know, can you post the output of 'ls -al' on the directory you are sharing?
also what unix groups do your users belong to (the users connecting from vista that is)?

---

### Post by HuaiDan on 2009-12-29
ls -al


> 
drwxrwxr-x  3 dh dh  4096 2009-12-29 21:31 Permissions




The name of this folder is 'Permissions'.   I followed this guide:

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

Now I have read-only from all windows machines. I can browse and download, but I can't delete/create. From any linux client, permissions work exactly as planned, but if I use the same user name, dh, which is the owner, on any windows client, I get read-only.

Also, Windows asks me to authenticate when I connect to the server (start\run  \\ipaddress) , not when I open the protected share. Linux asks for authentication only when I open the protected share.

---

### Post by doas777 on 2009-12-29
> **HuaiDan said:**
> ls -al





The name of this folder is 'Permissions'.   I followed this guide:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now I have read-only from all windows machines. I can browse and download, but I can't delete/create. From any linux client, permissions work exactly as planned, but if I use the same user name, dh, which is the owner, on any windows client, I get read-only.

Also, Windows asks me to authenticate when I connect to the server (start\run  \\ipaddress) , not when I open the protected share. Linux asks for authentication only when I open the protected share.

try running this:
```
sudo chmod o+w Permissions
```

my suspicion is that the group info is not being relayed correctly. 
I noticed that you said that the smbpasswd did not have to match the unix users passwd. that is not entirely correct. if dh's sambapasswd is differant from their unix passwd, then that would explain the issue. 

also on your share definitions, are you stating "Read Only = no", and are you using "security = user"?

---

### Post by HuaiDan on 2009-12-29
Thanks,  I'll try that.


I have both read only = no and security = user.

The password I use for owner is the same for both the linux user account and the smbpasswd account.  I just mentioned using a complex password for the linux user account 'guest' (disabling shell access is also important here for any users created solely for share access), then leaving a blank password for 'guest' on smbpasswd.

---

### Post by HuaiDan on 2010-01-06
bump

---

### Post by HuaiDan on 2010-01-09
I fixed it, but if someone could shed some light on exactly why it works now and didn't work before, I would consider that extremely enlightening.


Basically, somewhere between un-installing samba, giving samba4 a whirl then giving up, then re-installing samba, I noticed /var/lib/samba/usershares disappeared. Samba wouldn't let me right-click on a folder and create the share, instead notifying me about /var/lib/samba/usershares missing. I was about to create the folder, but hunch told me not to. I decided to experiment, leave usershares out of the equation, and set up my shares in smb.conf only.

That's what worked. It allowed me to set up varying permissions on different shares for different users.  So why didn't the "windows"-style of creating shares work?

Again, if anyone has any feedback on this, don't hold back. I'm quite curious about how this works now.

---

