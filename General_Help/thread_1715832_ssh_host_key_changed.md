---
title: "ssh host key changed?"
date: 2011-03-27
forum: General Help
---

### Post by unbuntunewb on 2011-03-27
I am having trouble with XBMC hanging and having to do a hard reset, I was worried about corrupting data on my HD so I wanted to ssh into this computer from another to reboot it more gracefully, however I get this message

nunya@nunya-desktop:~$ ssh nunya@192.168.1.101
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
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

Im sort of worried, however it is worth noting that I recently started to use a VPN service so perhaps that has something to do with this. Can anyone advise? I went to here /home/nunya/.ssh/known to check on whatever is it talking but the whole file is gibberish.

Thanks.

---

### Post by andrewthomas on 2011-03-27
> **unbuntunewb said:**
>  I went to here /home/nunya/.ssh/known to check on whatever is it talking but the whole file is gibberish.
 
Thanks.
 There should be a hostname and IP in there

---

### Post by crispy_420 on 2011-03-27
Couldn't deleting the offending key get you going? Then when you reconnect it will acquire the key like i was the first time?

---

