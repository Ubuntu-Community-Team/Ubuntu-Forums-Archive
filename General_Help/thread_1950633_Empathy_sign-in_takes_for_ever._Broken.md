---
title: "Empathy sign-in takes for ever. Broken?"
date: 2012-04-01
forum: General Help
---

### Post by Hirobian on 2012-04-01
My issue is that empathy takes for ever to sign in. 

It used to work alright, I just noticed because I decided to try it, recently I had to replace my 250GB HDD on this Dell Inspiron 1546 Laptop for a new 360GB Toshiba HDD.
I had to install Windows 7 and Ubuntu on it, everything works fine (except Windows ofcourse*facepalm*), but Empathy seems to be broken.

I've already tried removing and reinstalling empathy but that didn't change anything, does anyone know what I could do?

---

### Post by HiImTye on 2012-04-01
what are you trying to sign in to?

---

### Post by raja.genupula on 2012-04-01
> **Hirobian said:**
> My issue is that empathy takes for ever to sign in. 

It used to work alright, I just noticed because I decided to try it, recently I had to replace my 250GB HDD on this Dell Inspiron 1546 Laptop for a new 360GB Toshiba HDD.
I had to install Windows 7 and Ubuntu on it, everything works fine (except Windows ofcourse*facepalm*), but Empathy seems to be broken.

I've already tried removing and reinstalling empathy but that didn't change anything, does anyone know what I could do?

did you made a reinstall from purge removing ?

---

### Post by HiImTye on 2012-04-01
raja, please don't instruct people to make system altering changes before you know what the problem is :P

---

### Post by raja.genupula on 2012-04-01
> **HiImTye said:**
> raja, please don't instruct people to make system altering changes before you know what the problem is :P

> I've already tried removing and reinstalling empathy but that didn't change anything, does anyone know what I could do? I am talking about this .

---

### Post by Hirobian on 2012-04-01
Note: Consider me a beginner, I may not understand unless explained. Aslo this may or may not be important but I am using Ubuntu 10.04 LTS Lucid Lynx.

> **raja.genupula said:**
>  Did you make a reinstall from purge removing? 

Purge? I only uninstalled the program via the USC (Ubuntu Software Center) I was thinking of doing it via the SMP (Synaptic Package Manager) but I am unsure if I should.

[QUOTE=HiImTye]What are you trying to sign in to? [/QUOTE]

I'm trying to sign into my MSN Messenger account via Empathy, it used to work, maybe I'm doing something wrong in the options?

-/-/-/-/-/-/-/-/-

[B]ALSO! I just remmembered that aMSN and Emesene Have also not been able to sign in.
[/B] 
I don't know if this will help but I found a **debug window for Empathy**, I will be attaching the results to this post.

---

### Post by Hirobian on 2012-04-01
Sorry for the double post but I will be making a new thread as this threads title is about Empathy and I just realized that the problem is affecting aMSN and Emesene aswell.

Here is the link to the new thread, I have rewritten the information, please answer there.

[http://ubuntuforums.org/showthread.php?p=11810409#post11810409](http://ubuntuforums.org/showthread.php?p=11810409#post11810409)

---

### Post by HiImTye on 2012-04-02
you might have better luck if you remove the butterfly plugin for telepathy and revert to the libpurple plugin for MSN
```
sudo apt-get remove telepathy-butterfly
```if it doesnt help you can always just add it again. note, once you remove the plugin you will need to remove your account and then add it agian or you won't see any results

---

### Post by Hirobian on 2012-04-02
I will try that in an hour(I need to get home from school ^^ ) it's 3:02 eastern time as I post this message.

---

### Post by Hirobian on 2012-04-02
I tried removing telepathy, nothing good really happened so I reinstalled it.

(Took a good guess to figure out the command to get it back)

---

### Post by Hirobian on 2012-04-03
I am begining to think this is a bug, should I report it?
 
Sofar noone else has replied stating they had the exact same problem and  I haven't been able to find out the cause. (I'm just not experienced  enough to fix it myself at the moment, I'm still learning the basics of  Ubuntu)
 
If anyone thinks I should report this bug, please mention. If noone  replies within this week I will report it as I will have no other way to  try and have the problem resolved.
 
If anything else comes up, if my friend fixes it for example, I will let you guys know.

---

### Post by Hirobian on 2012-04-11
I gave up on the idea of inputing a bug report and upgraded to Ubuntu 11.10 Oneiric Ocelot at the same time I reinstalled Windows 7.

I decided mainly to Upgrade to Ubuntu 11.10 Oneiric Ocelot while I wait for the release of 12.04 Precise Pangolin, to test out the new interface to see if I like it.
Anyways Emesene and empathy now work again. I strongly believe a recent  update for 10.04 Lucid Lynx broke the two programs. If I descide to  return to Lucid Lynx, I will come back to this thread to update the  status of the programs.

---

