---
title: "uninstall/reinstall cedega without wiping games?"
date: 2010-03-28
forum: General Help
---

### Post by kraylus on 2010-03-28
i just installed WoW via cedega and without the cds i had to download it. a whopping 7.5gb download!

in any case, i had problems with the launcher whining bout permissions. i tried a few things and now im at the point where cedega doesnt do anything anymore. you click play and nothing happens. doesnt even twitch. just sits there.

so i installed wine and ran wine wow.exe from the cli and works fine (go figure).

id still like to keep cedega around because i know from past experiences that there are games that itll run that wine wont.

but since its broken, how can i "reset" it to the way it was before i broke it? is there a way to uninstall and reinstall it without wiping out my WoW download? id hate to have to spend another four hours getting that.

edit: scratch that. after applying the patch, it doesnt go past the login screen. something about a missing library. sigh....

---

### Post by Ozymandias_117 on 2010-03-28
Assuming cedega works the same as wine... uninstalling it shouldn't get rid of your stuff. If you want to just make sure, rename the folder where it stores your games before you uninstall so it won't mess with it.

---

### Post by kraylus on 2010-03-28
well, as it turns out i figured out that problem. sort of

while i was still trying to get things to work, i remembered that i checked "native linux app" for ***** and giggles and cedega crashed when i ran wow. it was after that when it stopped working completely.

once i rechecked native linux app, wow started working fine.

of course, everytime i patched wow, itd run the launcher when it was done and id have to re-chmod the directories.

otherwise, it runs flawless.

graphical glitches here and there, but thats to be expected. just happy its working. lower fps than in windows, but much better latency.

now if you can tell me why i have to tell cedega to run wow as a native linux app id be impressed.

deuces!

ryan

---

