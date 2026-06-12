---
title: "Switch VT using alt instead of ctrl+alt?"
date: 2011-11-24
forum: General Help
---

### Post by frostyfrog2 on 2011-11-24
Does anyone know of a way to switch virtual terminals from Xorg with alt instead of ctrl+alt at boot? I know I can do it if I run [FONT="Courier New"][COLOR="DimGray"]echo "1" > /proc/sys/kernel/sysrq[/COLOR][/FONT] then press ALT+SysReq+R, but I would like to switch without doing that.

xorg.conf.d/10-me.conf
```

Section "ServerFlags"
	Option	        "VTSysReq"   "on"
	Option		"DontZoom"   "on"
EndSection

```

[RIGHT]Running ***[COLOR="Blue"]Arch[/COLOR][COLOR="Silver"]Linux[/COLOR]***[/RIGHT]

---

