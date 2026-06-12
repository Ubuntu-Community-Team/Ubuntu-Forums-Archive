---
title: "Minimize logs me out - why?"
date: 2010-02-14
forum: General Help
---

### Post by zcacogp on 2010-02-14
Chaps, 

Odd one this, and I have done a bit of a search and found nothing helpful, so I suspect it may not be a common problem. 

I'm running 9.10 Karmic on an X31 Thinkpad, and whenever I try to minimize (minimise for any fellow brits reading!)  a window, it logs me out. I can log back in again fine, but when I try to minimize another window - I'm logged out again. It doesn't take me to a "Do you want to logout?" screen, it just logs me out. The screen goes black for a couple of seconds, and I am shown the login screen. 

It happens with all windows. Firefox, Nautilus, Open Office Applications. 

Anyone have any ideas? Thanks, in advance, for any help. 


Oli.

---

### Post by Satoru-san on 2010-02-14
Has it always done this, or is it recent?

If it is recent, when did you first start noticing it? Did you do anything like an update or install a program from apt or source, etc?

---

### Post by zcacogp on 2010-02-14
OK, quick update ... 

I have just (literally just!) tried an update, and been given this error message: 

"An error occurred. The following details are provided: 

W: Failed to fetch [http://ppa.launchpad.net/ricotz/testing/ubuntu/pool/main/g/gnome-shell/gnome-shell_2.28.1~git20100211-0ubuntu1~9.10~ricotz1_i386.deb](http://ppa.launchpad.net/ricotz/testing/ubuntu/pool/main/g/gnome-shell/gnome-shell_2.28.1~git20100211-0ubuntu1~9.10~ricotz1_i386.deb)
  404  Not Found"

Is this relevant? 


Oli.

---

### Post by zcacogp on 2010-02-14
Satoru-san, 

Thanks for your reply. 

It is recent. Within the last couple of days. Funnily enough, I was playing around the Cairo-Dock on the machine in question, and it may have started just after removing Cairo-Dock. 

Now you have asked, I am wondering whether this is relevant. 


Oli.

---

### Post by Satoru-san on 2010-02-14
Never played around with cario dock, but that seems to be the problem, you could look it up on google or submit a bug.

As far as the other one, that is from the testing ppa repository. I am not sure why updating would pull from that repo. Are you trying to run unstable?

---

### Post by zcacogp on 2010-02-14
I've had a gander on Google and not found anything, which slightly concerns me. Makes me wonder whether it is something I have done wrong (as opposed to it being a known issue.) 

Ummm, I'm not quite sure what you mean by "Run Unstable". I'm not doing anything adventurous, and don't have any "unsupported" repositories (I don't think ... ) Does that answer the question? 


Oli.

---

### Post by audiomick on 2010-02-14
Open the synaptic package manager and go to the second tab, "other software", I think, under 
preferences> software sources
and see what is selected there. It looks like you have a ppa source enabled for whatever reason. If you don't know what it is good for, maybe it would be just as well to disable it.

---

