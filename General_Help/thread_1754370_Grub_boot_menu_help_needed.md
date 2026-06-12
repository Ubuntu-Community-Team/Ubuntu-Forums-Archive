---
title: "Grub boot menu help needed"
date: 2011-05-10
forum: General Help
---

### Post by seubill on 2011-05-10
Can someone inform on how to change the font text size and also the font colors in the Grub menu in 11.04 Natty?

Editing /etc/grub.d/05_debian_theme doesn't do it in Natty.

I'm using a custom background theme in the Grub menu.


Thanks.

---

### Post by satish_j on 2011-05-10
Did you run the foll command after editing the file?
```

sudo update-grub

```

---

### Post by seubill on 2011-05-10
I edited the file as root, saved and quit.

Then ran "sudo update-grub" from terminal.

Changes did not work.

---

### Post by davegt72 on 2011-05-10
Are you using grub? Natty uses grub2, so try running:

   ```
sudo update-grub2
```

---

