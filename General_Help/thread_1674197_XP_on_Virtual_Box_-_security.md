---
title: "XP on Virtual Box - security"
date: 2011-01-23
forum: General Help
---

### Post by qwertyjjj on 2011-01-23
If I install VirtualBox and run XP inside of Linux, do I need to have AV and a firewall running on the VirtualBox or do all the computer connections go through ports on the Linux box.

---

### Post by howefield on 2011-01-23
Your Windows virtual machine will behave just like a "normal" installation with respect to security and should be treated in the same way.

So yes is the answer.

---

### Post by hakermania on 2011-01-23
In my opinion, it depends.
If you provide your VM a custom IP, then yes, if not, then only be ware of viruses, and not the hackers that can hack into your machine, because, simply, they can't.

---

### Post by Timmer1240 on 2011-01-23
If you want a good layer of security for xp I would install sandboxie it runs your browser in a sandboxed environment so the browser cant affect the local system just one of the tools I use for windows.Another good one is Returnil you can set it up so all changes to the machine can be erased on reboot just a few ideas for you.

---

### Post by Vaphell on 2011-01-23
you can also use snapshots
clean install of xp, customize, install what you need but don't do anything risky (browse the shady websites, running untrusted apps), create a snapshot, every time you want to use that xp use the snapshot so any changes during the last session are discarded, so even if your virtual system is hosed it will be the case only in that session - it would work very much like a live cd session of ubuntu. You'd have to store the files in a shared directory on the host system because there would be no persistence so usefulness of this scenario depends on what you want to do with your xp. Either way having a clean snapshot of a freshly installed system is handy.

---

### Post by Rubi1200 on 2011-01-23
> **howefield said:**
> Your Windows virtual machine will behave just like a "normal" installation with respect to security and should be treated in the same way.

So yes is the answer.
+1 to that!

---

### Post by qwertyjjj on 2011-01-24
The VB has an IP of 10.0.2.15 so doesn't that mean it is given an IP address by Ubuntu and all comms go through Ubuntu?

Secondly, what is a good firewall for ubuntu> Most of the firewall GUIs seem to rewuire exact settings of IP addresses/ports. Is there something like COMODO that works in Ubuntu?

---

### Post by JGJones on 2011-01-24
> **qwertyjjj said:**
> The VB has an IP of 10.0.2.15 so doesn't that mean it is given an IP address by Ubuntu and all comms go through Ubuntu?

Secondly, what is a good firewall for ubuntu> Most of the firewall GUIs seem to rewuire exact settings of IP addresses/ports. Is there something like COMODO that works in Ubuntu?
Simply put - in Windows XP - IF you can browse the Internet (ie via IE) then it does have a connection to the Internet and thus can be infected - just treat it as if it is a separate machine to your computer. It'll want AV and firewall and so on to be installed.

Vaphell's suggestion of using snapshots is the best idea too - build up your XP machine and do updates only. Install the necessary software that you want. Make a safe snapshot where you know everything is fine.

Then if you ever get infected somehow in Windows XP - you simply just restore the snapshot which revert back to that state. However if you're doing this, you will want to make a shared folder so that you can share data.

And IF you do revert to the snapshot you will want to run an av scan on the files in the shared folder to ensure there's no infected files (it will not affect Ubuntu, but you don't want to reinfect your Windows XP).

Hope that helps.

---

### Post by qwertyjjj on 2011-01-25
> **JGJones said:**
> Simply put - in Windows XP - IF you can browse the Internet (ie via IE) then it does have a connection to the Internet and thus can be infected - just treat it as if it is a separate machine to your computer. It'll want AV and firewall and so on to be installed.

Vaphell's suggestion of using snapshots is the best idea too - build up your XP machine and do updates only. Install the necessary software that you want. Make a safe snapshot where you know everything is fine.

Then if you ever get infected somehow in Windows XP - you simply just restore the snapshot which revert back to that state. However if you're doing this, you will want to make a shared folder so that you can share data.

And IF you do revert to the snapshot you will want to run an av scan on the files in the shared folder to ensure there's no infected files (it will not affect Ubuntu, but you don't want to reinfect your Windows XP).

Hope that helps.

Is it best to use an imaging software for the snapshot like Macrium?

---

### Post by coldraven on 2011-01-25
Just use the VirtualBox Snapshot utility, see the screenshot.
Also I exported a copy to my external USB hard drive for a backup.
VirtualBox File>Export Appliance.
It does not take as long as it says it will, trust me!

---

### Post by qwertyjjj on 2011-01-25
> **coldraven said:**
> Just use the VirtualBox Snapshot utility, see the screenshot.
Also I exported a copy to my external USB hard drive for a backup.
VirtualBox File>Export Appliance.
It does not take as long as it says it will, trust me!

The snapshot took all of half a second to run, is that correct? Shouldn't it image the entire XP drive area?

The export to disc seems to take a lot longer.

---

### Post by coldraven on 2011-01-30
> The snapshot took all of half a second to run, is that correct? Shouldn't it image the entire XP drive area?

The export to disc seems to take a lot longer.

AFAIK the "drive" is just a file that can expand if you want. The snapshot is just saving the  file and then starting a new one . The new one will only contain what is added.
Look in /home/[COLOR=Red]username[/COLOR]/.VirtualBox/Machines/[COLOR=Red]your VM[/COLOR]/Snapshots 

Exporting saves the whole caboodle and takes a while.
You can tell that I'm an expert :p

---

### Post by CharlesA on 2011-01-30
Snapshots aren't saved in the exported VM.

---

### Post by mosaic2s on 2011-01-30
> **Vaphell said:**
> you can also use snapshots
clean install of xp, customize, install what you need but don't do anything risky (browse the shady websites, running untrusted apps), create a snapshot, every time you want to use that xp use the snapshot so any changes during the last session are discarded, so even if your virtual system is hosed it will be the case only in that session - it would work very much like a live cd session of ubuntu. You'd have to store the files in a shared directory on the host system because there would be no persistence so usefulness of this scenario depends on what you want to do with your xp. Either way having a clean snapshot of a freshly installed system is handy.

thats a great tip.

---

### Post by coldraven on 2011-01-31
> Snapshots aren't saved in the exported VM.
Well I never knew that!

Nice tip from Vaphell, thanks. I've been using a shared folder for transferring files in and out of the VM. Now I think I'll make some folders in it for XP programs to use.

---

### Post by CharlesA on 2011-01-31
> **coldraven said:**
> Well I never knew that!

It's worded weirdly on their site, but this is what it says:

> OVF cannot describe snapshots that were taken for a virtual machine. As a result, when you export a virtual machine that has snapshots, only the current state of the machine will be exported, and the disk images in the export will have a *"flattened"* state identical to the current state of the virtual machine.

---

