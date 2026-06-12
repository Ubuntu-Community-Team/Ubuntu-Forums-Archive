---
title: "Upgrade 11.04 beta to stable"
date: 2011-04-28
forum: General Help
---

### Post by 1Michael1 on 2011-04-28
I'm currently running 11.04 beta.
How am I able to upgrade to the latest stable of 11.04 without any data loss?

I tried the command update-manager -d but I can't seem to find anything new there.

Thanks

---

### Post by Teraspes on 2011-04-28
I'm in the same situation as you.

---

### Post by mörgæs on 2011-04-28
There are countless posts in the forum about this. Once again: Just apply all the updates as usual, and you will get to the final 11.04.

---

### Post by chunky bacon! on 2011-04-28
> **mörgæs said:**
> There are countless posts in the forum about this. Once again: Just apply all the updates as usual, and you will get to the final 11.04.


Countless posts, huh?  Maybe someone should make a sticky or a how-to.

At any rate, I google searched the forum, and this thread was the only one that really showed up answering the question out of the countless posts.

So, thanks for answering, however, this is a bit confusing to me as well. 

I upgraded to the Beta a few days ago, and when running updates, I get told that everything is up to date.  :confused:

Does this imply that there was no difference between 11.04 beta and 11.04 stable?  Just wondering.

---

### Post by ratcheer on 2011-04-28
Run "lsb_release -a" and see if it says you are still on "development". If it doesn't, you are already on the final release version.

Tim

---

### Post by chunky bacon! on 2011-04-28
> **ratcheer said:**
> Run "lsb_release -a" and see if it says you are still on "development". If it doesn't, you are already on the final release version.

Tim


Thank you! That answers the question.

---

### Post by 1Michael1 on 2011-04-28
Thanks a bunch!

Solved.

---

