---
title: "Can't make SSH connection from WAN"
date: 2006-01-31
forum: General Help
---

### Post by hartnady on 2006-01-31
Hello my fellow Linux enthusiasts!

I have a problem... I have openssh installed and running on my machine at home.

From my home LAN, I can connect using SSH, but at work I can't.

Port 22 is open and forwarded to my machine from my router.

Any ideas?

---

### Post by ScreemingBlue on 2006-01-31
Are you sure Port 22 is allowed out from your work? It is very likely that port 22 is blocked outbound. Yoo may want to change the port your SSH server listens on. You could change your home router to port forward for example 443 or 80 to 22 so that your SSH server is listening on 443 or 80. 

Hope this makes sense.

---

### Post by hartnady on 2006-01-31
I am using Putty at work to connect to 2 other servers (one in Georgia, Atlanta and one in Paris, France) both on SSH port 22.

---

### Post by ScreemingBlue on 2006-01-31
That squashes that one then...

What error messages are you getting in your Putty event log?

The other thing is to check your /etc/ssh/sshd_config file and make sure that the server is listening on 0.0.0.0 or your internal IP address.

---

### Post by cloneofsnake on 2006-02-07
Hi, I'm not even quite there yet but I'm trying to do the same thing.

I've tried searching for "ubuntu ssh guide" and found:

[http://www.ubuntuforums.org/showthread.php?t=27305](http://www.ubuntuforums.org/showthread.php?t=27305)

[http://ubuntuguide.org/#sshserver](http://ubuntuguide.org/#sshserver)

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

[http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

I got ssh installed last night, I'm at work now... so, in order for me to ssh home, I'll need to forward port 22 on my router to my ubuntu, right?  and let's say my username is snake and my home ip is 66.94.234.13.  Then I'll just need to type:

ssh snake@66.94.234.13:22

Is that correct?  (I'm not sure about that port 22 part!)

Thanks!

---

### Post by stoffe on 2006-02-07
[QUOTE=cloneofsnake]Hi, I'm not even quite there yet but I'm trying to do the same thing.

I've tried searching for "ubuntu ssh guide" and found:

[http://www.ubuntuforums.org/showthread.php?t=27305](http://www.ubuntuforums.org/showthread.php?t=27305)

[http://ubuntuguide.org/#sshserver](http://ubuntuguide.org/#sshserver)

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

[http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

I got ssh installed last night, I'm at work now... so, in order for me to ssh home, I'll need to forward port 22 on my router to my ubuntu, right?  and let's say my username is snake and my home ip is 66.94.234.13.  Then I'll just need to type:

ssh snake@66.94.234.13:22

Is that correct?  (I'm not sure about that port 22 part!)

Thanks![/QUOTE]
If you have told your roter to forward port 22 (or  if you have no router at all) all you need to type is:

ssh snake@66.94.234.13

Port 22 is the default.

For those having trouble with this, can you test it without the router? That is, is it possible for you to connect the computer directly and then see if it is possible to connect from the outside? If so, you will know that the problem is with the forwarding.

Other possible causes is that your ISP doesn't allow the connection to be made. If you can connect inside the LAN, that is no guarantee for the traffic to be allowed by the ISP, or by your router. So those two are the places I'd look for first.

---

