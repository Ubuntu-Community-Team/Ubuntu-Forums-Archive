---
title: "Opening  synaptic packaging manager"
date: 2010-02-05
forum: General Help
---

### Post by Chatterton on 2010-02-05
Attempting to upgrade Firefox to 3.6. On opening synaptic package manager I get :- 
    An error occurred 
  E: dpg was interrupted, you must run 'dpkg--configure-a' to correct the problem.
  E:_cache->open()failed,please report.

 On entering 'dpkg--configure-a' on terminal I get 'command not found.

 On 8.04(hardy)
 Help! And to whom does one report?

---

### Post by plucky on 2010-02-05
> **Chatterton said:**
> Attempting to upgrade Firefox to 3.6. On opening synaptic package manager I get :- 
    An error occurred 
  E: dpg was interrupted, you must run 'dpkg--configure-a' to correct the problem.
  E:_cache->open()failed,please report.

 On entering 'dpkg--configure-a' on terminal I get 'command not found.

 On 8.04(hardy)
 Help! And to whom does one report?

```
sudo dpkg --configure -a
``` you need the spaces.

Good Luck

---

### Post by Chatterton on 2010-02-05
Thanks Plucky ,that worked perfectly and I was able to open synaptic and I now know that linux-generic 2.6.24.26.28 described as complete generic linux kernel is broken. I tried Edit Fix broken packages but no result.What should I do next.

---

### Post by plucky on 2010-02-05
> **Chatterton said:**
> Thanks Plucky ,that worked perfectly and I was able to open synaptic and I now know that linux-generic 2.6.24.26.28 described as complete generic linux kernel is broken. I tried Edit Fix broken packages but no result.What should I do next.

```
sudo apt-get install -f
``` is another way of fixing broken packages.

If that doesn't work,can you please post the complete error so we can see what is causing the error.If it is long,enclose in [noparse]```

```[/noparse] blocks.

Good Luck

---

### Post by Chatterton on 2010-02-10
Thank you Plucky,that worked perfectly.All the Firefox 3.6 are now shown as installed, however when I start Firefox it is still 2.Any suggestions?

---

### Post by plucky on 2010-02-10
> All the Firefox 3.6 are now shown as installed, however when I start Firefox it is still 2.Any suggestions? 



Can't help with that as I am still on 3.5.7

But found [this](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html)

Scroll down to the Hardy 8.04 instructions.

Good Luck

---

