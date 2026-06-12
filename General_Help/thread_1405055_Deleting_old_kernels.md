---
title: "Deleting old kernels"
date: 2010-02-12
forum: General Help
---

### Post by owlcroft on 2010-02-12
Everywhere I search--and I've looked long and hard--the method for freeing up space by deleting old kernels is made to sound very simple: go into Synaptic, select the outdated kernels, mark for complete removal, and Apply.  Easy.

***But*** . . . when I mark a particular kernel for removal, Synaptic also wants to remove a lot of other things, some of which do not bear version numbers and seem generic.  I am, to put it mildly, very leery of just telling it to go ahead, lest I end up losing things I should have kept and having a dead or at least crippled box.

Say, for example, that I mark for Complete Removal the line **linux-image-2.6.22-15-generic**; when I go to Apply that one deletion, I get a laundry list of to-die files that includes:

[LIST]
[*]linux-generic
[*]linux-image-generic
[*]linux-restricted-modules-generic
[*]linux-restricted-modules-2.6.24-27-generic
[*]linux-ubuntu-modules-2.6.24-27-generic
[*]linux-restricted-modules-2.6.22-15-generic
[*]linux-ubuntu-modules-2.6.22-15-generic
[/LIST]
Only two of those look like what I want gone; even if those -27s are fragments of the new kernel that didn't install, what about the rest?

Oh, and the failed install left me with three broken dependencies:

[LIST]
[*]linux-image-generic
[*]linux-restricted-modules-2.6.24-7-generic
[*]linux-ubuntu-modules-2.6.24-7-generic
[/LIST]

*Running at present 8.04 with kernel 2.6.24-26-generic and up to date except for the latest kernel (which has no room to go in)*.

Help, please?

---

### Post by colobix on 2010-02-12
OH you've misunderstood this my friend.
Synaptic is a package manager. Kernel is just the link (if you can call it that) you use to access ubuntu from grub.
You get a new kernel after each system update, so if the new update has any bug or is giving you problems you can use the old kernel to exclude the new updated packages.
If you want to remove kernels you must use a grub editor.
But don't remove a kernel until you're 100 % sure that the newest update didn't give you any problems.
You can always restore your grub by using the startup manager.
Now, when it comes to free space, ubuntu will delete every unnecessary data on every 30th (or whatever it is)  time you start ubuntu.
You can also use recovery mode to free space.
And also, remember to clean your browser history.
Hope this helped you.

---

### Post by lotharmat on 2010-02-12
I tend to keep 2 Kernels - The current one and the previous one that way if the current one suddenly craps out on me I can still use the previous one.

Kernels can be removed via synaptic I do it whenever a new one comes out

---

### Post by iponeverything on 2010-02-12
if you do a

sudo apt-get clean

it should clear up enough space for you get your new kernel installed.

---

### Post by plucky on 2010-02-12
> **iponeverything said:**
> if you do a

sudo apt-get clean

it should clear up enough space for you get your new kernel installed.

Not if there is a separate /boot partition.

---

### Post by Techsnap on 2010-02-12
> 

[LIST]
[*]linux-generic
[*]linux-image-generic
[*]linux-restricted-modules-generic
[/LIST]
Those are just meta packages, you should be able to remove those without error.

---

### Post by philinux on 2010-02-12
@Owlcroft,

What does this command show?

```
df -h
```

---

### Post by ratcheer on 2010-02-12
I have deleted several old kernels by removing them with aptitude and I have never noticed any ill effects. Just make sure to update-grub after doing it.

Tim

---

### Post by MooPi on 2010-02-12
> **philinux said:**
> @Owlcroft,

What does this command show?

```
df -h
```
  It shows how much disk space is free or in use. The " -h " shows the amounts in readable gigabytes or megabytes.

---

### Post by ssulaco on 2010-02-12
use the terminal
> **ssulaco said:**
> Yes,keep the two most current kernels and remove the rest,you can remove unwanted kernel images and headers via the terminal
```
sudo apt-get remove --purge 2.6.xx-xx-*
```
where xx is the kernel you want to remove,

---

