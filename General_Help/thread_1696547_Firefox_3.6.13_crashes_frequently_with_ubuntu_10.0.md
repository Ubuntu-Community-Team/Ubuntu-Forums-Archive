---
title: "Firefox 3.6.13 crashes frequently with ubuntu 10.04 64bit"
date: 2011-02-27
forum: General Help
---

### Post by davidbowie on 2011-02-27
```
(npviewer.bin:4348): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))

(npviewer.bin:4348): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPObject 0x7f98c07fa390 is no longer valid!

```New profile doesn't help and neither does safemode. I am thinking about trying a fresh install. Sometimes the whole gui freezes. Any help greatly appreciated!

---

### Post by Vaphell on 2011-02-27
i guess you use 32 bit flash, consider trying 64bit version
this addon makes it easy to sort things out and automates the task
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by davidbowie on 2011-02-27
Thanks! I will try it and update the thread. I knew there was a flash conflict with 64bit but i didn't know there was this add-on.

---

### Post by davidbowie on 2011-02-27
Well it crashed once so far. I am still getting a bunch of this crap
```
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2076): Gdk-WARNING **: XID collision, trouble ahead

```

---

### Post by davidbowie on 2011-02-28
well i updated to 2.6.32-28 and in safemode, firefox spits out hundreds of the errors above and after restart i got something new in safemode.
```
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 306 error_code 9 request_code 138 minor_code 26)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection closed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```I am thinking i need to re-install firefox.. Any thoughts?

---

### Post by davidbowie on 2011-02-28
Is there a program or add-on like [PeerBlock]("http://www.peerblock.com/") that i can use for Ubuntu? I think blocking all website adds and various flash adds will minimize the problem greatly.

---

### Post by Vaphell on 2011-02-28
so have you changed to 64 bit or not? what does the about:****plugins (type that in address bar) page say about flash version? because i think npviewer.bin is related to 32to64 wrapper which shouldn't take place in case of native 64bit plugin.

addons you can use to minimize problems:
adblock plus (must have, blocks all kinds of unnecessary crap), noscript (allows blocking scripts and other stuff, powerful but may appear annoying), flashblock (easy to figure out what that is)
also try alternative browsers like chromium or opera

do these error messages indicate the exact source of problems? do they mention any file/path (other than npviewer.bin that is)?

---

### Post by frotzed on 2011-02-28
Also, consider simply trying to reinstall flash via a different method [like this](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html).

---

### Post by davidbowie on 2011-02-28
> **Vaphell said:**
> so have you changed to 64 bit or not? what does the about:plugins (type that in address bar) page say about flash version?

Well it showed flash at the bottom and it was 10.2 iirc. After i did what frotzed suggested, flash doesn't even show up in the about:plugins.
> 
addons you can use to minimize problems:
adblock plus (must have, blocks all kinds of unnecessary crap), noscript (allows blocking scripts and other stuff, powerful but may appear annoying), flashblock (easy to figure out what that is)
also try alternative browsers like chromium or operaThanks!

> do these error messages indicate the exact source of problems? do they mention any file/path (other than npviewer.bin that is)?Not that i am aware of. I just c/p what terminal put out.

---

### Post by Vaphell on 2011-03-01
my firefox with 64bit flash installed via flash-aid addon shows:
```
File: /usr/lib/mozilla/plugins/libflashplayer.so
Version: 
Shockwave Flash 10.3 d162
```

---

### Post by davidbowie on 2011-03-05
> **frotzed said:**
> Also, consider simply trying to reinstall flash via a different method [like this]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html").

Well i did this as per "kpox January 18, 2010" post because previous posts had broken links. I already had the 'getlibs' packages so it didn't work. "nubo" posts looked promising because it sidestepped the wrapper all together, but i didn't quite have the brass ones to try.

My about plugins looks like this > File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.2 r152   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl YesI have the flash-aid and ABP add-on's and i am still getting erroneous lines of code such as this
```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```Thanks so far for all the input!:KS

Edit: I updated to FF 3.6.14 and kernel 2.6.32-29

---

### Post by davidbowie on 2011-03-05
I restarted my comp and now i get "Shockwave Flash 10.3 d162" in about plugins :confused:

I am getting a new(er) error ```
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64

```

Yay progress.....

---

### Post by skag on 2011-03-05
[http://ubuntuforums.org/showthread.php?p=10524668](http://ubuntuforums.org/showthread.php?p=10524668)  try what the last guy says... worked for me :)

---

### Post by davidbowie on 2011-03-06
Thx skag i'll check it out.

more code... FF hasn't crashed in a while but now flash videos crash and have artifacts.
```
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64

(<unknown>:2351): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:2351): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


```

---

### Post by jcolyn on 2011-03-06
Try upgrading Firefox to 3.6.14

3.6.15 should be available this week then go to synaptic and type flash in the search box. Check to make sure flashplugin-installer is the only flash that is installed

---

### Post by davidbowie on 2011-03-06
> I updated to FF 3.6.14 and kernel 2.6.32-29I think for the most part this thread is solved. Thanks everyone!

My browser isn't crashing so I am happy. I can live with buggy videos.

---

### Post by davidbowie on 2011-03-08
well i was too quick to solve it.. It crashed with the same code from post #14

---

