---
title: "How do I turn off annoying shutdown beeps in 9.04?"
date: 2009-10-19
forum: General Help
---

### Post by RonB123123 on 2009-10-19
I upgraded to 9.04 recently and it has a very annoying beep when I shutdown my computer even when the volume is muted. How do I turn it off?

Thanks,
Ron

---

### Post by renkinjutsu on 2009-10-20
```
sudo modprobe -r pcspkr
```
that fixes it for the current boot..
and for the permanent fix: ```
sudo echo pcspkr >> /etc/modprobe.d/blacklist.conf
```

---

### Post by RonB123123 on 2009-10-20
The first command ran fine but the 2nd one said

$ sudo echo pcspkr >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied

??

---

### Post by scouser73 on 2009-10-20
I used the advice set out in this tutorial - [[COLOR="Red"]**Ubuntu: Disable The Shutdown Beep**[/COLOR]]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown")

---

### Post by renkinjutsu on 2009-10-20
try this instead ```
sudo -s
echo pcspkr >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by mechro on 2009-10-20
> **scouser73 said:**
> I used the advice set out in this tutorial - [[COLOR="Red"]**Ubuntu: Disable The Shutdown Beep**[/COLOR]]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown")

From reading that tutorial, possibly renkinjutsu meant to write...

```
sudo -s
echo blacklist pcspkr >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by RonB123123 on 2009-10-20
Sweet it worked. Thank you very much everyone.

---

### Post by toDIEisGAIN on 2009-11-01
I too have been helped by this thread. Thank you.

---

