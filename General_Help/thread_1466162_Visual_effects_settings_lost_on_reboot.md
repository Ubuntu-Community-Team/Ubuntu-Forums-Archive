---
title: "Visual effects settings lost on reboot"
date: 2010-04-30
forum: General Help
---

### Post by NikitaUtiu on 2010-04-30
I have just upgraded to Lucid Lynx. Just after that the borders of disappeared. Anyway, I found out I can get them back if I enable Standard Visual effects from the appearance menu. The only problem ?i have is that the options don't get saved  and I need to do this over again every time I reboot.
:confused::confused::confused:

---

### Post by dino99 on 2010-04-30
sudo dpkg --configure -a

---

### Post by DeadMetal on 2010-04-30
I have exactly the same problem after upgrading. Running that command does not solve the problem for me (and I don't see how it could). Please help!

---

### Post by mhgsys on 2010-04-30
Try reinstalling your videocard drivers; 

I guess your running a new os version with the old drivers.

---

### Post by DeadMetal on 2010-04-30
I already did, Administration -> Hardware drivers says that I am now running 'version current (recommended)' of the nvidia-drivers. According to Synaptic that is 195.36.15-0ubuntu2. I also tried switching back to the older version in the list, that did not make a difference.

Also, when enabling the visual effects after booting, they will just work fine. So the drivers work fine as well.

It's just that after a reboot appearently Ubuntu disables the effects again (or forgot that we enabled them) and also the window borders.

---

### Post by mhgsys on 2010-04-30
That's odd. . did you try updating everything. . ?

I'm kinda running out of ideas. 



bump 4 more users to come in .

---

### Post by r-senior on 2010-04-30
I've got the same problem after upgrading 9.10 -> 10.04.

I've not got to the bottom of it, but I have an ugly workaround.

Assuming compiz is installed, add /usr/bin/compiz --replace as a startup application.

See [http://ubuntuforums.org/showthread.php?p=9202600#post9202600]("http://ubuntuforums.org/showthread.php?p=9202600#post9202600")

---

### Post by pqwoerituytrueiwoq on 2010-04-30
your window border (aka window decorations) went away?
i just reload compiz settings using the compiz icon
it does not happen very often i did a fresh install though

---

### Post by DeadMetal on 2010-04-30
> **r-senior said:**
> I've got the same problem after upgrading 9.10 -> 10.04.

I've not got to the bottom of it, but I have an ugly workaround.

Assuming compiz is installed, add /usr/bin/compiz --replace as a startup application.

See [http://ubuntuforums.org/showthread.php?p=9202600#post9202600]("http://ubuntuforums.org/showthread.php?p=9202600#post9202600")

Thanks, this workaround works for me as well, after booting I have window borders and visual effects working just fine.

The other suggestions mentioned in the other thread and in the bug reports did not solve the problem, but this one did.

---

### Post by dim_par on 2010-04-30
I solved this problem by an easiest way, by activating visual effects and then by saving these settings from System-> Preferences->Startup Applications Preferences->Options->Remember currently Running Application

---

### Post by r-senior on 2010-04-30
Your approach probably does exactly the same thing dim_par, although I'd agree it's easier as long as there aren't other running applications that you don't want all the time.

Point is though, we shouldn't need to be doing this. There would appear to be something that stops compiz loading properly at startup after an upgrade.

I wonder if this has something to do with it? Does this make any sense to anyone? What is/was compiz.real?

```
Apr 30 13:13:39 localhost gnome-session[21489]: WARNING: Could not launch application '107b2324a463b43b3f126773245297578600000046050023.desktop': Unable to start application: Failed to execute child process "/usr/bin/compiz.real" (No such file or directory)

```

I've got similar errors in ~/.xsession-errors.

Are we perhaps missing a symbolic link? If anyone has a Lynx, perhaps clean install, that doesn't have this problem, perhaps they could look for /usr/bin/compiz.real?

EDIT: I can also "fix" this with a symbolic link (removing the startup app):

$ sudo ln -s /usr/bin/compiz /usr/bin/compiz.real

---

### Post by r-senior on 2010-04-30
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617")

---

### Post by fizikz on 2010-04-30
> **DeadMetal said:**
> I already did, Administration -> Hardware drivers says that I am now running 'version current (recommended)' of the nvidia-drivers. According to Synaptic that is 195.36.15-0ubuntu2. I also tried switching back to the older version in the list, that did not make a difference.

Also, when enabling the visual effects after booting, they will just work fine. So the drivers work fine as well.

It's just that after a reboot appearently Ubuntu disables the effects again (or forgot that we enabled them) and also the window borders.

I also had the same problem with the nvidia drivers installed from Administration -> Hardware drivers. I have since uninstalled those and blacklisted nouveau, and installed the drivers from nvidia's website. It might be worth giving it a shot.

---

### Post by thinktogrowrich on 2010-05-02
> **dim_par said:**
> I solved this problem by an easiest way, by activating visual effects and then by saving these settings from System-> Preferences->Startup Applications Preferences->Options->Remember currently Running Application

Thanks to dim_par.  This solution worked perfectly, first time!

---

### Post by DeadMetal on 2010-05-03
Well, all 3 solutions will work, it is just which one you prefer.

I went with running "sudo ln -s /usr/bin/compiz /usr/bin/compiz.real" because that is a one-time command instead of Gnome having to remember something for each boot.

---

### Post by adolphsn on 2010-05-03
Same problem with 10.04 Visual Effects and X mouse
Lost settings on reboot, found the solution:
Configuation Editor, /apps/gnome-session/options
Check: auto_save_session.

---

### Post by XGhozt on 2010-05-06
I'm having this same problem on 10.04 just after the reinstall. At first I couldn't boot, and I had to do a recovery and then when it did boot I lost my visual settings..settings.

But now I can't use the run console (alt-f2). Doing a metacity replace works, but then I lose compiz and again my visual settings.

Any ideas?

---

### Post by twills805 on 2010-09-26
This happened to me after a minor update, not an upgrade or reinstall...

Adding **/usr/bin/compiz --replace** to my startup apps worked for me, so thanks a lot. Interestingly adding the sym link did not work, and i couldnt find the compiz.real error in my xsessions log...

Will keep an eye on the bug report

Cheers all
Tom

---

### Post by lotvx on 2011-06-05
> **dim_par said:**
> I solved this problem by an easiest way, by activating visual effects and then by saving these settings from System-> Preferences->Startup Applications Preferences->Options->Remember currently Running Application


this one worked for me , thanx

---

