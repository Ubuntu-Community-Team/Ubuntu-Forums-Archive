---
title: "HELP(no launcer)"
date: 2012-05-12
forum: General Help
---

### Post by gruntb23 on 2012-05-12
How do you reset 12.04 back to all default settings. Im asking cause my windows controls are gone as well as the application launcer on start up. I have to run programs through the terminal which i am not very good with.

---

### Post by Enigmapond on 2012-05-12
Try this in the terminal:

```
unity --reset
```

---

### Post by gruntb23 on 2012-05-28
I tried that a few times this is what i get then it just stays there  unity --reset unity-panel-service: no process found Checking if settings need to be migrated ...no Checking if internal files need to be migrated ...no Backend     : gconf Integration : false Profile     : default Adding plugins Initializing core options...done Initializing composite options...done Initializing opengl options...done Initializing decor options...done Initializing vpswitch options...done Initializing snap options...done Initializing mousepoll options...done Initializing resize options...done Initializing place options...done Initializing move options...done Initializing wall options...done Initializing grid options...done Initializing session options...done Initializing gnomecompat options...done Initializing animation options...done Initializing fade options...done Initializing workarounds options...done Initializing scale options...done compiz (expo) - Warn: failed to bind image to texture Initializing expo options...done Initializing ezoom options...done compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2600a98  compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2600aa6

---

### Post by MadmanRB on 2012-05-28
you are having issues with unity, to bypass it might be wise to install something like xfce so you can have another session to load with a GUI.
You may have to remove your hidden unity folder, but we will get to that later after you install XFCE

---

### Post by gruntb23 on 2012-05-28
I do not have a gui. The only reason I can use the internet is thankfully because when typing firefox in the terminal firefox opens. I can't access anything else because I don't really know the terminal that well and the program launcher(the bar to the left of the screen) is missing

---

### Post by ExSuSEusr on 2012-05-29
Open your terminal.

Copy and paste this into the terminal.  Hit enter.  Type in your password.  It might take a few to download depending on your connection speed.

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

Once it is complete - log out / power down.  Power back up and at the splash screen where it asks you to choose a user click on the little icon and select "Cinnamon" - then log in.

It isn't Unity, but it will give you a "desktop" to work with.

---

### Post by gruntb23 on 2012-05-29
Thank helped me get somekind of a desktop back, thank you. Now how do I go about finding out what went wrong so I can get unity back?

---

### Post by adit on 2012-05-30
> Now how do I go about finding out what went wrong
Immediately before the problem occurred, what are the packages you have installed?  Did you use gconf-editor immediately before the problem occurred?

---

