---
title: "Scan Vista for Problems/Errors"
date: 2010-12-29
forum: General Help
---

### Post by ut1988 on 2010-12-29
I have had problems starting Windows Vista in that nothing happens when I start up the computer. Windows starts loading up and then after a brief blue flicker in the screen (it doesnt seem to be the blue screen of death) it restarts and does this again.
I can get into the system and back up files with Ubuntu 10.04 if I choose to re-install windows.
However, is there a way I can use Ubuntu to scan the system for errors to find out what the problem is exactly and fix it like that?

Thanks

---

### Post by mike555 on 2010-12-29
Sounds like a boot sector virus....... it might be fixed by using a "live" cd with an anti-virus , like "dr.web" from; [http://www.freedrweb.com/livecd/](http://www.freedrweb.com/livecd/)

---

### Post by endotherm on 2010-12-29
prolly not, but there may be other ways. try booting into safemode, or boot from a vista disk to get to the Recovery console ([http://www.ehow.com/how_6835726_start-vista-recovery-console.html](http://www.ehow.com/how_6835726_start-vista-recovery-console.html)) and run this command to check the integrity of your system files:
```

sfc.exe /SCANNOW

```

if you have not made any changes to your system, it may be a simple filesystem problem. running chkdsk /f from recovery mode may help if that is the case.

---

### Post by ut1988 on 2010-12-29
> **endotherm said:**
> prolly not, but there may be other ways. try booting into safemode, or boot from a vista disk to get to the Recovery console ([http://www.ehow.com/how_6835726_start-vista-recovery-console.html](http://www.ehow.com/how_6835726_start-vista-recovery-console.html)) and run this command to check the integrity of your system files:
```

sfc.exe /SCANNOW

```

if you have not made any changes to your system, it may be a simple filesystem problem. running chkdsk /f from recovery mode may help if that is the case.

Is this on Ubuntu or on Windows Recovery Console?
When I start Windows it asks if I want to repair, and is about to start the repair process when the same problem occurs!

---

### Post by endotherm on 2010-12-29
> **ut1988 said:**
> Is this on Ubuntu or on Windows Recovery Console?
When I start Windows it asks if I want to repair, and is about to start the repair process when the same problem occurs!
it's a windows utility.
it sounds like you will probably have to backup and reinstall then. lame.

---

