---
title: "Update Manager Stalls"
date: 2011-05-12
forum: General Help
---

### Post by twistymcgee on 2011-05-12
I have Ubuntu 11.04 and I've been trying to apply the latest updates via the Update Manager.  When I click Install Updates, it starts going through the process and then seems to stall.  When I expand the details, it looks like it's displaying some Changelog information.  Nothing happens after that.  Anyone having a similar issue or could help me resolve the issue?

---

### Post by manzdagratiano on 2011-05-12
Open a terminal and run:

```

$ sudo apt-get update
$ sudo apt-get upgrade

```

This will give a more verbose output as regards what might be happening while updating your system.

---

### Post by twistymcgee on 2011-05-12
I get the same thing.  I see a percentage progress indicator saying "Reading Changelogs" and then when it gets to 100% it seems to display some change logs using "less" by the looks of things.  When I get to the end, I'm not sure how to get out of that view to carry on.  CTRL-C seems to make my terminal unusable.

---

### Post by twistymcgee on 2011-05-13
I have figured it out.  When the changelog displays, you have to hit the "q" key to exit displaying the changelog to continue with the update.  Seems to happen every update.  There must be a setting somewhere where I can change it to not display the changelog.

---

