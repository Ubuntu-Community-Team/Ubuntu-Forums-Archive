---
title: "ssh problem"
date: 2011-03-27
forum: General Help
---

### Post by unbuntunewb on 2011-03-27
I have an odd problem. I can ssh into my desktop from my laptop but I cannot ssh into my laptop from my desktop. This is all on my home network. 

My laptop is wifi and my desktop is wired. When I try to ssh from my desktop to laptop I keep getting a connection refused error, doesnt matter what port I use either.

For the heck of it I tried to ssh from my desktop *into* my desktop (that is correct, not a typo) and I got this error earlier today. Im kinda concerned. 

nunya@nunya-desktop:~$ ssh nunya@192.168.1.101
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
"big long string of numbers"
Please contact your system administrator.
Add correct host key in /home/nunya/.ssh/known_hosts to get rid of this message.
Offending key in /home/nunya/.ssh/known_hosts:8
RSA host key for 192.168.1.101 has changed and you have requested strict checking.
Host key verification failed.

Does this have anything to do with it? 

Thank you

---

### Post by andrewthomas on 2011-03-27
It could be that you are using dhcp with both computers and their IPs got switched so the key that is stored has a different IP associated with it. 
 
To test it out look in the ~/.ssh/authorized_keys file and ~/.ssh/known_hosts and look at the IPs
 
 
EDIT: I assume that you have disabled password authentication, correct?

---

### Post by SeijiSensei on 2011-03-27
All that message means is that the last time you connected to your local machine with SSH it had a different host signature.  That can happen if you recently installed openssh-server on the machine so that it generated a new key.  The easiest solution is to delete $HOME/.ssh/known_hosts so the file will be rebuilt.  After deleting the known_hosts file, you'll be asked to accept the remote's signature as happens any time you visit a new host.

As for connecting to your laptop, I suspect you didn't install openssh-server on that machine.

---

