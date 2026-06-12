---
title: "yahoo mail problem ubuntu 9.10 firefox 3.5.8"
date: 2010-04-03
forum: General Help
---

### Post by gja on 2010-04-03
Since this week I have problems accessing my yahoo mail messages.
Lauchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/551578](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/551578)

Does this affect all yahoo mail users or just some?
Any ideas on how to fix it or work around the issue?

Any help is greatly appreciated.

---

### Post by gja on 2010-04-03
No-one experiencing the same issue?

---

### Post by bark50 on 2010-04-03
I have Ubuntu 9.10, Firefox 3.5.8, and 3 Yahoo email accounts which I have no difficulty accessing.  Sorry, but I'm no help!

---

### Post by dcstar on 2010-04-03
> **gja said:**
> No-one experiencing the same issue?

Rename your .mozilla folder so a fresh profile is created and check it again.

Chances are there is only a problem with your installation.

---

### Post by gja on 2010-04-04
Thanks for your reactions.

Earlier I have already tried removing all my cookies. No luck.
I just tried renaming the .mozilla. No luck either.

I even tried downloading Google Chrome, and the same issue pops up there.

Other ideas?

---

### Post by Nisal on 2010-04-04
it should be a problem with cookies but even u tried chrome hmm that can't be anyway it working fine with me

---

### Post by gja on 2010-04-04
Tried removing firefox using Synaptic.
Firefox shortcut still working?!

Then removed Ubufox and firefox gnome support.
Firefox gone!

The removed .mozilla.

Reinstalled ubufox + FF gnome support.
No Luck. (sigh)

Tried installing the UserAgent Switcher to present firefox as IE8. 
Even worse. Won't open Yahoo mail.

Any other ideas?
I'm about to reinstall my entire pc, but if that won't work either...

---

### Post by _khAttAm_ on 2010-04-04
^try with live CD, other OS.. etc first.. 

Even before that, try using a Proxy (find a HTTP proxy that works for you from here: [http://www.samair.ru/proxy/type-01.htm](http://www.samair.ru/proxy/type-01.htm)) and see how it goes...

---

### Post by gja on 2010-04-04
Just tried an old 8.10 live cd with Firefox 3.03.
No problem with yahoo mail there!

From all previous posts I can only conclude that I have a wrong system setting somewhere?

---

### Post by Anita_Tsai on 2010-04-04
> **dcstar said:**
> Rename your .mozilla folder so a fresh profile is created and check it again.

Chances are there is only a problem with your installation.

I also have the problem,well,I final solve it as the guy said.Thank u !

---

### Post by gja on 2010-04-04
I upgraded to 10.04, the problem just follows the upgrade.

Same problem.

---

### Post by gja on 2010-04-04
Did a fresh install of 9.10.
Didnt update yet so im on Firefox 3.5.3

I can now open my Yahoo messages, but the first attempt does not always succeed.

If I empty my spambox and check a few minutes later, the spam is back again?

If I delete emails, they show up again a few minutes later.

If I sign out, it hangs.

Something is fishy, but what...

---

### Post by gja on 2010-04-04
So I updated the fresh 9.10 install.
This updates Firefox 3.5.3 to Firefox 3.5.8 

Now I have the same issues all over again.

Full circle.

---

### Post by gja on 2010-04-05
Downloaded Epiphany through Synaptic.

When opening Yahoo mail in Epiphany, it forces the classic view.

It Just Works.
Firefox Does Not.

Something needs fixing.

---

### Post by bark50 on 2010-04-05
Gja, I have absolutely no idea what's going on with your Yahoo email and Firefox, but if you ever find a solution -- and if the solution is something that can be understood by a complete idiot like me, please post it here.  You have an intriguing problem.

---

### Post by gja on 2010-04-06
My facebook and yahoo mail issues I had all weekend have also magically disappeared now.

What the...?!

Also look in this thread:
[http://ubuntuforums.org/showthread.php?t=1446100&page=2](http://ubuntuforums.org/showthread.php?t=1446100&page=2)

---

### Post by lavinog on 2010-05-29
> **gja said:**
> 
When opening Yahoo mail in Epiphany, it forces the classic view.


I figured out how to use epiphany with the new yahoo mail:

When you try and switch to the new mode it gives you a message that your browser is unsupported, and forces you to use the classic mode.
The url should look like this:
[http://us.mg1.mail.yahoo.com/dc/system_requirements?browser=blocked](http://us.mg1.mail.yahoo.com/dc/system_requirements?browser=blocked)

Change the browser=blocked to browser=unsupported and it should give you a warning about your browser not being officially supported, but it should allow you to continue anyway.

I haven't messed with it much, but everything seems to work just fine.

---

### Post by Putto on 2010-08-24
Hi all,

I had the same problem too and tried the various solutions on this and other forums - cookies, .mozilla folder, updates etc.. All no luck.

What worked was to reject images loading from the suspect servers (in my case, s.yimg.com). While the login page is loading, hit the padlock in the lower right corner of the window. The dialog box will list all of the items that Firefox is trying to obtain. Select the one causing the problem, tick the box for "Block images from <server>", close, refresh and ta-da. 

Hope that helps. Cheerio.

---

