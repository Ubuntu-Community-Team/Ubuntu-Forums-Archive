---
title: "Ubuntuzilla Thunderbird updated now won't start"
date: 2010-07-09
forum: General Help
---

### Post by jamesisin on 2010-07-09
I just got back from holiday to see that Ubuntuzilla had an update for Thunderbird available.  I ran the update and now Thunderbird won't start.  The cursor spins and than stops.  I don't see Tb appearing in the Sys Mon either during the cursor spin or afterwards.  I tried reinstalling through Synaptic but saw no change in behavior.

Little help?

---

### Post by cariboo on 2010-07-09
Try starting Thunderbird in a terminal, and paste the output in your next post.

---

### Post by jamesisin on 2010-07-09
Thanks, but I'm afraid that's not looking very hopeful either:

```
~$ thunderbird
~$ thunderbird %u
~$ sudo thunderbird %u
[sudo] password for xxxxxxxx: 
~$ 

```

As you can see I tried a few variations on the theme.  Nada.

---

### Post by jamesisin on 2010-07-10
Any other ideas?  Anybody?

---

### Post by nanotube on 2010-07-11
> **jamesisin said:**
> Any other ideas?  Anybody?

Probably you are runinng into this:
[http://ubuntuforums.org/showpost.php?p=9538228&postcount=25](http://ubuntuforums.org/showpost.php?p=9538228&postcount=25)

(and for now we're just gonna hope that your running thunderbird with sudo didn't mess up the ownership of any files in your tb profile... :) )

---

### Post by jamesisin on 2010-07-13
Thanks.  That did the trick.

(I had trouble with the first command but just used Nautilus to make a copy of the folder onto my Desktop.)

---

### Post by nanotube on 2010-07-13
cool. :)

btw, for the future, if you have an ubuntuzilla-related question, i'm more likely to see it if you post in the ubuntuzilla subforum. :)

---

