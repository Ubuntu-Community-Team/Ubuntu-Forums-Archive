---
title: "Why did Ubuntu install Namoroka?"
date: 2011-01-09
forum: General Help
---

### Post by sat_e_llite on 2011-01-09
So I booted up my Ubuntu PC and apparently there's a software update. I accepted and after it installed everything, I found that the Firefox logo turned into a plain blue globe, which is also the icon of experimental builds of Firefox.

I checked the version to be 3.6.14pre, this puzzles me as this appears to be a nightly build.

Is this because I have Minefield (Firefox 4 b9pre) installed?

By the way, this is the build identifier.
> #

#     Build identifier: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14pre) Gecko/20110107 Ubuntu/10.10 (maverick) Namoroka/3.6.14pre

---

### Post by marl30 on 2011-01-09
Seems like you added the Mozilla test PPA.

---

### Post by sat_e_llite on 2011-01-09
> **marl30 said:**
> Seems like you added the Mozilla test PPA. How do I revert back to a stable build?

---

### Post by marl30 on 2011-01-09
Did you use Ubuntu Tweak to install it? You could us it (Ubuntu Tweak) to purge the Mozilla PPA. Or manually go through your source list and remove the Mozilla PPA, then uninstall that version, and re-install the normal Firefox.

---

### Post by sat_e_llite on 2011-01-09
> **marl30 said:**
> Did you use Ubuntu Tweak to install it? You could us it (Ubuntu Tweak) to purge the Mozilla PPA. Or manually go through your source list and remove the Mozilla PPA, then uninstall that version, and re-install the normal Firefox. I don't have Ubuntu Tweak. I don't even know how Mozilla PPA got in my system.

I can't seem to find it in the Synaptic Package Manager. Maybe I'll give Ubuntu Tweak a try.

EDIT: I removed the source file using Ubuntu Tweak, uninstall Namoroka and re-installed Firefox. Is this how it should be done?

EDIT 2: I went into the software centre, I found PPA for Mozilla under installed software, Firefox is no longer under that and only XUL + XPCOM application runner is present, is this necessary or it's ok to remove it?

---

### Post by marl30 on 2011-01-09
> **sat_e_llite said:**
> I don't have Ubuntu Tweak. I don't even know how Mozilla PPA got in my system.

I can't seem to find it in the Synaptic Package Manager. Maybe I'll give Ubuntu Tweak a try.

EDIT: I removed the source file using Ubuntu Tweak, uninstall Namoroka and re-installed Firefox. Is this how it should be done?

EDIT 2: I went into the software centre, I found PPA for Mozilla under installed software, Firefox is no longer under that and only XUL + XPCOM application runner is present, is this necessary or it's ok to remove it?

Well, the Mozilla PPA isn't where you get the original Firefox from, so it's safe to remove that PPA. The regular Firefox is from the official Ubuntu PPAs.  I don't know what XUL + XPCOM are.

---

### Post by Frogs Hair on 2011-01-09
If you activate the daily build to install Firefox Beta 4 / Minefield it will also upgrade Firefox to Namoroka . This is not a bad thing if don't mind the updates. This thread has some good information. [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

