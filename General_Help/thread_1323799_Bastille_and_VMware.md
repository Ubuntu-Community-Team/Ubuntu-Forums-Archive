---
title: "Bastille and VMware"
date: 2009-11-12
forum: General Help
---

### Post by Dead Die Jazz on 2009-11-12
Ok, it seems as if I outsmarted myself here. Yesterday or the day before, I installed and configured Bastille. Yesterday, I tried to install VMware in an attempt to salvage and retrieve stuff from my old winxp account. Only, unlike everybody else on the internet, and indeed, unlike my previous attempt to install VMware 7 on ubuntu (not sure if it was 9.04 or 9.10) on a now failed attempt to run ubuntu, the .bundle refused to do anything, with archive manager not knowing what to do with it, and the terminal having no idea either. Which has lead me to conclude that I must have done something in bastille to screw things up. So I removed, and then followed as best I can, doing a locate when the directory didn't exist, Bastille according to [these instructions]("http://docs.hp.com/en/5992-5099A/ch04.html"). However, even after this, my computer has no idea what to do with 'VMware-Workstation-Full-7.0.0-203739.i386.bundle'. And I even checked the md5 hash of this bundle, which is a4286d08c2b302f1d3a164dcdc36c884. Given that on the VMware website it's a4286d08c2b302f1d3a164dcdc36c884, I don't think it's a corruption issue. FWIW, the SHA1 hash was 8319f92d99be12c806d1f86372ebbe7fdcb658a3. If you want, I can post my incompetent (sanitised) fumblings with the terminal which removed bastille and attempted to run the vmware bundle as sudo once again.

So basically what I'm asking is: Was I right in thinking that bastille was blocking vmware? How do I install vmware given that sudo (drag and drop .bundle) gives a command not found error, as do attempts to do it with commands like --gtk-?

Of course, all of this is based on the premise that VMware is the easiest way to reconstruct a install of winxp so that I can backup and retrieve stuff like playlists and addressbooks to use in linux, and if it isn't, please do stop me before I smash my ubuntu even further.

---

### Post by running_rabbit07 on 2009-11-12
Would Sun VirtualBox work for that? It is what I have always used. Sorry if this isn't very helpful.

---

### Post by Dead Die Jazz on 2009-11-12
hmmm. Assuming what your referring to is in my applications directory listed as 'Virtual Box OSE', it seems that it refuses to use a real harddisk, or even a non virtual machine harddisk image, thus preventing that from happening. I think anyway, there is a very good chance I'm missing something.

---

### Post by Soul-Sing on 2009-11-12
maybe something you knew allready, it is ((of course ) possible to revert bastille
quote: [https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)
> Should you decide that you would like to undo any, or all of the changes made to your Ubuntu system by Bastille Linux, you may use the RevertBastille command to undo all changes made by the Bastille Linux tool. For example, open a Terminal application, and type the following command at the prompt to revert (undo) the changes made by Bastille Linux:

```
sudo RevertBastille
```

maybe your out of troubles with this "solution".

---

### Post by Dead Die Jazz on 2009-11-12
argh, shoot me now.

---

### Post by Dead Die Jazz on 2009-11-12
Ok, well assuming I didn't do something nasty with my /interesting/ attempt to revert Bastille, it seems that I was wrong to assume that Bastille was at fault for blocking VMware, as now reinstalling VMware and using the above command doesn't seem to have in any way helped install vmware.

However, I did a bit more looking around, and [found this]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-vmware-6.5.-file-format-with-.bundle-whats-that-672673/"), and instead of just going sudo and trying **chmod +x <name> then sudo ./<name>** seems to have managed to do the right voodoo chants that got the GUI installer up and running and installing nicely. So yes, I do apologise for this display of incompetence, now to figure out how to mark this thread as solved. I'd be interested to know what exactly chmod +x did, but I can look up that later if need be.

---

