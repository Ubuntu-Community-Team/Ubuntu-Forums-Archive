---
title: "Empathy Status keeps changing"
date: 2009-11-03
forum: General Help
---

### Post by slugicide on 2009-11-03
I just want to set my status as "away" and keep it there, but Empathy changes it back to "available" every time the screen changes or I log in or out. Is there any way to do this?

---

### Post by Altay_H on 2009-11-04
I'm having a similar problem. Empathy constantly changes my status back to available even if I just leave my computer unattended. Does anyone have any ideas?

---

### Post by neverland888 on 2009-11-04
same prob. here, when i set status to Away, and leave mouse idling for couple of minutes, it changes status to Available by itself. 

it does not matter if i set status from empathy window or from gnome right top corner, same thing happens.

---

### Post by LuK_green on 2009-11-05
It seems Empathy is way too clever. And I couldn't find how it behaves. I was told by one of my Empathy contacts it puts the away status after 3 minutes of idle.

Also, as I noticed, if you set an away status manually, Empathy will not change it back to "available" if you are still working at the computer. But if you take a break for a half of an hour, Empathy will change status to "available" when you'll come back to work.

It is a very big disappointment for me not to be able to change these settings and even not to know precise values, on which Empathy's behaviour is based. The only information in Empathy help is "If you do not use your computer for a while, or if the screensaver is on, the status will be automatically set to Away." "For a while", huh?.. :(

P. S. I have not found any keys in Gnome registry, which could help me with Empathy. Is that really a Linux application which doesn't allow to change its settings? :(:(:(

---

### Post by slugicide on 2009-11-05
I'm really hoping someone can chime in here with some help. Please?

---

### Post by neverland888 on 2009-11-06
> **LuK_green said:**
> It seems Empathy is way too clever. And I couldn't find how it behaves. I was told by one of my Empathy contacts it puts the away status after 3 minutes of idle.

Also, as I noticed, if you set an away status manually, Empathy will not change it back to "available" if you are still working at the computer. But if you take a break for a half of an hour, Empathy will change status to "available" when you'll come back to work.

It is a very big disappointment for me not to be able to change these settings and even not to know precise values, on which Empathy's behaviour is based. The only information in Empathy help is "If you do not use your computer for a while, or if the screensaver is on, the status will be automatically set to Away." "For a while", huh?.. :(

P. S. I have not found any keys in Gnome registry, which could help me with Empathy. Is that really a Linux application which doesn't allow to change its settings? :(:(:(
i agree, this is probably the way it works, and i suppose it uses settings "Regard this computer as idle after" from screensaver preferences to deal with status changes. If the idle settings is for e.g. 5 minutes if you leave pc idling for 5 minutes and when you come back after 5 minutes empathy changes status to Available.

So it is possible to tweak idle setting to more than 5 minutes, but not more than 2 hours, so it's not exactly an fix to the problem. I've set idle setting to 1 hour to test, and it does not changes status if the idle was less than hour, but if it was more, then it changes as soon as you come back.

---

### Post by wadelius on 2009-11-16
Until this gets fixed I'm sticking with Pidgin. Does anyone know if it has been filed as a bug?

---

### Post by slugicide on 2009-11-16
I'm on the verge of dropping this for Pidgin. It is seriously irritating to have the *app* deciding what *my* status is. What's next, a browser that decides where I want to go?

---

### Post by LuK_green on 2009-11-22
> **neverland888 said:**
> i agree, this is probably the way it works, and i suppose it uses settings "Regard this computer as idle after" from screensaver preferences to deal with status changes. If the idle settings is for e.g. 5 minutes if you leave pc idling for 5 minutes and when you come back after 5 minutes empathy changes status to Available.

So it is possible to tweak idle setting to more than 5 minutes, but not more than 2 hours, so it's not exactly an fix to the problem. I've set idle setting to 1 hour to test, and it does not changes status if the idle was less than hour, but if it was more, then it changes as soon as you come back.

Thanks for a solution, neverland888! It is not very obvious, really! Now I'm quite happy with Emphaty, because I discovered a "busy" status, which doesn't change if you move a mouse or whatever. Although, it would be more rational for Empathy not to cancel "away" status if it was put manually.
(Went to the bug tracker =))

