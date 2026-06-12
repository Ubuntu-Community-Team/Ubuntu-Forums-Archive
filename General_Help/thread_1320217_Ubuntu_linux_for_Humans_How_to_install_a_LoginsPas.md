---
title: "Ubuntu linux for Humans: How to install a Logins/Passwords Server, with clients?"
date: 2009-11-09
forum: General Help
---

### Post by frenchn00b on 2009-11-09
HI


a Server box for all the network password/logins clients of the network that are running Linux, based on the MAC (the router make the job to control the mac address to make it easier)

How can an HUMAN achieve this?


):P):P

[B]Click on me:
[LDAP for LINUX : ]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")[/B]
  
  
  
  
--

---

### Post by P4man on 2009-11-09
Im not even sure its theoretically possible, as the server wouldnt see the MAC addresses since it communicates over IP with the router.  Once you have a router between the client and the server the mac address is undetectable afaik.

That aside it sounds like a terrible idea to me to be honest. There is a reason they invented the tcpip network stack and implemented user accounts on top of that. If you are going to manage access based on a hardware mac address, its going to be a nightmare to maintain. But again I think its not even possible. Why on earth would you want to do this?

---

### Post by frenchn00b on 2009-11-09
> **P4man said:**
> Im not even sure its theoretically possible, as the server wouldnt see the MAC addresses since it communicates over IP with the router.  Once you have a router between the client and the server the mac address is undetectable afaik.

That aside it sounds like a terrible idea to me to be honest. There is a reason they invented the tcpip network stack and implemented user accounts on top of that. If you are going to manage access based on a hardware mac address, its going to be a nightmare to maintain. But again I think its not even possible. Why on earth would you want to do this?

so ok. I obey. How do univerties do the job? 

They have an unique server for logins and passowrds. 

The clients are mac, xp, and linux. 

How can I do this, similar ?
and and ... HUMAN ;) that Ubuntu Motto

---

### Post by Johnsie on 2009-11-09
A university  network would have a server holding a database of usernames and passwords. That database would be queried any time someone attempts to log in to the network.

In most univerities this is done using a microsoft product called Exchange Server which is currently the leading software in that genre. There are similar programs for Linux out there. However, even with the Windows version, it would take an IT expert to set up rather than a 'human' to set this kind of infrastructure up. With Linux this process is even more complicated.

---

### Post by P4man on 2009-11-09
> **frenchn00b said:**
> so ok. I obey. How do univerties do the job? 


Do what job? Even if I knew, you could hardly expect me to describe some general network topology and security implementation that "universities" use? When I was there last it was simple we all had an account on the AS/400 and logged in to dumb terminals :)

> They have an unique server for logins and passowrds. 

The clients are mac, xp, and linux. 
How can I do this, similar ?


If you want to manage user accounts you probably want  a directory service like active directory  and/or samba and/or (open)ldap. You can use that to manage users on pretty much any OS.

Then again I really dont know what you're asking so perhaps you can clarify your question by explaining the problem and what it is you want to achieve. Honestly though, if you want to set up your own directory service, you're gonna have to do a lot of reading I suspect... perhaps you can start here:
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

---

### Post by frenchn00b on 2009-11-09
> **Johnsie said:**
> A university  network would have a server holding a database of usernames and passwords. That database would be queried any time someone attempts to log in to the network.

In most univerities this is done using a microsoft product called Exchange Server which is currently the leading software in that genre. There are similar programs for Linux out there. However, even with the Windows version, it would take an IT expert to set up rather than a 'human' to set this kind of infrastructure up. With Linux this process is even more complicated.

It means that everyone use Linux and NFS completely Unsecured, because no one is able to install a LDAP, Kerberos, .. or do not know the name. 

Please what is the name of for linux the.: >   A university  network would have a server holding a database of usernames and passwords. That database would be queried any time someone attempts to log in to the network.
  
that may handle the mac, xp, and linux? 

On the client side, I recall my admin just asked my MAC address, and did very little changes, but what? and It worked. 
He said```
. you have to wait, dude, one hours for getting your login and password working, because it is made by the samba. 
``` 
There was no single, no single one windows machine, in that admin servers chamber. I went several times, bugging and nagging for help with Linux. They have Debian in that one, only. 

Well it is possible, if we work together guys ! x10000 we can make Linux FOR HUMANS, as it is written on that cdrom carton cover. ;)

