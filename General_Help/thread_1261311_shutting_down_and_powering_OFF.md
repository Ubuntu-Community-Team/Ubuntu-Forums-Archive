---
title: "shutting down and powering OFF"
date: 2009-09-08
forum: General Help
---

### Post by woodsw75 on 2009-09-08
HI there :P

I am a complete novis when it comes to Ubuntu and Linux.... I have read the posts about shutting down from Ubuntu, however.... i dont understand and i was wondering if some kind person could explain to me how to make it so that my computer shuts down properly and powers down (when using ubuntu)

sorry to be such a pain and really looking forward to any help! 

best wishes 

Will :)

---

### Post by P4man on 2009-09-08
Im assuming the normal "shut down" from the top right menu is not working for you?
What happens when you ask it to shut down ?

---

### Post by GoldenSun on 2009-09-08
you can do it by terminal
restart
```

sudo shutdown -r now

```

shutdown
```

sudo shutdown -h now

```

---

### Post by woodsw75 on 2009-09-09
> **P4man said:**
> Im assuming the normal "shut down" from the top right menu is not working for you?
What happens when you ask it to shut down ?

When i go to shut down the computer it does not power down and instead shows a black screen with flashing - for input commands?!

does this make sense??

thanks for replying to me ... very much appreciated!

---

### Post by dynamics on 2009-09-09
Same issue here tooo.... 
I searched a few threads and found that the best solution is pressing Ctrl+ Alt + Del. This shuts off and again restarts the comp. Immediately press your Power button before the Grub appears.
This is what I am following for the time being.
Sometimes Logging out from user account and then Shutting down helps. But no guarenty that this will always work. I am using Dell 1555 and ATI Radeon Mobility 4570 graphic card.

Hope some one will post a simple solution not involving adding/removing/changing anything in Kernal and all those painful procedures.
:(

---

### Post by t4ggs on 2009-09-09
the solution is quite simple, open a terminal, enter
```
sudo gedit /boot/grub/menu.lst
```

then in the first entry of ubuntu, at the end of the kernel line, add the following:
acpi=force noapic


example: u should have something like this:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		77a79dd7-aaa0-4128-ba5c-16e106bc9801
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=77a79dd7-aaa0-4128-ba5c-16e106bc9801 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet


make it looks like this:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		77a79dd7-aaa0-4128-ba5c-16e106bc9801
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=77a79dd7-aaa0-4128-ba5c-16e106bc9801 ro quiet splash acpi=force noapic
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

hope it helps

---

### Post by t4ggs on 2009-09-10
and u will have to restart

---

