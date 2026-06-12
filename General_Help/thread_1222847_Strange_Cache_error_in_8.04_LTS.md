---
title: "Strange Cache error in 8.04 LTS"
date: 2009-07-25
forum: General Help
---

### Post by Michl on 2009-07-25
I am a little surprised that in a Dell 220
that is running 8.04 LTS I cannot update
anymore because I am getting an error message:

E: dpkg was interrupted, you must manually run 'depkg --configure...
E: -cache ->opem() failed, please report

This is surprising because I am very conservative with
this computer and don;'t customize anything.

In any case, I can;t run synaptic package manager
either, and I am afraid of manually running 'dpkg
--configure' due to bad experiences in the past.

I am assuming this is due to some past update and
I was hoping to avoid this sort of thing with LTS.

Advice is appreciated.

---

### Post by gettinoriginal on 2009-07-25
> E: -cache ->opem() failed, please report
This message usually comes up when you have more than one package manager open at the same time, ie "synaptic/terminal/add remove".  Close all but one, then try again for what ever you were trying to do when you got the message.  If it still fails, you should not be afraid to run "depkg --configure".  :P

---

### Post by Michl on 2009-07-25
> **gettinoriginal said:**
> This message usually comes up when you have more than one package manager open at the same time, ie "synaptic/terminal/add remove".  Close all but one, then try again for what ever you were trying to do when you got the message.  If it still fails, you should not be afraid to run "depkg --configure".  :P

Only have one package manager running.  Also
rebooted, etc., tried many times, etc.

---

### Post by Michl on 2009-07-25
I ran dpkg configure and that got rid
of the error message, but now I have
a new situation when updating.  The
security updates -- like firefox 3.0
and pulse, etc. cannot be authenticated.
There are all standard packages that have
been updated many times.

---

### Post by gettinoriginal on 2009-07-26
My updates used to do that, so I had to repair my software sources list.  Other people have had the same problem due to proxy or wireless networking settings.  And yet others have solved it by changing their mirror server.

---

### Post by Michl on 2009-07-26
With trepidation I followed the
directions and ran
dkpg --configure -a

with trepidation because typically you're asked
about keeping and changing configuration files
and that can be a nightmare.  Fortunately, I was
only asked about my smb configuration.

Then I had the authentication problem, and
I couldn't get rid of it no matter what I
tried using the Update Manager.  So back
to the terminal and ran

apt-get update

and now the Update Manager is back to normal.

I did not think it was appropriate to change the software sources since I did not change them before the problem
and believe that should not be a problem for an LTS
distro.

I am still puzzled why this happened. My aim on this
computer where I had the problem is to run an LTS
distro that is foolproof for ordinary folks to use.
This was the first glitch since I installed Hardy
on this computer.  I wish I could diagnose the
problem with certainty.

---

