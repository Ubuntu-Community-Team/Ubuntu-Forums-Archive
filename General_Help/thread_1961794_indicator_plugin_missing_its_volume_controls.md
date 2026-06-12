---
title: "indicator plugin missing its volume controls"
date: 2012-04-19
forum: General Help
---

### Post by Eniliad on 2012-04-19
I've done a great deal of monkeying around with sound settings today - earlier, to get the computer to recognize and use a USB headset, and later, when I discovered upon trying to restore the earlier settings that I had royally screwed something up in the process. I've almost got everything working again, but there's one irritating problem - the xfce4-indicator-plugin is missing its volume icon. This is important for me to recover, because my media program minimizes into the volume menu when "closed", with media controls... which is currently invisible. Therefore, I have to re "open" it from the menu in order to get it back up. If anyone could help me get this back the way it's supposed to be, I'll be eternally grateful.

Running the latest Xubuntu, internal motherboard sound card... I'll be happy to provide any info I can upon request. Sadly, I can't tell you what things I did earlier that screwed this up - if I could, I'd simply correct it. :) However, I can tell you that I've tried restarting the system, and completely uninstalling and reinstalling the xfce4-indicator-plugin package.

EDIT: Fixed it myself. Turns out that I had removed a package related to PulseAudio, and reinstalling it did not replace it. Doing so corrected the problem.

---

