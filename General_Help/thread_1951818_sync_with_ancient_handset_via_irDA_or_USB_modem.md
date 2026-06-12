---
title: "sync with ancient handset via irDA or USB modem"
date: 2012-04-03
forum: General Help
---

### Post by dragonfly41 on 2012-04-03
I'm trying to get an antique Sony Ericsson mobile handset T68i to sync with Ubuntu 10.10.

I don't have a bluetooth dongle so I have two options:

[LIST]
[*]by infrared
[*]by USB-modem
[/LIST]
I have an old USB modem - Mobile Action MA-8910P which interfaces to the handset.

I've installed multisync via Synaptic Package Manager but the multisync GUI doesn't launch (although it did work once for some reason then stopped launching).

Accessories > Multisync

and I've tried sudo multisync
and I get this ..
> (multisync:4834): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but SIGCHLD action was set to SIG_IGN and ECHILD was received by waitpid(), so exit status can't be returned. This is a bug in the program calling g_spawn_sync(); either don't request the exit status, or don't set the SIGCHLD action.

plugin_API_version
short_name
long_name
plugin_init
Segmentation fault
So two questions:-


[LIST]
[*]how to setup infrared connection to the handset (which has irDA enabled)
[*]how to setup multisync connection to the handset (which needs a modem driver)
[/LIST]
...

I've found this old thread on compiling the MA-8910P driver which I might try.

[http://figvam.blogspot.co.uk/2007/01/mobile-action-8730p-usb-cable-and-linux.html](http://figvam.blogspot.co.uk/2007/01/mobile-action-8730p-usb-cable-and-linux.html)

This is on a Dell Inspiron 1720 laptop.


[EDIT]

Apparently the Dell Inspiron 1720 doesn't have irDA so I have to rely on USB modem option.  

But I'm still interested in how to setup irDA on another (Aspire) laptop.

I've found this howto

[https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto)

---

