---
title: "Evolution calendar duplicate after system re-install"
date: 2011-02-06
forum: General Help
---

### Post by Aterus on 2011-02-06
I'm having a bit of a problem with Evolution. Recently i had to reinstall the system anew, after my upgrade to 11.04 Alpha. I've got things up and running, but after getting Evolution up, i now have two separate entries "On This Computer" in the calendar section. Each of them has a calendar, which is obviously one too much. Is it possible to delete one extra calendar? Right-click doesn't give me an option to delete, and purge functions does nothing as well.

Any suggestions?

---

### Post by Habitual on 2011-02-06
you *could try* this:

Exit Evolution.
Open a terminal

```
mv ~/.evolution ~/.evolution.org
```

Fire up Evolution and re-setup the account?

Just an option.
You'll "lose" any and all previous mail settings which can easily be returned by shutting down Evolution again and in terminal
```
mv ~/.evolution.org ~/.evolution
```

HTH

Peep this thread over at [Fedora*]("http://forums.fedoraforum.org/showthread.php?t=255609")
Post #4

---

### Post by dcstar on 2011-02-07
> **Aterus said:**
> I'm having a bit of a problem with Evolution. Recently i had to reinstall the system anew, after my upgrade to 11.04 Alpha.
........[LIST=1]


[*]"Alpha" software is called that for a reason - it is NOT ready for production use.
[*]**All** issues for pre-release software must be posted in that relevant support forum. The main forums are for released versions only.
[/LIST]

---

### Post by Aterus on 2011-02-07
I probably should have been more clear. I am using the stable version, 10.10. After testing 11.04 (and failing) i came back to the latest stable release.

Anyway, it seems i found the method to fix the issue. The reasons behind the extra "On this computer" appearing is an "extra" entry created in a configuration file after and update of Evolution.

Navigate to .gconf/apps/evolution/ - you may need to press Ctrl+H to see the hidden folders

Now enter the folder, that represents the the area of problem: calendar, address book etc.

Open %gconf.xml that is in the folder with a text editor

Navigate to the bottom of the file and you will see a duplicate entry "On this Computer". The original one is at the top of the file, the annoying one is on the bottom.

Delete the content (the duplicate entry at the bottom of the file) between the two <string> and </string> tags and save. I also delete the left over <li>/</li> tags just for the sake of tidiness.

Reboot the machine and launch evolution.


The problem should now be fixed. Use the same approach to fix duplicate address books, notebooks and so on.

---

