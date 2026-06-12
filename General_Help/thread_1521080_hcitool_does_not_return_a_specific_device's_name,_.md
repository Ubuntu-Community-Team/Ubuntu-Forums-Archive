---
title: "hcitool does not return a specific device's name, though finds all other devices"
date: 2010-06-30
forum: General Help
---

### Post by Knitter on 2010-06-30
Hi,

I've just installed Ubuntu 10.4 and was trying to use a small bash script for which I need hcitool to return the device name.

The problem is that hcitool returns nothing when I query for the device's name using the address. The address was found using hcitool's scan option, so I know the device is responding.

Also, I can pair the laptop with the phone using gnome's bluetooth application, what I can't do is get hcitool to return the device's name.

I've tried scanning for other devices and querying for their names, and I tried using another laptop with Ubuntu installed to get the phone's name, in all cases hcitool returns the device's name, only when issuing the query from my mac to this specific phone does hcitool fail.

I'm issuing the following commands:

```
knitter@knitter-laptop:~$ hcitool scan
Scanning ...
	<address omitted>	<name omitted>
	00:8D:31:8C:0C:0A	KntSE
	<address omitted>	<name omitted>

```

After getting the list of devices that were found I grab my phone's address and ask for the name.

```
knitter@knitter-laptop:~$ hcitool name 00:8D:31:8C:0C:0A
knitter@knitter-laptop:~$
```

As you can see, when scanning for devices I get both the address and the name, but when asking for the name I get nothing, and I really needed to use the **hcitool name <address>** command for the script as it would make things easier.

As anyone had a similar problem?

Regards,

Knitter

---

### Post by dino99 on 2010-06-30
[http://manpages.ubuntu.com/manpages/lucid/man1/hcitool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/hcitool.1.html)

---

### Post by Knitter on 2010-06-30
A RTFM answer is quite nice, but I have red and re-red those man pages and have found nothing useful about the problem.

If you'd kind enough to provide a more to the point answer, I would appreciate it.

Regards,

Knitter

---