---

### Post by LKjell on 2009-11-26
That's it Empathy does not show any empathy.

---

### Post by soulfire on 2009-11-28
I reported this on Empathy Bugzilla, here's the link

[https://bugzilla.gnome.org/show_bug.cgi?id=603226](https://bugzilla.gnome.org/show_bug.cgi?id=603226)

---

### Post by markp1989 on 2009-11-30
im having the same problem its doing my ******* head in.

i set my status to invisable so people dont talk to me when im doing somthing , if the screen goes dark from idle , as soon as i move the mouse the status gets changed back to busy and people start talking

i like getting set to away when im not there, if i was set online before, but when im invisable, there should be no auto changing! 



any fix? cause this is gettting on my nervs.

edit: im also having problems when setting status using the indicator-applet  see here: [http://ubuntuforums.org/showthread.php?p=8414938](http://ubuntuforums.org/showthread.php?p=8414938)

---

### Post by neverland888 on 2009-12-05
my final fix,

apt-get remove empathy
apt-get install pidgin

couldn't sort this status thing and msn file transfer is unsupported, empathy is just not good enough to replace pidgin.

---

### Post by Velaru on 2009-12-05
Judging from [https://bugzilla.gnome.org/show_bug.cgi?id=566832](https://bugzilla.gnome.org/show_bug.cgi?id=566832) this is how they want empathy to behave. Not how you or i want it to behave how they want it to. I have yet to ever see this problem in any messenger client that i have used including some really really bad versions of aim way back in the day.


As much as i think empathy has promise it all around never should have been moved to Ubuntu's default IM client in its current form. Empathy developers seem to be taking empathy down the route of they know best and thats just the way its gonna be.

welcome back pidgin.

---

### Post by varanasi on 2009-12-24
Empathy is disappointing in a number of ways.  The status setting is just nutty.  I set it to invisible; empathy sets it to busy.  Changing my own screen alias simply doesn't work.  The one line entry box is a pain.   Where are some usable preference/config files?  Do the developers think we are windows users?  (And the Facebook plugin does several odd things in empathy that it doesn't do in pidgin.)

---

### Post by stew721 on 2009-12-24
This issue with the constant status changes is definitely my single biggest problem with Empathy.  I've not seen another client that doesn't allow you to control your privacy in such a fundamental way.

If I set myself to invisible, then perhaps I actually want to be "invisible", eh?  Otherwise, I'd have set my status to something else, no?!?  This isn't exactly rocket science here.  The developers need to give their heads a shake if they really want it to function as-is.

---

### Post by benzs_s on 2009-12-28
Does anyone know if there's going to be a manual option to set this? Judging by the bug report posted above, only changes to the automatic system are being considered.

For now i'm going back to pidgin, heh

---

### Post by slugicide on 2009-12-28
> **benzs_s said:**
> Does anyone know if there's going to be a manual option to set this? Judging by the bug report posted above, only changes to the automatic system are being considered.

For now i'm going back to pidgin, heh


As far as I know the devs consider that a feature, not a bug. I've also switched back to Pidgin. I can't believe they want to control my fµcking status.

---

### Post by grafted_scion on 2010-01-23
Just leave the cursor in the statusfield like you where about to edit "away" it will stay that way until you remove the cursor from the statusfield.

---

### Post by brownknight on 2010-05-09
I am also staying with pidgin until this "status" option is fixed.

---

### Post by Topper4125 on 2010-08-31
> **neverland888 said:**
> my final fix,

apt-get remove empathy
apt-get install pidgin

couldn't sort this status thing and msn file transfer is unsupported, empathy is just not good enough to replace pidgin.

After spending the better part of the day to gain any kind of control at all of empathy, this seems to be the only working option.

This was a fresh install of Ubuntu, and I couldn't get empathy to change my status at all on any service I use (Yahoo, MSN, Facebook, IRC).

---

### Post by bama_boy on 2012-02-05
It is 2012 and Empathy still does not have option to rememer status after restart. It is ridiculous. I'm using Empathy at home and thinking of changing it to Pidgin. :(
Empathy is too simple and user-friendly, less settings more Windows-like.

---

