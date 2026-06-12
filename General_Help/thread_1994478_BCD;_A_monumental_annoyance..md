---
title: "BCD; A monumental annoyance."
date: 2012-06-02
forum: General Help
---

### Post by AnonymousJustified on 2012-06-02
In Windows Vista and 7, the old boot.ini from Windows XP has been replaced. It has been replaced with something called the BCD. BCD runs almost the exact same as boot.ini, albeit a little more customizable. Oh, that and only Windows can mess with it.

And, I made the stupid mistake of making Ubuntu the default boot and setting the waiting time to zero.

I don't have access to Windows in any form on this PC now. And I need to boot Windows. ](*,)

I figured that if I could run Control Panel in WINE, I may be able to fix this, but I am hung up on how.

---

### Post by Ron S on 2012-06-02
Hi 
To get grub back try pressing the left shift key on boot up . If that doesn't work boot into ubuntu and  edit grub buy changing the grub timeout value as described in answer 1.
[HTML]http://askubuntu.com/questions/43020/decrease-grub-timeout[/HTML]Hope it helps.

---

### Post by AnonymousJustified on 2012-06-02
Well, GRUB doesn't help at all, sadly. It's not detecting the Windows Vista OS, meaning I can't access that via GRUB.

Is there some way to make it run via GRUB? I'm running on a Wubi install, if it helps.

---

### Post by bcbc on 2012-06-02
You need a windows repair CD. You can normally burn one from Windows (bit late for you, but maybe you know someone with the same version of windows).
Or you can download a repair CD ISO and burn it for about $10USD from here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Then I believe it's (from the repair command prompt):
```
bcdedit /timeout 10
```

---

