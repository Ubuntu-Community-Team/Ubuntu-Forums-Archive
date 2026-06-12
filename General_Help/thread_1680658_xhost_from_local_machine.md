---
title: "xhost from local machine"
date: 2011-02-02
forum: General Help
---

### Post by flubbard on 2011-02-02
This seems similar to questions that have already been asked, but I have not been able to find the answer.  

I would like to be able to have one local user connect to the X of another local user and run an X program.  On fedora, I can simply run:

$ xhost +

and then have the other user run:

$ sol --display=0.0

This is not working on my ubuntu (10.10).  I am guessing that there is an additional level of Xauth restrictions, but I cannot find out how to get past them.  Both users are local to the machine.  I would like to not use sux or gdsu as both require you to enter the password and I would like this to be seemless.  I am aware of the security concerns and believe that I have mitigated them.

Any help would be appreciated.

  - flub

---

### Post by gmargo on 2011-02-03
Try specifying DISPLAY as ":0" instead of "0.0".

---

### Post by flubbard on 2011-02-03
Same result.  I should mention that there was an error in my original post, the command I am trying to use is:

$ sol --display=:0.0

I forgot the ':' in the original post.

I also forgot to include the error in the initial post.  


** (sol:2036): WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

  - flub

---

### Post by rnerwein on 2011-02-03
> **flubbard said:**
> This seems similar to questions that have already been asked, but I have not been able to find the answer.  

I would like to be able to have one local user connect to the X of another local user and run an X program.  On fedora, I can simply run:

$ xhost +

and then have the other user run:

$ sol --display=0.0

This is not working on my ubuntu (10.10).  I am guessing that there is an additional level of Xauth restrictions, but I cannot find out how to get past them.  Both users are local to the machine.  I would like to not use sux or gdsu as both require you to enter the password and I would like this to be seemless.  I am aware of the security concerns and believe that I have mitigated them.

Any help would be appreciated.




  - flub

hi 
don't use "xhost +" without trusted hosts.
because 
 +       Access is granted to everyone, even if they aren't on the  list
               (i.e., access control is turned off). !!!!!!!!!!!!!!!!!!!!
try: xhost + localhost

ciao

---

### Post by flubbard on 2011-02-03
Right.  However, in this case I have a trusted environment.  Also, shouldn't it still work with xhost +.  Going for least restrictive first.  

Is there something within ubuntu that stops this from working that doesn't appear on other distros (fedora seems to handle it fine)?

 - flub

---

### Post by flubbard on 2011-02-03
As I look more at this (comparing it to another install of eeebuntu which work), it appears that the problem lies in the 

GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

message.  Is it possible that there is an issue with Maverick (10.10) that is causing my trouble?

 - flub

---

### Post by jboyson on 2011-02-03
I was able to accomplish this using the commands below.

On local system /usr/bin/xhost +
On local system ssh -x username@remotehost

The remote system was Solaris.

---

### Post by flubbard on 2011-02-03
the problem here is that I would like to go from one local user to another.  Therefore ssh isn't really an option.  The local and remote are both on the same machine, just different sessions or terminals.

 - flub

---

### Post by thundre on 2011-03-10
I'm having the same problem, trying to run a second copy of Firefox on a restricted account.  I have done

xhost +SI:localuser:user2

xclock gives a warning "none of the authentication protocols are supported", but it works anyway.

In firefox it seems to be fatal.  Firefox also gives a warning about not being the owner of /tmp/orbit-user1.  Why is it checking orbit-user1 instead of orbit-user2?

edit to add:

I found a workaround.  Instead of "su user2" and then typing "firefox" in the new shell, I just "gksu -u user2 firefox".

---

