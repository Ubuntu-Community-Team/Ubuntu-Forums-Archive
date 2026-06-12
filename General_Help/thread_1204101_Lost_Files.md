---
title: "Lost Files"
date: 2009-07-04
forum: General Help
---

### Post by Toshikazu on 2009-07-04
Hi, I cut and pasted a couple of video files into another folder. Next time I went to find them, they where gone!

I searched my whole computer for them and they cannot be found. They are not in the trash nor in the lost+found foler.

Is there possible way to recover them? I have no idea what happened to them :(

Toshi

---

### Post by Boondoklife on 2009-07-04
How did you search? I have found that using sudo find / -name "<name of file>" is the best bet in a terminal as for some reason nautilus cant always find things.

But keep in mind you will need the exact name, you can use wild cards if you only know part of it.

---

### Post by WRDN on 2009-07-04
If you have deleted the files, then, firstly, reboot into a LiveCD environment, as that will not touch the HDD. If you continue using the current boot, then the OS may overwrite the data, making it much much harder to retrieve.

From a LiveCD, you can use Photorec to recover deleted files. See [here]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive") for details on using it.

---

### Post by Bucky Ball on 2009-07-04
```
locate name_of_file
```... replacing 'name_of_file' with the correct data, also works in a terminal, and you can also use wildcards. If you know it is an mp4:

```
locate *.mp4
```... should find every mp4 on your machine.

---

