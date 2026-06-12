---
title: "Firefox crashing"
date: 2010-12-06
forum: General Help
---

### Post by dln9 on 2010-12-06
I just upgraded to Lucid 10.04 - a clean installation on a new machine.  

I am running Firefox 3.6.12 - it came with Ubuntu.  

For profile 1, all is fine.  

For profile 2, Firefox crashes *all the time*.  Meaning - Any web site we navigate to, it crashes while loading the web page.  If we click on "Add-ons", it crashes.  If we click on "Preferences", it crashes.  

How do I go about fixing this, short of a complete reinstallation of Lucid, which I would really want to avoid doing, since I have a lot of settings I'd have to redo.  

Thanks.

---

### Post by karthick87 on 2010-12-06
Try creating a new profile

```
firefox profilemanager
```

---

### Post by dln9 on 2010-12-06
Thanks.  A couple followup questions.  

Are you saying:  

1)  That I should create a new Firefox profile within Ubuntu Profile #2, in addition to the existing Firefox profile within Ubuntu Profile #2?  

2)  That I should create a new Firefox profile within Ubuntu Profile #2, and delete the existing Firefox profile withing Ubuntu Profile #2?  

3)  If your meaning is #2 above, does the Firefox profile manager allow for the deletion of an existing Firefox profile?  (I've never used the Firefox profile manager before.)  

4)  If you meaning is #1 above, why would I keep the existing Firefox profile, and how would the user of Ubuntu Profile #2 indicate to Firefox which Firefox profile to use?  

5)  Would any of the options above that involve changing the Firefox profile involve losing the already installed Firefox add-ons?  

Thanks in advance.

---

### Post by dln9 on 2010-12-07
I still can't get Firefox to work for Ubuntu User #2.  

It works fine for Ubuntu User #1.  But, for Ubuntu User #2, it crashes whenever I try to do anything.  

I tried deleting Ubuntu User #2's Firefox profile (including files), and then deleting Ubuntu User #2 and the related home folder, and then setting up a new Ubuntu User.  But that new Ubuntu User has the same problem with Firefox crashing, while Ubuntu User #1 continues to have no problem using Firefox.

---

### Post by John James on 2010-12-23
i'm having exactly the same problems!

I changed Dansguardian (downgraded to an earlier version) and I'm wondering if this was connected at all.

I tried uninstalling the 2nd user stuff and think that it is very strange that suddenly FF has this problem.

I can't access the preferences window or add-ons! Haven't yet tried to create a new profile as it has been said that this didn't solve the problem.

I did delete the profile 2 and when I restarted FF it created a new one (I think).

sorry not much help.

---

### Post by John James on 2010-12-23
Just in case anyone was wondering.

I installed "edubuntu-menueditor" as it was the only thing about profile manager from synaptic. But this wasn't really useful. :icon_frown:

Then I thought it might be an add-on problem.

Anything I added recently which I had forgotten about? Yep. I installed the moonlight add-on for FF. so took that off and what do you know... all back to normal for the 2nd user profile.

So if anyone has a similiar problem I would guess that it might be an add-on in the 1st users firefox add-ons. maybe not moonlight but another. Maybe check them one by one.

Hope this helps someone

---

### Post by dln9 on 2010-12-23
I also have moonlight (aka Silverlight plug in) installed.  I'll bet that's the problem.  

I won't test that, though.  Everything is working, I just don't want to mess with it anymore.  I'll just tell people who ask that Firefox won't work properly for some reason.  

In the meantime I installed Chromium for user #2 (the wife) to use.  It works just fine.

---

### Post by a__l__a__n on 2011-01-04
Firefox is crashing this morning after applying updates. (I don't know whether it would have worked before applying updates...)  When I attempt to start it from the command line, it immediately returns with "Killed".  

Any ideas?

Btw, I uninstalled and reinstalled to see if that would fix it.  It didn't.

This is under ubuntu 10.04 64bit

Ok, a second reboot fixed it.  Sorry for the spam....

---

