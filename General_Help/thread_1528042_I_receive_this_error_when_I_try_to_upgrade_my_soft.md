---
title: "I receive this error when I try to upgrade my software via Update Manager."
date: 2010-07-10
forum: General Help
---

### Post by Brii on 2010-07-10
```
E: empathy-common: subprocess installed post-installation script returned error exit status 2
E: empathy: dependency problems - leaving unconfigured
E: nautilus-sendto-empathy: dependency problems - leaving unconfigured
```

Has anyone come across this before? Any help would be greatly appreciated :D

---

### Post by robsoles on 2010-07-10
Can you remember doing anything to empathy?

---

### Post by Brii on 2010-07-10
> **robsoles said:**
> Can you remember doing anything to empathy?

No, I've never touched it. This all started once when I was installing updates on my laptop and then it ran out of battery and died right when the updates were installing.

---

### Post by robsoles on 2010-07-10
ah. That explains plenty.


If it isn't too much of a mess then removing it and re-installing it has a chance of fixing it for you -

Open "Ubuntu Software Centre" and type empathy into the search box, "Empathy" should become first result - in 10.04 LTS it has 'Remove' as button to right end while selected, in earlier versions you had to take 'more info' to get to remove or install a package - click 'Remove'.

Wait for it to finish and then just click 'Install', wait for that to finish, close software centre, try updating - post back your new error message if any and we'll tackle it some more from there if need be.

---

### Post by Brii on 2010-07-11
> **robsoles said:**
> ah. That explains plenty.


If it isn't too much of a mess then removing it and re-installing it has a chance of fixing it for you -

Open "Ubuntu Software Centre" and type empathy into the search box, "Empathy" should become first result - in 10.04 LTS it has 'Remove' as button to right end while selected, in earlier versions you had to take 'more info' to get to remove or install a package - click 'Remove'.

Wait for it to finish and then just click 'Install', wait for that to finish, close software centre, try updating - post back your new error message if any and we'll tackle it some more from there if need be.

Thanks for the help. I followed your instructions to uninstall Empathy from Ubuntu Software Center only to be met with an error there. So I went to Synaptic Package Manager and tried it there and it almost worked. I was able to uninstall all of the Empathy related packages  except for Empathy-common. I get this error when I attempt to remove it. And update still isn't working.


```
E: empathy-common: subprocess installed post-removal script returned error exit status 2

```

Thoughts?

---

### Post by robsoles on 2010-07-11
poop.

Please open terminal and type in

```
sudo aptitude -f -v install empathy
```

Then copy the output that comes from that into your next post unless you are absolutely certain that it has fixed the problem - if it can't fix the problem then the output of the command above should help us move on with your problem.

---

### Post by Brii on 2010-07-11
> **robsoles said:**
> poop.

Please open terminal and type in

```
sudo aptitude -f -v install empathy
```

Then copy the output that comes from that into your next post unless you are absolutely certain that it has fixed the problem - if it can't fix the problem then the output of the command above should help us move on with your problem.

hehe 'poop.'

Nice, the updates installed without the error. =D 
Thanks, I have to memorize that code haha.

---

