---
title: "A Bit Confused - 64 Bit Thunderbird"
date: 2010-12-13
forum: General Help
---

### Post by Quarkrad on 2010-12-13
Just install 64 bit 10.10 and have this version of Thunderbird **Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101208 Thunderbird/3.1.7** which to me looks like the 64 bit version.  Before I clean installed 10.10 64bit I backup up my old 32 bit /home/.Thunderbird folder.  I copied this backup folder to my new 64 system and all my mail was there as before.  I discovered that the Calendar was not working and un-installed.  I cannot install the Calendar from Thunderbird/Tools/Add-ons/Install - onto the Mozilla web site and download the latest calendar tool.  I have googled and found the 64 bit Calendar  **lightning-1.0b2-tb-linux.xpi** but Thunderbird will not install that either. I get the message** Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem.**  So I'm slightly confused about getting the Calendar on my 64 bit Thunderbird.

---

### Post by Quarkrad on 2010-12-14
bump

---

### Post by wojox on 2010-12-14
lightning-1.0b2-tb-linux.xpi is still in beta. Try installing from the repo's.

---

### Post by SlugSlug on 2010-12-14
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

---

### Post by Quarkrad on 2010-12-14
sluslug - I tried installing from your link and I got **Lightning 1.0b1 could not be installed because it is not compatible with Thunderbird 3.1.7**. Also (I'm a newbie) not sure how to download from repositories.

---

### Post by SlugSlug on 2010-12-14
sorry my bad,

use this one
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)

---

### Post by uRock on 2010-12-14
I haven't had any trouble.

---

### Post by InonS on 2010-12-15
In Lucid Lynx

When I try to update from the Thunderbird 3.1.7 64 bit add-on menu I get:
> Lightning could not be installed because it is not compatible with  your Thunderbird build type (Linux_x86_64-gcc3). Please contact the  author of this item about the problem

When I try to update by clicking the .xpi file directly from the repo using Firefox 3.6.13 I get:
> Lightning 1.0b2 could not be installed because it is not compatible with Firefox 3.6.13.

Footnote:
In Windows XP, however, it works properly. (maybe the FF or TB versions I'm using under XP are not the same as the ones I'm using in Ubuntu -- I'm not sure right now...)

---

### Post by Quarkrad on 2010-12-15
Thank you for that last link - I now have a calendar. :)

---

### Post by SlugSlug on 2010-12-15
[InonS]("http://ubuntuforums.org/member.php?u=1206247")

Right clcik the file and save as.. 

then in thunderbird , tools > addons > install>

browse to where u just saved that 10b2 file

---

### Post by InonS on 2010-12-15
SOLVED.

Thanks guys!

Some one should get mozilla to fix that -- I ran into it in installing some other add-ons --
If it's an add-on for TB, then FF should know not to try to install it on itself. Rather, it should check if TB is installed, and if it is, launch the TB add-on installer. At the very least, it should give a better message to the user. Something like
> This is an add-on for TB. Save it to disk and install from within TB.
Instead of the wholely misleading
> Lightning 1.0b2 could not be installed because it is not compatible with Firefox 3.6.13.
which I got...

---

