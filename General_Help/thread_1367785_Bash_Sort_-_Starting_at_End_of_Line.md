---
title: "Bash Sort - Starting at End of Line"
date: 2009-12-29
forum: General Help
---

### Post by raywood on 2009-12-29
I have a text file whose contents are directory listing output, like this:

```
./folder1/make-me-number-two
./folder1/put-this-last
./folder2/belongs-at-start-not-end

```

A normal sort will put these three lines in the order shown.  A simple reverse sort will replace 1-2-3 with 3-2-1.  But what I want is for them to be sorted in alphabetical order, but starting with the last character in the filename.  In that case, they would be resorted from 1-2-3 to 2-3-1, because their last letters are o, t, and d, respectively.

In case of a tie, I want to progress backward along the filename, looking at character (end-1) and then (end-2) and so forth as needed.  So a filename ending with aaa would come before a file ending with aba.

Can it be done in bash, or with some other easy-to-learn (as in minutes, not hours) Ubuntu tool?

---

### Post by iponeverything on 2009-12-29
It's fairly easy, but it smells suspiciously like a homework assignment.

---

### Post by falconindy on 2009-12-29
man sort

---

### Post by kaibob on 2009-12-29
> **raywood said:**
> But what I want is for them to be sorted in alphabetical order, but starting with the last character in the filename.  In that case, they would be resorted from 1-2-3 to 2-3-1, because their last letters are o, t, and d, respectively.

I guess I'm having a mental block but wouldn't the sort order based on the last letter be 3-1-2?

Anyways, you could use the rev command before sorting. For example,

> $ rev file
owt-rebmun-em-ekam/1redlof/.
tsal-siht-tup/1redlof/.
dne-ton-trats-ta-sgnoleb/2redlof/.

---

### Post by falconindy on 2009-12-29
Ok that's way simpler than what I had in mind. Forgot all about rev.

---

### Post by raywood on 2009-12-30
Passing note to the first poster:  Yes, it could be a homework assignment, two or three weeks after the semester's end.  You could check me out, right?  I have 86 posts here over the past 2.5 years, posting especially in the summer.  So, yeah - it definitely sounds like a student.  But anyway, thanks for the help.  From each according to his ability, as the saying goes.

Kaibob - you are so right - I think I even had 3-1-2 and then changed it.  Thanks for the pointer to rev.  That seems to be exactly what the doctor ordered.

I was gonna wish y'all a happy new year, wasn't sure whether to make it a happy new decade, started to reflect that it could depend on whether the clock on these things was originally supposed to start with Jesus being born in the year 1 or the year 0 - besides which, I don't know how they'd deal with the partial year in either case, unless he happened to be born exactly on New Year's, which we'll never know - and then I remembered reading that he was actually born in 4 B.C., which if you think about it was a miracle in itself.  So, you know, screw it.

---

