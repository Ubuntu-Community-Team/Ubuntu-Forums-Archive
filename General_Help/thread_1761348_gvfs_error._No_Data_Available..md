---
title: "gvfs error. No Data Available."
date: 2011-05-18
forum: General Help
---

### Post by Roasted on 2011-05-18
Sometimes I get this error with .gvfs mounted CIFS shares:

[B]Error: No data available 
Please select another viewer and try again.[/B]

This is interrupting my backup procedure as there are times during the backup it just shuts off. When I click on my share, I get this error, which tells me something happened to the connection during the backup process. It also does this at times even if my system has been idle for a while and I click on the share to explore the data, which also suggests it's not isolated to JUST when I run backups. 

Does anybody know what I can do to fix it?

---

### Post by dimaspivak on 2011-12-20
Sorry to resurrect an old thread, but I get this same error with my Western Digital My Book Live. Anyone ever stumble upon a fix or workaround?

-Dima

---

### Post by Roasted on 2011-12-21
Oh man. I wish I had tagged more info in that thread when I posted it. I'm having zero issues now and have no idea how (if) I fixed it...

Can you give more information on your issue? Maybe it'll help get my memory going.

---

### Post by Newbunto on 2012-05-10
[SIZE=2]As with others, I intermittently get a dialog box saying

**Could not display "smb://*user*@*host*/*share*/".**
Error: No data available
Please select another viewer and try again.

when clicking on a network share as listed on the left hand side in nautilus. Clicking OK to the dialog box and clicking on the share again then works. (In the actual message 'user', 'host' and 'share' are substituted with the correct information.)

Any explanation? fix? workaround?

I have six network shares and I think they all exhibit the same problem from time to time. Those shares are spread over two different servers (running two different distros i.e. not the same as each other and neither is Ubuntu, although one is Mint).[/SIZE]

---

### Post by Newbunto on 2012-05-14
[SIZE=2]More specific information:

The shares that are on the server running Linux Mint get a different error

**Error: invalid argument**

and this seems to occur after coming out of Hibernation on the client (and perhaps *only* after that). So let's ignore those ones here. It's probably the same as e.g. [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/382555](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/382555)

The shares that are on the *other* server get the error that started this thread and this error occurs intermittently throughout the day.
[/SIZE]

---

### Post by Newbunto on 2012-06-22
This behaviour has changed with Ubuntu 12.04

All shares now give the "Invalid Argument" message.

The shares on one server only give this message once, after resuming from hibernation. (This is as before.)

The shares on the other server give this message intermittently, including after resuming from hibernation. (This is different.)

---

