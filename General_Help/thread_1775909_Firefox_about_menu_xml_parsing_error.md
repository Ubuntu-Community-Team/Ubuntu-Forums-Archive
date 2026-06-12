---
title: "Firefox about menu xml parsing error"
date: 2011-06-05
forum: General Help
---

### Post by Mountjudo on 2011-06-05
In firefox 5 beta there is an option to change "update channels." After trying to change mine from beta to stable, forgetting that I had installed it through a ppa (firefox-next) the about menu just died on me. 

Every time I open the about menu (help -> about firefox) I get the following error:

XML Parsing Error: undefined entity
Location chrome://browser/content/aboutDialog.xul
Line Number 41, Column 15:

            ```
  &channel.description.start;<label id="currentChannel"/>&channel.description.end;<label id="channelChangeLink" class="text-link" onclick="gChannelSelector.show();">&channel.change;</label>
```I have searched for a solution but the only thing that looks like it could help is either reinstalling firefox or resetting my preferences which I want to keep as a last resort.

Running wubi install of Ubuntu 11.04 (natty) with unity and firefox 5 beta (latest through firefox-next ppa).

Any ideas or help?

---

### Post by Mountjudo on 2011-06-21
Update:

I have created a new profile for Firefox and at the beginning it works fine but after some time the same problem with the about menu happens and I have also found that I cannot access my privacy settings in preferences. 

Any help? I'm out of ideas and though the problem isn't urgent it is quite annoying.

---

### Post by mfraser on 2011-06-22
Did an update in Kubuntu 11.04 this morning which upgraded Firefox to Firefox 5. Clicking Help > About Firefox

XML Parsing Error: undefined entity
Location: chrome://browser/content/aboutDialog.xul
Line Number 41, Column 15:              &channel.description.start;<label id="currentChannel"/>&channel.description.end;<label id="channelChangeLink" class="text-link" onclick="gChannelSelector.show();">&channel.change;</label>
--------------^

---

### Post by Mountjudo on 2011-06-22
I've had this problem for two weeks, nothing changed in those two weeks. 
The day you, Mr. Fraser, comment about it, Firefox sends out an update to fix it.
Thank you.

---

### Post by vic_xyz on 2011-08-12
Same problem for me, Ubuntu 11.04, upgrade Firefox to 5.

FIXED!

As I noticed the version of the language packages were still 4.0, after upgrading  firefox language packages (e.g. firefox-locale-en) through synaptic manager, the About Page works now ...:)

---

