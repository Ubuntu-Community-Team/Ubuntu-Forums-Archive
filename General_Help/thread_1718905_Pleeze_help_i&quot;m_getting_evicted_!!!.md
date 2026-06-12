---
title: "Pleeze help i&quot;m getting evicted !!!"
date: 2011-04-01
forum: General Help
---

### Post by number1songwriter on 2011-04-01
**Says I'm selecting to work off line, but I'm not.**             
                                                                When I was logging off he Log-off box highlighted 'suspended' shut down without my selecting it. I was going to log-off as usual, but it shut down suddenly. Rebooting, when I try to get on line it says I have selected 'work off-line'. I did not select that, and even after I go under 'file' and uncheck 'work off line' it does not allow me to get on line? When I pull up another browser page, again, it says I selected to 'work off-line' when I did not, but it seems to make no difference. Whether I 'uncheck' the 'work off-line' under 'file' or not it always says 'work off-line' has been selected, and logging back in makes no difference?

Pleeze help... I'm about to get evicted if I can't sell some stuff I have recorded ads on my Ubunto pages that I need to get 'online' with 
Pleeze?

---

### Post by crispy_420 on 2011-04-01
Quick and dirty solution: create a new user to get what you need fast and worry about the why's later. That is my opinion. Worst case scenario, since we are doing triage at this point, create said new user via single user mode (recovery option at boot).

This sounds too important for the why's and how's right now. You can resolve those later after you sort your current issue out.

---

### Post by Don Barzini on 2011-04-01
> **number1songwriter said:**
> Rebooting, when I try to get on line it says I have selected 'work off-line'. I did not select that, and even after I go under 'file' and uncheck 'work off line' it does not allow me to get on line? When I pull up another browser page, again, it says I selected to 'work off-line' when I did not, but it seems to make no difference. Whether I 'uncheck' the 'work off-line' under 'file' or not it always says 'work off-line' has been selected, and logging back in makes no difference?

Do you have any network connectivity? Have you tried opening a terminal window and pinging a server on the internet?

In a terminal window try...

```
ping -c 5 8.8.8.8
```

By "browser" are you talking about the Firefox browser?

If the above command works.... then just temporarily rename your Firefox folder. It is a hidden folder and by renaming it, a new profile will be created on Firefox startup.

It is in your home directory and is named **.mozilla**. You can do this in a terminal window....

```
mv .mozilla .old-mozilla
```

Then re-open Firefox.

Give it a try.

---

