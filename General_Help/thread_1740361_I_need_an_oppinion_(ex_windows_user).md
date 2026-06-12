---
title: "I need an oppinion (ex windows user)"
date: 2011-04-26
forum: General Help
---

### Post by 200k on 2011-04-26
I have been a windows user my whole computing career. Over the last few months I have really taken a liking to linux, and have been test driving different distros on my virtual machine 

 I know very little to nothing when it comes to linux, but from what I can see so far, ubuntu will be the distro I plan to merge over to. 

 As far as applications go, I noticed that many of my windows apps have are also native to linux. The one thing I must have is a ftp server (I do not use it often, only to stream movies to devices throughout my house, and to occasionally send friends files when chatting online). 

 Now i know there are many choices when it comes to ftp servers in linux, and originally I wanted to stay away from the gui, so anything gui is out. So I finally figured out how to set up the ftp server from the terminal and I just wasnt liking it. 

 Even though it has a gui, i really liked Filezilla Server for windows, and I got it up and running through wine, although I could no longer use port 21. So i set it to a # past 2000. 

 My question is, from a linux standpoint was this a poor choice to do? My ftp server is password protected, and the user is binded to the home directory of the ftp. Are there any security risks I should be aware of while running this server through wine? Does that make me more vulnerable to attack (I dont think that it would, Im just unsure)?

 Thanks again for all the support and help!

---

### Post by papibe on 2011-04-27
I would recommend using sftp instead of ftp. There's no significant differences from the user point of view, but it is far more secure. The server side comes included in the openssh-server package. Unfortunately, it is mostly admin old school (by editing config files).

On the other hand, there are several GUI on the client side. There's a native Filezilla client available on the Software Center (also KFTPGrabber and JFTP).

I hope it helps.

---

