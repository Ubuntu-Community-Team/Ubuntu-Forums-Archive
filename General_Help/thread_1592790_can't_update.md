---
title: "can't update"
date: 2010-10-10
forum: General Help
---

### Post by brickellcat on 2010-10-10
I'm a newbe
I Just installed Maverick 10:10
Then Updated 2 updates
Now I cant update. This the message:
> phil@phil-PC:~$ sudo apt-get update
[sudo] password for phil: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

can anyone help?:confused:

---

### Post by Pollox on 2010-10-10
Are you currently running Synaptic, Software Center, Update Manager, etc.? Make sure those are closed and try again.  Also, have you tried turning it off and on again? (Seriously, always try that if possible when encountering a problem.)

---

### Post by brickellcat on 2010-10-10
None of the other apps are running and i did a restart too.:(

---

### Post by Pollox on 2010-10-11
> **brickellcat said:**
> None of the other apps are running and i did a restart too.:(

Oh my. That's rather odd. A user [here]("http://www.linuxquestions.org/questions/linux-newbie-8/e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-temporarily-unavailable-360554/") suggests ```
sudo rm /var/lib/apt/lists/lock
``` but I can't say if that might cause problems, so try that at your own risk. That's all I've got. Good luck.

---

### Post by brickellcat on 2010-10-11
Well The problem healed it's self. I guess it really was a "Resource temporarily unavailable" issue

Thanks for your reply.
I''d mark it as solved if I knew how

---

### Post by Pollox on 2010-10-11
> **brickellcat said:**
> 
I''d mark it as solved if I knew how

Thread tools. Top right in red.

---

