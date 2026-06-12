---
title: "Lost Alt-Tab behavior; can't make any key combination switch windows"
date: 2012-05-10
forum: General Help
---

### Post by okok on 2012-05-10
I installed 12.04 a few days ago. At some point, I am not sure how, I lost the ability to switch between open windows using Alt-Tab. I am using Gnome Classic, but the same is true about unity.

I tried different suggestions I already found: to assign Alt-Tab to various window-swtiching options in System Settings -> keyboard -> shortcuts; to use gconf-editor and assign it to apps -> metacity -> global_keybindings -> switch_windows; to change settings in CompizConfig (which can be installed, but won't run in 12.04).

What else can I do to get back the ability to switch windows by using the Alt-Tab combination?

So far not only am I unable to make the old funcionality of Alt-Tab return, I have also failed in assining other key combinations to the window-switching action, which renders my OS almost unuable for me.

Any idea?

---

### Post by apochry on 2012-05-10
Metacity shouldn't have anythig to do with that since Unity 3D and Gnome Classic (as far as I know) use Compiz.

CompizConfig (CCSM) should, most definitely, run in 12.04. If it doesn't something is wrong with your Compiz installation.
You can try to reinstall it. For how to do that you will need to dig deeper in the forums.

- Christo

---

### Post by okok on 2012-05-10
> **apochry said:**
> Metacity shouldn't have anythig to do with that since Unity 3D and Gnome Classic (as far as I know) use Compiz.

CompizConfig (CCSM) should, most definitely, run in 12.04. If it doesn't something is wrong with your Compiz installation.
You can try to reinstall it. For how to do that you will need to dig deeper in the forums.

- Christo

Thank you very much. I was eventually about to solve this problem, and a host of other strange window behaviours, by doing the following:

1. Running GConf Cleaner
2. Making CCSM work by [changing the locale to en_US]("http://ubuntuforums.org/showpost.php?p=10731896&postcount=3")
3. setting up the behaviours I wanted in CCSM

---

### Post by apochry on 2012-05-11
I'm glad that the issue is resolved!

Please mark this thread as** [SOLVED]** using the "Thread Tools" above the first post.
Thank you.

- Chtisto

---

### Post by zman58 on 2012-06-17
I was able to get the alt-tab working properly with Gnome 3 Classic (with effects) by following post #10 by mc4man in the following thread:
[http://ubuntuforums.org/showthread.php?t=1953792&highlight=alt-tab+gnome+classic](http://ubuntuforums.org/showthread.php?t=1953792&highlight=alt-tab+gnome+classic)

Here are the steps required:
Start gconf-editor and navigate as follows...
gconf-editor -> /apps/compiz-1/general/screen0/options/
Now add an additional value string to "active_plugins" called: staticswitcher. It will end up at the end of the existing list of values.
Exit from gconf-editor.

Afterwards you can start using the Alt-Tab and it will switch applications properly. No restart or logout is required.

Much thanks to mc4man!

---

### Post by dimples7848 on 2013-02-22
Stumbled across this thread because I could get back to my normal <Alt>Tab windows switcher after upgrading to 12.04. Many thanks for this solution.

---

