---
title: "Grub not showing XP"
date: 2009-10-25
forum: General Help
---

### Post by Nitewalker on 2009-10-25
Just did install of 9.10 on machine that has WinXP on it, grub does not show XP so that you can choose it to boot into it?  Worked fine on 9.04 before, what do I need to do to get dual boot back.....XP drive shows up alright and can access it and other drives on machine, just won't dual boot anymore:confused:

---

### Post by oldfred on 2009-10-25
The latest version should have the prober but just incase. If this does not work you need to add a file. This assumes you did a clean install and have grub2 not an upgrade.

Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

---

### Post by Nitewalker on 2009-10-25
SOLVED: Thanks, ran update-grub2, all works as advertised now for dual boot:popcorn:

---

