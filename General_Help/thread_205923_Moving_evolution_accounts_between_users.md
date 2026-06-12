---
title: "Moving evolution accounts between users"
date: 2006-06-29
forum: General Help
---

### Post by spin on 2006-06-29
Hi all,

I'm reorganizing my user profiles, and would like to move an evolution (mail) account from one user account to another. This means, all the mail in all the right places, and account settings intact.

At first, I tried to simply move the .evolution folder into my new home folder (it worked before, with another email program ;), but that didn't work. I also tried using the "multi-file" import wizard from inside Evolution, but that didn't work either.

So, has anyone got a clue on how I could proceed?

regards,
spin

---

### Post by mrvw0169 on 2006-07-02
Argh, this is driving me crazy too... I figured it out once before but I forgot to write down what I did.

I'm in the same boat - just reinstalled Ubuntu and copying back configs... I've copied my entire ~/.evolution, ~/.gconf/apps/evolution, and ~/.gnome2_private/Evolution... What's driving me nuts is that starting Evolution asks me to go through their "first-run" wizard no matter what...

Oh wait, maybe I'll go through the wizard first and recopy the ~/.evolution folder on top... hmm...

EDIT: Oh man, that worked... Had to delete the new ~/.evolution folder that the wizard created first then recopy my "real" ~/.evolution folder...

---

### Post by spin on 2006-07-02
Yeah!

That worked for me too! Thanks a lot for the help!

---

