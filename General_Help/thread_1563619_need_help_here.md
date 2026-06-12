---
title: "need help here"
date: 2010-08-29
forum: General Help
---

### Post by k_umalakshmi on 2010-08-29
I installed new version of ubuntu yesterday. Now some softwares in my windows hav gone missing...does any1 know wot has gone wrong???

---

### Post by k_umalakshmi on 2010-08-29
I hav ubuntu & windows vista working on d same system....

---

### Post by Smart Viking on 2010-08-29
Can you boot into windows and ubuntu?

Most likely you have screwed something up while partitioning.

What kind of software is missing?

---

### Post by k_umalakshmi on 2010-08-31
> **Smart Viking said:**
> Can you boot into windows and ubuntu?

Most likely you have screwed something up while partitioning.

What kind of software is missing?

Actually this new version of Ubuntu 10.04 has a feature in which v can install it inside windows. I just did tht. my windows defender n few other thing r not working now....

---

### Post by k_umalakshmi on 2010-08-31
> **Smart Viking said:**
> Can you boot into windows and ubuntu?

Most likely you have screwed something up while partitioning.

What kind of software is missing?

Actually this new version of Ubuntu 10.04 has a feature in which v can install it inside windows. I just did tht. my windows defender n few other thing r not working now....

I can boot into both without any prob

---

### Post by inso_741 on 2010-08-31
I doubt it's got anything to do with installing ubuntu...
what error msg's do you get when you try to open the said apps?

---

### Post by coffeecat on 2010-08-31
> **k_umalakshmi said:**
> Actually this new version of Ubuntu 10.04 has a feature in which v can install it inside windows.

That sounds like Wubi which has been around for some time now. All your Ubuntu system goes into its own folder, C:\ubuntu. Apart from its own registry entry, it doesn't affect anything else on your Windows C: drive, so something else must have happened for your Windows apps to go AWOL. 

What do you mean, your apps have gone missing? Are they missing from the apps menu? Are they in the menu, but fail to start? Are they listed in the Remove apps utility in the Control Panel?

---

### Post by k_umalakshmi on 2010-09-01
> **coffeecat said:**
> That sounds like Wubi which has been around for some time now. All your Ubuntu system goes into its own folder, C:\ubuntu. Apart from its own registry entry, it doesn't affect anything else on your Windows C: drive, so something else must have happened for your Windows apps to go AWOL. 

What do you mean, your apps have gone missing? Are they missing from the apps menu? Are they in the menu, but fail to start? Are they listed in the Remove apps utility in the Control Panel?



By apps i meant my windows defender, paint, wordpad n many other thing tht r already present went v install windows.
Do u think i shud reload windows again???

---

### Post by k_umalakshmi on 2010-09-01
> **inso_741 said:**
> I doubt it's got anything to do with installing ubuntu...
what error msg's do you get when you try to open the said apps?

it's says Cannot load since it cannot find tht program. windows defender starts while v boot d system..

---

### Post by coffeecat on 2010-09-01
> **k_umalakshmi said:**
> By apps i meant my windows defender, paint, wordpad n many other thing tht r already present went v install windows.
Do u think i shud reload windows again???

Those are apps but, yes, they do come with the OS rather than having to be installed later. Perhaps the Windows registry got corrupted somehow. That might explain why Windows can't find them. Before you think of reinstalling Windows, try restoring to a restore point before you installed Ubuntu in Wubi. That will get you a functioning registry again, but you will lose Ubuntu because the older registry won't have an entry for it. Then you'll have to reinstall Ubuntu again.

Or see if anyone else has any better ideas.

---

### Post by inso_741 on 2010-09-01
In windows open RUN(press crtl+r) type in 'control appwiz.cpl,,2' without the quotes and see if you can reinstall those missing apps

---

### Post by k_umalakshmi on 2010-09-01
> **coffeecat said:**
> Those are apps but, yes, they do come with the OS rather than having to be installed later. Perhaps the Windows registry got corrupted somehow. That might explain why Windows can't find them. Before you think of reinstalling Windows, try restoring to a restore point before you installed Ubuntu in Wubi. That will get you a functioning registry again, but you will lose Ubuntu because the older registry won't have an entry for it. Then you'll have to reinstall Ubuntu again.

Or see if anyone else has any better ideas.

I did try restoring...but it din help...nothing actually happened. Everything is still d same

---

### Post by k_umalakshmi on 2010-09-01
> **inso_741 said:**
> In windows open RUN(press crtl+r) type in 'control appwiz.cpl,,2' without the quotes and see if you can reinstall those missing apps

ya...i did tht now...it's not showing any of those things in it

---

### Post by inso_741 on 2010-09-01
your windows os is probably infected...and I can assure you that installing ubuntu has nothing to do with it...

---

### Post by k_umalakshmi on 2010-09-02
oh....so der's no other way but 2 reinstall my windows OS? :(

---

### Post by inso_741 on 2010-09-02
you can clean it with an antivirus and then repair it using windows installation cd.....although a complete reinstall will be faster

---

### Post by k_umalakshmi on 2010-09-02
how do i repair it???
i don know much abt these things.

---

### Post by inso_741 on 2010-09-02
just boot the installation cd and it'll offer you a repair option...for more details please see windows repair documentation...just google it

---

### Post by k_umalakshmi on 2010-09-02
Thank u......

N how do i add networks in ubuntu through terminal???
I hav a few wireless networks here but i can't connect it jus through those networks it shows directly

---

### Post by coffeecat on 2010-09-02
> **k_umalakshmi said:**
> N how do i add networks in ubuntu through terminal???
I hav a few wireless networks here but i can't connect it jus through those networks it shows directly

New problem = it would be better if you started a new thread. But a hint first. You really don't want to be adding wireless networks with the terminal. There's a perfectly good GUI panel app near the top-right of the screen called Network Manager for that. Why do you want to use the terminal? If you are having trouble connecting with Network Manager you need to do some troubleshooting first that may involve the terminal, but just using the terminal to try to connect isn't the way to go.

Post details of what the problem is **in your new thread**. You need to give adequate information.

---

### Post by inso_741 on 2010-09-02
> **coffeecat said:**
> new problem = it would be better if you started a new thread. But a hint first. You really don't want to be adding wireless networks with the terminal. There's a perfectly good gui panel app near the top-right of the screen called network manager for that. Why do you want to use the terminal? If you are having trouble connecting with network manager you need to do some troubleshooting first that may involve the terminal, but just using the terminal to try to connect isn't the way to go.

Post details of what the problem is **in your new thread**. You need to give adequate information.

+1

---

### Post by k_umalakshmi on 2010-09-03
Ohk...no prb...thanx a lot guys

---

