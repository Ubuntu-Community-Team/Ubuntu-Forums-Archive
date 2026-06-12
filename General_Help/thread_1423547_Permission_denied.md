---
title: "Permission denied"
date: 2010-03-06
forum: General Help
---

### Post by crimlaw on 2010-03-06
I am attempting to move files from my sub folders under file system -> Home to file system -> usr -> (whatever file), but it says I do not have permission.  It give me an error, and when I click on more details, it says permission denied. 

I am the only person who uses this laptop and should have full administrative powers.  How do I get permission?

---

### Post by d3v1150m471c on 2010-03-06
You are trying to move files into your root filing system. You do have permission when elevate to root privileges.
```

gksudo nautilus

```
Use with caution.

---

### Post by crimlaw on 2010-03-07
Thanks for the quick response yesterday.  I thought it would be an easy box to check, or I had to go enter my password somewhere.  I will just continue to create new folders on my Home drive for new things.  I don't want to get into anything that might be dangerous in the terminal, I have VERY little knowledge of its workings still.

---

### Post by Swagman on 2010-03-07
> **crimlaw said:**
> Thanks for the quick response yesterday.  I thought it would be an easy box to check, or I had to go enter my password somewhere.  I will just continue to create new folders on my Home drive for new things.  I don't want to get into anything that might be dangerous in the terminal, I have VERY little knowledge of its workings still.

You don't have to go into the terminal to run that command, just press left alt + F2  and enter gksudo nautilus.

You will be prompted for your password and then the file manager "Nautilus" opens up.

As the previous poster stated.... **"Use With Care"**.
If your not moving stuff that's already there about... Just copying your stuff into.. wherever.  you will be alright.

But if in doubt.. leave the bugger alone !!

:-)

---

