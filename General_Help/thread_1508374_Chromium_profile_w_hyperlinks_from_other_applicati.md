---
title: "Chromium profile w/ hyperlinks from other applications"
date: 2010-06-12
forum: General Help
---

### Post by hunteke on 2010-06-12
I recently started using Chromium after I noted it's speed.  ZOMG is it fast and stable!  However, one killer feature (for me) of Firefox is the ability to use multiple profiles.

I found out that I can do this with Chromium via the command line option [FONT="Courier New"]--user-data-dir[/FONT].  For example:

```
$ chromium-browser --user-data-dir="$HOME/.config/chromium/class123Paper"
```

However, this doesn't appear to register with my Lucid desktop the fact that it's running, so anytime I click a hyperlink from another application, Chromium starts up with the default configuration (equivalent to [FONT="Courier New"]--user-data-dir=$HOME/.config/chromium[/FONT]).

What happens when I do likewise with Firefox is that the first profile opened registers itself, then other applications open hyperlinks in a new tab of the first profile open.  If I  have multiple profiles open, the first one still gets the click event.  If close the first profile, then the second one gets the click event.

I **very** much appreciate having profiles, so does anyone know how to mimic this Firefox profile-handing behavior with Chromium?

---

