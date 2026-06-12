---
title: "Laptop on a network"
date: 2006-04-30
forum: General Help
---

### Post by Koybe on 2006-04-30
This is a general question about Laptop and Linux.

When you have a 100% linux network with a server and some clients, you need to share files, authenticate users... 

My question comes when laptop is going on the network. How do you configure the server and the clients to :
- Take care of the datas and make a backup from the server
- Authenticate your users from the server
- Make share accessible for all users
- Manage the laptop on all this. The Laptot needs to authenticate and get the datas even outside of the network.

Any ideas?

---

### Post by cilynx on 2006-04-30
There are many ways to do backups.  One of the more popular is "mondo / minit".
Radius is generally the accepted solution for remote authentication.
If the network is purely *nix machines, use NFS or NFS-over-SSH for filesharing.
If there will be Windows machines on the network as well, use SMB (samba).

That's just a rough overview.  If you have more specific questions, don't hesitate to ask.

---

### Post by Koybe on 2006-04-30
Nice but as you said, it's an overview.
- Thank you for mondo... never heard of it. I'll have a look.
- I haven't tought about a radius server... do you have a good documentation about it. I was more planning on a NIS server... but i was wondering how to make it for laptop when they're not on the network.
- Another question.. How to sync datas between server and laptop? Rsync or another tool ok... but how to do it without any interaction from the user? 

Maybe more question just passing trough... ;)

---

### Post by cilynx on 2006-04-30
I find it's easier to get into detailed solutions easier as more details of the "problem" come out through going back and forth.

I hadn't heard of mondo until a couple weeks ago.  I found that it has a pretty nice following.  I started using it because it allows backups to a NFS server.  Thanks to that, I now had a couple of NFS servers that do nothing but hold backups.

Radius is a fun topic.  I've yet to find an "easy" way of setting it up.  Long ago and far away, I setup a radius server authenticating against an LDAP database.  This particular setup was for a 2000+ user dial-up server where we didn't want each user having an account on the machine.  For system level authentication as opposed to LDAP, it's a lot easier.  I quasi-documented that project here:
[http://www.wolfteck.com/ldapfreeradauth/]("http://www.wolfteck.com/ldapfreeradauth/")

For syncing data, I use rsync.  Another though if the laptop is always going to be connected to the server through high-bandwidth connections when in use would be to have your home directory actually be a share on the server.  That can solve a lot of problems (and create a lot more)...

---

### Post by Koybe on 2006-04-30
> **cilynx]Radius is a fun topic.  I've yet to find an "easy" way of setting it up.  Long ago and far away, I setup a radius server authenticating against an LDAP database.  This particular setup was for a 2000+ user dial-up server where we didn't want each user having an account on the machine.  For system level authentication as opposed to LDAP, it's a lot easier.  I quasi-documented that project here:
[http://www.wolfteck.com/ldapfreeradauth/]("http://www.wolfteck.com/ldapfreeradauth/")
[/quote]
I'll have a read  said:**
>  For syncing data, I use rsync.  Another though if the laptop is always going to be connected to the server through high-bandwidth connections when in use would be to have your home directory actually be a share on the server.  That can solve a lot of problems (and create a lot more)...
Yeah that should be ok. But the laptop needs also to access the datas while it's away... The problem is : when using the rsync?

---

