---
title: "WOW, did I get a ton of email ...."
date: 2010-01-13
forum: General Help
---

### Post by johenkel on 2010-01-13
that is what I saw this morning on my screen.

And, oops, my total email count is negative ... how did that happen ?

tztz

johenkel

---

### Post by bkratz on 2010-01-13
Anything interesting?

---

### Post by Shippou on 2010-01-13
Maybe the counter is in integer type, and your mail is out of range. IMHO what happened basically is that the number is very large. What happens most of the time is that the numbers round off (i.e. starts from the negative part backwards), hence the very large negative number.

I think Evolution is programmed in C (or C++?) so getting integer overflows is somewhat common. The indication is getting a very large negative number like what you have got.

I think this is not a very serious error, and should be corrected once your number of mails falls within the bounds of an integer. But maybe you should consider filing a bug about this one.

---

### Post by insane_alien on 2010-01-13
you have over 1 billion read emails? they can't conatin much, if each one is 500 characters then thats 500GB of email, not counting the headers, images, etc. etc.

---

### Post by john newbuntu on 2010-01-13
Note to self: Always initialize variables. Always use unsigned integers/long for counts that can never be negative. Always create a testing framework like JUnit for pre-production testing.  Quadruple check these when working in a financial institution.
Ok, moving on...

---

### Post by johenkel on 2010-01-13
Well, once I restarted evolution, I had only my 252 usual emails. :)
Maybe I should've quit evolution while doing the updates ?

Anyway, it shows the right amount now.

johenkel

---

