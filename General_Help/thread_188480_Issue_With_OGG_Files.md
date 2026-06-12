---
title: "Issue With OGG Files"
date: 2006-06-04
forum: General Help
---

### Post by OffHand on 2006-06-04
Hi

Whenever I try to launch an OGG file it changes the note icon into a text file icon and the file size changes to 0 bytes. I also get this error message:

[i]The filename "01 - Track 1.ogg" indicates that this file is of type "Ogg multimedia". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/i]

Does anyone know how I can solve this issue?

---

### Post by blackjack6.21.91 on 2006-06-04
The error thinks that you are trying to play an empty file.  Change *.ogg to *.txt, open it, and see if there is anything there.  If it says something else, just tell us.

---

### Post by OffHand on 2006-06-04
[QUOTE=blackjack6.21.91]The error thinks that you are trying to play an empty file.  Change *.ogg to *.txt, open it, and see if there is anything there.  If it says something else, just tell us.[/QUOTE]
It's an empty text file... after the double click. Before that it shows the right file size.

I think I found what may have caused the issue. When I right click I have the option: open with 'script'. I think I changed something when I was trying to get scripting in Nautilus to work. I cannot remember what though. Is OGG somehow associated with scipting or with the command script?

---

### Post by blackjack6.21.91 on 2006-06-04
move all of the files from
~/.gnome2/nautilus-scripts
onto your desktop (or somewhere safe)
did that fix the problem??

---

### Post by OffHand on 2006-06-04
[QUOTE=blackjack6.21.91]move all of the files from
~/.gnome2/nautilus-scripts
onto your desktop (or somewhere safe)
did that fix the problem??[/QUOTE]
There are no files in that folder. I think I remember what I did (although I am not 100% certain). I might have right clicked a OGG file, went to properties, open with, add, use a custom command  >> script.

---

### Post by blackjack6.21.91 on 2006-06-04
Then right click another ogg, click open with, and set it to your music player.

---

### Post by OffHand on 2006-06-04
[QUOTE=blackjack6.21.91]Then right click another ogg, click open with, and set it to your music player.[/QUOTE]
OMG!! What was I thinking... Ok, it's Sunday morning.... yeah... that's it!
Thanks man  :mrgreen:

---

### Post by blackjack6.21.91 on 2006-06-04
No problem dude.  Thank insomnia that I'm conscious enough to help you.  And thank linux that I'm not in bed w/ someone :).  Just kidding.

---

