---
title: "Broke my Jaunty install."
date: 2009-10-04
forum: General Help
---

### Post by Grock1722 on 2009-10-04
Hello All-

Was attempting to uninstall evolution vis synaptic, and apparently got a little carried away.  My ubuntu now boots fine until the part where the login screen is supposed to be displayed, and instead a black screen with the cursor visible is present.  I can access the terminal, but i dont know how or what to do from here.  Would someone please be willing to give me a hand?

thanks so much in advance,
G

---

### Post by snowpine on 2009-10-04
Try this:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then reboot... let me know if works. :)

---

### Post by Portable_Jim on 2009-10-04
> **snowpine said:**
> Try this:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```Then reboot... let me know if works. :)
That should work.

---

### Post by a-web on 2009-10-05
I have a similar problem...  does this fix require an internet connection?  It does not fix my problem.

---

### Post by snowpine on 2009-10-05
> **a-web said:**
> I have a similar problem...  does this fix require an internet connection?  It does not fix my problem.

Hi A-web, yes, it does require an internet connection... also you said your problem is "similar" which means it is not exactly the same... :) ... you should provide more details about your specific problem either here or in a separate thread.

---

### Post by undecim on 2009-10-05
If you still have the packages in your cache (which as far as I know, they aren't ever automatically deleted), you shouldn't need an internet connection.

---

### Post by a-web on 2009-10-05
Thanks.  I did post this elsewhere... but I was getting anxious and looking around at other posts.

[http://ubuntuforums.org/showthread.php?t=1283304](http://ubuntuforums.org/showthread.php?t=1283304)

---

