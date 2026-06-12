---
title: "No_pubkey 2ebc26b60c5a2783"
date: 2009-12-16
forum: General Help
---

### Post by iandcph on 2009-12-16
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


i get this error when i try to check for updates... anyone knows how to solve this? i'm new to linux and i'm really enjoying the OS a lot. it makes me do a lot of things because it's faster and it is REALLY more stable. i was able to install some updates but after it, it showed me this error. i dunno how to troubleshoot this issue and i do need help. :). thanks guys! and by the way, i'm ian and i am from the philippines. :). 

- using a sony VAIO VGN-NR310e laptop
- Linux Ubuntu 9.10, Gnome ver 2.28.1
- planning to Partition Ubuntu to my PC
 -- AMD Athlon XP 64 4400+
 -- Asus M2N MXSE
 -- Nvidia GeForce FX 8500GT se
 -- 2 GB Kingston RAM
 -- Motorolla Fax/Modem
 -- would there be any issues?

Thanks and more power!

---

### Post by fooman on 2009-12-16
open a terminal (applications > accessories > terminal),  and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```enter your password when prompted.... see if that works.

---

### Post by howefield on 2009-12-16
Find the key here and save the content to a text file and import into Synaptic and reload.


[http://pgp.mit.edu/](http://pgp.mit.edu/)
keyserver.pgp.com

---

### Post by iandcph on 2009-12-16
> **fooman said:**
> open a terminal (applications > accessories > terminal),  and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```enter your password when prompted.... see if that works.


< -- >

worked like a charm. :). thanks. gonna keep this in my notes.

---

### Post by shaon3343 on 2009-12-16
hi, in future if you face same kind of problem and you cant find tha key than I think this small script will help you a lot , check it out:
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys]("http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/")

---

### Post by shaon3343 on 2009-12-16
**oops!!! I just noticed that that script doesn't work fine in ubuntu 9.10!!! I was atempting to get a key for " [COLOR=DarkRed]deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-fre[/COLOR]" but  it doesn't work. But it worked fine for this same ppa when i used ubuntu 9.04!! whats the probs ??** I also run the command " [COLOR=#800000]sudo wget -O &#8211;  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -"  
[COLOR=Black]it also failed to fetch a key for that ppa.[/COLOR] :( :( 
[/COLOR]

---

