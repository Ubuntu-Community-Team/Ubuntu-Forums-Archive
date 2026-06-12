---
title: "Network Single Logon - Ldap, NFS"
date: 2010-12-04
forum: General Help
---

### Post by thebulk on 2010-12-04
Hi there,
 
I am in need of a little help. I am looking into setting up a network of Ubuntu machines and require a single single logon approach. I have included a more detailed picture of what I am after and why I need it. I have some knowledge of Ubuntu and really want to expand it.
 
The only way to describe what I am looking for is roaming profiles. I know this is a 'windows' term but I want to set up a network of ubuntu machines where users can logon to any machine on the network with one username and password and have access to their files/home directory and a network share which are stored on a central server without having access to other peoples home directories .
 
I know I need to have an LDAP server for user authentication which I have already set up but not sure what other software or services I need to install and configure.
 
The reason I want to set this up is a group of friends and myself have formed an amateur/hobby/non-profit film making group and we want to use open-source as much as possible. Ubuntu is our choice for operating system but we need them to be networked to share internet access and files. We have around 5 computers one of which will be the server for files and authentication.
 
Any help or how-to's would be really great

---

### Post by defishguy on 2010-12-05
This is the [[COLOR="Red"]_HOWTO_[/COLOR]]("http://tuxnetworks.blogspot.com/2010/04/ldap-client-lucid-lynx.html") that I've followed successfully.

---

### Post by thebulk on 2010-12-05
Hi

Thanks for your reply, I will certainly check this out as I follwed his howto to install the LDAP server.

I will give this howto a go and post back on here to let you know how I got on.

Cheers

---

### Post by thebulk on 2010-12-08
Hi all,
 
I have tried this how-to several times now but have had no joy with it unfortunately. I am sure that I am configuring this correctly but I have had several errors thrown at me.
 
The first error is: 
 
'Setting up libnss-ldap (264-2ubuntu2) ...
update-rc.d: warning: libnss-ldap start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)'
 
I got this one when installing the packages at the start. I continued through the how-to hoping it would not affect the outcome. It didn't appear to, however I got the following error at the terminal screen:
 
Failed to enumerate nameservice: No such file or directory
passwd... nameservice unavailable.
 
I have checked the configuration files but cannot work out what is wrong as when I perform ldapsearch -x, all the users I have set up are there.
 
I have tried logging in from the login screen of the client but the ldap users do not appear and if I try clicking on other and typing in their username and password I get Authentication Failure appear on the login screen.
 
I am completely stumped by this and do not know where to go on this one. I am almost ready to give up.
 
Is there any chance someone who has used this how to with success let me take a look at their config files (All those edited in the how to) so I can try to work out where I have gone wrong with mine.
 
Cheers

---

### Post by thebulk on 2010-12-24
Hi all,
 
Sorry to have posted again but I am not having any luck and I need to get this working as soon as possible for a project I am working on.
 
I have since tried this how-to guide again and I appear to still have no luck with it. I have tried searching through the code and config files but I haven't managed to work out whats wrong. It was suggested to me that I should look through the config files expecially at the addresses to the ldap server but they all apppear to be correct.
 
Has anyone followed this how-to and had a successful outcome? If you have, then please could you contact me here or by PM and let me know what you did to make it work or if possible, if someone is willing too could you let me take a look at your client config files so I can try to work out what is wrong with mine.
 
Thanks in advance for your help.

---

### Post by supremedalek on 2011-02-09
Do I take you were successful or did you give up?

---

