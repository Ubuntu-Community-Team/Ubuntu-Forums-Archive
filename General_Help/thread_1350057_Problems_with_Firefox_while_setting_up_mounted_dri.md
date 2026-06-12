---
title: "Problems with Firefox while setting up mounted drives"
date: 2009-12-08
forum: General Help
---

### Post by cAlpha on 2009-12-08
I was changing my fstab file (/etc/fstab) to automatically mount my shared file partition and my Vista partition on startup (in order to share my Firefox profile), all within my new installation of Ubuntu 9.10.    

I made the changes to fstab, mounted them via the command line (sudo mount -a) and was able to access both partitions--though for some reason the Vista partition didn't show as a shortcut on my desktop as it did in 8.04.  

I tried to tweak the fstab file show the Vista partition would show on the desktop with no success.  **So, I restarted hoping the changes would go into effect and after logging in, I was getting the "Firefox is already running" error when trying to open up Firefox.  **

I checked the profile I'd set up and there weren't any lock files to delete.  I also checked running processes and there isn't one for firefox listed.  

Thus, I'm stumped.  My only thought is that since I set up a profile in Firefox that shared the one I was within Vista, it may be having trouble accessing it and I'm getting the error for that reason.  Along those lines, I'm able to navigate to my Vista partition via the mounted location using the command line, it doesn't show as mounted (as my shared file partition DOES) within the file browser window.  

Any thoughts?

---

### Post by dcstar on 2009-12-09
> **cAlpha said:**
> I was changing my fstab file (/etc/fstab) to automatically mount my shared file partition and my Vista partition on startup (in order to share my Firefox profile), all within my new installation of Ubuntu 9.10.    

I made the changes to fstab, mounted them via the command line (sudo mount -a) and was able to access both partitions--though for some reason the Vista partition didn't show as a shortcut on my desktop as it did in 8.04.  

I tried to tweak the fstab file show the Vista partition would show on the desktop with no success.  So, I restarted hoping the changes would go into effect and after logging in, I was getting the "Firefox is already running" error when trying to open up Firefox.  

I checked the profile I'd set up and there weren't any lock files to delete.  I also checked running processes and there isn't one for firefox listed.  

Thus, I'm stumped.  My only thought is that since I set up a profile in Firefox that shared the one I was within Vista, it may be having trouble accessing it and I'm getting the error for that reason.  Along those lines, I'm able to navigate to my Vista partition via the mounted location using the command line, it doesn't show as mounted (as my shared file partition DOES) within the file browser window.  

Any thoughts?

NTFS does not support file/folder names starting with a ".", Linux Firefox uses files starting with that.

Linux Firefox cannot use profiles on NTFS.

---

### Post by cAlpha on 2009-12-09
> **dcstar said:**
> NTFS does not support file/folder names starting with a ".", Linux Firefox uses files starting with that.

Linux Firefox cannot use profiles on NTFS.



Thanks for your reply.  I'm using absolute references though, so that can't be it.  

I'm sharing a Firefox profile between Vista and 8.04, and it worked for 9.10 for a minute, but then I ran into to the problem I mentioned.  

Any other thoughts?

---

