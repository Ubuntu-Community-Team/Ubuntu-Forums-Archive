---
title: "Update Manager &quot;Check&quot; button not working in Natty."
date: 2011-06-21
forum: General Help
---

### Post by Zerauskire on 2011-06-21
I can open Update Manager fine and it runs though it's little gambit of "Building data structures" etc... 

Up at the top it says "The package information was last updated 13 hours ago."

Before I updated to Natty I used to be able to just click on the "Check" button and it would prompt me for my password and then check for updates.

Now if I click the "Check" button it goes grey for a bit, never asks me for my password and then just comes back up with the same "The package information was last updated 13 hours ago." message.

However, if I actually load up the terminal and type out "sudo apt-get update" then go back and load the Update Manager again it will say "The package information was last updated less than one hour ago." which is what should be happening when I click the "Check" button.

I've tried deleting my lists but this didn't resolve the issue. Any clue what else could be happening here?

I also noticed that I had some updates available when I loaded Synaptic Package Manager that didn't show up when i loaded the Update Manager.

I've also tried re-installing update-manager. I've gone as far as to do a complete removal and installed it again. Still not working right.

I think it has something to do with the fact that it's not prompting me for my password like it used to...

---

### Post by Zerauskire on 2011-06-23
Ok. So here's the deal. Since it was not prompting me for the password I wanted to see how it was launching.

In the properties of the "Update Manager" icon I noticed that all it had in the command line was "/usr/bin/update-manager".

If I open the termnial and type in "sudo update-manager" it would work fine. So i changed the command to "su-to-root -X -c /usr/bin/update-manager" and this seems to be working fine now. 

Is there any problems with doing it this way? Also, can someone look at the properties of their update-manager launcher and see if the command is different than mine?

I know there is also a gksu command that can be used for similar results. I just want to make sure that even though what i'm doing works, it's the right way to do it.

Thank you!

---

