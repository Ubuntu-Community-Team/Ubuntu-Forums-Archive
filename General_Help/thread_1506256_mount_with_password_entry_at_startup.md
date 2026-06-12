---
title: "mount with password entry at startup"
date: 2010-06-10
forum: General Help
---

### Post by oxsf on 2010-06-10
Hi

I have a number of disks which I currently mount manually using:
sudo mount /path/to/mount
when I start up the machine
I then enter my password twice (once for sudo and once for the network drive)

This is fine, apart from the fact that I sometimes forget to do it, so I'd like to automate it.  The thing is, I want to retain manual entry of the network drive password.
I could just write a bash script to run these commands, which I think would do what I want.
Ideally, then, I'd like a term to open and run the script (accepting user input) when I log in to Gnome.  
Is this do-able?  Can I add a command to the startup menu to run a script in a term?
Or is there a "better" way?

Thanks

---

