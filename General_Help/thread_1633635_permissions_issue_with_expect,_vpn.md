---
title: "permissions issue with expect, vpn?"
date: 2010-11-29
forum: General Help
---

### Post by thebighere on 2010-11-29
Hello,

I have an automated cron job which uses expect to connect the VPN, then mount the remote drive, then php to copy files

All of this works fine when I am sudo or root and run the file like . script

But when I try a cron job, or I try to run it from a php script from the browser, it won't connect the vpn.

I allowed the wwwrun user access with no password to run the script, and I made sure all the folders and files in question are accessible, chmod-wise

any ideas?  any way to test to see if it's another issue (not permissions?)

thanks

---

