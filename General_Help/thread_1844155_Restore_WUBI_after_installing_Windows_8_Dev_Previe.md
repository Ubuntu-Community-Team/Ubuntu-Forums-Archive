---
title: "Restore WUBI after installing Windows 8 Dev Preview?"
date: 2011-09-14
forum: General Help
---

### Post by MASTER260 on 2011-09-14
The fact that [[COLOR=#339933]Windows[/COLOR]]("http://www.neowin.net/forum/topic/1025498-restore-wubi-after-installing-8102/page__pid__594310548#") 8 will now have its own GUI bootloader, Metro-styled no less, I personally find amazing, but not if it breaks Ubuntu & Joli OS' versions of WUBI. (Yes Joli OS has its own special version of WUBI.) Umm... any idea how to get Ubuntu & Joli OS back?
 
Thanks,
M260
 
P.S. My [[COLOR=#336699]Win[/COLOR]]("http://www.neowin.net/forum/topic/1025498-restore-wubi-after-installing-8102/page__pid__594310548#") 7 partition seems to be fine, just to let you know.
 
EDIT: Well, that's weird - my Win 7 bootloader is back, which thus allows me to go into WUBI... I wonder, considering how the Windows 8 bootloader apparently works, if it has to do with the fact that I made Windows 7 the default to boot to... Anyone wanaa test?

---

### Post by Thedark7 on 2011-09-19
I'm having the same problem. I guess I'll try making Windows 7 the default...

Is it still safe to uninstall wubi? Can I install Ubuntu and use grub for the triple boot?

---

### Post by raja.genupula on 2011-09-19
[http://ubuntuforums.org/showthread.php?p=11265065](http://ubuntuforums.org/showthread.php?p=11265065)

look at this

---

### Post by varunendra on 2011-09-19
> **Thedark7 said:**
> I'm having the same problem. I guess I'll try making Windows 7 the default...

Is it still safe to uninstall wubi? Can I install Ubuntu and use grub for the triple boot?
It is perfectly safe to uninstall a wubi ubuntu installation from within the Windows in which it is installed. Simply uninstall it like a normal application.

As for triple booting, it 'should' work if you install ubuntu in parallel to win7/8 and let grub be installed on the MBR. It should definitely work if current boot loader is win7's boot loader. But I can't say the same about Win8's boot loader (if that is default) since it is rather new. But again, if you have installation DVDs of Win7 or Win8, then you can always restore their MBR replacing grub in case it causes problems.

So if you can dedicate a partition to ubuntu (and I suggest you should), the go ahead. Install ubuntu in its own partition, let grub be installed at MBR, and it should take care of everything.

---

