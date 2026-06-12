---
title: "May all files in /tmp be deleted?"
date: 2011-03-28
forum: General Help
---

### Post by hangle on 2011-03-28
i discovered that my password failed when i executed the 'synaptic package manager'. however, the system still recognised my password when i ran 'sudo' .  i had a moment of panic.  i realised  that if i restarted the system, then  i would unable to login successfully.  i eventually figured out that if i used 'sudio' to become a superuser, than i could run 'passwd' to re-establish my password.  this worked. 

the reason i am writing to this forum is understand how i might have encountered problems with my password.  

i suspect that the problem occurred when when i wiped out my '/tmp' directory.  i did a 'rm -r *' in this directory having received that my /tmp partition was full.   the question i have is there files in this directory that should not be deleted. 

another problem surfaced after deleting the files in '/tmp' .
------------------------------------
[CENTER]An error occurred while loading or saving configuration information for gvim. Some of your configuration settings may not work properly.
[LEFT]-------------------------------------------------------
[/LEFT]
[/CENTER]

---

### Post by wyliecoyoteuk on 2011-03-28
Normally /tmp is usually cleaned out when the system shuts down.
It is used by some programs for caching, or storing temporary config files, etc.
/tmp can get filled when downloading large files,for example, if an FTP client uses it for caching.

Deleting files in the /tmp folder which are in use by a program can cause problems.

---

