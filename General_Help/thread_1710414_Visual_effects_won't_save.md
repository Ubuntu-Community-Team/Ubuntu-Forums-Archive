---
title: "Visual effects won't save"
date: 2011-03-19
forum: General Help
---

### Post by sorryiambad on 2011-03-19
Hi there

I just installed ubuntu 10.10 today and I'm having a little trouble. When I  go to system>preferences>appearance and then the visual effects tab, it is always on "none". When I click "extra" it blinks the screen a couple times, I click "keep settings" and close out of it but nothing changes. When I go back to visual effects it is back on "none". Any advice on how to make sure "extra" stick?

---

### Post by sorryiambad on 2011-03-19
Sorry for the bump, but does anyone have any advice on what I can do? If it has anything to do with anything my video card is an ATI Radeon HD 5800 series and I'm using the ATI/AMD proprietary FGLRX graphics driver.

---

### Post by sorryiambad on 2011-03-19
shameless second bump

---

### Post by karrank% on 2011-03-19
I have 10.4 and there's a green check mark at the top margin of that dialog box you need to check, then wait for the system to apply your settings, THEN close the dialog box. That should do it.

---

### Post by sorryiambad on 2011-03-19
Heres a screenshot of what I have. I don't see anything to green or anything.

---

### Post by vivek.pandey on 2011-03-19
do you mean to say, you click on system->preferences->start up applications
if is it so you shouldnt click on it so uncheck it

---

### Post by karrank% on 2011-03-19
> **sorryiambad said:**
> Heres a screenshot of what I have. I don't see anything to green or anything.

Right. I got things a little confused. When you click Custom > Preferences on THAT dialog box, it brings up Simple CCSM (Compiz Config Settings Manager) box with the options I mentioned. (Mind, I'm rinning 10.04 but looks the same)

Hope this helps.

---

### Post by sorryiambad on 2011-03-19
> **neo_aryan said:**
> do you mean to say, you click on system->preferences->start up applications
if is it so you shouldnt click on it so uncheck it

No, it is system->preferences->appearance then the "visual effects" tab. 

I'll try to clarify. I installed ubuntu tweak and compiz and some other fun things but for a lot of the customization it requires you to change the "visual effects" to extra. I can change it to extra but nothing changes and then if I open up visual effects again it is back on "none".

---

### Post by sorryiambad on 2011-03-20
So I tried doing the custom settings then clicking the green check but each time it would uncheck "enable extra animations" and here is a screenshot of what it tells me. Any more ideas?

---

### Post by karrank% on 2011-03-20
> **sorryiambad said:**
> So I tried doing the custom settings then clicking the green check but each time it would uncheck "enable extra animations" and here is a screenshot of what it tells me. Any more ideas?

I clicked BOTH "enable animations" AND "enable extra animations", figuring nothing succeeds like excess.

---

### Post by sorryiambad on 2011-03-20
> **karrank% said:**
> I clicked BOTH "enable animations" AND "enable extra animations", figuring nothing succeeds like excess.

Yeah I can get both of them checked. But when I click the green check the "enable extra animations" unchecks itself automatically and I get what you see in the screenshot. What plugins could I be missing? I don't understand.

---

### Post by karrank% on 2011-03-20
Forgot to ask, is your h/w even up to running compiz? used to be a general issue not so long ago, you might want to check.

---

### Post by karrank% on 2011-03-20
> **sorryiambad said:**
> Yeah I can get both of them checked. But when I click the green check the "enable extra animations" unchecks itself automatically and I get what you see in the screenshot. What plugins could I be missing? I don't understand.

I found the ORDER in which I checked those boxes produced different results.

WTH?? weird but true.

Give that a shot.

---

### Post by sorryiambad on 2011-03-20
> **karrank% said:**
> Forgot to ask, is your h/w even up to running compiz? used to be a general issue not so long ago, you might want to check.
Yeah for sure.

> **karrank% said:**
> I found the ORDER in which I checked those boxes produced different results.

WTH?? weird but true.

Give that a shot.
I did and I thought it was going to work for a second. BUT when I click the big green check to save it the enable extra effects unchecks BY ITSELF and when I completely exit and return to the visual effects tab "none" is still checked off instead of "custom" 

I don't understand this at all. I had all of this working fine yesterday. I was dual booting windows and ubuntu 10.10 and windows was giving me problems so I just did a clean install of ubuntu again now I can't get my WOBBLY WINDOWS :'(

---

### Post by karrank% on 2011-03-20
> **sorryiambad said:**
> Yeah for sure.


I did and I thought it was going to work for a second. BUT when I click the big green check to save it the enable extra effects unchecks BY ITSELF and when I completely exit and return to the visual effects tab "none" is still checked off instead of "custom" 

I don't understand this at all. I had all of this working fine yesterday. I was dual booting windows and ubuntu 10.10 and windows was giving me problems so I just did a clean install of ubuntu again now I can't get my WOBBLY WINDOWS :'(

I hear ya. Hated the wobblies at first, now can't live without 'em.

Drawing a blank here atm though.

Have you drilled down into CCSM itself? 

Maybe giving it (and yourself?) a rest, at least maybe a restart/reset might help.

---

### Post by karrank% on 2011-03-20
Also forgot to mention the sticky in Desktop Environments forum (and that forum itself) might have a bit more focused advice in this area. I found it really helped a lot when I first started out with Linux, Ubuntu, and Compiz all of three and a half years ago.

---

### Post by sorryiambad on 2011-03-20
> **karrank% said:**
> Also forgot to mention the sticky in Desktop Environments forum (and that forum itself) might have a bit more focused advice in this area. I found it really helped a lot when I first started out with Linux, Ubuntu, and Compiz all of three and a half years ago.

Well somehow after uninstalling/installing compiz and stuff OVER and OVER again I got it to work. But now when I go to Compiz this is what I get. It's all grayed out lol so I have my wobbly windows but I cannot change anything anymore. Any idea on why it won't let me change anything?

---

### Post by karrank% on 2011-03-20
That shot looks ok to me, if it's grayed out/unselectable as you say, maybe there's a h/w display lag or driver issue (proprietary display drivers installed/enabled?) that you haven't accounted for. Or multiple instances of CCSM maybe?

---

