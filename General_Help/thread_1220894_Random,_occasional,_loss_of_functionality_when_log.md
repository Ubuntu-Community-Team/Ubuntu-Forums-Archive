---
title: "Random, occasional, loss of functionality when logged in"
date: 2009-07-23
forum: General Help
---

### Post by michelstpierre on 2009-07-23
Hi, I need some help to troubleshoot my server.  I'm getting occasional error 403 from Apache, sometimes it works, sometimes it doesn't; the problem seems to come and go by itself.  The server is setup with 9.04 since May and everything has been working very well until end of June.  In May and June I was sometimes working on the system and sometimes logged off and never had any problems.  Went on vacation for the first 2 weeks of July, got a few emails from people that the server was - sometimes - reporting error 403.  
I started to investigate about a week ago.  It's really weird...  A page can work ok and an hour after I hit refresh and I get error 403, if I wait some time (15 minutes maybe) and hit refresh then I get the page.  When I log in the server with my user account, i can do some work and eventually I get errors that I no longer have permissions, I can browse the folders but any attempt to open the files return a permission error; even files in my home folder, waiting some time and then I can access the files.  When this happens, Apache also returns error 403 (consistent).   Waiting some time seems to resolve the problem.  
Another way to recover the permissions is a logout.  While Apache returns error 403, I canNOT login with my user account.  But if I'm already logged in when apache starts to return 403, if I logout the apache (well, the permissions) come back.  
The server is a Dell, dual core, 4GB of RAM with Ubuntu 64 bits 9.04 server edition.  I recently added the desktop to help debug this thing.  The problem is more or less the same; when permissions are gone, gnome cannot start any application, always return a permission error.  If Nautilus is open, it can no longer browse the folders, any click on a different folder returns a Nautilus message box about permissions and then Nautilus crashes.
It's really weird.  The intermittent aspect of the problem is the really weird part. I have no clue where to start.  Thanks for any help.

---

