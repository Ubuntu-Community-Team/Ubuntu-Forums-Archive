---
title: "GLIBC 2.8 on Hardy"
date: 2010-02-02
forum: General Help
---

### Post by Darkheart on 2010-02-02
Not sure where to start with this, so I am taking the most general approach--  If this needs to be somewhere else, sorry and please point me to the right forum...

Installed a new program that calls for GLIBC 2.8 and it immediately errors and quits( `GLIBC_2.8' not found ). 

Running Hardy Heron, YES, I know it is getting long in the tooth, but LTS? I should be able to install GLIBC 2.8?  This boy can not find any reference to do so.  

I'd upgrade, but running a laptop Dell Inspiron 6000 with ati X300 mobility (NEVER AGAIN WITH ATI! Give me Nvidia or give me death!) that has been put into legacy and is no longer supported by ati. So I am stuck on Hardy until I get a new laptop (Sometime in the year 2525 at the rate I can save money)

The question(s) is/are: 

 1.  Can GLIBC 2.8 (/lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.8')
be installed on Hardy Heron easily?

2. Can it GLIBC 2.8 be installed with non-standard repos?

3.  Can GLIBC 2.x be custom compiled *easily* to Hardy or am I looking at a whole can of worms.  ("Dood, solution: apt-get dist-upgrade" >remember ATI?<)

Finally if I am looking under the wrong rock...

Where may I find a forum to guide me through this- if one exists?

Thanks!  

Darkheart

---

### Post by Darkheart on 2010-02-22
Oookay... been a couple of weeks and not even a passing comment? :confused: No clue from anyone.  I'll try another more specific part of this forum area.

---

### Post by mc4man on 2010-02-22
> not even a passing comment? 
I can certainly give you a passing comment - the odds are if you do this it will not end well.
Most likely your app is looking for a libc6 of 2.8 (or higher), possibly some other related libs.
Any time I've seen someone who either willfully or inadvertently upgraded their libc6 they've been looking for a way to revert short of a full re-install, not posting to say how great things were...

---