### Post by alucardni on 2010-02-12
I've followed [this]("http://guia-ubuntu.org/index.php?title=Borrar_kernels_antiguos") guide to uninstall old kernels in my netbook, it's in spanish but I think its very understandable ;-)

---

### Post by owlcroft on 2010-02-12
I do have a separate /boot partition, and using **df -h** shows it with 122M size, 121M used, and 0% available.  Of course; I knew that much.

There is, as I understand it, a drastic difference between editing the Grub menu, which merely removes older kernels from the start-up menu, and deleting them--as with Synaptic--which actually removes the files from the drive and thus frees up the needed space.

The suggested Spanish-language instructions, when run through the Google translator, reinforce my concerns, as the boxed, highlighted warning states *Do not uninstall the linux kernel-image-generic as it is necessary to receive updates of the kernel.*  Which was my undertanding, and why I am concerned that Synaptic threatens to remove it.

My understanding is that Synaptic is just a GUI for apt.  Would using the command-line input--
[B][INDENT]
sudo apt-get remove --purge 2.6.xx-xx-*[/INDENT][/B]
--do anything different from what Synaptic wants to do?  (With, of course, the correct numbers for **xx**)

---

### Post by ssulaco on 2010-02-12
> **owlcroft said:**
> 
My understanding is that Synaptic is just a GUI for apt.  Would using the command-line input--
[B][INDENT]
sudo apt-get remove --purge 2.6.xx-xx-*[/INDENT][/B]
--do anything different from what Synaptic wants to do?  (With, of course, the correct numbers for **xx**)
The asterisk,is a wildcard,so the command will pull everything that is related to 2.6.xx-xx kernel,for me its easier to just run the command.You may prefer to use synaptic and thats fine,its a matter of choice.recommend keeping the 2 most recent  kernels.....dump the rest

---

### Post by ironclaw on 2010-02-13
> **owlcroft said:**
> Say, for example, that I mark for Complete Removal the line **linux-image-2.6.22-15-generic**; when I go to Apply that one deletion, I get a laundry list of to-die files that includes:

[LIST]
[*]linux-generic
[*]linux-image-generic
[*]linux-restricted-modules-generic
[*]linux-restricted-modules-2.6.24-27-generic
[*]linux-ubuntu-modules-2.6.24-27-generic
[*]linux-restricted-modules-2.6.22-15-generic
[*]linux-ubuntu-modules-2.6.22-15-generic
[/LIST]
Only two of those look like what I want gone; even if those -27s are fragments of the new kernel that didn't install, what about the rest?

Oh, and the failed install left me with three broken dependencies:

[LIST]
[*]linux-image-generic
[*]linux-restricted-modules-2.6.24-7-generic
[*]linux-ubuntu-modules-2.6.24-7-generic
[/LIST]
It seems to me that the removal of the first 5 packages in the list of 7 is due the current broken dependencies, rather than the removal of 'linux-image-2.6.22-15-generic'. I guess Synaptic doesn't allow you to apply without somehow removing the broken dependencies or fixing them. Can you mark the removal of 'linux-image-2.6.22-15-generic' and the install of 'linux-image-2.6.24-27-generic' and apply both at the same time? That should fix the dependency issues with 'linux-generic' and all the rest.

Or just remove all the kernels you don't want including the broken dependencies (i.e., 'linux-generic' etc.) to free up space, then just reinstall the meta-packages 'linux-generic', 'linux-image-generic', and 'linux-restricted-modules-generic' to update to the latest kernel.

---

### Post by wolfe on 2010-02-13
you can also remove old kernels with ubuntu tweak

---

### Post by timgood on 2010-02-13
> **wolfe said:**
> you can also remove old kernels with ubuntu tweak

