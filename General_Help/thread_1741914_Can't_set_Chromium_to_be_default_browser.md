---
title: "Can't set Chromium to be default browser?"
date: 2011-04-28
forum: General Help
---

### Post by Roasted on 2011-04-28
I have Chromium on 11.04 and I can't set it to be default. If I go into preferences and select it, nothing happens. If I open Chromium, it asks every single time if I want it to be my default browser. Regardless of what I say, it asks me each time.

Any ideas?

---

### Post by 1Michael1 on 2011-04-28
I've got the same problem on my laptop, odd enough it works on my desktop for some reason.

---

### Post by hwttdz on 2011-04-28
If you try setting it on the command line what sort of errors if any do you get:

sudo update-alternatives –config x-www-browser

select chromium and save. 

It also looks like the brute force way would be to change the link x-www-browser in /etc/alternatives to point to your program of choice (in this case chromium).  Required disclaimer: using sudo is dangerous, you can mess up your system, be careful "this gun is loaded" and "this might void your warranty".

---

### Post by Roasted on 2011-04-28
This worked, but in the preferences menu it still says Chromium is not my default. However, I don't get prompted constantly about whether or not I want Chromium to be my default each time I open it.

1Michael1 - Did you do a fresh install of 11.04 or did you upgrade from a previous version of Ubuntu?

Does a bug exist, or should I file one?

---

### Post by tomgnu on 2011-04-28
> **Roasted said:**
> I have Chromium on 11.04 and I can't set it to be default. If I go into preferences and select it, nothing happens. If I open Chromium, it asks every single time if I want it to be my default browser. Regardless of what I say, it asks me each time.

Any ideas?

Select applications then system settings then preferred applications then change web browser to chromium.

---

### Post by KegHead on 2011-04-28
Hi!

Maybe remove and reinstall?

KegHead

---

### Post by Roasted on 2011-04-28
> **tomgnu said:**
> Select applications then system settings then preferred applications then change web browser to chromium.

Even then, in the Chromium preferences it won't register as being default. Hmm...

---

### Post by KegHead on 2011-04-28
Hi!

I'm looking at chromium now.....there is a wrench..opened it...preferences...select chromium.

Hmm.

KegHead

---

### Post by zalberico on 2011-04-28
I'm having the same issue as well (in gnome and unity).  Keghead, you're not paying attention to what the problem is.

---

### Post by fanless on 2011-04-29
I can't set Chromium as my default browser, either, on a clean install of 11.04. This is what I get when I try to set the default browser in terminal...


fanless@SR2150NX:~$ sudo update-alternatives &#8211;config x-www-browser
update-alternatives: error: unknown argument `&#8211;config'

I don't actually know what I am doing, so I may be doing it totally wrong.

> **hwttdz said:**
> If you try setting it on the command line what sort of errors if any do you get:

sudo update-alternatives &#8211;config x-www-browser

select chromium and save. 

It also looks like the brute force way would be to change the link x-www-browser in /etc/alternatives to point to your program of choice (in this case chromium).  Required disclaimer: using sudo is dangerous, you can mess up your system, be careful "this gun is loaded" and "this might void your warranty".

---

### Post by Blasphemist on 2011-04-29
Chromium is my preferred browser and I don't remember having any trouble setting it to be. In preferred applications it is set as the default and it shows that it is in the chromium preferences.

---

### Post by computingchap on 2011-04-30
I have the same problem. A fresh install of 11.04 desktop 64, and each time I open chromium I press the 'set as default' option but then when I check in settings it says it is not the default. When I press the 'make chromium my default browser' button nothing happens. I also had this problem when I created a vm at work 2 days ago, so it is definitely a bug.

---

### Post by hobbbid hobbin on 2011-04-30
> **fanless said:**
> I can't set Chromium as my default browser, either, on a clean install of 11.04. This is what I get when I try to set the default browser in terminal...


fanless@SR2150NX:~$ sudo update-alternatives –config x-www-browser
update-alternatives: error: unknown argument `–config'

I don't actually know what I am doing, so I may be doing it totally wrong.

It should be "sudo update-alternatives --config x-www-browser" That's why your getting an error. Although changing it like this doesn't work anyway. If you run "preferred applications" you can change it so chromium is your default browser. However chromium still doesn't think it's the default browser and will ask you every time you launch it. this new system's confusing :confused:

---

### Post by Blasphemist on 2011-04-30
> **hobbbid hobbin said:**
> It should be "sudo update-alternatives --config x-www-browser" That's why your getting an error. Although changing it like this doesn't work anyway. If you run "preferred applications" you can change it so chromium is your default browser. However chromium still doesn't think it's the default browser and will ask you every time you launch it. this new system's confusing :confused:

So you go into chromium tools, preferences and tell it is the default browser as well as telling ubuntu through preferred applications. It worked for me.

---

### Post by notoriousdbp on 2011-04-30
I had the same problem.  Solved it by going into preferred applications and setting Chromium as my preferred app.  Didn't fully kick in until after a reboot though.

---

### Post by computingchap on 2011-05-01
Thanks notoriousdbp.

Going to preferred applications and setting chrome as the preferred web browser, and then after rebooting and opening chrome followed by clicking the 'set as default' option worked.

A good workaround -- but would be nice if Ubuntu guys could get it fixed as it's one of the most common things people do after install...

---

### Post by lamb123 on 2011-05-01
+1 for setting it from "preferred applications"

---

### Post by gtaluvit on 2011-05-03
I had the same problem where it didn't seem to stick until I set it in Preferred Applications. I noticed in startup apps that there's some new thing that does a gconf -> dconf conversion. I'm wondering if Unity wants dconf and Chromium wants gconf and the gconf translation doesn't happen until login. Just a thought.

---

### Post by leosrain on 2011-05-31
> **tomgnu said:**
> Select applications then system settings then preferred applications then change web browser to chromium.

This solution worked perfectly for me. Chromium is finally my default browser. 

Thanks!

Sean

---

### Post by uRock on 2011-05-31
I think AppArmor may the reason that setting Chromium as the default browser(when the change is attempted within the browser's settings) doesn't change the system settings. Though it may be a minor annoyance, it is nice to see security applications doing their jobs. :p

---

### Post by Roasted on 2011-05-31
I just did a fresh install of Ubuntu 11.04 after I redid my hard drive structure (wanted to incorporate software raid 1 for my home directory). I had no issues now making it the default browser. I assume the bug has been fixed.

---

