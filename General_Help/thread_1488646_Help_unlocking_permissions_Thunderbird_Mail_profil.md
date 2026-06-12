---
title: "Help unlocking permissions Thunderbird Mail profile"
date: 2010-05-20
forum: General Help
---

### Post by SVEN1 on 2010-05-20
I am running Ubuntu 9.04. Uninstalled Thunderbird Mail 2.0. Saved my profile folder to my home folder.
It is padlocked I can't change permissions(now root owner) so I can swap the file with the new Thunderbird 3.0.4 I just installed.

Anyone help me with this?

---

### Post by thebigob on 2010-05-20
open a terminal and use the following command;

```

sudo chown -R "yourusername": "pathtofiletochangepermissionson"

```

---

### Post by SVEN1 on 2010-05-20
> **thebigob said:**
> open a terminal and use the following command;

```

sudo chown -R "yourusername": "pathtofiletochangepermissionson"

```


Is this correct?

sudo chown -R sven: /etc/thunderbird/profile

nothing happens

or 

sudo chown -R sven: /home/sven/etc/thunderbird/profile

I get not found

I'm still new at working the terminal

See screen shot for location and file

---

### Post by SVEN1 on 2010-05-20
Looks like it's now unlocked. I closed out the home folder to do something else then had to open it again for a photo and noticed the profile folder is now unlocked.
Not sure which command did it.

Thanks:)

---

### Post by dino99 on 2010-05-20
the last one was the good one

---

### Post by SVEN1 on 2010-05-20
OK, looks like I now have to do the same thing to the profile folder in the Thunderbird file before I can drop the old profile into.

=========================================================
I replaced the new 3.0.4 folder profile with the 2.0 profile. Nothing from inside that profile shown up when Thunderbird was opened.
Tried a number of times. That's ok, there was only a couple emails I wanted to retrieve in there anyways. I ended up replacing the new profile folder. Then just adding my email info back into Thunderbird. I was just experimenting today whether I wanted to use Thunderbird for all my email address'. I usually just go to my mail thru my browser.

---

