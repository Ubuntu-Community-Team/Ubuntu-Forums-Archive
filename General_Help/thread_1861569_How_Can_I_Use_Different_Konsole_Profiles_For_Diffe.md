---
title: "How Can I Use Different Konsole Profiles For Different Applications?"
date: 2011-10-15
forum: General Help
---

### Post by dniMretsaM on 2011-10-15
Before when I wanted to create a launcher for a terminal application that would launch it in it's own Konsole profile, I would set a terminal option (Icon Settings -> Application -> Advanced Options -> Terminal -> Terminal options) for it like this: [FONT=Courier New]--profile name[/FONT]. So right now I'm trying to set up a launcher for Emacs to open in it's own profile (named "Emacs"). The command for the luncher is [FONT=Courier New]emacs -nw[/FONT] and [FONT=Courier New]--profile Emacs[/FONT] is the option. It still loads in the default "Shell" profile. I know it's not an Emacs only problem as I get the same results with other applications such as Lynx. Did something change from KDE 4.6.x to 4.7.x? How can I fix this problem?

---

### Post by dniMretsaM on 2011-10-16
Bump.

---

### Post by dniMretsaM on 2011-10-17
Bump.

---

### Post by dniMretsaM on 2011-10-18
Annnndddd......... Bump.

---

### Post by vehemoth on 2011-10-22
It works fine for me well sort of.
When I run the exec command ( -e ) it won't run in any profile.
So what I did was I created the htop profile (should work the same for emacs) and in the command section (where it has /bin/bash etc.) I replaced it with htop.
Now when I run konsole --profile "htop" it spawns a new window using the profile htop and with htop running in it.

---

### Post by dniMretsaM on 2011-10-22
> **vehemoth said:**
> It works fine for me well sort of.
When I run the exec command ( -e ) it won't run in any profile.
So what I did was I created the htop profile (should work the same for emacs) and in the command section (where it has /bin/bash etc.) I replaced it with htop.
Now when I run konsole --profile "htop" it spawns a new window using the profile htop and with htop running in it.

That's a good idea. I'll give it a try.

---

### Post by dniMretsaM on 2011-10-22
Well, I ended up having to create an Emacs.profile in ~/.kde/share/apps/konsole/. Apparently creating a profile thought Konsole's interface doesn't create one so you can't access it through the command line. Kind of a pain, but I got it to work (finally).

---

