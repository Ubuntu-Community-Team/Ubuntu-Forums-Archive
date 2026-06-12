---
title: "map permissions"
date: 2006-01-24
forum: General Help
---

### Post by Wolfbite on 2006-01-24
Hey, I installed Ubuntu for the first time yesterday, and thanks to this board, I'm ever so slightly starting to get the hang of things. :D 

However, I really need help with this one:

I copied my mp3 folder from my mounted windows harddrive to home/username. However, all the maps and sub-folders doesn't allow write as default, so I have to change them all so they allow Write, at least for owner. Doing this individually would take forever, though. Is there any command to check the Write option for the mp3 folder and all its subfolders?

---

### Post by kaamos on 2006-01-24
```

chmod +w /home/username/mp3folder -R
```

---

### Post by Wolfbite on 2006-01-24
[QUOTE=kaamos]```

chmod +w /home/username/mp3folder -R
```[/QUOTE]


Ahaha, it worked like a charm, thanks a bunch. :) 

BTW, I'd love a short explanation for what I just did. What is chmod, +w and -R? I suppose +w checks the write box, but that's all I can decipher from that command. ^^

---