Indeed, and this is by far the easiest method. Ubuntu Tweak is available from GetDeb, here: [http://www.getdeb.net/updates/Ubuntu/9.10/?q=tweak]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=tweak")

Hope this helps.

---

### Post by Swagman on 2010-02-13
I  was interested in cleaning up the old kernels & grub so installed Ubuntu-tweak.

Looks a nifty little tool.

re: kernel removal: removed all up to v18

Got lots of cant find sda errors on the way though so I hope when I reboot it hasn't buggered the system.

It was a PITA to get 9:10 fresh installed on this as I have multiple SATA drives. (**NO** IDE drives) and had to resort to apt-get removing DMRAID to fettle 9:10 on.

I really don't fancy a memory refresher course !!

---

### Post by owlcroft on 2010-02-21
Well, hoping that it was just the most recent download that was broken, I tried removing each of these individually (still via Synaptic):

# linux-restricted-modules-2.6.24-7-generic
# linux-ubuntu-modules-2.6.24-7-generic

Regrettably, Synaptic still wants to also take out the generic items--

# linux-generic
# linux-image-generic
# linux-restricted-modules-generic

--which I still cannot believe would be A Good Thing.  I am hoping that someone will be able to tell me what to do here, besides install yet another gadget.  Shouldn't Synaptic be able to do this?

---

### Post by Swagman on 2010-02-21
Interesting bump

Reminds me to let readers know that Ubuntu-Tweak worked just Champion

Recommended.

---

### Post by owlcroft on 2010-02-24
I'm at a loss here.  Is there no one reading this who can explain in straightforward terms why Synaptic wants to also remove the generic modules, whether or not that is tolerable, and what it is or is not safe to do?

Surely this cannot be the first time this issue has arisen. . . .

---

### Post by mcduck on 2010-02-24
> **owlcroft said:**
> Well, hoping that it was just the most recent download that was broken, I tried removing each of these individually (still via Synaptic):

# linux-restricted-modules-2.6.24-7-generic
# linux-ubuntu-modules-2.6.24-7-generic

Regrettably, Synaptic still wants to also take out the generic items--

# linux-generic
# linux-image-generic
# linux-restricted-modules-generic

--which I still cannot believe would be A Good Thing.  I am hoping that someone will be able to tell me what to do here, besides install yet another gadget.  Shouldn't Synaptic be able to do this?

make sure you aren't trying to uninstall the *current* kernel version. Trying t do that would indeed uninstall those metapackages as well. But removing *old* kernel versions shouldn't do that.

---

### Post by scouser73 on 2010-02-24
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don&#8217;t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don&#8217;t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

I always remove the old generic and headers and have had no problems afterwards.

---

### Post by owlcroft on 2010-02-27
I deeply appreciate that those who post responses here are a valuable Ubuntu-community resource and are trying to help out people like me.  But folks, it would greatly augment the value of your replies were you to actually read what the OP--here, me--has actually written.

I *know* that older kernels are not deleted in upgrades; I *know* that one does not delete the current, running kernel; I *know* that the GRUB menu is not the linux image; I *know* that one is not supposed to remove anything that is not an actual linux image.  I have said all those things, most or all in the very first post.

What I keep trying to find out is either why Synaptic wants to also remove, besides the kernel images I specify, the other files--

# linux-generic
# linux-image-generic
# linux-restricted-modules-generic

--and whether I can allow it to do so, or how to remove the unwanted kernel images without also removing those things.  Synaptic is not giving me a line-item veto: it always wants to remove those files even when all I call out is one particular kernel image.

Please, can anyone answer those exact questions?

---

### Post by ironclaw on 2010-03-01
Can you run
```
sudo apt-get check
```
to check for broken dependencies?

I cannot see why it is not safe to remove the 3 metapackages that you specified, since they don't actually contain anything themselves - they just always depend on the latest kernel packages, so that the system is automatically updated. You can always reinstall them after they are removed. Of course, it is a mystery as to why Synaptic is forcing this, and I think they may be being removed due to broken dependencies.

---

### Post by mcduck on 2010-03-02
> **owlcroft said:**
> I deeply appreciate that those who post responses here are a valuable Ubuntu-community resource and are trying to help out people like me.  But folks, it would greatly augment the value of your replies were you to actually read what the OP--here, me--has actually written.

I *know* that older kernels are not deleted in upgrades; I *know* that one does not delete the current, running kernel; I *know* that the GRUB menu is not the linux image; I *know* that one is not supposed to remove anything that is not an actual linux image.  I have said all those things, most or all in the very first post.

What I keep trying to find out is either why Synaptic wants to also remove, besides the kernel images I specify, the other files--

# linux-generic
# linux-image-generic
# linux-restricted-modules-generic

--and whether I can allow it to do so, or how to remove the unwanted kernel images without also removing those things.  Synaptic is not giving me a line-item veto: it always wants to remove those files even when all I call out is one particular kernel image.

Please, can anyone answer those exact questions?
No, it's not safe to remove those metapackages. (Or if you remove them, you should re-install them again immediately). They are the exact tool that makes it possible to install new kernel updates into your system without replacing the existing kernel files, and removing those packages would stop you from receiving any kernel updates in the future.

The idea is that those packages always have the latest available kernel versions marked as their dependencies, so the kernel update updates those metapackages to their latest versions, and they then bring the actual new kernel packages along as dependencies (leaving the old kernel packages as "orphaned" packages on your system).

This is why I suggested that perhaps you are trying to uninstall the latest kernel version, since those metapackages shouldn't depend on any other than the very latest version of your actual kernel packages.

---

### Post by owlcroft on 2010-03-04
Yes, there are broken dependencies.  This all arose when I tried to install the latest kernel update.  Owing to the absurd fact that older kernels are all retained, it turned out, as the process attempted to proceed, that there was insufficient space in the directory for the install; the partial process then left me with those broken dependencies.

Am I correct, then, in deducing from those last two posts that I can allow Synaptic to do whatever it wants to do ***if*** I then immediately re-download the generic files?  If so, which generic files?  The ones for the older kernel that is still the running one?  Or would I just then try to download as a package the newer kernel?

I realy, *really* don't want to end up having to do a total re-install. . . .

---

### Post by ironclaw on 2010-03-04
> **owlcroft said:**
> Am I correct, then, in deducing from those last two posts that I can allow Synaptic to do whatever it wants to do ***if*** I then immediately re-download the generic files?  If so, which generic files?  The ones for the older kernel that is still the running one?  Or would I just then try to download as a package the newer kernel
Right, there is no immediate danger in removing 'linux-generic', 'linux-image-generic', and 'linux-restricted-modules-generic'. In fact, you can reboot and do whatever you want and you wouldn't even notice anything different (provided that you can currently reboot). However, as mcduck and I pointed out, these packages are necessary for automatic updates, so it is dangerous in the long run if these packages are removed permanently. So, do make sure that you reinstall them.

In other words, you can let Synaptic remove these metapackages while you remove old kernels to make space for new ones. After that, reinstall these metapackages, and Synaptic should automatically download the newest kernel, since that is a dependency of the metapackages. To make sure that everything is okay before you reboot, check that the new vmlinuz and initrd files are in /boot/, and that the GRUB config in /boot/grub/ points correctly to them.

---

### Post by mcduck on 2010-03-05
> **owlcroft said:**
> Yes, there are broken dependencies.  This all arose when I tried to install the latest kernel update.  Owing to the absurd fact that older kernels are all retained, it turned out, as the process attempted to proceed, that there was insufficient space in the directory for the install; the partial process then left me with those broken dependencies.

Am I correct, then, in deducing from those last two posts that I can allow Synaptic to do whatever it wants to do ***if*** I then immediately re-download the generic files?  If so, which generic files?  The ones for the older kernel that is still the running one?  Or would I just then try to download as a package the newer kernel?

I realy, *really* don't want to end up having to do a total re-install. . . .

You should never install any specific kernel package versions manually. Just install the *linux-generic* metapackage and it'll bring the latest kernel version packages along it as dependencies (and also the  *linux-image-generic*
& *linux-restricted-modules-generic* metapackages) and makes sure you'll also get kernel updates in the future).

If you just install some specific kernel version then that's all you get, that exact version and no updates.

..and yes, you can even remove all the kernel packages, just make sure you don't reboot the machine unless you have at least one working kernel installed.

---

### Post by owlcroft on 2010-03-06
My thanks to all, especially ironclaw and mcduck.  That all aounds very reassuring, and I will try it tomorrow (it's quite late now).  But it makes sense and I don't doubt it'll work.  (How many tombstones have that carved on them?)

---

