---
title: "Shutdown Dialogue Keeps Appearing"
date: 2010-05-01
forum: General Help
---

### Post by noo2buntu on 2010-05-01
I've just installed Ubuntu 10.04 and have the following problem.

Every few minutes or so the Shutdown Dialogue Window pops up saying the system will shutdown automatically in 60 seconds and begins counting down.

Is there anyway I can stop this from happening?

---

### Post by dino99 on 2010-05-01
tweak the power saving settings to not hibernate every 10 seconds :)

---

### Post by noo2buntu on 2010-05-01
Thanks for the quick response. Not wishing to appear ignorant how do I tweak the hibernating?

---

### Post by dino99 on 2010-05-01
> **noo2buntu said:**
> Thanks for the quick response. Not wishing to appear ignorant how do I tweak the hibernating?

top menu: system --> pref --> sreensaver --> power saving

---

### Post by noo2buntu on 2010-05-01
> **dino99 said:**
> top menu: system --> pref --> sreensaver --> power saving

I've disabled the screensaver having previously tweaked the power management but to no avail. The Shutdown Dialogue still appears every few minutes or so and starts counting down. This means I am unable to leave my computer unattended.

I also have problems with the nvidia drivers - could this be related?

---

### Post by dino99 on 2010-05-01
> **noo2buntu said:**
> I've disabled the screensaver having previously tweaked the power management but to no avail. The Shutdown Dialogue still appears every few minutes or so and starts counting down. This means I am unable to leave my computer unattended.

I also have problems with the nvidia drivers - could this be related?

check nvidia-settings (dont know) and look into the bios settings first

---

### Post by noo2buntu on 2010-05-02
> **dino99 said:**
> check nvidia-settings (dont know) and look into the bios settings first

Well - it seems both of the problems are related to the nvidia drivers (or lack of them). 

I missed out on 9.10 and it looks like I'll be missing out on 10.04 as well.

I've reinstalled 9.04 - which incidentally uses the grub loader whereas 10.04 uses grub2. Some times when I boot up it fails with "grub rescue>". Looks like remnants of grub2 have been left in the boot sector. Can I clean the boot sector of all remnants of grub2?

Thanks for your time.

---

