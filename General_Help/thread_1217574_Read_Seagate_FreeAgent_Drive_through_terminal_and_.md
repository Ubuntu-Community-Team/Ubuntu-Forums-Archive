---
title: "Read Seagate FreeAgent Drive through terminal and rsync for backup"
date: 2009-07-19
forum: General Help
---

### Post by sschr on 2009-07-19
Thanks for looking at this ... I'm a relative noob. I tried Debian from get-go, but Ubuntu is awesome! To start, I can read and write to Seagate FreeAgent 250g drive in GUI, but in the terminal it is highlighted in green as such:

root@scott-desktop:/media# ls
cdrom  cdrom0  floppy  floppy0  [COLOR=DarkGreen]FreeAgent Drive[/COLOR] (highlighted)

When I type

root@scott-desktop:/media# cd FreeAgent Drive
bash: cd: FreeAgent: No such file or directory

I cannot access it. Hey, I'm just starting out.

I'm doing this so I can rsync to backup to the drive. Please help!:confused:
Thanks,
Scott

---

### Post by brookie on 2009-07-19
Hi Scott, and welcome, 
I'm using Intrepid and rsync too on my seagate drives. I use grsync via the GUI. Install grsync through System/Administration/Synaptic Package Manager.
Search for grsync and install. 
After it installed it was under Applications/Internet so I didn't want it there an moved it to System tools. To do this just right click on Applications and select Edit Menus and remove it from Internet and add it to System Tools.

* note the some users had trouble with freeagent drives because by default the power save is turned on on the drive and they spin down and linux could not see them. i plugged my drives into my windows system and used the seagate software to turn off the power save feature.

Hope this helps,
brook

---

### Post by mikewhatever on 2009-07-19
This is an odd mount point, FreeAgent Drive, but if that's what it is, **cd FreeAgent\ Drive** should get you in. You can also use tab auto-completion instead of typing the whole thing, in other words, start with cd Free and then hit tab. That should auto-complete the mount point.

---

### Post by sschr on 2009-07-19
Thanks[COLOR=DarkGreen] Brook[/COLOR], that did the trick. I still wanted to know how to access it the terminal, and [COLOR=DarkGreen]mikewhatever[/COLOR] provided some invaluable info. Thanks to both of you! And [COLOR=DarkGreen]mikewhatever[/COLOR], I know Linux is not Windows, and, believe me, I don't want it to be. I hate Windows. I'm reading a couple books on Linux, but I've never seen the syntax you gave me.
Thanks,
Scott

---

### Post by t0p on 2009-07-19
Yeah, what mikewhatever said.  In Linux you can't have spaces in file names in terminal input.  So you need to use the back-slash to escape a space. Hence **Freeagent\ Drive**.

Incidentally, is [this]("http://www.maplin.co.uk/Module.aspx?ModuleNo=223570") your drive?  Or [this]("http://www.maplin.co.uk/Module.aspx?ModuleNo=227775")?  I want to get a drive, but I want to know about compatibility.

---

### Post by sschr on 2009-07-20
Hey Top, the second drive you mentioned is the one I'm using. Hope this helps.
Scott

---

