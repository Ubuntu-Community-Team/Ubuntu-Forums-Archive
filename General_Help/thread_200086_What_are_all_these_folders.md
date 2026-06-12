---
title: "What are all these folders?"
date: 2006-06-19
forum: General Help
---

### Post by Fred Doolie on 2006-06-19
Perhaps this is a general Linux question rather than Ubuntu but the again sometimes different Linuxes set things up differently (see [www.puppyos.com](www.puppyos.com)) for what I mean.

What are all these folders in my root and what are they for? 

I see that sometimes people say set up a seperate parttion for /var and one for /home and one for /etc..... Why? What do I actually need to back up; just /home?:roll:

Oh, speaking of seperate partions, I have an 80 gig drive. Should I just split it 50/50 it between / and /home?

---

### Post by IYY on 2006-06-19
If you want to back up configuration files, you'll need to back up the /etc directory.

---

### Post by vigleik on 2006-06-19
[QUOTE=Fred Doolie]Oh, speaking of seperate partions, I have an 80 gig drive. Should I just split it 50/50 it between / and /home?[/QUOTE]
You certainly don't want a 40GB root partition, that's a giant waste of space. About 10G (a little bit more if you want to install lots of big games etc, a bit less if you know you won't install much extra) should be sufficient. You might also, depending on how much ram you have, want a swap partition.

Also, you might (depending on how much you like to play with your computer) want to install another linux distro, or another copy of ubuntu, next to the one you're installing now, for experimentation.

You can find lots of recommendations for how to do this on the forum. For example, I like the following idea:
/ 10 GB
/home 59 GM
swap 1GB
And another 10GB in reserve to possibly install something else on.

Vigleik

---

### Post by Jucato on 2006-06-19
For your first question (what are all these folders for), you could read this (very) short explanation from the wikis: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by Fred Doolie on 2006-06-19
[QUOTE=IYY]If you want to back up configuration files, you'll need to back up the /etc directory.[/QUOTE]

So, my backup list is now
/home
/etc

Anything else?
------------------------------------------

Assumption: To do a full "clean-up and rebuild" I would:
1) Reformat and do a clean Ubuntu install
2) Reinstall the apps and games I wanted.
3) Restore my backups of /home and /etc
and I'd be pretty much back to everything set up like it was?

---

### Post by Fred Doolie on 2006-06-19
[QUOTE=Fenyx]For your first question (what are all these folders for), you could read this (very) short explanation from the wikis: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)[/QUOTE]

That's the ticket. Thanks.

---

### Post by Third Thoughts on 2006-06-19
[QUOTE=Fred Doolie]So, my backup list is now
Assumption: To do a full "clean-up and rebuild" I would:
1) Reformat and do a clean Ubuntu install
2) Reinstall the apps and games I wanted.
3) Restore my backups of /home and /etc
and I'd be pretty much back to everything set up like it was?[/QUOTE]

Just about, you'd have to run synaptic again. Backing up etc doesn't back up the programs you've installed, just their config files. However, etc does contain the list of repositories synaptic uses and the list of programs you've installed. So once you restore etc, Synaptic will have a list of all the programs you want installed. It will look for the newest version, download it, and you'll be up and running. Of course that first time you run synaptic after the install will take forever. Personally I don't bother backing up etc however because I find that I download alot of unessecessary programs, so if I have to restore I kind of end up cleaning up my system as well and only re-installing what I need.

~Andrew S.

---

