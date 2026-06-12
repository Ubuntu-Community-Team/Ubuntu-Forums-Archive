---
title: "Some Programs not working"
date: 2010-12-03
forum: General Help
---

### Post by Coach_Mark on 2010-12-03
I wasn't sure where to put this one, so...

i keep trying to download mail (evolution) and it shows it's downloading, but nothing displays.  meanwhile, i have another program (3rd party) that sits there saying starting, but never does anything beyond that.  still yet another program (3rd party) won't even launch.  now, all 3 of these programs worked perfectly after i did a reinstall yesterday.  the reinstall included a complete run of updating Ubuntu (using 9.10).  but, since last night...nothing.

any ideas?

---

### Post by Coach_Mark on 2010-12-04
here is what evolution is doing...

I create the message...it says it's receiving the message...but there is no message in the inbox.  this happens every time i download fresh mail.

the puzzle is, when I first set it up, it worked just fine.  but no mail has arrived in the inbox (or any folder) for 3 days.  but it has at my yahoo account where this says it is pulling the mail from.

wth?

---

### Post by Coach_Mark on 2010-12-04
also...3 days ago, i installed and used another program (Think or Swim from TDAmeritrade).  I worked fine.  But, since then, any time I launch it, all I get is the box in this screenshot.  It came up the first time I launched it, loaded the new version and the program worked perfectly.  Now...all it does is sit there with this box showing on the screen...for hours.

wth?

---

### Post by HarrisonNapper on 2010-12-06
Bump.
 
I'm not sure on this one. For TOS, it could be unrelated. Try uninstalling and reinstalling it. But I've had that problem before in Evolution and it resolved itself. I haven't used Gnome or Evolution as my primary toolset in awhile, though; does anyone know where Evolution's connection logs are?

---

### Post by Coach_Mark on 2010-12-06
OK.  The mail thing seems to relate back to my provider.  There is a whole series of threads on the Evolution help site.  Apparently it doesn't work with their stuff anymore...so...switching to Thunderbird.  

still trying to figure out why other installed programs just hang there, though.  any help with that would be awesome.

---

### Post by Coach_Mark on 2010-12-07
I think I finally figured it out.  I created the folder needed for the program and then used "sudo" to install.  When it did, part of the installer was to create the folder for the program.  it created the folder again, but inside the folder i created.

so...how do i uninstall a 3rd party program so i can reinstall it without a program conflict?

---

