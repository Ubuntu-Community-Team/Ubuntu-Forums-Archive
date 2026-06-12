---
title: "&quot;Open containing folder&quot; in Firefox doesn't work"
date: 2010-02-23
forum: General Help
---

### Post by Objekt on 2010-02-23
Lately I've noticed that the "open containing folder" right-click menu item doesn't work in Firefox 3.6.  It does nothing.  That action used to open Nautilus, showing the folder where the file had been downloaded.

What gives?  I set up Firefox long ago to call Nautilus when asked to open a folder.  Shouldn't Firefox be asking me what app to use, if it weren't set up properly?

---

### Post by Objekt on 2010-03-02
Anyone?  Bueller?

I can't believe something so simple is broken.  Isn't there any way to fix it?

---

### Post by Objekt on 2010-03-19
I know I'm not the only one having this problem.  The standard fix* doesn't work.  There must be some other way.

*Usually you see suggestions to manually create Booleans and strings in Firefox's "about:config" page, which supposedly tell Firefox to launch Nautilus when you try to open something from the Tools->Downloads window.  I did that weeks ago, but it had no effect on the problem.  I can't open things I just downloaded, or the folder they're in, from the Downloads window.  It's very annoying.

---

### Post by Objekt on 2010-03-31
Last night, I noticed that this problem does NOT exist, running Firefox or Swiftfox under Ubuntu Netbook Remix 9.10 on my Aspire One.  Nautilus opens, as it should, in the circumstances described above.

Is this bug possibly unique to Ubuntuzilla-installed versions of Firefox?  I don't see why it would be, but then that's why it's a bug.

I'm really, really tired of talking to myself here.  Hasn't someone else had this problem?

---

### Post by lovinglinux on 2010-03-31
The about:config settings suggested on other forum posts doesn't work here either. You need to go to Applications tab in  Firefox Preferences, then browse the "file" content type, then click the corresponding action menu, select "Use other", browse /usr/bin/nautilus.

I don't think is an Ubuntuzilla bug, since the same problem happens here with Firefox 3.6 from the firefox-stable ppa and with the binaries downloaded from Mozilla site.

---

### Post by Objekt on 2010-03-31
That worked!  THANKS!  :D

---

### Post by ngc on 2010-04-18
Thank you, this fixed the problem for me in Kubuntu 9.10 as well (obviously, setting the target to dolphin rather than nautilus).

---

### Post by alexxroche on 2010-07-13
Thank you [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), you cylons really ARE helpful ;-) (Your advice fixed a similar problem for me.)

---

### Post by lovinglinux on 2010-07-13
> **alexxroche said:**
> Thank you [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), you cylons really ARE helpful ;-) (Your advice fixed a similar problem for me.)

You are welcome.

---

