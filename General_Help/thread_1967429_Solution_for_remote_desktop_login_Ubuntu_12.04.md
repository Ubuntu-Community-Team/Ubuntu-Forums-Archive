---
title: "Solution for remote desktop login Ubuntu 12.04"
date: 2012-04-28
forum: General Help
---

### Post by akabei75 on 2012-04-28
I need for my users to be able to easily login remotely (with desktop GUI) to my brand new Ubuntu 12.04. I have searched the web and found tons of information about VNC, Vino, FreeNX, Citrix etc. However I am not very tech-savvy and cant really figure out what I need and how to get it up :-)

My users come from different platforms, some from Windows and some from Mac OS X. What software should I be looking to get them to be able to remotely login to desktop on my server?

Also I found several places talking about enabling Remote Desktop som the System->Preference->Remote Desktop
But I cant seem to find such a thing :( 

Id be really thankful for any help!

Regards,
S.

---

### Post by akabei75 on 2012-04-28
Experimenting with vino fails miserably :-)
*[FONT="Courier New"]** (vino-server:1249): WARNING **: The desktop sharing service is not enabled, so it should not be run.[/FONT]*

---

### Post by prshah on 2012-04-28
> **akabei75 said:**
> 
Also I found several places talking about enabling Remote Desktop som the System->Preference->Remote Desktop
But I cant seem to find such a thing :( 


Search in the "dash" for remote; you will find an option for "Desktop Sharing".

If you can't find it for any reason, run the below command from a terminal, or from the Alt+F2 "Run a command" box```
vino-preferences
```

Please post back if you need more help.

---

### Post by darknuts on 2012-04-29
I'm glad to see that vino is still there. I was using reminna for a bit but I was unsuccessful in setting up a connection. My only question is this. How do I configure vino to listen on a specific port?

---

### Post by darknuts on 2012-04-29
Oh never-mind. I figured it out. dconf editor did the trick.

---

### Post by fackamato on 2012-05-01
> **darknuts said:**
> Oh never-mind. I figured it out. dconf editor did the trick.

What did you change and where?

---

### Post by amiq on 2012-05-02
check this:
[http://binarytreehouse.blogspot.com/2012/04/easy-installation-of-freenx-server-in.html]("http://binarytreehouse.blogspot.com/2012/04/easy-installation-of-freenx-server-in.html")

works for me on 12.04 but I have not been able to resume a session.

---

### Post by djhsickboy on 2012-05-03
Or you could install xrdp on the Ubuntu box, then when you connect using the Microsoft RDP client, you'll be given an XRDP login screen, just put your username and password in (you can leave the 'module' as sesman-Xvnc)

Haven't tried from a Mac but you can get the MS RDP client on there so hopefully that'll work too, also only tried over LAN, so not sure if this works remotely!

---

### Post by Sijmen on 2012-05-04
This is what I did with my Xubuntu 12.04:

By cavalier911:
[http://ubuntuforums.org/showthread.php?p=10744047](http://ubuntuforums.org/showthread.php?p=10744047)

There was a website with pictures and everything, but I can't seem to find it.

Or something like this(same setup):
[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

---

### Post by quang777 on 2012-07-10
Anyone get xrdp to work with copy and paste? From my Win7 PC, if I try running vncconfig to enable copy/paste, it disconnects me. I can resume my session, but copy and paste still doesn't work.

Q

---

### Post by imachavel on 2012-07-10
remote desktop kernel version 12.4 huh?

Really the issue is, that no matter how it's configured, port 3389 needs to be opened on your router and your firewall, to allow outside clients access to your host. So on the router, port 3389 needs to be open with the i.p. address of your computer.

I've never really been a genius with rdp, once you have the settings configured in remote desktop viewer, you can try remotely connecting to your computer via the terminal, I believe with such a command "rdp 192.168.x.x;3389" assuming you have the 24 cidr and according subnet, basic class c address. Or you can try using the remote desktop viewer. Either way if the connection doesn't work, it's an issue with port forwarding and firewall security, most likely if you connected to the correct i.p. address.

Also is this from within a LAN or are you trying to remote in over a WAN like through a VPN. Either way this is out of my league, but hopefully this info, as well as all the info provided by everyone else, gets you in the right direction :popcorn:

---

### Post by purushottamaher on 2013-04-30
Hi ,

Try the below link solution :

[http://forums.esds.co.in/f4/access-ubuntu-server-remotely-via-rdp-instead-vnc-4617/](http://forums.esds.co.in/f4/access-ubuntu-server-remotely-via-rdp-instead-vnc-4617/)

It will help you...

Thanks,
Purushottam Aher

---

### Post by wkitty422 on 2013-11-30
> **quang777 said:**
> Anyone get xrdp to work with copy and paste? From my Win7 PC, if I try running vncconfig to enable copy/paste, it disconnects me. I can resume my session, but copy and paste still doesn't work.

i'm not coming in from w7 but instead vista... using kubuntu 12.04.03 with one large update... using xRDP and then connecting with the vista RDP client... needing to copy/cut and paste from vista into the rdp session... did you find an answer for your situation from w7? it may help me with mine and vista... perhaps a setting somewhere??

thanks! ;)

---

### Post by Diego_Sousa on 2014-03-09
What did you do?

---

### Post by Diego_Sousa on 2014-03-09
> **darknuts said:**
> Oh never-mind. I figured it out. dconf editor did the trick.
What did you do?

---

