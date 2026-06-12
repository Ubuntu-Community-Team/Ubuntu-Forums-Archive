---
title: "indicator-multiload segmentation fault"
date: 2012-03-06
forum: General Help
---

### Post by Fraoch on 2012-03-06
I reinstalled Ubuntu 11.10 32-bit today.  I kept my old /home directory.

After installation, indicator-multiload worked for a while (this is called "System Load Indicator" by Software Centre.)  Suddenly it has stopped appearing and attempts to start it aren't hopeful:

```
$ indicator-multiload
/usr/share/indicator-multiload/preferences.ui

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_construct: assertion `datadirectory != NULL' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_add_icon_data: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed

** (indicator-multiload:6450): CRITICAL **: multi_load_indicator_get_icon_datas: assertion `IS_MULTI_LOAD_INDICATOR (self)' failed
Segmentation fault
```

Ouch!  I removed the program from Startup Applications, removed the .indicator-multiload.json file from my /home menu and reinstalled it a half-dozen times, doing a complete uninstall through Synaptic.  Still no change.

Oddly I can't load /usr/share/indicator-multiload/preferences.ui just to look at it either, Firefox tries to open it but opens blank tab after blank tab after blank tab, kind of like the file is referencing itself in an endless loop.  I can open the file in Text Editor, it sort of looks like an XML file.

Any ideas?

Thank you.

---

