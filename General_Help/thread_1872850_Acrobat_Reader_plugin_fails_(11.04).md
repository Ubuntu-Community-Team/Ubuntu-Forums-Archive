---
title: "Acrobat Reader plugin fails (11.04)"
date: 2011-10-31
forum: General Help
---

### Post by msewing on 2011-10-31
Acrobat plugin in Firefox 7.0.1, 64 bit, (also in earlier FF versions).  I get good display of a single pdf, but if I close it and wait ~20 seconds, the acroread process goes defunct (seen in ps) and further attempts to show pdfs fail with blank (white or black) screen.  

Ps info:

```
12151 ?        Sl     0:00  \_ /usr/lib/firefox-7.0.1/plugin-container /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so -greomni /usr/lib/firefox-7.0.1/omni.jar 11767 true plugin
12164 ?        S      0:02  |   \_ /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /opt/Adobe/Reader9/Browser/intellinux/nppdf.so --connection /org/wrapper/NSPlugins/nppdf.so/12151-2
12175 ?        Z      0:01  |       \_ [acroread] <defunct>
```


If I manually kill npviewer.bin, I can load a new pdf OK. I've tried disabling other plugins and extensions, but no effect.

Maybe this is Adobe's bug, but... Does anyone have a magic bullet to offer?

TIA
Martin

---

### Post by mike555 on 2011-10-31
You don't need Adobe reader bloat or the plugin....... the builtin pdf reader is much lighter and can be made to open in Firefox window by installing "MozPlugger".

---

