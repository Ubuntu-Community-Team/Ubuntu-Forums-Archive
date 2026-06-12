---
title: "RCS Revision Number Precision"
date: 2011-03-02
forum: General Help
---

### Post by rpaskudniak on 2011-03-02
Bottom line first:  I need revision control software that will use true decimal revision numbers and allow revision numbers like 1.01 or 1.001.

Now for the long version:

Greetings.

For once, I am not asking an earth-shattering question about the internal combobulations of Ubuntu.  I just need a pointer in the right direction.

As far as I can see, RCS assign revision numbers by adding 1 to the number to right of the dot.  Note, I did not say *to the right of the decimal point*.  That is because an RCS revision number is simply a pair of numbers separated by a dot.  Proof: Following revision 1.9, you would get revision 1.10; this is numerically equal to 1.1 but revisions 1.1 and 1.10 are quite far apart.  Also, you can have branches like 1.23.4.

So what's my problem with this? In a word: CPAN. (OK, so that's an acronym, not a word. :rolleyes: ) I have already experienced error messages when installing a module whose version looked like 6.3.10 - The Makefile wants a true decimal number.

But I want revision numbers that are truly decimal and allow greater precision, like 1.09, and 1.10 and so on.

[LIST]
[*]Can RCS be manipulated into behaving this way, assuming I religiously avoid branches?
[*]Is there any other revision control software that allows the higher precision revision counting?
[*]Is such software available for both Linux and Cygwin environments?
[/LIST]

Thanks for pointers here.

---

