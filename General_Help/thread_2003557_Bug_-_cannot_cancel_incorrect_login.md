---
title: "Bug? - cannot cancel incorrect login"
date: 2012-06-14
forum: General Help
---

### Post by Azdour on 2012-06-14
Hi,

On Xubuntu 12.04 in my lightdm.conf under [SeatDefaults] I have:

```

greeter-hide-users = true
allow-guest = false

```

The bug I seem to have found is:

[LIST]
[*]Enter your login name
[*]When it asks for the password click on Cancel
[/LIST]

At this point I would expect it to go back and ask for the login name but it does not. It gets stuck here and I have to reboot/restart the computer in order to login correctly.

---

### Post by Artemus on 2012-07-01
> **Azdour said:**
> Hi,

On Xubuntu 12.04 in my lightdm.conf under [SeatDefaults] I have:

```

greeter-hide-users = true
allow-guest = false

```

The bug I seem to have found is:

[LIST]
[*]Enter your login name
[*]When it asks for the password click on Cancel
[/LIST]

At this point I would expect it to go back and ask for the login name but it does not. It gets stuck here and I have to reboot/restart the computer in order to login correctly.



Same problem here. It is very annoying.

You can get around it without rebooting by going to a virtual console (ctrl-alt-F2), logging in there, and running "sudo service lightdm restart". Still annoying, but at least you don't have to reboot.

---

### Post by Azdour on 2012-07-18
Hi,

I hope they fix it soon as its a real pain for normal users...

---

