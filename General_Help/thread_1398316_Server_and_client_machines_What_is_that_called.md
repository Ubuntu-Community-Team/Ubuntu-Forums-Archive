---
title: "Server and client machines? What is that called?"
date: 2010-02-04
forum: General Help
---

### Post by ticknubbs on 2010-02-04
When I was in school there was a computer lab that had all ubuntu machines that you logged into with your credentials and it would verify your credentials and you could access your files no matter what machine you were logged into. What is this called? I have heard NIS and NFS thrown around a lot. Me and my friend are starting a business and want to have a server and a couple of client machines that we can log into anywhere around the office to access our files. Does anyone know where I can find a very easy and user friendly guide to doing this? Thanks.

---

### Post by cgb on 2010-02-04
You could do something like this with NFS and LDAP.  The below link should give you a good starting point but not sure if there is a better reference someone else might be able to provide. 

[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by tgalati4 on 2010-02-04
You can set up a bunch of Ubuntu desktop machines and right click on a folder and activate sharing.  Then the folder will show up on other machines when you go to "Network" places.

What you probably had was a server using NFS (network file system) which is an older, UNIX file-sharing protocol.  

Modern linux distros use FUSE (file system user space) that allow secure (secure socket layer--SSL) sharing.

So you don't need the server anymore to share files.  It can be done from machine-to-machine--but the machines need to be turned on.

If you set up an Ubuntu server, you can set up a web-based file repository so that anyone with a browser can see and grab the files--you can secure it with passwords and access them internally or externally depending on permissions that you have set.

So at a minimum, I would set us an Ubuntu Hardy server with LAMP and a couple of Ubuntu desktop machines.  Experiment with sharing between desktops then figure out what other business software you need to run on the server.

I'm working on SugarCRM for a couple of clients ([http://sugarcrm.com](http://sugarcrm.com)).  It's helpful for keeping track of customers and runs well on Hardy server.  The Community Edition is open source and it's free and free--gratis e libre.

---

### Post by ticknubbs on 2010-02-05
Thanks for the input. I will mess around with those since this is a new system and there is nothing I can mess up. If there are any other tutorials out there broken down even more those would be appreciated as well!

---

### Post by tgalati4 on 2010-02-06
[https://help.ubuntu.com/](https://help.ubuntu.com/)

There's so much documentation out there, you just have to search for it.  Ask specific questions in the forum--or better yet--search the forums first for answers.

---

