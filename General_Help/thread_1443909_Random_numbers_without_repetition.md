---
title: "Random numbers without repetition"
date: 2010-03-31
forum: General Help
---

### Post by ayozito on 2010-03-31
How can i generate randoms numbers without repetition?? Because with RANDOM i can generate random numbers, but sometimes some are repeated.

---

### Post by Npl on 2010-03-31
store every number already used and then compare new numbers if they are unique. Requires an ever growing list of used numbers of course.

if you are using a small sequence of numbers (say 1 to 100) then you should look at [random permutations]("http://en.wikipedia.org/wiki/Random_permutation")  (some algorithms to generate them are linked at that page I believe)

---

### Post by john newbuntu on 2010-04-01
The key to randomness is the seed value otherwise they are only pseudo-random.  So long as that changes (such as that from /dev/random) you will most likely get a new value.  You could also query [http://www.random.org/](http://www.random.org/) that generates randomness from atmospheric noises.

---

### Post by HermanAB on 2010-04-01
Do you want a random number, or a permutation, or a maximal length sequence?

Some Googling will clear it up for you.

---

