---
title: "MBR Explained"
date: 2009-08-19
forum: General Help
---

### Post by Penguin Guy on 2009-08-19
_When Removing Linux_
```

        [COLOR="Silver"]*Hard Disk*[/COLOR]               : The Master Boot Record tells the 
|-----|---------|-------|       : computer which partition to boot from. 
| MBR | Windows | Linux |       : It is currently pointing to Linux  
|-----|---------|-------|       : because that's where [GRUB]("http://ubuntuforums.org/attachment.php?attachmentid=125732&d=1250864044") is installed
   |                ^           : You can find it at [COLOR="Green"]/boot/grub[/COLOR].
   -----------------'           :


```

```

        [COLOR="Silver"]*Hard Disk*[/COLOR]               :
|-----|---------|-------|       : If you delete Linux, [GRUB]("http://ubuntuforums.org/attachment.php?attachmentid=125732&d=1250864044") goes with it;
| MBR | Windows | [COLOR="Silver"]Empty[/COLOR] |       : the MBR will still be pointing to where 
|-----|---------|-------|       : [GRUB]("http://ubuntuforums.org/attachment.php?attachmentid=125732&d=1250864044") was, but there will be nothing there.
   |                ^           : Obviously, the system will not boot.
   -----------------'           :


```

```

        [COLOR="Silver"]*Hard Disk*[/COLOR]               :
|-----|---------|-------|       :
| MBR | Windows | [COLOR="Silver"]Empty[/COLOR] |       : The [Windows CD]("http://ubuntuforums.org/attachment.php?attachmentid=125738&stc=1&d=1250865025") command [COLOR="Green"]fixmbr[/COLOR] points
|-----|---------|-------|       : the **M**aster **B**oot **R**ecord back to Windows.
   |       ^                    :
   --------'                    :


```


_When Installing Windows_
When installing Windows the opposite will happen. The MBR will be changed to boot Windows rather than grub. Look into the command [FONT="Courier New"][COLOR="Green"]grub-install[/COLOR][/FONT] to reinstall grub and fix this problem.

---

