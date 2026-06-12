---
title: "Problems with dual boot on laptop"
date: 2011-11-18
forum: General Help
---

### Post by Mazate on 2011-11-18
Ok, I finally took the plunge and attempted installation of Ubuntu along side windows 7 on my laptop.  As a side note, Ubuntu works perfectly on it.  Anyway, now that I've done it I have a small (or not so small problem).  When I select windows 7 to boot, the windows splash screen comes up and for a few seconds it appears to be loading.  Then, the screen goes dark and 3-4 seconds later the laptop shuts off.

Thats bad.

It's a Toshiba laptop but that's about all I know.  It's about a year old so not too ancient.  If anyone has any recommendations it would be most appreciated.

---

### Post by elliotn on 2011-11-18
try repairing windows and reinstall grub

---

### Post by Mazate on 2011-11-18
> **elliotn said:**
> try repairing windows and reinstall grub


What is the procedure for reinstalling grub?

---

### Post by rng on 2011-11-18
Can you try "safe booting" of windows7 ?

---

### Post by oldfred on 2011-11-18
If you can boot Ubuntu & it starts to boot Windows, reinstalling grub will probably not help. Grub has done its part as it is just a boot loader and once the system takes over it is finished.

Post this to see if the Windows install has all its files still.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by rng on 2011-11-18
If windows partition was shrunk (for ubuntu installation) without defragmenting it first, windows files could have been lost.

---

### Post by Mazate on 2011-11-19
> **rng said:**
> If windows partition was shrunk (for ubuntu installation) without defragmenting it first, windows files could have been lost.


Well, no I didn't defrag.  Wish I had known.  I did a windows repair and windows now loads fine.  However, when I go to shut down windows, it goes through its usual process, i.e. windows splash screen saying that it's shutting down.  Finally, it "shuts down" but the laptop doesn't shut off.  I have to manually hold down the power button to finish it off.  Anyone heard of this?

---

