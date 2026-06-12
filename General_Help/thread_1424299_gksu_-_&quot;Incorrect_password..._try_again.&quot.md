---
title: "gksu - &quot;Incorrect password... try again.&quot;"
date: 2010-03-07
forum: General Help
---

### Post by marshmallow1304 on 2010-03-07
I think this started just lately.  gksu refuses to authenticate me; it just tells me my password is incorrect.  sudo and gksudo both work fine.  This is no problem if what I want is in the menu, because I can just change gksu to gksudo, but some functions, like the Check button in Update Manager, don't work.

---

### Post by sisco311 on 2010-03-07
Weird... gksudo is just a symbolic link to gksu. 

Run gksu-properties and make sure that the *Authentication mode* is set to *sudo*.

---

### Post by marshmallow1304 on 2010-03-07
> **sisco311 said:**
> Run gksu-properties and make sure that the *Authentication mode* is set to *sudo*.

That was it.  It was set to *su*.  Thanks.

---

### Post by oaliaso on 2010-11-07
just encountered this issue as well.
the above solution worked for me. thanks sisco311

I had trouble figuring out that the issue stemmed from a difference in gksu vs gksudo. 

Thank god I know how to use google lol

---

### Post by Jose Catre-Vandis on 2011-05-08
Thanks this helped me too :)

---

### Post by frosty555 on 2011-06-19
Thanks sisco311! I was having exactly the same problem.

I installed Ubuntu Server 11.04 32-bit on my computer, and then I installed xubuntu-desktop ontop of that, and once I had a nice XFCE desktop to play with I discovered that most programs I attempted to run from the System->Administration menu, such as the Synaptic Package Manager, they would pop up asking me for my administrator password.

And no matter how carefully I typed the password, it was always wrong.

After examining the launcher, I discovered that it was using "gksu" to authenticate, and gksu didn't work even though gksudo worked just fine. Following your instructions I ran gksu-properties and indeed the authentication mode was "su". Changed to to "sudo" and voila! No more problem!

I've been banging my head on the wall for days on this one, I was about to toss the entire XFCE installation.

Thank you!

---

### Post by pmorrone on 2011-08-07
> **frosty555 said:**
> Thanks sisco311! I was having exactly the same problem.

I installed Ubuntu Server 11.04 32-bit on my computer, and then I installed xubuntu-desktop ontop of that, and once I had a nice XFCE desktop to play with I discovered that most programs I attempted to run from the System->Administration menu, such as the Synaptic Package Manager, they would pop up asking me for my administrator password.

And no matter how carefully I typed the password, it was always wrong.

After examining the launcher, I discovered that it was using "gksu" to authenticate, and gksu didn't work even though gksudo worked just fine. Following your instructions I ran gksu-properties and indeed the authentication mode was "su". Changed to to "sudo" and voila! No more problem!

I've been banging my head on the wall for days on this one, I was about to toss the entire XFCE installation.

Thank you!


All, 

Thanks for posting this solution.  I ran across the same problem recently, googled forums for solutions, and came over this thread.  It worked for me as well.

Thanks much.

---

### Post by aesa1983 on 2011-08-17
hi i just tried the gksu with the 11.7 drivers and wow to my surprise i am stuck cus this is all the help i have been able to find on this issue but i do not get any errors nor in the install or anything else. any help would be greatlly apreciated and also i am kind of a nub but not i have been doing this on and of for like 7 years but never as steady as lately and i would greatly appreciate the help i don't know what kind of info i need to provide.

---

