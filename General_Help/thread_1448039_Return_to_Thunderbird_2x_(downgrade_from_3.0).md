---
title: "Return to Thunderbird 2x (downgrade from 3.0)"
date: 2010-04-06
forum: General Help
---

### Post by afrodeity on 2010-04-06
Hi everyone,

I am now totally unproductive due to the recent upgrade to Thunderbird 3.0. It is soooooo heavy on resources. I need to downgrade back to the old version which was working just fine. How do I do this the easy way?

Is there a ppa I can install from?

People in the thirdworld don't all have high-end computers with RAM galore. We need to survive under 1gb and with less than 2ghz CPU

THanks.:mad:

---

### Post by colorlessprism on 2010-04-06
i believe thunderbird is in the repo's. use synaptic to remove 3.X, and to install thunderbird,

---

### Post by afrodeity on 2010-04-06
Do I have to force it to install the old version? I don't want to lose all my email.

---

### Post by afrodeity on 2010-04-06
It not in the repos!

---

### Post by lovinglinux on 2010-04-06
I presume you upgraded Thunderbird to 3.x using **ubuntu-mozilla-daily** ppa right? If that is the case, then simply disable that ppa from Software Sources and re-install Thunderbird. If you have Firefox 3.6 (Namoroka) you will need to re-enable the ppa, then go to Synaptic, select thunderbird, then click "Package >> Lock version". This way the ppa won't try to upgrade it again. You could also remove that ppa entirely and download Firefox from Mozilla or use Ubuntuzilla (32bit).

> **afrodeity said:**
> Do I have to force it to install the old version? I don't want to lose all my email.

You won't lose tour mails. They are stored in the thunderbird profile and don't get deleted, even if you remove the application, just like Firefox. Thunderbird mails are located under ~/.thunderbird

---

### Post by afrodeity on 2010-04-09
The mozilla daily ppa is disabled, but still not finding the old thunderbird. Do I need to purge the archive?

---

### Post by lovinglinux on 2010-04-09
> **afrodeity said:**
> The mozilla daily ppa is disabled, but still not finding the old thunderbird. Do I need to purge the archive?

Do an update, then remove it and install it again.

---

### Post by afrodeity on 2010-04-09
Okay, uninstalling and reinstalling works. It got me back to thunderbird 2.X but all my mail is gone. Ooops.

---

### Post by afrodeity on 2010-04-09
I checked my home folder, there is now a mozilla-thunderbird folder, a thunderbird folder and a thunderbird3.1 folder. Oh dear.

---

### Post by lovinglinux on 2010-04-09
> **afrodeity said:**
> I checked my home folder, there is now a mozilla-thunderbird folder, a thunderbird folder and a thunderbird3.1 folder. Oh dear.

Yep. I don't know why they don't just create a new profile instead of cloning everything to a different folder. This just creates confusion.

---

### Post by Cityscape on 2010-04-09
> **afrodeity said:**
> I checked my home folder, there is now a mozilla-thunderbird folder, a thunderbird folder and a thunderbird3.1 folder. Oh dear.
Your mail is probably in the thunderbird3.1 folder. In that case just copy the contents of thunderbird3.1 into the "thunderbird folder".

---

### Post by afrodeity on 2010-04-10
Copying the files over to my .mozilla-thunderbird folder worked. Thanks, I feel as light as a butterfly. No heavy shredding for me.
:)

---

### Post by afrodeity on 2010-05-19
damn shredder installed with the lucid upgrade. This really takes choices away from users, forcing us to install bloatware.

---

### Post by lovinglinux on 2010-05-19
> **afrodeity said:**
> damn shredder installed with the lucid upgrade. This really takes choices away from users, forcing us to install bloatware.

If you like a clean and simple e-mail client, try [Simple Mail](https://addons.mozilla.org/en-US/firefox/addon/5593) extension for Firefox.

---

### Post by afrodeity on 2010-05-19
It's actually not as bad as I thought, thunderbird three is a lot more responsive on lucid for some reason, maybe its leaner or the system is faster or a combination of the two. So guess I will live with it for now. Just would be nice to have choice when the upgrade occurs, and some intelligent feedback, like "try thunderbird three, because we know its leaner than it was in karmic", and "we are ubuntu are doing everything we can to avoid bloatware and unnecessary cpu & ram hogging", that kind of thing.

---

### Post by uRock on 2010-05-19
I love the newer version. When you delete an email, it actually deletes the one on the server, too. It isn't Shredder though.

---

### Post by afrodeity on 2010-05-19
Aha, mystery solved, its not shredder which was too heavy by far.

---

### Post by uRock on 2010-05-19
> **afrodeity said:**
> Aha, mystery solved, its not shredder which was too heavy by far.

I tried Shredder when I was using Karmic and wasn't pleased with it. It wasn't worth the effort.

---

### Post by afrodeity on 2010-05-19
Felt like my entire system was one application which would use all my resources forever, turning me into a slave in the process.

---

### Post by lovinglinux on 2010-05-19
> **afrodeity said:**
> Aha, mystery solved, its not shredder which was too heavy by far.

Shredder is just the development codename of Thunderbird 3, just like Namoroka is for Firefox 3.6.

---

### Post by afrodeity on 2010-05-20
Codename for a ten-ton elephant.

---

