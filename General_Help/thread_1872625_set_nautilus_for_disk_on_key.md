---
title: "set nautilus for disk on key"
date: 2011-10-31
forum: General Help
---

### Post by ilantal on 2011-10-31
How do I control which program is activated when I plug in disk on key?
It used to be Nautilus which is what I want, but now Archive manager comes up and I want to get rid of this behaviour.

Thanks,
Ilan

---

### Post by ilantal on 2011-10-31
If under Removeable Media I check "Never prompt or start programs on media insertion" it will not open the archive manager, but that kills all removable media.
Under the media there is CD audio, DVD video etc but no disk on key (even under Other Media).

Where did it ever get the notion to open the Archive manager and how can I convince it NOT to do that, but rather to open Nautilus? Even though this is Linux, I feel as helpless as if I were in Windows! Ugh, there MUST be a way!:confused:

---

### Post by desigi on 2011-10-31
I'm experiencing the exact same behavior with my mounted hard drives. The icon in the unity bar automatically launches Archive Manager and not Nautilus like in 11.04. I have to click on the Home Folder icon to gain access to the mounted hard drives via Nautilus.

---

### Post by desigi on 2011-10-31
I removed the inode/directory entry under the Added Associations sections in the mimeapps.list file. Everything works now. Not sure why file-roller was setup to open up.

The file is located here: ~/.local/share/applications/mimeapps.list

Hope it helps.

---

### Post by ilantal on 2011-11-01
Thank you very much desigi! Your suggestion was right on the mark. I too have no idea how the association was setup, but it was a pain. The worst part was feeling like an idiot being back in Windows. This is Linux and WE are supposed to have control. I couldn't find anyone who had the problem and solved it. Full points go to you!

Ilan

I can't remember how to mark the thread as solved.

---

