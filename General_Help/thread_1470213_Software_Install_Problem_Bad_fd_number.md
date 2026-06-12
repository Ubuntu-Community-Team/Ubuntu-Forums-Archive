---
title: "Software Install Problem: Bad fd number"
date: 2010-05-02
forum: General Help
---

### Post by Nsight7 on 2010-05-02
I am trying to install some cosmic ray shower software from [http://nuclear.llnl.gov/simulation/](http://nuclear.llnl.gov/simulation/) and I am having problems.

In particular, I am trying to install v1.5 of CRY (Cosmic-ray Shower Library).  The instructions given in the install guide are relatively simple, yet my install fails from the very first "make".  The instructions specify to head to the top-level directory and simply type *make*.  The readout I get in the terminal is as follows:

```
research@research-laptop:~/Muon/cry_v1.5$ make
/bin/sh: Syntax error: Bad fd number
make[1]: *** [depend] Error 2
make: *** [lib] Error 2
research@research-laptop:~/Muon/cry_v1.5$
```Additionally, I then get a setup txt file in the top-directory that reads:

```
# source setup
#
# Execute the correct setup script
#

cd /home/research/Muon/cry_v1.5

setenv test_if_this_is_csh 2>/dev/null \
&& setenv SETUP_SHELL csh || export SETUP_SHELL=sh

source setup.$SETUP_SHELL `/bin/pwd`

cd - > /dev/null
```I have tried many of the standard error correcting measures here that I have read about, but still can't fix this problem.  I have tried this install on three different computers and two distributions.  The current one is an hours-fresh install of 10.04 LTS 64 so everything OS-wise should be on the up-and-up.  I particularly don't understand the setup file printout and would LOVE some clarification there.  This work is pretty important to my finishing out my MS thesis this summer.

Thank you!

---

### Post by Nsight7 on 2010-05-03
Bump!

Any ideas at all guys?  I am pretty used to working in Ubuntu so I would like to keep my work there, but this little issue would definitely force me to migrate temporarily at least.  I would MUCH rather not have to deal with the learning curve associated with learning another Linux OS just to finish out a relatively short-term task.

---

### Post by Nsight7 on 2010-05-03
More info:

Just wanted to report that, on both Debian 5 and Fedora Core 12, I am receiving precisely the same error.  I am going to give openSUSE 11.2 a try (since it is on one of my laptops), but I suspect this will largely go the same way as Ubuntu, Debian, and Fedora Core went.

---

### Post by Nsight7 on 2010-05-04
Okay, I am going to suppose that nobody has any suggestions on this given the lack of replies.  I have emailed the developers of the software and I will continue fooling with the software, so if I find anything out regarding the installation of this simulation software, I will post back.  Until then, thanks for your time!

---

### Post by gmargo on 2010-05-04
It's a bug in src/Makefile.  

Here's a patch:
```

--- cry_v1.5-orig/src/Makefile  2007-11-20 21:12:06.000000000 -0800
+++ cry_v1.5/src/Makefile       2010-05-04 12:21:47.000000000 -0700
@@ -14,7 +14,7 @@
        @echo "Done making $(LIB)"
 
 depend: .makedepend
-       @makedepend -f .makedepend $(CXXFLAGS) $(SRC) >& /dev/null
+       @makedepend -f .makedepend $(CXXFLAGS) $(SRC) > /dev/null 2> /dev/null
 
 .makedepend:
        @touch .makedepend


```> I have tried many of the standard error correcting measures here that I  have read about, but still can't fix this problem.The first thing I did was to remove all of the at-signs (@) from the makefiles.  Then it was obvious.

---

### Post by Nsight7 on 2010-05-05
Thanks for the help!  I actually fixed it too, but differently.

I went into Makefile.common and added the line

```
SHELL=/bin/bash
```

to the beginning of the file.

One must also make sure they have makedepend and thus need

```
sudo apt-get install imake
```

Finally, once I got around that and started getting other errors that seemed related to the actual code, I had to add a couple of header files to each .cc file.  It seems that the version of g++ they were running, which is like 5+ years old, would compile the code without the appropriate headers without spitting errors.  Mine, however, would not.  I think I mostly had to add:

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
```

Once would see exactly which declaration errors were made (stuff like 'strcmp' and 'atof' and the like), and then one could add the appropriate headers.

After all this was done it compiled no problem and I ran the code without issue.  Next we shall see if I can interface it properly with geant4.

Of note, I didn't get the shell error when running Fedora Core 12.  I believe it runs bash and NOT dash, which is why it didn't encounter the same syntax error regarding the shell, i.e. Bad fd number, this despite my trying to simply run the scripts in what I understood to be their native shells in Ubuntu anyhow, namely either sh or tcsh.

What a friggin' adventure...

---

