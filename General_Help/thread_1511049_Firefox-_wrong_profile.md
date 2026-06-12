---
title: "Firefox- wrong profile"
date: 2010-06-16
forum: General Help
---

### Post by PDA1 on 2010-06-16
How do I force Firefox to recognize a certain default firefox profile I have?

For whatever reason I can't get FF to show all of the add-ons I have.  Yes, they are installed and they appear when as icons when I first boot up but after I close FF and start it again there are no icons (like Adblock).

Any ideas?

---

### Post by lovinglinux on 2010-06-19
Start Firefox from command-line with this:

```
firefox -P
```

Then select the profile you want and make it default, by ticking the option "Don't ask at startup".

You can also force a profile to be opened with this command:

```
firefox -P "profilename"
```

---

