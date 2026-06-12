---
title: "Display and sound stop updating if no there is no input from keyboard or mouse"
date: 2010-09-20
forum: General Help
---

### Post by Xzenome on 2010-09-20
This is one of the strangest problems that I have ever had with Ubuntu, so strange in fact, I have no idea how to report the bug.

Since upgrading to the beta for the new Maverick Meerkat (I am fully up-to-date as of 10 minutes ago), I have had this problem. It exists from pretty much the start of the boot process, right through normal desktop use and then until the end of the shutdown process -- so all the time then.

I can't fully work out what is affected and what isn't.

[LIST]
[*]boot process repeatedly stalls unless a key is tapped
[*]music often/always gets stuck in a continuous loop, but then breaks that loop if a key is held down or the mouse is continuously moved -- occurs both in flash player and totem
[*]terminals only update their display when I move my mouse or press a key, so for example, I'm running aptitude safe-upgrade and it will look like it's stalled, but then I move the mouse and it suddenly prints however many lines of usual output
[*]when in battery mode, unless I keep moving the mouse the harddrive seems to spin down prematurely and more often that you would expect
[*]if left to its own devices, the computer will never complete the shutdown process, it will just hang -- if I press something like ctrl or esc regularly during the shutdown process, it will shut down with no problems.
[/LIST]

Hardware is a Lenovo Ideapad S12 (Intel Atom processor, Intel graphics). This behaviour is a regression from perfect behaviour under Lucid.

Help! I'm so confused.

---

### Post by Xzenome on 2010-09-20
Bug reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822)

---

