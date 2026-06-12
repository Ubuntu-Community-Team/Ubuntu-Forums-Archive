---
title: "Evolution Folder Missing"
date: 2009-09-02
forum: General Help
---

### Post by Bharath on 2009-09-02
Hi,

I searched for more than an hour regarding this problem and could not get help from the forums... so I am posting this...

My folder "Sourcng Validated1" is missing from Evolution. **_please help me to recover it._**

I checked in /home/bharath/.evolution/mail/local -- it has the following(concerned files):

Name                                                Size      Type                Date Modified
Sourcing Validated1                             2.0GB      mailboxfile      Wed 02 Sep
Sourcing Validated1.cmeta                    117b        Unknown          Wed 02 Sep
Sourcing Validated1.ev-Summary            32.MB      Unknown          Wed 02 Sep
Sourcing Validated1.ev-summary-meta    492.6KB    Unknown          Wed 02 Sep
Sourcing Validated1.ibex.index              8b            Plaintext         Thu 13 Aug
Sourcing Validated1.index.data             0b            Plaintext          Thu 13 Aug

But in evolution I am not able to see...... I have lot of info in this folder....

Help!!!!

Bharath

---

### Post by dcstar on 2009-09-03
> **Bharath said:**
> Hi,

I searched for more than an hour regarding this problem and could not get help from the forums... so I am posting this...

My folder "Sourcng Validated1" is missing from Evolution. **_please help me to recover it._**

I checked in /home/bharath/.evolution/mail/local -- it has the following(concerned files):

Name                                                Size      Type                Date Modified
Sourcing Validated1                             **2.0GB **     mailboxfile      Wed 02 Sep
Sourcing Validated1.cmeta                    117b        Unknown          Wed 02 Sep
Sourcing Validated1.ev-Summary            32.MB      Unknown          Wed 02 Sep
Sourcing Validated1.ev-summary-meta    492.6KB    Unknown          Wed 02 Sep
Sourcing Validated1.ibex.index              8b            Plaintext         Thu 13 Aug
Sourcing Validated1.index.data             0b            Plaintext          Thu 13 Aug

But in evolution I am not able to see...... I have lot of info in this folder....

Help!!!!

Bharath

There was a known issue with 32-bit Evolution with a 2GB maximum file size (this does not apply to 64-bit AFAIK).

I would suggest copying the whole .evolution folder to a 64-bit install, or - if possible - installing 64-bit Evolution on you machine.

---

### Post by Bharath on 2009-09-04
Hi David,

I dont have a 64-bit machine.... nor 64-bit OS with me..... I am not that techie to fiddle with my current installation..... my machine (laptop) contains all the critical data in my company.....

**Is there a way to split the file and then reload it to my Evolution..... pleas let me know.....**

.........if only I had known 2 GB limit.... I would have maintained Evolution properly.....

Bharath

---

