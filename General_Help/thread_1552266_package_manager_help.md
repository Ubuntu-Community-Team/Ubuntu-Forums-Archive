---
title: "package manager help"
date: 2010-08-13
forum: General Help
---

### Post by ninhalo5 on 2010-08-13
[RIGHT]Hi, I'm having an issue with my package manager. I keep getting an error about a package not being recognized and it will shut down. I tried adding a repo for jdownloader and it's getting hung up. I've since removed the link from the sources list and for some reason it is still being read. 
[/RIGHT]
 "E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
E: The list of sources could not be read."
I even get the error in terminal my system will not update or allow me to look for programs now.
Any idea how I can repair this?

Thank you

---

### Post by ASchweitzer on 2010-08-13
Try updating your sources. Hit the 'reload' button. Also, are you sure your changes to sources.list stuck? Did you edit with sudo?

---

### Post by QLee on 2010-08-13
> **ninhalo5 said:**
> [RIGHT]Hi, I'm having an issue with my package manager. I keep getting an error about a package not being recognized and it will shut down. I tried adding a repo for jdownloader and it's getting hung up. I've since removed the link from the sources list and for some reason it is still being read. 
[/RIGHT]
 "E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
E: The list of sources could not be read."
I even get the error in terminal my system will not update or allow me to look for programs now.
Any idea how I can repair this?

Thank you

From the screenshot, you need to go to the Synaptic menu Settings->Repositories and correct the mistake you made when deleting that repo that gave you trouble. I would then do a Reload from the menu and proceed as normal.

---

### Post by Soul-Sing on 2010-08-13
> **ASchweitzer said:**
> Try updating your sources. Hit the 'reload' button. Also, are you sure your changes to sources.list stuck? Did you edit with sudo?

via ```
sudo nano /etc/apt/sources.list
```

---

### Post by ninhalo5 on 2010-08-13
I tried removing it from the software sources, highlit the line then clicked remove. I can't find it in the source list any more.
Right now I'm not able to get to the reload button, when I hit close on the error button it closes the entire program.

I just received a new error msg and took a screenshot of it.
I'm still in the learning process of Linux so I'm sure I'm doing something wrong...

Thanks

---

### Post by Soul-Sing on 2010-08-13
after removing the line
close all apt/dpkg/package managers and run
```
sudo apt-get update
``` in the terminal.

---

### Post by ninhalo5 on 2010-08-13
Same thing...

jeff@jeff-laptop:~$ sudo apt-get update
[sudo] password for jeff: 
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
jeff@jeff-laptop:~$

---

### Post by JBAlaska on 2010-08-13
You have to navigate to: **/etc/apt/sources.list.d/** and remove the file: **jd-team-jdownloader-lucid.list**

Then run:
```
sudo apt-get update
```

---

### Post by snowpine on 2010-08-13
Try:

```
gksu gedit /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
```

Contact the maintainer of this repository (jd-team, whoever that is, it's not a standard Ubuntu repository) for the correct format.

If you are usure, just type a # symbol at the start of line 1 to comment out the line so it is skipped.

Save the file, quit Gedit, and try 'sudo apt-get update' again.

---

### Post by ninhalo5 on 2010-08-13
"You have to navigate to: **/etc/apt/sources.list.d/** and remove the file: [B]jd-team-jdownloader-lucid.list"

[/B]Sweet, that worked thank you.

---

