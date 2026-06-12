---
title: "Edubuntu!!!!!!"
date: 2009-09-20
forum: General Help
---

### Post by N1k0n on 2009-09-20
Hi All

Logged out of Ubuntu 9.04 yesterday, Today it's Edubuntu and I cant log in? :confused:
I must have installed something, but what! who knows? 
I was in the process of getting my laptop fully Ubuntu'd (if that's word! :)) for the last couple of days so Ive been downloading/installing various things, but I'm quite sure I would have noticed something called Edubuntu!!!

I'm still running a dual boot with Vista (said quietly :) ) and as soon as I've got everything working its adios Windows!! :lolflag:

Any help would be appreciated

Thanks in advance

---

### Post by bodyharvester on 2009-09-20
go to the ADD//REMOVE feature and in the search box type in "edubuntu" and make sure the ticky boxes are un-tickied (make sure you search all available applications)

dunno if thats a solution though :|

---

### Post by N1k0n on 2009-09-20
Thanks for quick reply Bodyharvester, but I cant login :confused:

---

### Post by bodyharvester on 2009-09-20
> **N1k0n said:**
> Thanks for quick reply Bodyharvester, but I cant login :confused:

what? cant you make a new user or anything? damn, i dont think im gonna be able to help if you cant log in :( not that i had many good ideas, sorry man:|

EDIT: there is a way to get in, ive seen it in a polst somewhere when i first came here, ill go see if i can find something

---

### Post by P4man on 2009-09-20
I suppose you installed some packages that depended on edubuntu, but that doesn't explain why you cant log in? What happens when you try to log in, does t not accept your password ?

If its a password thing, then upon booting, go in to grub menu, select the recovery mode. Then open a root shell. At the prompt type:

```

passwd yourusername

```
type in a new password, then reboot

```
reboot
```

If its not a password issue, then please elaborate a bit.

---

### Post by N1k0n on 2009-09-20
OOPS sorry people..... It was a '1D 10 t user error' for the reason not being able to log in :oops:

...so now I'm in Ill go and try and locate what I need to delete...

Cheers you guys! :popcorn:

---

### Post by N1k0n on 2009-09-20
I've searched in my ADD/REMOVE and I have nothing installed with regards to Edubuntu!
:confused:

---

### Post by P4man on 2009-09-20
> **N1k0n said:**
> I've searched in my ADD/REMOVE and I have nothing installed with regards to Edubuntu!
:confused:

You wouldn't see it there. It could be a program that *depends* on some stuff from edubuntu. Ubuntu will automatically install those dependencies, but it might make your ubuntu look like edubuntu now. If you're curious what caused it, go system > adminstration > synaptic. Then file > history and have a look.
I suspect the only thing that actually changed is the splash though. If you want to restore that, try this:

```
sudo dpkg-reconfigure usplash-theme-ubuntu
```

---

