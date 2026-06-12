---
title: "Windows Network Problems...Again!"
date: 2012-04-26
forum: General Help
---

### Post by acanning on 2012-04-26
Hello All
 
I wonder if you might be able to help. I have a common setup in that I want to use an Ubuntu machine for basic file sharing within a small Windows 7 network. I can create shares using Samba with guest access but I really want proper secure user access although all users will access the same folder on the server. The problem is that it doesn’t work. Windows can see the shared folder but always asks for a password when I try to access the folder. The username/password I enter never works.
 
This is what I have done so far... 
 
Installed Ubuntu Desktop ver 10.04 (as my server)
 
Installed Samba
 
Created User ‘Ash’ on Server using the same password as my Windows 7 machine.
 
Also created a samba user using command ‘sudo smbpasswd –a Ash’
 
My Samba config file is default other than this section at the end;
 
[MyFiles]
path = /Home/server/Public/Dropbox/
available = yes 
browseable = yes
read only = no
guest ok = no
writable = yes
 
What am I doing wrong? Why does my Windows machine always ask for a password and then not let me access the folder saying that my login or password isn’t correct. When I boot-up the Windows machine I have to enter my username and password so I thought that should cover the login to the shared folder. If I enable guest access then it works without asking for a password.
 
I haven’t enabled sharing using the Nautilis file browser...that’s right isn’t it? I configure using the smb.conf file.
 
I don’t operate a domain only a workgroup called ‘workgroup’.
 
I know lots of people have problems like this but I feel like I’ve tried everything with no success. Anyone have any suggestions.
 
Many thanks

---

### Post by zero2xiii on 2012-04-26
Hay,

Without the rest of the samba config file I can only guess the following:

Connecting to the ubuntu machine from another ubuntu computer will bring up a screen which has a "group" option. This group box usualy has "NOGROUP" in it. When I connect to my windows computer's share, the same box pops up. Even if my windows machine is on workgourp "somename" i still use group: "NOGROUP" in linux to connect. Otherwise I get a auth error.

Try not worrying about the workgroup to much first. Make sure (esp if using windows 7) it is allowed to connect to that share, in other words you are on a trusted network. Not a public network.

I might also suggesting submitting the full samba config file for people with more expertiece than me to actualy see the config file and have that "aha" moment. Because I have a strong feeling it is just a small config error since you say it works when you allow guest access.

Cherz

---

