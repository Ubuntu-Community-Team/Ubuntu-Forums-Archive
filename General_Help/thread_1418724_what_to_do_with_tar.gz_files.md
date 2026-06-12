---
title: "what to do with tar.gz files"
date: 2010-02-28
forum: General Help
---

### Post by sthrnpagan on 2010-02-28
I downloaded a tar.gz file for kildclient. I am not sure what to do with it. can someone help me?

---

### Post by aviedw on 2010-02-28
First i believe you have to extract it. Then you can use this command to install it 

sudo dpkg -i (package_name)

It makes things easier if you extract the tar to the desktop. But I think this should work for you.

---

### Post by 3rdalbum on 2010-02-28
> **sthrnpagan said:**
> I downloaded a tar.gz file for kildclient. I am not sure what to do with it. can someone help me?

On Linux, you don't install things by trawling the internet for software.

On Linux, you use the software repositories to search for and install programs. You can access the repositories by going to Applications > Ubuntu Software Center or System > Administration > Synaptic Package Manager.

You will find Kildclient in there.

.tar.gz files usually (but not always) contain source code rather than a compiled program. Compiling source code is not hard, but it takes time and you have to know how to do it. Not worth the trouble when Ubuntu's developers have compiled it for you.

---

### Post by sthrnpagan on 2010-02-28
> **aviedw said:**
> First i believe you have to extract it. Then you can use this command to install it 

sudo dpkg -i (package_name)

It makes things easier if you extract the tar to the desktop. But I think this should work for you.

thanks for your help unfortunatly i tried that command and it said

dpkg: error processing kildclient-2.9.0 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kildclient-2.9.0

---

### Post by Arkitekt on 2010-02-28
3rdalbums information is correct

in terminal type 'sudo apt-get install kildclient' it is an Ubuntu Developers maintained package in 9.10

---

### Post by sthrnpagan on 2010-02-28
> **Arkitekt said:**
> 3rdalbums information is correct

in terminal type 'sudo apt-get install kildclient' it is an Ubuntu Developers maintained package in 9.10


THANK YOU THANK YOU THANK YOU, I have been serching all day for a Linux mud client. I was about to give up and use Wine to run the client i used in windows. You have just relieved a lot of frustration.

---

