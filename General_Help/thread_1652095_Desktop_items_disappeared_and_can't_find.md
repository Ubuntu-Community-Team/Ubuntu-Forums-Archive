---
title: "Desktop items disappeared and can't find"
date: 2010-12-24
forum: General Help
---

### Post by Pithikos on 2010-12-24
Today in the morning I went to start my computer. I noticed that I had forgotten the external hdd on through out the night. When I logged into ubuntu I heard some weird noise from the external hhd like it was reloading from the same area.
Then finally when everything was loaded the desktop didn't have any files or icons!:shock:
I don't understand this as my Linux installation is in an internal hhd. I restarted the computer and same thing. They are also missing from the Desktop folder. Any idea what happened?

This drives me nuts as I had many things on the desktop that was crucial!

Happy xmas btw! :P

---

### Post by Pithikos on 2010-12-24
**** I've become good at this 8)

I used *locate* and noticed that my Desktop folder was moved to some random folder for unknown reason. So just removing it again fixed it.

---

### Post by bilkay on 2010-12-26
> **Pithikos said:**
> **** I've become good at this 8)

I used *locate* and noticed that my Desktop folder was moved to some random folder for unknown reason. So just removing it again fixed it.
You're good, eh? :P

This should be so basic, so why can't I figure it out? I was messing around trying to see if I could share a common desktop with my server. Before I started, I had a "Desktop" folder in my home directory, and the contents of that folder (another folder and a picture or two) was all that showed up on my desktop.

I renamed "~/Desktop" to "~/Desktop.bak" and created a new "~/Desktop" folder as a mountpoint. After I mounted the remote "Desktop" folder there, I didn't like the results, so I put the original "Desktop" folder back where it was (i.e., renamed ~/Desktop.bak to ~/Desktop). But now, my desktop is cluttered with icons for all the files, links and folders in my home directory. If I move the icons to trash, what it was pointing to goes with it.

Ideas?

---

### Post by bilkay on 2010-12-26
> **bilkay said:**
> You're good, eh? :P

This should be so basic, so why can't I figure it out? I was messing around trying to see if I could share a common desktop with my server. Before I started, I had a "Desktop" folder in my home directory, and the contents of that folder (another folder and a picture or two) was all that showed up on my desktop.

I renamed "~/Desktop" to "~/Desktop.bak" and created a new "~/Desktop" folder as a mountpoint. After I mounted the remote "Desktop" folder there, I didn't like the results, so I put the original "Desktop" folder back where it was (i.e., renamed ~/Desktop.bak to ~/Desktop). But now, my desktop is cluttered with icons for all the files, links and folders in my home directory. If I move the icons to trash, what it was pointing to goes with it.

Ideas?
I found the answer: It's in ~/.config/user-dirs.dirs

This line: XDG_DESKTOP_DIR="$HOME/Desktop"

---

### Post by Pithikos on 2010-12-26
lol I guess in this thread we answer to our own questions ;D

---

### Post by the.scarecrow on 2011-01-10
Hey bilkay, you just rescued me with this thread. I think Cryptkeeper screwed my Desktop folder causing it to disappear from my Home folder dumping all my folders onto the Desktop. The solution is hard to find but this thread gave me the clue I needed.

I renamed the file ~/.config/user-dirs.dirs to ~/.config/user-dirsbak.dirs

Rebooted and the file was automatically re-created with all my folders going back into the right places.

Thanks

---

