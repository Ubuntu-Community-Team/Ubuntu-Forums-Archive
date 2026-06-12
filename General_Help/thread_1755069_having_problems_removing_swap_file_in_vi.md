---
title: "having problems removing swap file in vi"
date: 2011-05-10
forum: General Help
---

### Post by caspian915 on 2011-05-10
Hi all,

I have been patiently trying to figure out how to tweak my version of ubuntu (currently 10.04 UNR) to play well with my Samsung N145. I managed to finally find the Samsung tools scripts that fix a few issues. However, a new one is caused wherein the fn keys dont' get released. I followed instructions to use vi to edit a keyboard release file. However, I now have an outdated .swp file that needs to be removed (from exiting the wrong way). I can't for the life of me get the damn thing to do what I want. Can someone please explain where I go from after the message I get below?

I read I have to "rm [name of file].swp" but vi tells me rm is not a command and pressing enter puts me into the non-swap saved version of this file.

> E325: ATTENTION
Found a swap file by the name "/lib/udev/rules.d/.95-keyboard-force-release.rules.swp"
          owned by: root   dated: Tue May 10 19:18:09 2011
         file name: /lib/udev/rules.d/95-keyboard-force-release.rules
          modified: YES
         user name: root   host name: Pierre
        process ID: 2379
While opening file "/lib/udev/rules.d/95-keyboard-force-release.rules"
             dated: Tue May 10 19:30:57 2011
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /lib/udev/rules.d/95-keyboard-force-release.rules"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/lib/udev/rules.d/.95-keyboard-force-release.rules.swp"
    to avoid this message.
"/lib/udev/rules.d/95-keyboard-force-release.rules" 38 lines, 2535 characters
Press ENTER or type command to continue

---

### Post by WorMzy on 2011-05-10
rm is a terminal command, not a vi command. execute it with :! or outside of vi.

---

### Post by caspian915 on 2011-05-10
Doh. That makes sense. This is my first time using vi. Thanks!

---

