---
title: "Skype + &quot;problem with audio playback&quot;"
date: 2009-06-26
forum: General Help
---

### Post by saskatchewan on 2009-06-26
ASUS eee 1000 + easypeasy 1.1 

I get no audio with Skype.

When ever I try to make a call I get the message "problem with audio playback"
I have tried reinstalling the software.  I have tried completely removing the software and reinstalling it from the website.

But no luck.

Suggestions please!!

---

### Post by saskatchewan on 2009-06-26
OK, I answered my own question.

But, this may help others that have the same issue.

I completely removed the version that comes with easypeasy and installed the Medibuntu packages.

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Then I selected the skype-static-oss from the synaptic.

This version seems much less "finicky" and works more dependibly.

---

