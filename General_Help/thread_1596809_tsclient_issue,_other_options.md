---
title: "tsclient issue, other options?"
date: 2010-10-14
forum: General Help
---

### Post by zinjashike on 2010-10-14
Greetings,

Currently my issue is this.  I use tsclient to connect to a Win7 machine at home and have it set to mount the Ubuntu drive.  I want to copy files from my Win7 machine over the internet to my Ubuntu system.  When I do this I get something along the lines of "\\tsclient\local not accessible" and a complaint regarding permission.  Is there a way to fix this, or an easier way to get files off my Win7 machine when away from home?  If so, any good guides on how to set it up too?  Thanks.

---

### Post by gradinaruvasile on 2010-10-14
You have to mount a folder that can be written by the user that launched tsclient - ex. your home directory and its subdirectories in most cases.
The system root folder is writable only by root (or you with sudo, but thats basically the same) - if you export that you should change directory to your folder to be able to write.

PS You should try Remmina as remote desktop client, it is way better than the default tsclient.

---

### Post by zinjashike on 2010-10-14
> **gradinaruvasile said:**
> You have to mount a folder that can be written by the user that launched tsclient - ex. your home directory and its subdirectories in most cases.
The system root folder is writable only by root (or you with sudo, but thats basically the same) - if you export that you should change directory to your folder to be able to write.

PS You should try Remmina as remote desktop client, it is way better than the default tsclient.

I'm not sure I fully understand your instructions, so bear with me (bit of a Linux newbie).

I ran Remmina, and made sure to use my home folder as the mountable share (inside Remmina).  In Windows I went to network places and my Linux home folder.  I then went to my documents folder.  I went to paste some copied files and this is the error I get:

"\\tsclient\shike\Documents is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

Attempt to access invalid address."

So basically, my Windows account doesn't have permission to write to my remote Linux machine?  How should I got about fixing that?

---

### Post by zinjashike on 2010-10-15
Bump I guess?

---

### Post by gradinaruvasile on 2010-10-15
Network places?
The tsclient exported drive should be mounted in Windows after you connect as a network drive (no drive letter). Look in the attachment (the "Other" section).
This protocol is not samba (windows sharing), it is done separately through the RDP protocol.
Also, what windows are you using? Is there an active firewall?

[http://www.brianmadden.com/forums/t/21164.aspx](http://www.brianmadden.com/forums/t/21164.aspx)

See the last post there and check those settings.

---

### Post by zinjashike on 2010-10-16
> **gradinaruvasile said:**
> Network places?
The tsclient exported drive should be mounted in Windows after you connect as a network drive (no drive letter). Look in the attachment (the "Other" section).
This protocol is not samba (windows sharing), it is done separately through the RDP protocol.
Also, what windows are you using? Is there an active firewall?

[http://www.brianmadden.com/forums/t/21164.aspx](http://www.brianmadden.com/forums/t/21164.aspx)

See the last post there and check those settings.

When I connect I see the drive in my computer.  After a while that message pops up though.  I have no active firewall enabled on my system.

The other PC OS I'm connecting to is Windows 7.

---

### Post by zinjashike on 2010-10-17
More info:

I only get the error when actually trying to read or write files specifically to the drive.  For example I can see the files in the drive just fine, proper names and all.  However, when I highlight them or try to get properties that's when the error occurs.  The error also occurs when I attempt to write files to the drive.

---

