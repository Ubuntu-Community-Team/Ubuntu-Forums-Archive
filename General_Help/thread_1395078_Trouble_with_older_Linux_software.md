---
title: "Trouble with older Linux software"
date: 2010-01-31
forum: General Help
---

### Post by Scarlette on 2010-01-31
Hello Ladies and Gents,

I'm having a spot of trouble with some older Linux connectionist modeling software (which I'm trying to install on Ubuntu). 

It can be found here: [ftp://ftp.crl.ucsd.edu/pub/neuralnets/tlearn_src/](ftp://ftp.crl.ucsd.edu/pub/neuralnets/tlearn_src/)

I have a basic understanding of makefiles and so forth--I'm able to change the "EXP_LOC=/usr/local/lib/exp/exp_table" in the makefile to one that actually exists. But even when I do this, I'm not able to run the binaries.

Any assistance would be *much* appreciated!

Best,
Steph

---

### Post by Scarlette on 2010-01-31
I think it may have to do with the "exponential look-up table," if that helps. Not sure what an exponential look-up table is, though.

---

### Post by gmargo on 2010-02-01
What problem are you having exactly?

I had no trouble compiling and running the software, although I don't know what to do with it.

The steps I followed:

[LIST]
[*]Edit Makefile to change EXP_LOC variable to an existing directory
[*]make
[*]make exp
[*]./tlearn
[/LIST]
And then tlearn runs and gives "ERROR: No -s specified: Invalid argument" because I have not supplied a required argument.  Have you gotten as far as this point?

---

