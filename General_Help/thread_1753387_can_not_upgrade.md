---
title: "can not upgrade"
date: 2011-05-08
forum: General Help
---

### Post by mk631219 on 2011-05-08
I have tried to upgrade my ubuntu 10.4 lucid lynx to maverick meerkat 10.10 and can not seem to get it to do so. I have tried different things that should have worked but for one reason or the other they do not work.
Just now I tried to do the following with no result but an error message.
                     p { margin-bottom: 0.08in; }   

  Perhaps the command line would work. First install aptitude, if it's not already installed (via the command line, "sudo apt-get install aptitude"). Then, install gksu, then try pressing Alt-F2 and entering "gksu gedit" (this is to run the text editor gedit with root and/or superuser priviledges -- which works in Debian, though frankly I'm not sure about Ubuntu with its sudo setup). Anyway, from here open the file /etc/apt/sources.list. In it, replace the instances of "lucid" with "maverick" (lucid being the name of 10.04, and maverick being the name of 10.10). Having done this, save it, and close gedit. Then open a terminal, and type "sudo aptitude update". Then, "sudo aptitude install apt aptitude". Then, "sudo aptitude safe-upgrade". Finally, "sudo aptitude full-upgrade".

As always, backup your important files first. Note, if in any of the steps above with aptitude, you're given a warning that half your system will be eliminated followed by the question "Accept this solution? [Y/n/q/?]", then by all means press "q" and don't proceed. At that point, rather than feeling that you must have the latest, it's best to simply abide by the old maxim "If it ain't broke, why fix it?"
  Could this be because I upgraded it from ubuntu 8.4 originally?

---

### Post by wilee-nilee on 2011-05-08
Go to software sources in menu-systems-admin-software sources. As the screen-shot shows, you want this line with the arrow pointing to read this way. Mine says root:software sources, I got to it from the repository in the settings dropdown in synaptic.

Make sure you are fully updated and upgraded in lucid, then use the update manager to upgrade; it should show the upgrade to maverick.

I will say though if it was me I would have everything backed up just to be safe.
[ATTACH]191612[/ATTACH]

---

