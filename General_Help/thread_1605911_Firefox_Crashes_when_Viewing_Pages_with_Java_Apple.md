---
title: "Firefox Crashes when Viewing Pages with Java Applets"
date: 2010-10-25
forum: General Help
---

### Post by jeff_ on 2010-10-25
Firefox is crashing whenever I go to a page with a java applet such as this one [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I get the following output in the command line:
GCJ PLUGIN: thread 0xb5e191f0: NP_Initialize
GCJ PLUGIN: thread 0xb5e191f0: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0xb5e191f0: NP_Initialize return
GCJ PLUGIN: thread 0xb5e191f0: GCJ_New
GCJ PLUGIN: thread 0xb5e191f0: plugin_data_new
GCJ PLUGIN: thread 0xb5e191f0: plugin_data_new return
GCJ PLUGIN: thread 0xb5e191f0: plugin_get_documentbase
gcjwebplugin.cc:886: thread 0xb5e191f0: Error: peer is NULL.
GCJ PLUGIN: thread 0xb5e191f0: plugin_get_documentbase return
gcjwebplugin.cc:319: thread 0xb5e191f0: Error: Documentbase retrieval failed. Browser not Mozilla-based?
GCJ PLUGIN: thread 0xb5e191f0: GCJ_New return
GCJ PLUGIN: thread 0xb5e191f0: GCJ_GetValue
GCJ PLUGIN: thread 0xb5e191f0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0xb5e191f0: GCJ_GetValue return
GCJ PLUGIN: thread 0xb5e191f0: GCJ_SetWindow
Segmentation fault

---

### Post by nerdleturtle on 2010-10-25
Forgive my utter noobyness(:confused:) but maybe you should try with a different browser (ie Google Chromium). If the crash replicates, this issue may extend beyond your browser....  If it doesn't, at least you can isolate the issue.
 
Good Luck:)

---

### Post by jeff_ on 2010-10-26
I tried Google Chrome and I get the following error:
The following plugin has crashed: /usr/lib/classpath/libgcjwebplugin.so

---

### Post by tripmix on 2010-10-26
This happened to me too, usually while having another tab open running flash. I installed firefox 4.0 (beta) and the icedtea java package. Seem to work ok for me now.

---

