---
title: "32-bit on AMD64?, difference in settings?"
date: 2010-08-02
forum: General Help
---

### Post by rlynwood on 2010-08-02
Hello,

On U's download page, Canonical says that the 64-bit version of U is not advised "for daily use," i.e., for the general public, I assume.  I'd love to know why they don't advise for general use the 64-bit version, even on 64-bit machines.  Is it because of the difficulty of getting the 64-bit version of Flash and other, similar problems, or is it because of any inherent instability?

I installed the 64-bit version on my newly built (not new, but not too old equipment) AMD64 machine in late April or early May.  Then, about a 1 1/2 month later, after downloading the routine updates, I clicked on Restart, as required.  It began installing the updates, then, after about 2-3 seconds, it completely crashed--completely!  Now no recovery tool can even see the partition it's on, though Gparted shows the OS/fs still there.

I'm trying to decide what to do about that.

Secondly, I'd like to know if there's any difference between the coding of the settings for the apps in the two (home is on a separate partition).  That is, can I replace my 64-bit U with a 32-bit one and keep/use my dot folders from before?

Ray

---

### Post by Smart Viking on 2010-08-02
Hi, i had 64Bit installed before and i can't see no difference expect 64bit is less supported and a little unstable(had some weird random logouts and that stuff), so i would recommend installing 32Bit because:

- performance is not noticeable slower
- your ram will be supported with PAE
- linux runs smooth anyway
- more stable, and more compatible software
- flash works better

Thats my experience anyway. :)

---

### Post by oldos2er on 2010-08-02
There's no longer any difficulty getting 64-bit flash, since Adobe pulled it. See [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940) for various opinions on the matter.

---

### Post by rlynwood on 2010-08-02
Thank both of you for your replies.  I have Flash installed and had no problem using it while the OS was working.  I'm not using it now because it crashed, as I said.  Now I'm using a crippled version of Ultimate Edition (of Ubuntu) 2.6.  (I haven't decided how to partition and reinstall the two.)

Ann, your link showed me a really extended "discussion" about my first question.  But it simply showed that everyone else is as perplexed as I am about U's admonition; it didn't answer the question.  Apparently, Canonical hasn't explained that anywhere.

Smart Viking's comment that my single gig of ram might be better used with the 32-bit version is useful info.  I read this evening that the 64-bit version uses ram less efficiently.  Glad to know that.


Does either of you or anyone else know if the settings for the apps in the 64-bit version can be used with the 32-bit version?

---

### Post by dcstar on 2010-08-03
> **rlynwood said:**
> 
........
Does either of you or anyone else know if the settings for the apps in the 64-bit version can be used with the 32-bit version?

No difference whatsoever.

---

### Post by rlynwood on 2010-08-03
I was referring to the settings stored in the dot folders in /home.  I assume that you were, too, but I just wanted to check.  I.e., I can copy the 64-bit-based home folder in my current, 64-bit U back over the newly installed 32-bit one without any functional effect or detriment, right?

---

### Post by linux18 on 2010-08-03
> **rlynwood said:**
> I was referring to the settings stored in the dot folders in /home.  I assume that you were, too, but I just wanted to check.  I.e., I can copy the 64-bit-based home folder in my current, 64-bit U back over the newly installed 32-bit one without any functional effect or detriment, right?
you can copy the files, because the files arent 64-bit I think the command from a new install with the partition as the only mounted device is:

sudo cp -rf /media/*/home/*/* ~/Downloads/

I used Downloads as the folder where your files from the old /home directory go, you can chance as needed. this will also download hidden folders making it possible to replace your firefox profile and bash aliases, etc.

---

### Post by oldos2er on 2010-08-03
> **rlynwood said:**
> Ann, your link showed me a really extended "discussion" about my first question.  But it simply showed that everyone else is as perplexed as I am about U's admonition; it didn't answer the question.  Apparently, Canonical hasn't explained that anywhere.

You're right, the answer is that there is no answer; and I find that as perplexing as you do. FWIW, I've been using 64-bit for two-and-a-half years or so with no issues.

---

