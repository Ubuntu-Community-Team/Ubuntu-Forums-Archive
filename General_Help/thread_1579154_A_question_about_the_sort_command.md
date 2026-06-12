---
title: "A question about the sort command"
date: 2010-09-21
forum: General Help
---

### Post by DanRhea on 2010-09-21
First off, though I'm a user of Ubuntu, I'm asking this in the context of running sort from a Windows command line (UnxUtils). I'm not sure where else to ask and I happen to trust this community.

Anyway... I've noticed that the sort command is field oriented (based on the way a key is declared).

The data I need to work with is flat ASCII data that is columnar and isn't delimited. The records run around 32K in length and can have several hundred rows.

If I format my sort like this:

sort -t '\0' -k 1.15,1.17 -k 1.18,1.25 -o bar.dat foo.dat

Does this have the effect (the -t part) of making the entire row appear as a single field and thus allow me to sort by columns 15 through 17 and then 16 through 25?

This seems to be working for me on my Ubuntu and Windows system but I want to be sure about this and check to see if there is a better way to do this.

I appreciate any advice on this (including directions to a better place to ask if that's the case). 

Thanks

Dan

---

### Post by DanRhea on 2010-09-21
Hi folks...

Never mind on this one... I gave the UnxUtils sort on Windows a real-world test. A file with 8,666 records that's 161,343,213 bytes and all it does is write this to the screen (the digits vary each time I try to run it)...

  sort: /tmp/sort0125200000: No such file or directory

I suspect this isn't going to fly with this Win32 implementation of GNU sort.

I've no doubt it would work with ubuntu (and I know it works with Open VMS on an ancient Alpha server) . I'll probably have to write something from scratch... in Windows... in VB.Net... by myself... in the dark... in a corner... I'll be fine. 

><

Dan  :)  (I'll try Perl first... I'll be okay... really)

---

