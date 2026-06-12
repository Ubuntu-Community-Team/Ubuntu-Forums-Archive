---
title: "Thunderbird no longer starts"
date: 2010-05-25
forum: General Help
---

### Post by rwigle on 2010-05-25
I have been running thunderbird.2.0.0.24+build1+nobinonly-0ubuntu0.8.04.1 successfully for some time now under Hardy.

This morning I tried to run it and I get the "wait" indication but then nothing.

I looked in my home folder and the folder .mozilla-thunderbird seems to be liked to .thunderbird, but both are listed in red and black. (Doesn't sound good.)

Any suggestions. I saw a similar bug for a newer version of thunderbird, but the symptoms in my case seem different.

---

### Post by dino99 on 2010-05-25
sudo apt-get install -f

sudo dpkg-reconfigure thunderbird

---

### Post by rwigle on 2010-05-25
Thanks for the suggestion. I tried that, and it didn't work, and I think I know why.

I just upgraded to Lucid on my laptop and I forgot that I was sharing the profile between two computers. I use unison to keep the laptop and (office) desktop synched, but of course they are no longer going to be consistent because of the different versions.

I think that is the problem. Mercifully, the files are still there on my laptop and I deleted the reference in unison so that they don't get removed next time I log in.

---

