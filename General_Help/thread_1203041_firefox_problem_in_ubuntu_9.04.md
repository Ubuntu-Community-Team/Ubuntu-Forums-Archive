---
title: "firefox problem in ubuntu 9.04"
date: 2009-07-02
forum: General Help
---

### Post by kuldeepsidhu on 2009-07-02
i hv updated my ubuntu 9.04 to the latest updates...it also includes firefox 3.0.11
previous i hv firefox 3.0.9.everything works fine in it..

but in new version facebook does not load properly..it hangs on waiting from facebook.com so many sites hangs up..llike ubuntuforums.com
 i also intalled latest veriosn 3.5, but the problem continues..

what should i do to solve the problem..??
how can i degrade the firefox to 3.0.9?

how toi restore ubuntu to previous state???

---

### Post by Jebtrix on 2009-07-02
Try clearing your profile and start fresh. Just rename ~/.mozilla to something else and restart firefox

---

### Post by lovinglinux on 2009-07-03
> **Jebtrix said:**
> Try clearing your profile and start fresh. Just rename ~/.mozilla to something else and restart firefox

See note below:

> **[color=#CC0000]Note:[/color]**

I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications stores their profiles (Thunderbird, Sunbird, etc), so removing this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla. Nevertheless, removing an entire profile is usually unnecessary and must be avoided, since just a few profile files are the usual culprits, otherwise you will remove all Firefox settings, extensions, themes, bookmarks and so on.

Unless you don't care about your Firefox settings, go ahead and rename or move ~/.mozilla/firefox. This might solve your problem. Nevertheless, I recommend reading the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). There are several tips there about improving Firefox performance, preventing situations like this and fixing common problems.

When you say sites hang up do you mean they do not load the page or Firefox becomes grey and you have to close it? These are very different problems and have different solutions.

BTW, if you since you already have installed Firefox 3.5, I would stick with it, since it is much faster (loading and responsiveness) than 3.0.11. Check my benchmarks on that thread for comparison. Keep in mind that Firefox 3.5 profiles are stored at ~/.mozilla/firefox-3.5.

---

### Post by kuldeepsidhu on 2009-07-03
firefox doesnot load the page....so many sites stops while loading the page...

---

### Post by lovinglinux on 2009-07-03
> **kuldeepsidhu said:**
> firefox doesnot load the page....so many sites stops while loading the page...

Disable ipv6 on Firefox Preferences, by setting the *network.dns.disableIPv6* preference to true.

1. Type **about:config** in the address bar, press Enter.
2. Find **network.dns.disableIPv6** in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

---

### Post by kuldeepsidhu on 2009-07-05
i have done it..but same thing happens...even new thread in ubuntuforums.org is not submitted from the firefox..the same screen continues loading.....

---

### Post by lovinglinux on 2009-07-05
> **kuldeepsidhu said:**
> i have done it..but same thing happens...even new thread in ubuntuforums.org is not submitted from the firefox..the same screen continues loading.....

Open Firefox Profile manager with this command:

```
firefox -P
```

Then create a new profile and launch it. Check if the same problem occurs.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by lovinglinux on 2009-07-05
Can you browse those sites with other browser?

---

### Post by kuldeepsidhu on 2009-07-05
yes i can browse those sites in windows..and opera in ubuntu..

---

### Post by lovinglinux on 2009-07-05
> **kuldeepsidhu said:**
> yes i can browse those sites in windows..and opera in ubuntu..

Just an update. 

I'm experiencing the same problem here today. I think is the Ubuntu forums site. It has been painfully slow today. Sometimes when I click to send a new post it keeps loading but doesn't change the page. If I launch the thread on another tab the reply is usually already there.

---

### Post by aysiu on 2009-07-05
> Note:

I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications stores their profiles (Thunderbird, Sunbird, etc), so removing this folder will delete their settings too.

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla. Nevertheless, removing an entire profile is usually unnecessary and must be avoided, since just a few profile files are the usual culprits, otherwise you will remove all Firefox settings, extensions, themes, bookmarks and so on. Thunderbird does not store its settings in .mozilla

It stores its settings in either .mozilla-thunderbird or .thunderbird

Renaming or moving ~/.mozilla/firefox isn't good enough, unfortunately. In my .mozilla folder, I have a *firefox* folder and a *firefox-3.1* folder. Maybe others have *firefox-3.5* folders. Better to get a fresh start by renaming or moving the entire .mozilla folder.

If people then wonder (which I have *never* seen happen in the past four years on the forums) where their Sunbird settings have gone, they can always copy that particular Sunbird folder back to the fresh .mozilla folder.

---

### Post by lovinglinux on 2009-07-06
> **aysiu said:**
> Thunderbird does not store its settings in .mozilla

It stores its settings in either .mozilla-thunderbird or .thunderbird

Renaming or moving ~/.mozilla/firefox isn't good enough, unfortunately. In my .mozilla folder, I have a *firefox* folder and a *firefox-3.1* folder. Maybe others have *firefox-3.5* folders. Better to get a fresh start by renaming or moving the entire .mozilla folder.

If people then wonder (which I have *never* seen happen in the past four years on the forums) where their Sunbird settings have gone, they can always copy that particular Sunbird folder back to the fresh .mozilla folder.

I agree, with most of your arguments. I have already removed the Thunderbird reference from my tutorial, but I didn't remember about these posts. Nevertheless, I'm posting these comments everywhere, because a lot of users don't recommend backing up the mozilla folder. They tell other users to just delete it. So, if they are going to delete, is better to delete firefox, isn't it? Additionally, I'm trying to make a point that while, deleting/moving/renaming ~/.mozilla is the easiest solution to several Firefox issues, it is usually unnecessary, because just deleting a couple of profile files might solve the problem.

I do agree with the different versions folder issue, tho.

---

### Post by aysiu on 2009-07-06
Yes, it's never a good idea to delete unless you've already established that the new profile is better.

The nice thing about moving the entire profile is that you don't have to try to figure out which one or two things are wrong with it. If the fresh profile works, you know something was wrong with the old profile, and then you can slowly start adding things back in (bookmarks, add-ons).

I can definitely see merit in your approach, too, though.

---

### Post by lovinglinux on 2009-07-06
> **aysiu said:**
> Yes, it's never a good idea to delete unless you've already established that the new profile is better.

The nice thing about moving the entire profile is that you don't have to try to figure out which one or two things are wrong with it. If the fresh profile works, you know something was wrong with the old profile, and then you can slowly start adding things back in (bookmarks, add-ons).

I can definitely see merit in your approach, too, though.

Yep. I prefer to go directly to the source of the problem. Take for example the complete mess of mozilla backups and Firefox installations that was made on [this thread](http://ubuntuforums.org/showthread.php?t=1197505). The solution was so simple, but I had to go through several additional steps to fix the problem. My instructions there started on post [#49](http://ubuntuforums.org/showpost.php?p=7562759&postcount=49). Nevertheless, I had a good feeling after fixing the mess :)

---

### Post by kuldeepsidhu on 2009-07-06
same problem with me...some sites are not working under ubuntu even in opera..but they work properly in windows..is their any problem with my installation??

---

