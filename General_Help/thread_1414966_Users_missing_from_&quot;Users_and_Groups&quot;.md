---
title: "Users missing from &quot;Users and Groups&quot;"
date: 2010-02-24
forum: General Help
---

### Post by txinga on 2010-02-24
I was setting up my wife on our laptop yesterday. I created an ID for her in the "Users and Groups" app, set a PW, and configured her rights to the machine. I set both of our profiles to not be able to see each other's files.
I then figured it was time to change my PW.
Well after I did these things, I logged in as her, checked the Users and Groups section and only saw root in the users list.
I logged out and back in as me and can only see root.
I noticed I also lost su capability.
I got my su back by booting to a prompt and typing adduser *myname* admin.
But, there is still only root listed in the Users and Groups section.
How can I add my other profiles back to this app?
Thanks,
Txinga

---

### Post by Huginn Navarita on 2010-02-25
just had the same problem on my xubuntu machine today...but I have installed the gnome desktop and was using that...I added a user...and was doing the switch user...when the whole system crash and after restarting...I only see 'root' in the table....and I can not FTP in....I can log in users normally.....and log in remotely over ssh, so Im interested also if anyone knows what is wrong there

---

### Post by Zill on 2010-02-25
Unfortunately, the Users and Groups GUI is still buggy in some circumstances.

Workaround:  use terminal commands (eg adduser) rather than the GUI.
[URL="https://bugs.launchpad.net/gst/+bug/240437"]
https://bugs.launchpad.net/gst/+bug/240437[/URL]

---

