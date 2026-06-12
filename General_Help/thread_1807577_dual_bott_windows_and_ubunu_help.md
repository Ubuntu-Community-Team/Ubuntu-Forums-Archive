---
title: "dual bott windows and ubunu help"
date: 2011-07-19
forum: General Help
---

### Post by bozobakin on 2011-07-19
i have 4 partition
1. for windows 2. for data 3.ubuntu and 4.swap for ubuntu
i installed ubuntu and it is working great,awesome os but here is my problem
i installed grub bootloader on 1.partition(with windows) and when i start pc grub shows up and i can choose os
if i chose ubuntu everything works but if i choose windows it just loads grub again(screen flashes and selector moves back to first selection and timer starts)
so i cant boot in windows and i really need windows(i actually dont but my sister whe uses same pc does need it)
i have unistalled grub for now and now using windows but where to install grub when i install ubuntu next time(ill do it tomorow)

---

### Post by seawolf167 on 2011-07-19
You'll want to install Grub on the MBR of that disk. Do no overwrite the Windows partition boot record or you won't be able to boot into Windows.

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is the dual boot guide for Windows and Ubuntu.

[Here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")is the how-to for reinstalling Grub. After you reinstall Grub, simply boot into Ubuntu and type the following commands to search for other boot loaders for other installations

```
sudo apt-get install os-prober
sudo update-grub
```

---

