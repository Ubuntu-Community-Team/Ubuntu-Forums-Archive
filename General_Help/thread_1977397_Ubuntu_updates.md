---
title: "Ubuntu updates"
date: 2012-05-10
forum: General Help
---

### Post by sunfromhere on 2012-05-10
Can someone help me here?

I download updates as soon as they appear. So, for once I went to scroll down to see what exactly I was updating, and I found out that there were some updates for programs and applications I don't have installed (f.e. Gwibber, Evolution etc). I know that these updates aren't large (couple of kb), but why is the updater doing this and how to turn it off?

Thanks.

---

### Post by 3rdalbum on 2012-05-10
You will only see updates for packages you have installed.

Gwibber and Evolution are both shipped on the default Ubuntu install, so unless you have removed them, you have them installed and therefore will get updates for them.

If you've removed the programs, then you may have a couple of residual packages left behind from these programs (such as "evolution-data-server" or "gwibber-common" or something like that) that are receiving updates. The correct term for this is "orphaned packages" - the main program was removed, but its dependencies weren't. These are the "orphans". The command "sudo apt-get autoremove" should list the orphaned packages and allow you to remove them, but check the list CAREFULLY in case there are things you still want or have been listed erroneously.

If you want to run 'sudo apt-get autoremove' but there are one or two packages listed there that you want to keep, just "sudo apt-get install" those packages and they will be marked as packages that you want to keep. They will no longer be listed in the autoremove list.

---

### Post by sunfromhere on 2012-05-10
Thanks for the reply.

"sudo apt-get autoremove" gives me 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded, but the updater still downloads updates for these orphans.

EDIT: locate gwibber and locate evolution gives a long list of filenames, but I do not have these installed on my computer.

---

### Post by 3rdalbum on 2012-05-11
> **sunfromhere said:**
> Thanks for the reply.

"sudo apt-get autoremove" gives me 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded, but the updater still downloads updates for these orphans.

EDIT: locate gwibber and locate evolution gives a long list of filenames, but I do not have these installed on my computer.

Just thinking about it a little more, I think a couple of Evolution packages are dependencies of the Gnome desktop, and I believe some Gwibber packages are dependencies of Ubuntu to provide some messaging features. Those packages wouldn't really be "orphans" if they are dependencies of things you've got installed, such as the Messaging Menu Indicator.

You can search in Synaptic Package Manager for Gwibber or Evolution and see which packages they are. If you mark them for removal in Synaptic, it will tell you what other packages will need to be removed. I've got a feeling it would give you a very long list of packages - if it does, or if there's anything else listed that seems important, abort and quit Synaptic straight away.

Sorry for the delay in replying, your post had fallen off the front page of the forum.

---

