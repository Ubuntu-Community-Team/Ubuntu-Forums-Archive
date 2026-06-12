---
title: "firefox crash: Gdk-WARNING **: XID collision"
date: 2010-01-26
forum: General Help
---

### Post by okhowaboutthisusername on 2010-01-26
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.1pre) Gecko/20100126 Ubuntu/9.10 (karmic) Namoroka/3.6.1pre

Firefox has been consistently crashing this evening, usually quite soon after launch.

```
$ firefox

(firefox-bin:5225): GLib-WARNING **: g_set_prgname() called multiple times
LoadPlugin: failed to initialize shared library /home/bally/.mozilla/plugins/nppdf.so [/home/bally/.mozilla/plugins/nppdf.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:5281): Gdk-WARNING **: XID collision, trouble ahead
Segmentation fault
```

Apparently, npviewer has something to do with Flash. Noting the warnings up top, I figured I should either update or remove it. The former did not work (I'll save that for another thread). Can anyone explain how to properly remove the damned thing? I tried moving the plugins manually and restarting FF but that led to:

```
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libflashplayer.so: cannot open shared object file: No such file or directory
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libflashplayer.so: cannot open shared object file: No such file or directory
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:3156):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
```

---

### Post by michael37 on 2010-01-26
[thread="1358591"]64-bit Flash for 64-bit Firefox[/thread]

---

### Post by okhowaboutthisusername on 2010-01-27
Thank you very much.

---

