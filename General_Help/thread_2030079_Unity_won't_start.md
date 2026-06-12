---
title: "Unity won't start"
date: 2012-07-20
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-20
An update probably caused this, but I'm not 100% sure. All I know is after restarting I can't seem to get Unity running any more. I also wasn't able to find any working solution on the internet. Unity isn't running on my computer and can't be started. I'm missing top and side bar, alt+tab switcher isn't working and desktop effects are gone too.

I should mention that I tried installing the new Webapps feature following [this how-to]("http://www.omgubuntu.co.uk/2012/07/how-to-install-ubuntus-new-web-apps-feature").

When I try running unity after logging in, this is what I get:

> $ sudo unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : /usr/lib/compiz/libunityshell.so: undefined symbol: bamf_tab_close
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"

Some help please?

---

### Post by javi_m on 2012-07-20
Same problem here. I can't say what was the problem, since i've been playing with plank, some themes, and after that, unity won't start anymore

I also installed webapps

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-21
Bump?

This looks really nasty :( Reinstalling compiz isn't helping, reinstalling unity/ubuntu-desktop either. I can't find anything anywhere about undefined symbol: bamf_tab_close. Any ideas anyone?

---

### Post by aoniumo on 2012-07-22
Same problem here.

I have to switch to gnome+cairodock to have a functional desktop

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-22
I'm giving up. This appears to be a bug that occured in one of the updates. A fix might come along some time in the future, and then again, it might not. I couldn't find a solution for 5 days and it's taken a lot of my time and energy already. I'm just about to clean re-install Ubuntu 12.04 again.

---

### Post by chicco83 on 2012-07-27
Same problem here.
But today I enabled the proposed repo, run a sudo apt-get update, and then upgrade unity to version 5.14. Now it seems to run normally.

---

### Post by Chdslv on 2012-07-27
If you have Compiz installed, open the CCSM and check whether the Ubuntu Unity Plugin is checked or not. You can go to Unity 2D to check CCSM. Hope this helps.

If Cairo (Gnome+effects) is on, the Ubuntu Unity Plugin is automatically unchecked in the CCSM, and when Unity is one it is automatically checked. I've just updated and checked.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-27
I did and it was checked (enabled). Apparently it was a bug which was later fixed, but I've already re-installed my Precise.

---

### Post by Chdslv on 2012-07-27
Well, I  never had a problem with Ubuntu.

Good luck!:D

---

