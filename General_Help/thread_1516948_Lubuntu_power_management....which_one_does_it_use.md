---
title: "Lubuntu power management....which one does it use?"
date: 2010-06-24
forum: General Help
---

### Post by Linuxperiment on 2010-06-24
Hi, I'm trying to do one of the fixes in the sticky about this issue:

--------------------------------------------
Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.

Current workaround is to open gconf-editor and browse to:
Code:

/apps/gnome-power-manager/general

And de-select the option use_time_for_policy
--------------------------------------------

I do not know the name of the power management it uses (i'm not sure if it uses the gnome power manager or not), so can anyone tell me? Thanks!

---

### Post by KIAaze on 2010-07-13
You might have more luck posting to their mailing-list: [https://launchpad.net/~lubuntu-desktop](https://launchpad.net/~lubuntu-desktop)

I'm currently also looking for how to configure power management on Lubuntu.

---

### Post by kerry_s on 2010-07-13
> **Linuxperiment said:**
> Hi, I'm trying to do one of the fixes in the sticky about this issue:

--------------------------------------------
Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.

Current workaround is to open gconf-editor and browse to:
Code:

/apps/gnome-power-manager/general

And de-select the option use_time_for_policy
--------------------------------------------

I do not know the name of the power management it uses (i'm not sure if it uses the gnome power manager or not), so can anyone tell me? Thanks!


yes, it uses "gnome-power-manager".
press-> **alt+f2**
type-> **gconf-editor**

if nothing happens, then it's not installed, which i don't think it is on the default lubuntu. use synaptic to install it & try again.

---

### Post by KIAaze on 2010-07-14
Yes, gconf-editor is indeed not installed by default under Lubuntu.

I tried changing all "suspend" strings in /apps/gnome-power-manager/ to "nothing" and deactivating the lid action running gconf-editor with and without sudo, but it didn't seem to work.

Temporary radical solution I used:
Added "exit 0" at the beginning of "/usr/lib/pm-utils/bin/pm-action"

This worked.

---

### Post by KIAaze on 2010-07-15
There is actually a power management GUI in Lubuntu:
Click on the icon of the battery in the notification area (bottom right), and click on Preferences to open the GUI.

Now I also know why I didn't notice it at first: The battery icon only shows up if the battery is charging or discharging... The icon behaviour can be changed in the power management GUI.

---

### Post by aeiah on 2010-07-15
as stated, you can get to it from the panel (if its visible). you can also launch the settings window with ```
gnome-power-preferences
```

---

### Post by hornbutu on 2012-11-04
although Ive checked and I do have gnome-power-mangement installed, when I type the code nothing worked.

Any ideas?

---

### Post by overdrank on 2012-11-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

