---
title: "Creating, Editing, and Removing Shares with the 'net share' command"
date: 2010-03-16
forum: General Help
---

### Post by mr.malibu on 2010-03-16
Hi all,

Based on the information I found on the [samba.org site]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetCommand.html#id2602578") describing how-to use the 'net' command to add/remove and list net work shares on a ubuntu box, you'd think it would be slam dunk to get it working, but alas, this is linux we're talking about.

So, I'm here to ask for some help!

I've attempted to create a new share using the following command:

net share add Music=/home/joeblow/Music -C testing -M 1 -S joeblow-desktop -Ujoeblow%joeblowpass

which results in this error:

NetShareAdd failed with: Access is denied

I've also tried deleting an existing share using the following command:

net rpc share delete documents -S joeblow-desktop -Ujoeblow%joeblowpass

which results in the error code (5) and no error message.

Note, I'm logged in as joeblow the user and I'm attempting to create create/delete shares in joeblows HOME directory.

Also, I can create and delete shares from joeblows desktop via "Places->Home Folder->..." method and I can access these shares remotely.

So the $1M dollar question is, what's the secret? What am I missing here?

All tips and pointers are welcome! Thx.

---

### Post by soltanis on 2010-03-16
Use fusesmb or smbmount. In my personal experience getting smbmount to work was a pain, fusesmb is really easy though.

```

sudo apt-get install fusesmb

```

Given a mountpoint and a properly written configuration file

```

fusesmb /media/network

```

It works like "Network Neighborhood" in Windows, i.e. it displays a list of all browseable shares and workgroups on locally connected systems. I use it on a pair of Linux servers to let them transfer/encode audio files and it works out really nicely.

---

### Post by lyall on 2010-03-16
read the following links, they should help you and give you a better understanding

**SettingUpSamba** [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

**Share files and folders with other computers**
[https://help.ubuntu.com/8.04/internet/C/networking-shares.html]("https://help.ubuntu.com/8.04/internet/C/networking-shares.html")

also see **TitleIndex** [https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
for Samba

there is a lot of info about Ubuntu on the TitleIndex
that should help you 

good luck and have fun learning

---

### Post by mr.malibu on 2010-03-17
Hi Guys,

Thanks for the information. I failed to mention a couple of key points that are driving me needs.

#1 My team is developing a java application and we need to be able to create/delete and list shares on users machine/account.  This application will run on a variety of Operating Systems including Windows and Linux. Ideally there would be an open source OS Independent library/API that would allow us to implement these features but to date, we not discovered any. We are however using [JCIFS]("http://jcifs.samba.org/") to accomplish some of these tasks, however, jCIFS does not provide the abililty to create or delete shares.

#2 As an alternative, we've been researching platform specific techniques for creating, deleting, listing, etc. existing shares and that is where the 'net share add', 'net share delete' etc commands come into play. 


#3 We've investigated a few different approaches and found that the 'net share add', 'net share delete', etc. commands are available on all the OS platforms we're looking at (Windows, Mac, Linux) and thus their use seem like a good way to go.

So, the bottom line is that some kind of a cross platform open source JAVA library that allows one to CRUD (Create, Read, Update, Delete) shares, control their permissions, etc. would be of the highest value followed any STANDARD OS platform specific means. 

Thanks again for your comments and feedback, however, now that you've got a more complete picture of our needs, we'd like to hear them.

---

