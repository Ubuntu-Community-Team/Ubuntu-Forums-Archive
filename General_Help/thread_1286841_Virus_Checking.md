---
title: "Virus Checking"
date: 2009-10-09
forum: General Help
---

### Post by jimmers on 2009-10-09
Gals and Guys,
I have been asked the question and it is beyond my Ken, so I have come to centre of knowledge (and indeed excellent advice), I have just converted 3 Windoze devotees, to Ubuntu, but because they are a group who share info and photos etc on CD's, there biggest problem is Viruses???( in Linux), but you know the score, if it does'nt come out of a box labelled Microsoft they do not trust, I have tried my best to calm their fears, as I write this they are sitting on my shoulder, their question is, is there a Application or Command Line Instruction to Automatically Virus Check CD's on ejection.

They are all running Jaunty

If there is answer out there, it will save me a lot of grief, I have told them they can do it manually, but being Ex Windoze they are lazy (maybe a bit to strong), although I have never come accross such an application during my time on Windoze.

As always all help and advice, greatly appreciated

Jimmers

---

### Post by SkyNet2029 on 2009-10-09
Hmm. So, one could use clam-av to scan the removable media for a virus. It has a command line interface as wella s a lazy point and click apparatus.
BUT..
why anyone would use this on linux only setup is strange. I could see a viable use to prevent infection to windows boxen, but there really is no need for anti-virus on a linux box.
sigh....
For a Linux binary virus to infect executables, those executables must be writable by the user activating the virus. That is not likely to be the case. Chances are, the programs are owned by root and the user is running from a non-privileged account. Further, the less experienced the user, the lower the likelihood that he actually owns any executable programs. Therefore, the users who are the least savvy about such hazards are also the ones with the least fertile home directories for viruses. 

Even if the virus successfully infects a program owned by the user, its task of propagation is made much more difficult by the limited privileges of the user account. [For neophyte Linux users running a single-user system, of course, this argument may not apply. Such a user might be careless with the root account.]

Linux networking programs are conservatively constructed, without the high-level macro facilities that have enabled the recent Windows viruses to propagate so rapidly. This is not an inherent feature of Linux; it is simply a reflection of the differences between the two user bases and the resulting differences between the products that are successful in those markets. The lessons learned from observing these problems will also serve as an innoculation for future Linux products as well.

Linux applications and system software is almost all open source. Because so much of the Linux market is accustomed to the availability of source code, binary-only products are rare and have a harder time achieving a substantial market presence. This has two effects on the virus. First, open source code is a tough place for a virus to hide. Second, for the binary-only virus, a newly compiled installation cuts off a prime propagation vector.

Each one of these obstacles represents a significant impediment to the success of a virus. It is when they are considered together, however, that the basic problem emerges.

A computer virus, like a biological virus, must have a reproduction rate that exceeds its death (eradication) rate in order to spread. Each of the above obstacles significantly reduces the reproduction rate of the Linux virus. If the reproduction rate falls below the threshold necessary to replace the existing population, the virus is doomed from the beginning -- even before news reports start to raise the awareness level of potential victims. 

The reason that we have not seen a real Linux virus epidemic in the wild is simply that none of the existing Linux viruses can thrive in the hostile environment that Linux provides. The Linux viruses that exist today are nothing more than technical curiosities; the reality is that there is no viable Linux virus.

Of course this doesn't mean that there can never be a Linux virus epidemic. It does mean, however, that a successful Linux virus must be well-crafted and innovative to succeed in the inhospitable Linux ecosystem.

---

### Post by oldos2er on 2009-10-09
Have them read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by oldsoundguy on 2009-10-09
> **oldos2er said:**
> Have them read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Thanks for posting that link!
Sometimes hard to find something like that and especially one that is  as comprehensive.

KUDOS to bodhi.zazen for it's creation!

It is going to get circulation OFF of this site as I am a member of an on line computer repair forum and have manged to get a couple of fed up Windows users to switch to Ubuntu after multiple efforts were made to fix their computers and said efforts failed.
(mind you, I still use Windows .. OFF LINE ONLY .. to run Adobe programs and stuff for my amateur photography .. filter programs and such)
And I also use the box to HELP Windows users fix their Windows boxes (posting fix pathways and the like.)

---

### Post by jimmers on 2009-10-09
Thanks Gals and Guys for your response, most appreciated, apart from skynet 2029, they read your response and decided that if is what Ubuntu is all about then SOD IT, they do not need to be talked down to.

---

### Post by CatKiller on 2009-10-09
> **jimmers said:**
> skynet 2029, they read your response and decided that if is what Ubuntu is all about then SOD IT, they do not need to be talked down to.

Skynet's response was very comprehensive. If they already knew all that he'd posted, then they wouldn't need to be here asking about viruses in Linux, would they? And if they don't already know all that he posted, he's hardly talking down to them, is he?

We're a community here. Play nice.

---

### Post by bobnutfield on 2009-10-09
> **jimmers said:**
> Thanks Gals and Guys for your response, most appreciated, apart from skynet 2029, they read your response and decided that if is what Ubuntu is all about then SOD IT, they do not need to be talked down to.

It's a shame that you or those you are coaching toward Ubuntu would feel that skynet2029 was talking down to anyone.  I read it a couple of times to see if I could see anything that could be interpreted as "talking down" and I could not see anything of the sort.  It appears to me that a member of the community was simply giving an EXCELLENT explanation why we Linux users need to be so much less concerned about viruses.  I personally enjoyed the post and will use it with my converts when discussing viruses.

---

### Post by amsum on 2009-10-09
Well, let me cut it short. I know its hard to convince a windows converter to make him believe that Ubuntu is really safe/virusfree. So, rather than preaching all about ubuntu's sacurity, here are the options you can use.
1) Clam AV (Not Automated, you need to give the path of Cd drive manually)
2) Avast ((Not Automated, you need to give the path of Cd drive manually)
3) BitDefender (Not Automated but they have right click option to scan any drive/files/directories)

I have used all the 3 above and it really helps in removing windows virus.
Again, windows virus is just for windows. you may have virus on your system but it is not going to effect your system in any way. It will just sit there as a file doing nothing.

---

### Post by StuartN on 2009-10-09
> **amsum said:**
> So, rather than preaching all about ubuntu's sacurity, here are the options you can use.

There is a lot to be said for this attitude - dealing with the perception of risk is just as important as dealing with risk. No argument about the safety of Linux will convince a sceptical boss so easily as "Yes, we run an up-to-date malware scan."

---

