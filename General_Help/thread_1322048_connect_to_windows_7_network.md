---
title: "connect to windows 7 network"
date: 2009-11-10
forum: General Help
---

### Post by KeeperMustDie on 2009-11-10
Hello,
I had problems logging in to windows 7 shared network via wireless from my laptop, I thought this was wireless problem, but now I'm running ubuntu in VMware and I having same problem. Ubuntu versio 9.10, Samba 4.0. There is two windows 7 PC's, both have perfect network connection with each other, firewalls is turned off. I can see those PC's when I go to Places->Network, but when I try to connect to first one I'm getting "Failed to retrieve share list from server" and the second one asks me for password, I do not have paranoia yet, and I don't use any password, if I click 'connect' with empty password the authentication window just pops up again after few seconds. Any help would be  appreciate.

---

### Post by jbrown96 on 2009-11-10
windows 7 uses something called homegroup by default, and it doesn't use samba. you will need to figure out how to force Win 7 to use samba.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
Try going to Places>connect to server. Set the type to windows share. The share name is the name of the folder. The server is the name of the PC, and the domain is the workgroup name. That's how I have to connect in 9.10. It tells me it can't mount the share at first, but puts a shortcut on the desktop, and it opens when I choose it. In my experience networking worked much better in 9.04.
On your second machine, try your UN and log on password, even though you have password protected sharing off.

---

### Post by alphaniner on 2009-11-10
I have a Win 7 share mounted through fstab on 9.04.  It's a wired network, but I don't think that should matter.  I do remember that I had to jump through several hoops (Windows firewall being just one of them) in order to make an accessible share.

---

### Post by KeeperMustDie on 2009-11-10
> **jbrown96 said:**
> windows 7 uses something called homegroup by default, and it doesn't use samba. you will need to figure out how to force Win 7 to use samba.

