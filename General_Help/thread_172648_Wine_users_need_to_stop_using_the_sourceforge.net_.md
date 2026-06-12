---
title: "Wine users need to stop using the sourceforge.net apt repository"
date: 2006-05-09
forum: General Help
---

### Post by YokoZar on 2006-05-09
The WineHQ APT repository at sourceforge is now officially obsolete - it was slow, would time out frequently, and could only handle one version of a package at a time.

If you have added one of the following lines in your /etc/apt/sources.list, you need to remove it:

[i]deb http://wine.sourceforge.net/apt binary/
deb-src deb http://wine.sourceforge.net/apt source/[/i]

Instead, use one of the following two lines:

**For Ubuntu Dapper (6.06):**
[i]deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main[/i]

**For Ubuntu Breezy (5.10):**
[i]deb http://wine.budgetdedicated.com/apt breezy main
deb-src http://wine.budgetdedicated.com/apt breezy main[/i]

[Budgetdedicated.com](http://budgetdedicated.com) has nicely provided us with the new APT repository, which has a ton of bandwidth and allows for different distributions, as well as more obvious upgrading (to go from breezy to dapper, simply change the word breezy to dapper just as you would with the official repositories).

These instrusctions are also available at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

If you have any Wine-related questions, feel free to post them here.  It would also be nice if this thread were stickied.

---

### Post by zalo on 2006-05-09
I finally gave up (font problems and flashing display). ](*,) 
It's working fine in VMWare. ;)

---

### Post by Shay Stephens on 2006-05-09
Thank you very much.  I have made the changes.

---

### Post by Peetke on 2006-05-09
Great! Thanx!

---

### Post by YokoZar on 2006-05-11
Is this the right forum for this thread?  It seems like it would be useful in other places too.

---

### Post by reazn on 2006-05-11
thanks

---

### Post by e1ektrob0y on 2006-05-11
[QUOTE=YokoZar]
Instead, use one of the following two lines:

**For Ubuntu Dapper (6.06):**
[i]deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/i]

[/QUOTE]
whenever i put either of those in /etc/apt/sources.list all i get is 
> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. for only that address. everything else downloads fine. what is happening?? it's obviously worked for other people.......................

---

### Post by Ramses de Norre on 2006-05-11
Works here.. sure you didn't made a typo?

---

### Post by e1ektrob0y on 2006-05-11
nah, i copied the text directly from both pages.

---

### Post by xXx 0wn3d xXx on 2006-05-11
Thanks :) Much faster then the old repos.

---

### Post by YokoZar on 2006-05-12
[QUOTE=e1ektrob0y]whenever i put either of those in /etc/apt/sources.list all i get is 
 for only that address. everything else downloads fine. what is happening?? it's obviously worked for other people.......................[/QUOTE]
Are you running apt-get update (or clicking refresh in synaptic)?

---

### Post by e1ektrob0y on 2006-05-12
[QUOTE=YokoZar]Are you running apt-get update (or clicking refresh in synaptic)?[/QUOTE]
yes, clicking refresh in synaptic but the messasge comes up before i get a chance to do that even. and when its downloading package info it says failed next to the address

---

### Post by YokoZar on 2006-05-13
[QUOTE=e1ektrob0y]yes, clicking refresh in synaptic but the messasge comes up before i get a chance to do that even. and when its downloading package info it says failed next to the address[/QUOTE]
Just a reminder to everyone, since I'm fairly sure this was e1ektrob0y's problem: there are no 64-bit packages.  You cannot install Wine using these packages on an AMD-64 system.

---

### Post by e1ektrob0y on 2006-05-14
[QUOTE=YokoZar]Just a reminder to everyone, since I'm fairly sure this was e1ektrob0y's problem: there are no 64-bit packages.  You cannot install Wine using these packages on an AMD-64 system.[/QUOTE]
so is that why i can't connect........cause i'm using amd 64-bit

---

### Post by Grimmy on 2006-05-14
Is there a gpg key for this repository so you don't get 

```

WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? 

```

?

---

### Post by YokoZar on 2006-05-17
[QUOTE=Grimmy]Is there a gpg key for this repository so you don't get 

```

WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? 

```

?[/QUOTE]
The packages are signed by me, but I haven't quite figured out the proper way to post a key for them yet and make nice instructions.

---

