---
title: "Ubuntu in the office...Part 2... HELP!"
date: 2006-03-20
forum: General Help
---

### Post by chazaq on 2006-03-20
While trying to print, as I mentioned on an earlier thread,  I cannot see any printers in the drop-down on the printer wizard.  
Here is the error log from my last attempt to print:

I [20/Mar/2006:12:50:03 -0500] Adding start banner page "none" to job 7.
I [20/Mar/2006:12:50:03 -0500] Adding end banner page "none" to job 7.
I [20/Mar/2006:12:50:03 -0500] Job 7 queued on '5635' by 'scheduler'.
I [20/Mar/2006:12:50:03 -0500] Started
filter /usr/lib/cups/filter/pstops (PID 9978) for job 7.
I [20/Mar/2006:12:50:03 -0500] Started
filter /usr/lib/cups/filter/foomatic-rip (PID 9979) for job 7.
I [20/Mar/2006:12:50:03 -0500] Started backend /usr/lib/cups/backend/smb
(PID 9980) for job 7.

And tat's all that happens, not printing occurrs.

On my Win2K Server box the Event log displays this:

Document 235, Remote Downlevel Document owned by scheduler was printed on LANIER 5635 RPCS via port IP_192.168.xxx.xxx  Size in bytes: 27022; pages printed: 0

Can anyone help me?

---

### Post by RavenOfOdin on 2006-03-20
Is your user group defined as one that has access to printers?

I'd also recommend checking:

System > Administration > Users and Groups > Select User > Properties > User Privileges

---

### Post by chazaq on 2006-03-20
Thanks for replying ... I will check on the groups and reply again soon...

---

### Post by chazaq on 2006-03-20
okay,  I did as you said...

System > Administration > Users and Groups > Select User > Properties > User Privileges

...and the user does have permission to setup printers.  

Oh by the way - I like your signature quote:
"Those who preach tolerance are themselves the most intolerant."

Additionally,  I will be in Mountain Home, AR visiting my mother around Memorial Day weekend

---

### Post by chazaq on 2006-03-21
I fixed it!
Here was the problem...
The machine name (host name) on the Ubuntu box was an old name from when I had Debian Sarge installed before I installed Ubuntu Breezy Badger.  After I corrected the host name I was able to print !!!

---

