---
title: "I dont see any icons on muy desktop"
date: 2009-11-15
forum: General Help
---

### Post by alek66 on 2009-11-15
In another (futile) attempt to release some memory by unloading some programs off the memory, I deleted some entries that appear on the StartUp programs... I think i erased an entry that managed the desktop everything works fine... but I dont see any icons, and if I make a right click on the desktop nothing appear.

How can I fix this?

---

### Post by arnab_das on 2009-11-15
see if this works.

[http://ubuntuforums.org/showpost.php?p=8322915&postcount=2](http://ubuntuforums.org/showpost.php?p=8322915&postcount=2)

---

### Post by alek66 on 2009-11-15
> **arnab_das said:**
> see if this works.

[http://ubuntuforums.org/showpost.php?p=8322915&postcount=2](http://ubuntuforums.org/showpost.php?p=8322915&postcount=2)

Thanks for the reply, I checked that post, and no problems there.
I erased some line in the startUp program applet on System->Preferences.

Is there a way to set the default Back?

---

### Post by arnab_das on 2009-11-15
> **alek66 said:**
> Thanks for the reply, I checked that post, and no problems there.
I erased some line in the startUp program applet on System->Preferences.

Is there a way to set the default Back?

there is. press alt+f2

type "alacarte"

now select your system menu and add the programs you had deleted. its simply a matter of checking/unchecking the icons.

---

### Post by alek66 on 2009-11-15
> **arnab_das said:**
> there is. press alt+f2

type "alacarte"

now select your system menu and add the programs you had deleted. its simply a matter of checking/unchecking the icons.

We seem to be on different pages... i erased some lines from here (see the picture)
[IMG]http://img692.imageshack.us/img692/9528/screenshote.png[/IMG]

---

### Post by arnab_das on 2009-11-15
> **alek66 said:**
> We seem to be on different pages... i erased some lines from here (see the picture)


oops. my bad. well what you can do is reinstall those programs u have deleted, if u can remember them. otherwise reinstalling ```
sudo apt-get install ubuntu-desktop
``` is one way.

---

### Post by fluffman86 on 2009-11-15
alt+f2, "gnome-session-properties"

---

### Post by alek66 on 2009-11-15
> **fluffman86 said:**
> alt+f2, "gnome-session-properties"

yes I know... thats the applet. I can access it. I want to have the defaults entries there... there used to be more. I deleted some.

Thank U all

---

### Post by chinmaya_n on 2009-11-15
Try this:

1.alt+F2 (run) : type "gconf-editor"
2. goto apps > nautilus > preferences 
  then see the option "show desktop" in right pane..... if it is checked!
  if not you check it and close ..! 

Reply what happend... **Dont change other values!**
To my knowledge .... Your desktop should be back! :popcorn:

---

### Post by alek66 on 2009-11-15
> **chinmaya_n said:**
> Try this:

1.alt+F2 (run) : type "gconf-editor"
2. goto apps > nautilus > preferences 
  then see the option "show desktop" in right pane..... if it is checked!
  if not you check it and close ..! 

Reply what happend... **Dont change other values!**
To my knowledge .... Your desktop should be back! :popcorn:

there is no "show desktop".... can you guide me to add that entry?

---

### Post by nortexoid on 2009-11-15
If you kill nautilus (or it's otherwise not running) your icons won't show on the desktop. Another reason they won't show is if in gconf the key name show_desktop is set to false. To check whether the latter is the case, open gconf-editor (hit ALT+F2 and run it there) and look under apps/nautilus/preferences.

---

### Post by chinmaya_n on 2009-11-16
It is here : (it should be there!)
*gconf-editor*

apps > nautilus > preferences : see in right pane for "show desktop" and check it if unchecked !

**Dont change other values with out knowing what it does!**
See the attachment, and if you could not find that post your screenshot!

---

