---
title: "Don't Run Startup Applications during RDP"
date: 2011-08-16
forum: General Help
---

### Post by Kissell on 2011-08-16
I have a nice script that I've placed in the Startup Applications that open some windows for me when I reboot the computer and login.

But when I connect remotely via RDP it runs this script too...  and that isn't desirable.  Is there a way I can prevent the script from running when I login through RDP?

Using xrdp.

---

### Post by gmargo on 2011-08-16
Why don't you add a line to the script to dump the environment variables to a file?  Then compare the two versions (local vs remote).  There might be a convenient difference you can use.

---

### Post by Kissell on 2011-08-27
Argh...  I had this working...  using a conditional testing for the value of the $DISPLAY environment variable which was different during a remote desktop session.  

Came back here to get the code because Ubuntu One ate my startup script.  It's still buggy syncing multiple computers and editing the file from different locations.

Anyway, so I never came back and posted the code here...  I'll figure it out again and then post the solution.

---

