---
title: "Building an Ubuntu-based network"
date: 2012-02-23
forum: General Help
---

### Post by Ange Blue01 on 2012-02-23
Hi there, I'm new to the Ubuntu forums and Ubuntu in general. I'm the volunteer system administrator for a church in the Midwest USA. I've been placed in charge of implementing a project to put computers in classrooms to modernize our child education program. I am a Linux user (openSUSE) at my home desktop PC so I am familiar with desktop Linux and the advantages over proprietary operating system solutions that would be rather expensive to purchase and manage.

The project calls for about 12 laptops placed in the various classrooms and larger gathering areas, connected to the Internet via a wireless network to display content on LCD televisions in the classrooms and projectors in the larger rooms. The primary purpose of the client PCs is to enable the educators to display streaming video and other content from the Internet and a local file server.

I was attracted to Ubuntu in particular due to the well-established community, commercial support options, and the LTS releases. I was originally planning on using Kubuntu on the clients, but because of the recent announcement of Canonical's ending support for Kubuntu, I've decided on Xubuntu. The educators are computer (Windows) literate but I think Unity would be a rather uncomfortable change for them and Xfce would be less of a change.

As my background is in Windows, I need some help accomplishing the project's goals using Linux, please forgive my analogies to Microsoft's systems.


[LIST]
[*]On the clients, I need to remove some packages such as the games, and install others, such as Chromium and XBMC.
[*]Users, mostly educators, should have their own user profiles, which I presume would be provided by LDAP on the server.
[*]The server needs to provide file sharing, through NFS or SAMBA. The shares need permissions based on groups: A second-grade teacher should not have access to the same resources as a sixth grade teacher for example.
[*]Group permissions should also restrict software settings, like Active Directory's group policies. For example, I need to remove the second (dock-like) toolbar in Xfce and prevent changes to it, educators' Firefox preferences such as pre-defined bookmarks should depend on their group membership, etc.
[*]No educator should have root-level access on any client PC.
[*]The server will be serving video files, which I presume would benefit from a media server such as Media Tomb.
[*]The server needs to act as a proxy server for the clients to filter content, again access should be limited along (LDAP) user groups.
[*]Package management needs to be centralized, like deploying software via Active Directory. It must be possible to easily install a given package to all clients.
[*]Similarly the clients should go to the server for package updates, like WSUS. I presume I will need to create a local repository and change the repo listfiles on the clients accordingly. Package updates, at a minimum security updates, should be installed on the clients automatically, without any interaction by the users.
[*]There need to be GUIs to manage all aspects of the system. While I'm comfortable with the terminal, I am only a volunteer and thus not always available. I will need to train the staff in charge of education on basic administration: adding/deleting users and passwords, managing Web filtering, etc. Web-based front-ends are certainly welcome.
[/LIST]

I've considered out-of-the-box server solutions such as Zentyal but I would prefer to do this using only free software.

I have purchased and read the Ubuntu Server Book so I am somewhat familiar with Ubuntu Server's approach. At this point I need to test feasibility so I have downloaded and installed stock Ubuntu Server 10.10 and Xubuntu 11.10 in VirtualBox.

So how should I begin?

Thanks!

---

### Post by MG&amp;TL on 2012-02-23
> **Ange Blue01 said:**
>  I was originally planning on using Kubuntu on the clients, but because of the recent announcement of Canonical's ending support for Kubuntu, I've decided on Xubuntu. 

You've been misinformed.  Canonical still supports Kubuntu, they've just moved the developer elsewhere, for various reasons. To my knowledge, Xubuntu and Lubuntu have no full-time paid developers either. 

So, Kubuntu is still a good choice, as is any *buntu. It really depends how powerful the computers are. (i.e. can they handle the chosen DE). You could have a variety, educating the users in software freedom. :)

---

### Post by Ange Blue01 on 2012-02-23
> **MG&TL said:**
> You've been misinformed.  Canonical still supports Kubuntu, they've just moved the developer elsewhere, for various reasons. To my knowledge, Xubuntu and Lubuntu have no full-time paid developers either. 

So, Kubuntu is still a good choice, as is any *buntu. It really depends how powerful the computers are. (i.e. can they handle the chosen DE). You could have a variety, educating the users in software freedom. :)

Wonderful! I'm a KDE Plasma user myself so supporting it will be easier, and the learning curve will be a little lower for the educators.

---

