---
title: "update manager is trying to install openoffice even though I have removed it."
date: 2011-02-14
forum: General Help
---

### Post by noalternative on 2011-02-14
I have customized lucid so it is easier on my computer specs.  My old laptop only has 256mb of ram.  So I have removed openoffice and replaced it with abiword/gnumeric and installed the lxde desktop.  I have had this configuration for a month and half now and update manager has never had a problem with it.  Now all of the sudden it does and is trying to reinstall openoffice all the time.  What can I do?

---

### Post by roger_1960 on 2011-02-14
Hi

I had a similar problem yesterday.  By searching synaptic for "openoffice" I found a few files left over from the old openoffice installation.  I removed these using synaptic and after that update manager behaved OK.  I suspect update manager was trying to update the remaining few files.

Hope this helps

---

### Post by Frogs Hair on 2011-02-14
Try ```
sudo apt-get remove --purge
``` The link may help explain why this happens.[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by kn0w-b1nary on 2011-02-14
you can also use Ubuntu tweak to empty cache and remove unneeded config files, as well as left over files not removed by apt-get autoremove.

Hope this helps!

---

### Post by noalternative on 2011-02-14
> **roger_1960 said:**
> Hi

I had a similar problem yesterday.  By searching synaptic for "openoffice" I found a few files left over from the old openoffice installation.  I removed these using synaptic and after that update manager behaved OK.  I suspect update manager was trying to update the remaining few files.

Hope this helps
Thanks everyone, particularly Roger.  update-manager is ok now.

---