---

### Post by frenchn00b on 2009-11-09
> **P4man said:**
> Do what job? Even if I knew, you could hardly expect me to describe some general network topology and security implementation that "universities" use? When I was there last it was simple we all had an account on the AS/400 and logged in to dumb terminals :)



If you want to manage user accounts you probably want  a directory service like active directory  and/or samba and/or (open)ldap. You can use that to manage users on pretty much any OS.

Then again I really dont know what you're asking so perhaps you can clarify your question by explaining the problem and what it is you want to achieve. Honestly though, if you want to set up your own directory service, you're gonna have to do a lot of reading I suspect... perhaps you can start here:
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

I have already a samba well working, almost, but working cool
But for Linux'es I do not want that smbdy who brings a strange pc, and do : 
su 
and power! All the linux machines are ****'ed up., i.e. the shared /home on the main file NFS & SAMBA server :( Additionly each linux box has its own login/password. You change it on a machine , and other stil remain the same login/passwd as before. Not good not good

---

### Post by P4man on 2009-11-09
> **frenchn00b said:**
> 
Please what is the name of for linux the.:   
that may handle the mac, xp, and linux? 

Samba can do it, you can make it act as a domain controller which can authenticate win linux and mac clients. Samba can do a lot more than just sharing folders over the network. See my links above.

```
On the client side, I recall my admin just asked my MAC address,
```

Wireless MAC? Or even it was wired your university probably has a router that blocks unauthorized mac addresses. That doesnt mean the network authentication relies on your mac address, its just a simple filter that disallows other *machines* from even connecting to the network (although that easy enough to circumvent).

> **frenchn00b said:**
> Well it is possible, if we work together guys ! x10000 we can make Linux FOR HUMANS, as it is written on that cdrom carton cover. ;)

Humans dont need directory services, network admins do. And they dont need fancy GUI's :)

---

### Post by frenchn00b on 2009-11-09
> **P4man said:**
> 
Humans dont need directory services, network admins do. And they dont need fancy GUI's :)

that s why... they are not humans. They certainly come from hell ;) 
 
With samba, can I share my nfs ? 
but samba is slow compared than nfs, what I heard.

---

### Post by frenchn00b on 2009-11-09
> sudo mount -t smbfs -o username=dlightman //development/project-code /mnt/pcode

You will then be prompted for the user password, and after successfully authenticating, the contents of the shared resource will be available locally via the mount-point specified as the last argument to the mount command. To disconnect the shared resource, simply use the umount command as you would with any other mounted file system. For example:

sudo umount /mnt/pcode

here it seems that at startup one logins in the user via samba, smbfs. 
So hte linux client pc cannot have the xdm and asking for login / passwords, based on the samba. In summary one startup, on user. 

So, the second like based on ldap and kerberos. Well I undertand 0. 
it is very ultra complicated, for me. Is there a already pre-configured files to copy paste, and pata / basta . it works? 

Kerberos and ldap, mainy times I have tried and finish reinstalling hte machine all over :( 
dpkg-reconfigure or xdialog menu to make it, or eventually a preconfigurator, does it exist? I saw that ldap / has a gnome/gtk frontend. 

Regards, your the Master , coming from command line world !! reverence

---

### Post by frenchn00b on 2009-11-09
> **P4man said:**
>   you're gonna have to do a lot of reading I suspect... perhaps you can start here:
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

here is the result of reading very complicated LDAP : 
I just made this review, ... specially for you ! Its seldom to find someone that knows about such IT expert things. 

[here a picture of the result]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

Could we do it, slowly step by step, please ?

---

### Post by frenchn00b on 2009-11-10
so daily bit progressing ... slowly slowy daily a bit

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch31_:_Centralized_Logins_Using_LDAP_and_RADIUS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch31_:_Centralized_Logins_Using_LDAP_and_RADIUS)

I installed those packages.

openldap
openldap-clients
openldap-devel
nss_ldap
openldap-servers


 I post when I have some new ...


I am looking for example of config files that work.
eventually those are ok,  [http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Configuring_Samba](http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Configuring_Samba)

man , google gives poor results of examples. seems no one is capable to install LDAP and SAMBA. Too complicated

---

### Post by frenchn00b on 2009-11-18
[http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif](http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif) 

is there auto installers?

---

### Post by frenchn00b on 2009-11-21
this is really cool  to read.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

ldap is the key

---

