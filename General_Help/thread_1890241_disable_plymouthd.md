---
title: "disable plymouthd"
date: 2011-12-03
forum: General Help
---

### Post by moongya on 2011-12-03
hi all,

I successfully managed to disable Plymouth from starting while booting.. result 32 sec booth time...
machine specs, core2 duo E4600, G31pr (motherboard)... os is lucid

i believe if plymouthd is disabled, we can further reduce the boot time...i suppose upstart initiates plymouthd, but could not find how to stop it from doing so..

now i have searched everywhere how to do that.. to no avail

can anyone help me please?

---

### Post by fantab on 2011-12-03
> **moongya said:**
> hi all,

I successfully managed to disable Plymouth from starting while booting.. result 32 sec booth time...
machine specs, core2 duo E4600, G31pr (motherboard)... os is lucid

i believe if plymouthd is disabled, we can further reduce the boot time...i suppose upstart initiates plymouthd, but could not find how to stop it from doing so..

now i have searched everywhere how to do that.. to no avail

can anyone help me please?

You can uninstall Plymouth

```
sudo apt-get remove --purge plymouth
```

Or to get a text boot you can do this From terminal:

```
sudo gedit /etc/default/grub
```Look for this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

and REMOVE "quiet splash" and SAVE the file.

Now you have to update grub
```
sudo update-grub
```

---

### Post by moongya on 2011-12-03
hey tnx for replying

modifying the grub, disables plymouth but not plymouthd...
n purging plymouth will remove a bunch of other required packages.. so that is not an option

 i need to prevent plymouthd from loading while boot

any ideas?

---

