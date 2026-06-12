---
title: "Multi boot grub config - quick question"
date: 2012-01-12
forum: General Help
---

### Post by warmnscsi on 2012-01-12
Can someone look at this grub.conf file for me real quick. The default is set to 3 so would that mean the windows partition would load if the user doesnt do anything? Doesn't it start at 0? I thought the windows partition would be considered "2".
 
```

[FONT=Calibri]#boot=/dev/hda3[/FONT]
[FONT=Calibri]default=3[/FONT]
[FONT=Calibri]timeout=20[/FONT]
[FONT=Calibri]splashimage=(hd0,2)/grub/splash.xpm.gz[/FONT]
[FONT=Calibri]title Red Hat Linux (2.4.20-31.9) (runlevel 3)[/FONT]
[FONT=Calibri]       root (hd0,2)[/FONT]
[FONT=Calibri]       kernel /vmlinuz-2.4.20-31.9 ro root=/dev/Volume00/LogVol00 3[/FONT]
[FONT=Calibri]       initrd /initrd-2.4.20-31.9.img[/FONT]
[FONT=Calibri]title Red Hat Linux (2.4.20-31.9)[/FONT]
[FONT=Calibri]       root (hd0,2)[/FONT]
[FONT=Calibri]       kernel /vmlinuz-2.4.20-31.9 ro root=/dev/Volume00/LogVol00[/FONT]
[FONT=Calibri]       initrd /initrd-2.4.20-31.9.img[/FONT]
[FONT=Calibri]title Win2K[/FONT]
[FONT=Calibri]       rootnoverify (hd0,0)[/FONT]
[FONT=Calibri]       chainloader +1[/FONT][FONT=Calibri][/FONT]

```

---

### Post by Mark Phelps on 2012-01-12
The first default, from what I remember about GRUB legacy, is the stanza # that is selected by default, and you're right, it starts with zero.  So, it being "3" probably forces GRUB to actually start with the first stanza -- #0.

And yes, I believe selecting the Windows stanza by default would require a "2".

---

### Post by warmnscsi on 2012-01-12
Awesome, thanks.

---

