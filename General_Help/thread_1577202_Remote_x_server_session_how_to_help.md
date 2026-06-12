---
title: "Remote x server session how to help"
date: 2010-09-18
forum: General Help
---

### Post by Coder68 on 2010-09-18
I am unable to get a remote x server session started.  The book we have for class describes how to do it, but does not give any steps or help.

I am using Ubuntu 8.10. in a VM - named u8 
I have this Virtualbox VM [u8] running on Ubuntu 10.04.

In u8:
I have unchecked the Deny TCP connections on the security tab of the log in window, and loged out/in and even rebooted.
I have tried to give permission to my X server by using xhost +laptop, but I get the following error.
[PHP]xhost:  bad hostname "laptop"[/PHP]I can add u8 though... but not sure why I would want to do that. 

I can ping my laptop by IP from my VM and vice versa. But I can't do it by name. 
I think the VM uses NAT by default, so I am going to reconfigure the network on the VM and try again.

Even if that works, I do not know what to do next.  The book talks about running [PHP]xclock &[/PHP] next.. but wouldn't that just run on the current PC? Don't I need to start some type of connection to the remote x server  or at least tell that command to run on u8 but show up here???? :confused:

I need a beginners guide to setting this up without "3rd party" software.  Can someone please point me to a good how to or guide me through this?

Thanks,

C68

---

