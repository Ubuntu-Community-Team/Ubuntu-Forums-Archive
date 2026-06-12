---
title: "Getting Firestarter with Synaptic"
date: 2009-09-10
forum: General Help
---

### Post by JoeHandford on 2009-09-10
Hi,

I have Universe enabled in Synaptic's repository list but I can't find Firestarter when I search. Can someone tell me what I might be doing wrong?

Cheers, Joe

---

### Post by misfitpierce on 2009-09-10
what happens when you just...

sudo apt-get install firestarter
 in terminal?

---

### Post by JoeHandford on 2009-09-10
Thanks Misfit,


That worked. apt-get appears to be a bit more reliable than synaptic for searching the repositories.


Cheers, Joe__

---

### Post by misfitpierce on 2009-09-10
Firestarter I think can be found in add/remove programs as well under applications

---

### Post by ajgreeny on 2009-09-10
I hope you didn't search for it as **F**irestarter.  Don't forget linux is case sensitive; firestarter is in there, but **F**irestarter is not!

---

### Post by mcduck on 2009-09-10
> **JoeHandford said:**
> Hi,

I have Universe enabled in Synaptic's repository list but I can't find Firestarter when I search. Can someone tell me what I might be doing wrong?

Cheers, Joe

Two things:

1. Don't use the quick search box, that's still a bit buggy. Use the proper search tool instead. (and make sure you are searching from package names, or package names & descriptions).

2. Make sure you have all applications selected on the left hand side panel. The search will only search from the packages/categories you have selected there. So if you, for example, have Graphics section selected the search won't ever find Synaptic (since it's not in that section).

---

### Post by chandru155 on 2009-09-11
Firestater is not a recommended one. Use gufw a Gui version of Ubuntu Firewall which is simple and powerfull.

---

### Post by XCan on 2009-09-11
gufw is simple, powerful... debatable. Guarddog would be the one I think of that can do everything firestarter can, but perhaps it's overkill?

---

### Post by Soul-Sing on 2009-09-11
> **XCan said:**
> gufw is simple, powerful... debatable. Guarddog would be the one I think of that can do everything firestarter can, but perhaps it's overkill?

Gufw is simple indeed, and as a project alive. (firestarter is not longer devel. for a long time now...) I strongly support (g)ufw.

---

### Post by Irvine_himself on 2009-09-11
I was researching Firestarter and Gufw and heard that there was some doubt as to whether Firestarter was a dead project?

I could not find an answer to this, but source forge now re-directs to    [http://www.fs-security.com/](http://www.fs-security.com/)    where the documentation page states that the docs were updated on the 8th of March 2009. This does kind of suggest that it has been re-started?

---

### Post by Soul-Sing on 2009-09-11
> **Irvine_himself said:**
> I was researching Firestarter and Gufw and heard that there was some doubt as to whether Firestarter was a dead project?

I could not find an answer to this, but source forge now re-directs to    [http://www.fs-security.com/](http://www.fs-security.com/)    where the documentation page states that the docs were updated on the 8th of March 2009. This does kind of suggest that it has been re-started?

The user man. is indeed recently updated. Not the project or devel.of firestarter.

---

