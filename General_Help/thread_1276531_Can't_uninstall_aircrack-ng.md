---
title: "Can't uninstall aircrack-ng"
date: 2009-09-27
forum: General Help
---

### Post by simartem on 2009-09-27
I am new to ubuntu. I have installed aircrack-ng but i think its an outdated version, when i go to the synaptic packet manager, i see that the aircrack-ng shown uninstalled. I think i installed the program manually, but i dont know how to remove the oudated version now. I tried "sudo apt-get remove aircrack-ng" but it doesnt remove it. 

I searched for "aircrack-ng" in my file system and its found in ```
"/usr/local/bin"
```  as executable. 

There is also a folder named "aircrack-ng" in ```
"/usr/local/etc"
```

There are also following files in directory 

```
"/usr/local/sbin"
```

Files : 

```

airbase-ng
airdriver-ng
aireplay-ng
airmon-ng
airodump-ng
airodump-ng-oui-update
airserv-ng
airtun-ng

```

So how do i remove the old one completely to make a clean version install with synaptic package manager ? Which directories should i delete or which command :(

---

### Post by Woody1987 on 2009-09-27
just delete the folder using sudo rm -r /path/to/folder and sudo apt-get rm /path/to/file

---

### Post by simartem on 2009-09-27
> **Woody1987 said:**
> just delete the folder using sudo rm -r /path/to/folder and sudo apt-get rm /path/to/file

Can you give me exact path in relation to my previous post because i dont want to delete a whole directory with some other application in it :) I am a newbie

Thank you very much

---

### Post by simartem on 2009-09-27
bump

---

