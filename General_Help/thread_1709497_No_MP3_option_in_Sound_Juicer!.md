---
title: "No MP3 option in Sound Juicer!"
date: 2011-03-18
forum: General Help
---

### Post by gabriella on 2011-03-18
Why do I not see an MP3 option in the encoding preferences of Sound Juicer?
Whats wrong?

---

### Post by tredegar on 2011-03-18
You probably need to install the **ubuntu-restricted-extras** package
Otherwise, just install an MP3 encoder like **lame**

---

### Post by gabriella on 2011-03-18
> **tredegar said:**
> You probably need to install the **ubuntu-restricted-extras** package
Otherwise, just install an MP3 encoder like **lame**

Yes ubuntu-restricted-extras is already installed as is the ugly-set-universe.

Actually there seesm to be something funny going on here. I had been using Asunder to rip CD tracks but when I used iut the other day kept getting a low bitrate (96kbps) eben though I was using VBR at the highest quality setting. I tried unistalling/re-installing a couple of times but no luck.

Then removed it and tried Sound Juicer, hence my question above.

Also both Assunder and Sound Juicer seem to retain my prefference settings even though I've removed and re-installed.

So I'm wondering if there's something else going on?

---

### Post by tredegar on 2011-03-18
> Also both Assunder and Sound Juicer seem to retain my prefference settings even though I've removed and re-installed.
If you would like _everything_ removed, including your preferences for an application,  try **sudo apt-get purge *application_name*** which is supposed to wipe *everything* to do with that application.

Then re-install it.

If that fails, create a new user. Login as them. They'll have the system-default preferences set rather than the user-preferences. Try that.

Best wishes.

---

### Post by gabriella on 2011-03-18
> **tredegar said:**
> If you would like _everything_ removed, including your preferences for an application,  try **sudo apt-get purge *application_name*** which is supposed to wipe *everything* to do with that application.

Then re-install it.

If that fails, create a new user. Login as them. They'll have the system-default preferences set rather than the user-preferences. Try that.

Best wishes.

Thanks tredegar! I tried that and it did remove some configuration files but upon reinstallation my original preferences were still set. Strange?? 
Obviously some thing remains somewhere.

I suspect all this might be linked to my abnormally low bitrate issue
[http://ubuntuforums.org/showthread.php?t=1709784](http://ubuntuforums.org/showthread.php?t=1709784)

---

