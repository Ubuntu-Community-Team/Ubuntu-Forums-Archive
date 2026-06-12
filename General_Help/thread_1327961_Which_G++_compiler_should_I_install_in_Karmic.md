---
title: "Which G++ compiler should I install in Karmic?"
date: 2009-11-16
forum: General Help
---

### Post by rpaskudniak on 2009-11-16
Greetings.

I doubt this is really relevant but I have just upgraded my Ubuntu from 9.04 -> 9.10.

In any case, I wish to install a C++ compiler.  Synaptic gives me a few choices:
[LIST=1]
[*]g++
[*]g++-4.4
[*]g++-4.4-multilib
[/LIST]


Observations:
[LIST]
[*]I see I have the same choices for gcc and in that case, all three versions are installed.
[*]I also see that if I choose any of these three option, it will also install libstdc++6-4.4-dev.
[*]If I choose either g++ or g++-4.4-multilib, it will also install g++-4.4 (option 2).  Hence, it would seem pointless to choose g++-4.4 alone.
[*]The above options are a subset of what displays when I choose "Development" in the left column of synaptic.  When I choose "Development (universe)" I see that g++-4.3 and g++-4.3-multilib are already installed.
[/LIST]
Hence, the question refines to: Shall I install option 1 or option 3, or both?

If I install both and then invoke the g++ compiler, what will it execute?  And does it make a helluva difference to me which one it executes? :rolleyes:  (Hmmm... Not so refined anymore.)

Just to muddy the issue a bit, for chuckles: Since I already have the g++-4.3 packages (observation #4), do I need to upgrade to g++-4.4 at all?

Final question: If I were to install the 4.4 compiler packages, I would leave the 4.3 stuff in place because I suspect every blessed executable is built with 4.3 libraries.  With both versions on my box (should I choose to install the 4.4 compiler) how would I guarantee which compiler I am invoking? (I could play inelegant games with $PATH and aliases.  UGH!)

Advice, please?

Thanks much.

Concise is my middle name..  NOT! :P

---

### Post by mc4man on 2009-11-16
It would appear your running karmic, in which case your system (default) gcc is 4.4.1

The g++ (and gcc, cpp) package is a dependency package, it just installs the g++ (or cpp) version that matches the default which in karmic is  4.4.1

You are free to install lesser versions of all, the default (system version) will stay the same and is what will be used.

If you wanted to use gcc-4.3 or g++-4.3 or cpp-4.3 (or any other lower version) then you would need to specify that in your configure, make, rules or appropriate source file as needed in a manner that your source accepts the flag


edit:
I do find this statement a bit odd
> I see I have the *same* *choices* for gcc 

you should already have gcc-4.4 and gcc-4.4-base installed (as it's the system default for karmic)

When you do a fresh install only the default gcc/gcc-base, ect. are installed ( in this case 4.4.1 versions

When you do an upgrade the prior's that were installed, (4.3 in jaunty), stay behind but the new ones should be installed (gcc-4.4, gcc-4.4-base

---

### Post by rpaskudniak on 2009-11-16
Thank you, mc4man.

I took your advice to mean I should install all 3 g++ packages at release 4.4, similar to the gcc 4.4 installations.

Before I did this, there was no man page for g++ and **g++ -v** yielded some short message before spouting "command not found". In fact, installing only options 2 and 3, omitting the g++ (option 1) left me in the same state.  Only after I installed the g++ did I get a man page and version information for g++.

There's the answer - install them all.

What the pre-installed 4.3 stuff was doing there (pet rock?) is a curiosity I will not chase at this time,  But I now have the needed g++ compiler accessible.

---

### Post by mc4man on 2009-11-16
> What the pre-installed 4.3 stuff was doing there 
They came along for the ride as part of your upgrade from jaunty, actually not bad to have, for some sources/uses the 4.4 gcc is not the best choice atm.

---

