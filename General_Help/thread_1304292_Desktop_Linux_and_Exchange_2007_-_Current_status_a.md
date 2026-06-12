---
title: "Desktop Linux and Exchange 2007 - Current status and the road ahead"
date: 2009-10-29
forum: General Help
---

### Post by swappa on 2009-10-29
Hi there
I know there are a lot of threads on this issue - getting Evolution to work with Exchange 2007. I for one cant make it work and, it is a show stopper with regards to doing a full switch from Windows to Ubuntu. I am not really requesting the technical solution here (if one exists) but i am hoping  that someone could shed some light on the development process - again, if one exists. I believe that there are a lot of people finding themselves in the same situation as I am - wanting to convert to Ubuntu but really cant ...is  the open source community working on this at all? 

Thanks

---

### Post by albandy on 2009-10-29
use davmail, it's a kind of proxy that converts exchange 2007 to imap, smtp, ldap and caldav protocols.

---

### Post by akakingess on 2009-10-29
Also, you may want to check out Launchpad, as I think there will be a bug report/feature request for it and you could "vote" for it to move it up the priority chain, and I believe you can also see some blueprints with what the developers are planning and if something has already been accepted and is being worked into an upcoming version. BTW, there is a link to Launchpad at the top of the forum home page, or every page I think.

---

### Post by revanb on 2009-10-29
Hi

I am sure people are working on it and I have used evolution successfully with MS servers before, but this was a while ago and prob. not with 2007 version. I don't know the current status as I don't have to interact with MS servers anymore.

I can however suggest a workaround if you really have no choice:

1) Install VirtualBox (A virtual computer on your linux desktop).

2) Install your copy of Windows inside VirtualBox.

3) Install the VirtualBox Guest Software inside Windows in VirtualBox.

Now you can do a number of things:
* You have a fully functional Windows running in a window inside Linux
* You can set up shared folders between Linux and the hosted Windows
* You can run Outlook inside the hosted Windows.
* You can run Linux all the time.

---

### Post by swappa on 2009-10-29
Thanks for the replies guys. 
I am currently using Vmware workstation and Windows 7 to get office 2007/Outlook installed that way. It works but it would be nice with a fully working Evolution/Exchange 2007 setup too ;)

I guess this ends up on the "would be very nice to have" feature list. 

Thanks

---

### Post by albandy on 2009-10-29
As I said before, if you use davmail proxy you can connect your evolution (mail,calendar, tasks and contact list) to exchange 2007

[http://sourceforge.net/projects/davmail/](http://sourceforge.net/projects/davmail/)

---

### Post by akakingess on 2009-10-29
check this one out, especially post #4, as that poster claims exchange support for Evolution, so maybe they have a cure?  [http://ubuntuforums.org/showthread.php?t=1299963](http://ubuntuforums.org/showthread.php?t=1299963)

Good Luck!

---

