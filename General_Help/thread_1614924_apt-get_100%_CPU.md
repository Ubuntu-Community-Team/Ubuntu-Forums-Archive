---
title: "apt-get 100% CPU"
date: 2010-11-06
forum: General Help
---

### Post by #define on 2010-11-06
Hi!
Sometimes, when Ubuntu is connected to Internet, process apt-get loads one of my CPU's cores to 100%, and I must reboot or suspend and wake up the system to stop it. 
How can I fix this problem?
*[FONT=Arial Black]Ubuntu 10.10 64bit, installed on clean disk and upgraded.[/FONT]*

---

### Post by sikander3786 on 2010-11-06
Can you please run **apt-get** in a terminal and **top** in another and post the output so we can have a look at it. Are you sure it is apt-get?

Actually gnome-system-monitor itself uses a lot of resources for all that graphs so it would be better to run **top**.

And are there any errors with apt-get or it is able to complete the operations successfully?

---

### Post by #define on 2010-11-06
> I And are there any errors with apt-get or it is able to complete the operations successfully?  I had never use it before. > Are you sure it is apt-get? Yes, I detect this fact in top in terminal.The gnome-system-monitor shows that one "CP" is loaded to 100%, but it do not show the apt-get in tab Processes. Outputs will be later.

---

### Post by #define on 2010-11-08
Here is outputs.
On second screen: 
Could not assess  to a lock file /var/...
(11.Resource is temporarily unavailable)
This lag repeats almost every day!

---

### Post by freshmeatz on 2010-11-17
yeah I can kill the process, but seems slow, doggy, etc after so if I don't restart the X server I get weird glitches. hasn't happened for a few days now, 10.10x64 on acer 5734z-4836

---

### Post by EmilioOo on 2010-12-04
> **#define said:**
> Hi!
Sometimes, when Ubuntu is connected to Internet, process apt-get loads one of my CPU's cores to 100%, and I must reboot or suspend and wake up the system to stop it. 
How can I fix this problem?
*[FONT=Arial Black]Ubuntu 10.10 64bit, installed on clean disk and upgraded.[/FONT]*

I've the same problem on 32 bit 10.10... 
In my case killing the process works fine.

Further details asap.

---

