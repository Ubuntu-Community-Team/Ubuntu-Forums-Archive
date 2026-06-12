---
title: "Setting up an Ubuntu client-server network"
date: 2006-06-21
forum: General Help
---

### Post by florizs on 2006-06-21
Hello, I'm planning to set up a client server network similar to an Microsoft Active directory or a Novell Tree network.

I need a way to let people log in to the network clients via a central server (OpenLDAP) and manage functions like network printing, file-sharing etc.

I was searching the forums but I can't find a good how-to for such a thing.
I have been looking at EdUbuntu but making a thin client setup does'nt appeal to me as much at the moment since it requires a beefy server and a good network.

Does anybody have a tip how this can be done or better yet point me to a good how-to?

thanks

---

### Post by Robgould on 2006-06-21
I have never been able to get it done with Ubuntu.  If you install opensuse 10.1, it will allow you to join the domain during installation.

---

### Post by florizs on 2006-06-21
Thanks for the help, but I don't want to join the ubuntu machines in a Windows network.
However I do need to have a similar file-sharing / user authentication feature.
I'm hoping there is such a thing for Ubuntu.

---

### Post by linuchsan on 2006-06-21
look for Samba PDC in google

---

### Post by florizs on 2006-06-21
But isn't that if you have Windows clients? I am talking about clients running Ubuntu.

---

### Post by zitch on 2006-06-21
I think what you're mainly looking for (in terms of file-sharing, at least), is NFS.  [This how-to](https://help.ubuntu.com/community/SettingUpNFSHowTo) might give you some help in that respect.  It looks this how-to also shows you how to use LDAP or NIS to create a central users and passwords system.

I know you don't want to do a thin-client setup, but these [how-tos on thin clients](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=thin+client) might give more hints of what you want to do.

ADD:  I just found [this how-to](https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto) and thought it might be useful too.

---

### Post by florizs on 2006-06-22
Zitch,
thanks for these how-tos!

I will be looking in to them and trying to set up a similar system.
the thing that amazes me is that Ubuntu is an easy to set up home-user Desktop-system but lacks easy for multiuser over multiple clients.
Maybe i'll write a tutorial myself later. i'll be seing what kind of stuff I'll run into. 
It's my belief that a multiuser/client system should be easy to setup and manage.

I'll keep posting my experiences here any how-to's welcome.
Thanks!!
Floris

---

### Post by textguru on 2006-09-21
> **florizs said:**
> Zitch,
thanks for these how-tos!

I will be looking in to them and trying to set up a similar system.
the thing that amazes me is that Ubuntu is an easy to set up home-user Desktop-system but lacks easy for multiuser over multiple clients.
Maybe i'll write a tutorial myself later. i'll be seing what kind of stuff I'll run into. 
It's my belief that a multiuser/client system should be easy to setup and manage.

I'll keep posting my experiences here any how-to's welcome.
Thanks!!
Floris

Any update on your evaluation for the thin client network?

---

### Post by florizs on 2007-03-22
> **textguru said:**
> Any update on your evaluation for the thin client network?

I'm momenarily quite busy but we will be setting up 3 systems.
one will be a suse enterprise system, one a winxp system and one Ubuntu system

I assume this will take place in april or may,  so expect evaluations after that

---

