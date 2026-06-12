---
title: "I want have a command to run while resuming."
date: 2009-08-23
forum: General Help
---

### Post by ednso on 2009-08-23
Hi guys,

At this weekend I decided to give I try on Ubuntu after many problems with openSUSE
11.1. Well, I am having a good experience with Ubuntu 9.04 and I am hopping to keep
it in my laptop.

My question is about suspend. My wireless cards is a crap rtl8187b (Realtek) that
works fine only if I run "iwconfig wlan0 rate 11M fixed" before connecting.
I have already this line on the file "/etc/rc.local". For resuming, I had to put
the module of this wireless card to be unloaded before suspend and probed
after resume. I have the line
```
SUSPEND_MODULES="rtl8187"

```on the file "/etc/pm/config.d/00sleep_module".

Unfortunately, after resuming, the wireless connection rate becomes 54 Mbps, so that
it stays unstable. So, is there any way of the system run
```

iwconfig wlan0 rate 11M fixed
```after reloading the wireless module in resume and before connecting to the net?

Any help is welcome.

Bye.

---

### Post by slakkie on 2009-08-23
Is your card configured in the interfaces file? You could force it there.. 

Define a post-up action:

```

iface wlanX inet static
address xx.xx.xx.xx
netmask 255.255.255.0
gateway xx.xx.xx.xx
post-up /sbin/iwconfig wlanX rate 11M

```

When ever that interface comes up, it will be set to 11M...

---

### Post by ednso on 2009-08-23
> **slakkie said:**
> Is your card configured in the interfaces file? You could force it there.. 

Define a post-up action:

```

iface wlanX inet static
address xx.xx.xx.xx
netmask 255.255.255.0
gateway xx.xx.xx.xx
post-up /sbin/iwconfig wlanX rate 11M

```When ever that interface comes up, it will be set to 11M...

I am sorry. I did not get.
Where am I suppose to put this?
And, these xx.xx.xx.xx, they should be there although my connection is dynamic?

Thanks.

---

### Post by H4F on 2009-08-23
I think you should do those changes in /etc/networks/interfaces
those xxxx should be ip. just comment out the whole line

---

### Post by slakkie on 2009-08-23
For DHCP it is even simpler:

```

iface wlan0 inet dhcp
post-up iwconfig wlan0 rate 11M

```

---

### Post by ednso on 2009-08-23
> **slakkie said:**
> For DHCP it is even simpler:

```

iface wlan0 inet dhcp
post-up iwconfig wlan0 rate 11M

```

It is not working. When the system start, the wlan0 interface does not come up.
If I make it comes up manually with "ifconfig wlan0 up", network manager cannot
gain access to the interface.

I have tried only the second line "post-up iwconfig wlan0 rate 11M". In this case
the interface will come up on startup and connect at 11M, but when suspend/resume
it connects again at 54M.

So. I more can I do?

Thanks.

---

### Post by ednso on 2009-08-23
Hi every one,

Problem solved. :P

I created I script "/etc/pm/sleep.d/00dam_rtl8187" containing:
```

#!/bin/bash
case "$1" in
    hibernate|suspend)
        # Stopping is not required.
        ;;
    thaw|resume)
        iwconfig wlan0 rate 11M fixed
        ;;
esac

```
I also moved the file "/etc/pm/config.d/00sleep_module" to
"/etc/pm/config.d/01sleep_module" so that it will be read after
"/etc/pm/sleep.d/00dam_rtl8187" suspending and before when resuming.
This have to be this way because the command "iwconfig wlan0 rate 11M fixed"
has to be executed after to module rtl8187 be reloaded.

I found instructions to do this at:
[http://en.opensuse.org/Pm-utils#Creating_your_own_hooks](http://en.opensuse.org/Pm-utils#Creating_your_own_hooks)

Any way, many thanks for the replies!

---

