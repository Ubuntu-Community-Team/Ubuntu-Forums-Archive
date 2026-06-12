---
title: "Edit Grub2 entries?"
date: 2009-12-23
forum: General Help
---

### Post by MaxRabbit on 2009-12-23
My Backtrack 3 entry after installing Ubuntu is configured improperly and will not boot. However, I know what I need to change in order to get it to work. But how do I change it? Everywhere I look, I see that I shouldn't touch the grub.cfg, and I can't edit it even if I try. It won't save, even using "gksudo gedit".

Appreciate the help!
max

---

### Post by quixote on 2009-12-24
Yeah, in terms of the interface, I'd say that Grub wasn't all that broken, but they fixed it anyway.  :P

Grub.cfg is made to be updated by running update-grub, and that gets any custom instructions from /etc/default/grub and, if I remember right, perhaps also in /etc/grub.d/.  There are detailed instructions [here]("https://help.ubuntu.com/community/Grub2#File%20Structure"), based on [this forum post]("http://ubuntuforums.org/showthread.php?t=1195275").  The main section of interest to you, I think, is the "File Structure" part in the first link.

---

### Post by MaxRabbit on 2009-12-25
> **quixote said:**
> Yeah, in terms of the interface, I'd say that Grub wasn't all that broken, but they fixed it anyway.  :P

Grub.cfg is made to be updated by running update-grub, and that gets any custom instructions from /etc/default/grub and, if I remember right, perhaps also in /etc/grub.d/.  There are detailed instructions [here]("https://help.ubuntu.com/community/Grub2#File%20Structure"), based on [this forum post]("http://ubuntuforums.org/showthread.php?t=1195275").  The main section of interest to you, I think, is the "File Structure" part in the first link.
Thanks a lot :) But I ended up just making grub.cfg not read-only, and editing it manually. This is Linux, you're supposed to get down and dirty if you want; and despite all the warnings of not touching grub.cfg, it is working fine :guitar:

---

### Post by ranch hand on 2009-12-25
This will NOT work.  The next time update grub is run, such as for a kernel update, it will be  overwritten and changed back to read only.

This is as it should be.

I have no idea what " Backtrack 3" is but what you need to do is go to /etc/grub.d/40_custom and put your correct entry in there and then run "sudo update-grub".  You should see a couple o things then.
A>/boot/grub/grub.cfg now is back to what it was and read only
B>/boot/grub/grub,cfg now has your proper entry at the end of the menu

I would save the 40_custom file, after editing to some other name so that you still have that file to use for something else if the need arises.

Your entry must start with;
```

echo "Adding Lxde on sda8" >&2 
cat << EOF

```
editing the stuff between the "  " to match the stuff in the same place in the entry you put in the grub.cfg file.

That entry should be copy/pasted in next and then, on the line below the "}" put;
```

EOF

```
You need to make sure that the permissions of your new file are executable as a program for it to work.

See my sig for more basic info on grub2.  The first 2 links in my post are the best in depth info on grub2 you can get.

The second one is the second link given by quixote and the first one he gave is mainly by the same feller, drs305.  He has been playing with grub2 since Karmic-testing Alpha2 when we got grub2 introduced to us.  It was a rough ride for a while.

Grub2 is very different.  It is also more flexible than grub-legacy which is no longer supported by anyone.

That said, if you just do not want to learn something nes or for some reason just hate grub2 there is a link in my post that will guide you in reverting to grub-legacy.  There is a title of some kind above it.

It is written by kanasnoob, another karmic-testing veteran.  Follow that and you will revert in good shape.  There is at least one pitfall that you will miss by his instructions.

---

### Post by quixote on 2009-12-26
Thanks for that, ranch hand!  Nice summary of the really necessary info in your sig link.  I get that grub2 brings all sorts of improvements -- grub-legacy dates from 1995 or something, right? -- but changing habits is always a stretch. :D

---

### Post by ranch hand on 2009-12-26
I was, like drs305 and kansasnoob, introduced to grub2 at Karmic-testing Alpha2 when it was unleashed on the world.  NO documentation worth a dime except Hermans stuff.  Rough ride for a while there.  We made all the mistakes you can make.

Os-prober is not part of the grub project and it is the biggest problem.  I fell in love with the "generic" or "symbolic" menu entries early on.  They never need upgrading.  You can format and install another (Debian based) OS and not have to edit that entry.  I do like to edit the label part of it but that has nothing to do with the operation of grub.

It helps if you just try to think of it as not being related to grub-legacy at all.

Grub-legacy, by the way, was almost as popular as a turd in the punch bowl when introduced.  I have seen some of it in achieves when it replaced lilo.

---

### Post by MaxRabbit on 2010-01-03
Thanks a lot, ranch hand. Can't say I understood all that you said, but enough to figure out how to fix my problem the correct way :)

---

### Post by ranch hand on 2010-01-03
Great.  Nothing like a system that works.

---