Well...ok, but I have almost none samba and linux/windows network experience at all, I tried search google but with no results. Maybe there is someone with more experience who had same problem or knows any tutorial(despite my useless search I can't believe that there is no tutorials how to do it)

---

### Post by KeeperMustDie on 2009-11-10
> **ST3ALTHPSYCH0 said:**
> Try going to Places>connect to server. Set the type to windows share. The share name is the name of the folder. The server is the name of the PC, and the domain is the workgroup name. That's how I have to connect in 9.10. It tells me it can't mount the share at first, but puts a shortcut on the desktop, and it opens when I choose it. In my experience networking worked much better in 9.04.
On your second machine, try your UN and log on password, even though you have password protected sharing off.

Thanks, this helped me a little, now I get prompted for a password on a first PC as it was on second PC. Now about step2: I tried, got: Failed to mount Windows share.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
Try opening it from the desktop after it tells you it failed. It works fine for me after the initial fail.

---

### Post by redjedi on 2009-11-11
> **ST3ALTHPSYCH0 said:**
> Try going to Places>connect to server. Set the type to windows share. The share name is the name of the folder. The server is the name of the PC, and the domain is the workgroup name. That's how I have to connect in 9.10. It tells me it can't mount the share at first, but puts a shortcut on the desktop, and it opens when I choose it. In my experience networking worked much better in 9.04.
On your second machine, try your UN and log on password, even though you have password protected sharing off.

Hi

I'm also having the same problem. I've tried a few different ways but no success.

When I try this method above, I don't get a link on my desktop, it just fails to mount.
If I bookmark it, I get a link in "Places" but it still asks for a password, which doesn't work.

Any ides?

---

### Post by KeeperMustDie on 2009-11-12
> **redjedi said:**
> Hi

I'm also having the same problem. I've tried a few different ways but no success.

When I try this method above, I don't get a link on my desktop, it just fails to mount.
If I bookmark it, I get a link in "Places" but it still asks for a password, which doesn't work.

Any ides?
Yeah, same here, no result, it seems Ubuntu do not support simple way to connect to win7 network, any not so simple ways?

---

### Post by TheCheeze on 2009-11-12
> **ST3ALTHPSYCH0 said:**
> Try going to Places>connect to server. Set the type to windows share. The share name is the name of the folder. The server is the name of the PC, and the domain is the workgroup name. That's how I have to connect in 9.10. It tells me it can't mount the share at first, but puts a shortcut on the desktop, and it opens when I choose it. In my experience networking worked much better in 9.04.
On your second machine, try your UN and log on password, even though you have password protected sharing off.

Works great for me, thanks! Is there any way I can make the shortcut there permanent?

---

### Post by ST3ALTHPSYCH0 on 2009-11-13
I haven't had any luck with that, but there is a way to edit your Fstab to auto mount windows shares.

I haven't attempted it yet, so you'll need to sort through [this](http://ubuntuforums.org/showthread.php?t=618429) and [this](https://wiki.ubuntu.com/MountWindowsSharesPermanently).

---

### Post by TheCheeze on 2009-11-13
I actually found a way. Create a luncher on your desktop and point it to the location of the mount. It will auto-mount it when you double-click it (password status pending)

---

### Post by ST3ALTHPSYCH0 on 2009-11-13
I like that. I'll have to give that a try.

---

### Post by KeeperMustDie on 2009-11-29
Problems is - the network should work, users do not need to search a way to simple connect to windows share, if Ubuntu has networking it should work properly. This is what is called user friendly, not a nice GUI. To whom I need to write about a problem? To samba developers?

---

### Post by ST3ALTHPSYCH0 on 2009-12-01
The truth is that I got my Ubuntu/windows7 network going fine now, but have yet to get my windows7/Vista network playing nicely. How's that for networking should "just work"?

---

### Post by rldev on 2009-12-14
I have the opposite problem. Karmic has no problem connecting to Win 7  computer. However, I do not know how to get win 7 to see Ubuntu pc. I want to mount my ubuntu media drive on win 7 machine. Ihave found nothing on google.

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
You have to add samba users. You can add any user name you like (I'd suggest your own) and either just press enter for the password (none) or go ahead and set a SAMBA passwd (it can be different than your password). [Here's](http://ubuntuforums.org/showthread.php?t=202605&highlight=add+samba+user) a complete samba setup guide. section 1.1  explain setting up samba users.

---

### Post by Thraka on 2010-09-24
Just installed Ubuntu and cannot get this to work either.. Oh well, I'm just going to put Win7 on it instead of Ubuntu. Last time I did Ubuntu I couldn't get network drivers working. That was 4 years ago. This was my second stab at it and while I got network working and video (w00t) this is an annoying deal killer. I need this machine up now. I'll come back in a few years I guess. Toodles.

---

### Post by misteromar on 2011-04-05
> **Thraka said:**
> Just installed Ubuntu and cannot get this to work either.. Oh well, I'm just going to put Win7 on it instead of Ubuntu. Last time I did Ubuntu I couldn't get network drivers working. That was 4 years ago. This was my second stab at it and while I got network working and video (w00t) this is an annoying deal killer. I need this machine up now. I'll come back in a few years I guess. Toodles.

Same for me, back to windows to do a simple task like this is just a joke.

On windows 7 made shared folder, I even made a new user account and gave that user full permissions.

On Ubuntu, Places, Connect to Server, select windows share. Now the easiest way and best to eliminate any errors was to put the IP of the windows machine and workgroup under domain. 

I get a pop up for credentials, refuse to connect no matter what credentials I try, I have permissions on the share.

It shouldnt be any more complicated than this, it is basic networking principles, yet it dosent work. I see it as a failure of the OS.

---

### Post by scankin430 on 2011-06-24
Windows7, by default, loads a service called "Windows Live Sign-In Assistant" which blocks the samba client from connecting to the share.  Disable the service on Windows and your problems are solved. [A fix from samba]("https://bugzilla.samba.org/show_bug.cgi?id=7577") is coming down the pipe...


This obviously won't apply to ALL situations but it drove me CRAZY yesterday.

---

### Post by bferd on 2011-06-29
Follow this updated Guide [HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=1740312") for the latest versions of Ubuntu and Windows

---

