---
title: "offline cd ripping fails"
date: 2010-08-05
forum: General Help
---

### Post by Citizen_Kane01 on 2010-08-05
Can anyone help with a fix for this strange behavior when ripping CD's to files:

When Ubuntu is online, everything works fine. When it is offline, cd ripping works for about 4 tracks and then the ripping process freezes.

I have tested this and it occurs consistently in Rythmbox, Sound Juicer and Asunder. Also happens when track details are typed in manually.

I have tested this with:
[LIST]
[*]Different cd's, so it is not a damaged disk.
[*]64bit and 32bit
[*]different physical machines, so it is not a drive problem.
[/LIST]

As I say, everything works fine when Ubuntu is online.

Any help please as I have to rip in offline situations.

---

### Post by ajgreeny on 2010-08-05
I wonder if you need to disable the CCDB query, which I think happens by default when ripping CDs.

Just a thought; I have no experience of this at all.

---

### Post by Citizen_Kane01 on 2010-08-06
Sounds like CDDB is the likely suspect. Going to do a hunt-down on launchpad. Strange thing is I tested it on a third Ubuntu machine (64bit) and it works fine offline! 

Looks like it is going to be an epic needle in the haystack event.

Do you know of a convenient way to enable/disable CDDB? It is a (non tech) friend of mines installs (her work and home laptop) which is giving the problem. She works with kids and music, so needs to rip 'on the go' without internet access at times.

---

