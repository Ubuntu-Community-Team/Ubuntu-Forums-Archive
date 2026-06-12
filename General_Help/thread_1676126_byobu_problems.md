---
title: "byobu problems"
date: 2011-01-26
forum: General Help
---

### Post by memilanuk on 2011-01-26
Hello all,

I've got an older PC running as a server downstairs in my house, with a fresh (as of last night) install of Ubuntu 10.04 LTS server on it.  For other reasons, I wiped the existing install and started fresh.  Once I got it rebooted and operational, I connected via ssh from my Macbook and commenced getting all the applicable updates for it (took a while!).  So, once everything is up-to-date, I installed screen and screen-profiles, and then tried running 'byobu-config' as the main user.  The problem is... when I go into the curses-based menu system and go to the 'Create New Windows' and select the various options (doesn't seem to matter which), the program dumps me to a distorted version of the #2 screen (top).  When I 'q'uit that it drops me back to a cli prompt with some errors about /home/username/.byobu/windows not existing, but not displaying anything I type.  It shows the error responses if I mis-type things (typing blind here, gimme a break ;) )but  it doesn't show my actual typing.  Ultimately, if I exit/quit enough it drops me back to my shell prompt in Terminal.app on my Macbook.

I've used screen-profiles before (including from the macbook), and never had any troubles setting things up.  Plain ole 'screen' still seems to work fine... any ideas as to what might up this time?

TIA,

Monte

---

### Post by nothingspecial on 2011-01-26
Same here, although I don`t use byobu-config.

editing .screenrc works.

Report a bug.

Launching byobu and pressing F9 and doing it that way does :P

---

### Post by memilanuk on 2011-01-26
unfortunately, F9 does something else inside OS X so it doesn't work as advertised inside Terminal.app/byobu.  There's probably a way around it, but its not something I've spent much time worrying about.

---

### Post by Habitual on 2011-01-26
Delete ~/.byobu and start over?

---

### Post by memilanuk on 2011-01-26
Actually... there is no ~/.byobu to begin with. 

Shouldn't that have been created somewhere along the line by one of the packages?

---

### Post by Habitual on 2011-01-28
It's not created until you run byobu or one of its companion utilities.

---

