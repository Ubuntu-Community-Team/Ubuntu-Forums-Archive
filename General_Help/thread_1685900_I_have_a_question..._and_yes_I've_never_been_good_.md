---
title: "I have a question... and yes I've never been good at titles."
date: 2011-02-11
forum: General Help
---

### Post by TheFolklorist on 2011-02-11
I'm not sure where to post this so I figured here would work. I'm sorry if its in the wrong place.

what do
2.6.35-25 generic and 2.6.32-28- generic at the boot screen mean? I can only boot into the second one, if I try to boot into the top one the light in my laptops monitor doesn't work. it was the same when I tried to use the live CD thing. I managed to get 10.10 upgraded from 10.04 but now i cant use the top thing, which wouldn't be a problem except sometime the windows side of my computer will restart after an update and then I'll automatically be started up into the first boot thing if I'm not at my computer. I then have to hard shutdown, which I heard is bad for my computer. Sorry if this is a dumb question, I'm kinda new to all of this.

---

### Post by riverfr0zen on 2011-02-11
You should really change the title of your post to something more descriptive if you expect help. Something like "Don't understand boot options" would have been fine.

Anyway, the options you asked about refer to the Linux kernel you want to boot into. The kernel is sort of the 'underlying system' behind Linux. It is constantly updated, and a new entry on the boot screen basically indicates that the kernel was upgraded (obviously when you upgraded from 10.04 to 10.10).

That the first option doesn't work indicates a problem with your upgrade. You should try and fix whatever the issue is -- probably an X11 (the windowing system) configuration issue from the symptom you described.

Until you fix it, however, you can modify your boot menu. Follow the instructions at the link below:
[https://help.ubuntu.com/community/BootOptions#Change Boot Options Permanently On An Existing Installation]("https://help.ubuntu.com/community/BootOptions#Change Boot Options Permanently On An Existing Installation"). 

However, I recommend instead of deleting the entry for the first option, just comment out the lines related to it. That way you can uncomment them and use the first option when you're trying to fix the issue. 

The options for each entry should look something like this:

```
title           Ubuntu 10.10, kernel 2.6.35-25-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.35-25-generic root=UUID=1f434s-64345-323s-342-3232323323 ro quiet splash
initrd          /boot/initrd.img-2.6.35-25-generic
quiet
```

So just comment them out by adding a '#' at the beginning of each line:

```
#title           Ubuntu 10.10, kernel 2.6.35-25-generic
#root            (hd0,4)
#kernel          /boot/vmlinuz-2.6.35-25-generic root=UUID=1f434s-64345-323s-342-3232323323 ro quiet splash
#initrd          /boot/initrd.img-2.6.35-25-generic
#quiet
```


Be careful when you edit the boot menu file!

---

### Post by cjhabs on 2011-02-11
> **TheFolklorist said:**
> I'm not sure where to post this so I figured here would work. I'm sorry if its in the wrong place.

what do
2.6.35-25 generic and 2.6.32-28- generic at the boot screen mean? I can only boot into the second one, if I try to boot into the top one the light in my laptops monitor doesn't work. it was the same when I tried to use the live CD thing. I managed to get 10.10 upgraded from 10.04 but now i cant use the top thing, which wouldn't be a problem except sometime the windows side of my computer will restart after an update and then I'll automatically be started up into the first boot thing if I'm not at my computer. I then have to hard shutdown, which I heard is bad for my computer. Sorry if this is a dumb question, I'm kinda new to all of this.

What you are seeing is that you have 2 kernels available for booting - this is not uncommon - I have 8 - they are added when the system does updates (not always, just when a kernel update is available).
I think you have a typo in the numbers - aren't they 2.6.32.25 and 2.6.32.28?

You can remove the uneccessary kernel and update your grub configuration, but you need to be careful because you can mess up your system boot process - I suggest you read up about grub2 before changing anything.

Also, there is a setting in the configuration that allows you to hide the menu - that is the default for a single OS system.

---

### Post by coffeecat on 2011-02-11
@riverfr0zen, those instructions are for legacy grub. With 10.04 updated to 10.10 the OP will have grub 2.

---

### Post by coffeecat on 2011-02-11
> **TheFolklorist said:**
> 2.6.35-25 generic and 2.6.32-28- generic at the boot screen mean?

As others have said, those are kernels. The 2.6.32 one is the 10.04 kernel and the 2.6.35, the 10.10 kernel. It's OK to use the older kernel for the time being but clearly something is wrong if you can't use the Maverick kernel. What laptop do you have? It might be worth doing a search to see if other owners have problems with your model of laptop in Maverick. It may be a driver issue - most drivers being kernel modules.

---

### Post by riverfr0zen on 2011-02-11
> **coffeecat said:**
> @riverfr0zen, those instructions are for legacy grub. With 10.04 updated to 10.10 the OP will have grub 2.

Huh, good thing you caught that. My box is on 10.10 but has been running since waaay back, so still uses grub. I didn't even know there's a grub2 ;)

---

### Post by coffeecat on 2011-02-11
> **riverfr0zen said:**
> I didn't even know there's a grub2 ;)

You will when you start trying to configure it! :-s

:p

---

### Post by TheFolklorist on 2011-02-11
Thanks for the replies, I now know what I'll be working on once I get home from work lol

---

