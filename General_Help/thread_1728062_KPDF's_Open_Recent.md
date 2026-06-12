---
title: "KPDF's Open Recent"
date: 2011-04-13
forum: General Help
---

### Post by james_mcl on 2011-04-13
I realise KPDF is quite old now but as this issue may recur when I move to a newer distro (well, newer than Hardy) with Okular I thought I'd better ask.

I use Gnome, but prefer KPDF to evince when viewing PDF files.

However, KPDF's "Open Recent" list behaves very oddly - there's no apparent way to clear it, and items which were on the list one day aren't on it another day (coinciding with old items reappearing on the list).

Is there any way to clear this list?

Similarly, is there any way to clear the list of recently opened files in the "Location" drop-down box in File-Open? (which also seems to mysteriously lose list items inbetween reboots).

Thanks,

James McLaughlin.

---

### Post by james_mcl on 2011-04-13
Ah - I think I've solved it. It seems ~/.kde/share/config/kpdfrc has some sort of problem on my system - it shows up as an unopenable file called "No name" in Nautilus, but is visible as kpdfrc in File-Open dialogs. After an attempt to open "No name" with ghex2 brought this to light, it was an easy matter to make the changes required and save the file.

Cheers,

James McLaughlin.

---

