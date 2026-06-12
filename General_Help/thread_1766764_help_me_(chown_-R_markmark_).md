---
title: "help me (chown -R mark:mark /)"
date: 2011-05-24
forum: General Help
---

### Post by Ferret_guy on 2011-05-24
ok so i typed in
```
chown -R mark:mark /
```and my computer just died i fixed the sudo command but when i booth up i get several errs saying thinks like cannot accesses ect... premishen denied so i typed in
```
chown -R root:root /
chown -R mark:mark /home/mark
```and i still get the same errs please help me

---

### Post by matt_symes on 2011-05-24
Hi

Reinstall.

Kind regards

---

### Post by Ferret_guy on 2011-05-24
i would prefer not to

---

### Post by linuxinstalledfromhdd on 2011-05-24
reinstall:(

---

### Post by doas777 on 2011-05-24
did you use sudo or were you root when you did that? 
if so, I'm sorry man, but I've never seen any way to recover from that. all you can really do is backup your user files and rebuild. the objects in /etc are accessed by many different service users, that are vital for system boot, and they cannot be all owned by root. unfortunately each subsystem may have its own service user, so the specific permissions are entirely defined by your specific set of software. 

it is theoretically possible but I am imagining that it would take many many many hours of research and individually chowning items.

---

### Post by Ferret_guy on 2011-05-24
is there ny way to avoid this? or would it be too painful to fix this

---

### Post by doas777 on 2011-05-24
> **Ferret_guy said:**
> is there ny way to avoid this? or would it be too painful to fix this
you would have to go through your passwd file, and determine for each user exactly what files in your entire system that that user must own, and then manually apply that ownership. its at least hundreds of commands, if not 1000+

---

### Post by linuxinstalledfromhdd on 2011-05-24
did you make backups of all your important stuff?  do you have a remastersys custom ubuntu rescue disc or something?  or any rescue disc? 

What made you input that command, just so we can understand... I  want you to punch them hard in the shoulder.

---

### Post by Ferret_guy on 2011-05-24
ok then is there any way to renistall but keep the config files so all my progams and settings atre the same? any progam that can handle this?

---

### Post by linuxinstalledfromhdd on 2011-05-24
yeah, that's what remastersys does..   So you didn't back it up? :(

---

### Post by Ferret_guy on 2011-05-24
well you know how that goes i was planing on it gut it never quite happend

---

### Post by doas777 on 2011-05-24
well, you could manually backup your known config files and your entire /home, but you could (if you have an external with enough space) back up the /etc folder. you would not restore it to your new system, but if you see an app that should be configured and is not, you can find the config file in your old /etc, and move it into your new one, changing the ownership on the way. not for the feint of heart, but there shouldn't be that many apps that have config files outside your /home. you can restore your whole /home, just make sure it is owned by you:you and the permissions are 640, except for personal scripts and executables (740)

---

### Post by linuxinstalledfromhdd on 2011-05-24
Do you have a spare hard drive?  Put that one aside.

Install the other one. 

Install Ubuntu 10.10

And then do your own data recovery.. 

[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

Should be easy.

---

### Post by doas777 on 2011-05-24
I don't think we quite need to dig out photorec, since nothing has been deleted in this case, but op, you do want to boot from live cd and backup your \home, since that is where all your userfiles and desktop config are.

---

### Post by matt_symes on 2011-05-24
Hi

Do you have a seperate home partition ? If you do, install on your root partition but don't format your home partition. Reinstalling all the apps should keep your configuration setting.

Why did you chown on the root partition ? I'm assuming you did it as root because nothing is working.

If not backup home from live cd.

Kind regards

---

### Post by Ferret_guy on 2011-05-24
ok thanks guys!

---

### Post by btindie on 2011-05-24
If you boot into a Live CD then it may be possible to write a bash script that uses the user/group ownership of the live system to fix the files/directories on your installed system - it would have to traverse the entire directory tree.

---

### Post by doas777 on 2011-05-24
oh, and when setting everything up again, consider creating a seperate home, as Matt suggests. it makes reinstalls a breeze. 
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Ferret_guy on 2011-05-24
thats an exlaint ided but i suck at scripts so unless its already out there or somone wants to help me then i think i will have to reinstall

---

### Post by linuxinstalledfromhdd on 2011-05-24
we have a saying for this here, you are burning daylight. :)

---

### Post by Ferret_guy on 2011-05-24
alright...

---

### Post by linuxinstalledfromhdd on 2011-05-24
Cool :)

---

### Post by matt_symes on 2011-05-24
Hi

Here's another tip for your that might work if your permissions are not to shot.

Open a terminal and type (on existing installation)

```
dpkg --get-selections > ~/package.list
```

If you can do that, backup this file.

When you have installed the new OS, open a terminal and type

```
sudo dpkg --set-selections < /path/to/package.list
```

Change /path/to to point to the path to the file.

```
sudo apt-get install dselect
```

```
sudo dselect
```

Select option i.

This will reinstall all your old apps.

Kind regards

---

### Post by Ferret_guy on 2011-05-24
thanks!

---

### Post by matt_symes on 2011-05-24
Hi

If the above does not work from a terminal, try from a console. You might be lucky

Kind regards

---

### Post by Ferret_guy on 2011-05-24
hmm my computer dosent reconise removable media in the Disk utility its empty

---

### Post by matt_symes on 2011-05-24
Hi

Boot into a live CD/USB and backup from there.

Kind regards

---

### Post by linuxinstalledfromhdd on 2011-05-24
[FONT=georgia, bookman old style, palatino linotype, book antiqua, palatino, trebuchet ms, helvetica, garamond, sans-serif, arial, verdana, avante garde, century gothic, comic sans ms, times, times new roman, serif]
Every duty which is bidden to wait returns with seven fresh duties at its back.  ~Charles Kingsley[/FONT]

---

### Post by Ferret_guy on 2011-05-24
wow this has got to be the dumbest thing ive done in a long time...

---

### Post by linuxinstalledfromhdd on 2011-05-24
[FONT=georgia, bookman old style, palatino linotype, book antiqua, palatino, trebuchet ms, helvetica, garamond, sans-serif, arial, verdana, avante garde, century gothic, comic sans ms, times, times new roman, serif]
It is an undoubted truth, that the less one has to do, the less time one finds to do it in.  ~Earl of Chesterfield[/FONT]

---

