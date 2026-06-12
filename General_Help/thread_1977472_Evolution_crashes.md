---
title: "Evolution crashes"
date: 2012-05-10
forum: General Help
---

### Post by Jonners59 on 2012-05-10
OK, basics:
Running CPU: Intel(R) Core(TM) iS-2500K CPU @ 3.30Ghz and 15.7GB RAM
Dist is Ubuntu 12.04 x86_64 and Desktop is UNity with xfce4
Evolution is 3.2.3-Oubuntu6

I have been using Evolution for a couple of years now, and since 11.04 had issues with calendar and contacts.  Seemed to fix that yesterday, but what I have now found from last night is that Evolution will not stay open.

At first it would load in to the setup tool.  I would make a dummy account and once in delete it and all was fine, my old accounts and settings were there.

From this AM I get the setup tool, but then it just disappears.

Run from terminal, this is what I get.
```
   	 	 	 	 	 	   $ evolution
  (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
   (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
   (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version

 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
   (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version

 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): camel-imap-provider-WARNING **: Unkown summary version
 (evolution:9494): GLib-CRITICAL **: g_variant_new_string: assertion `g_utf8_validate (string, -1, NULL)' failed
   (evolution:9494): GLib-CRITICAL **: g_variant_new_string: assertion `g_utf8_validate (string, -1, NULL)' failed

 (evolution:9494): GLib-CRITICAL **: g_variant_new_string: assertion `g_utf8_validate (string, -1, NULL)' failed
  (evolution:9494): GLib-CRITICAL **: g_variant_new_string: assertion `g_utf8_validate (string, -1, NULL)' failed
  **
GLib-GIO:ERROR:/build/buildd/glib2.0-2.32.1/./gio/gdbusmessage.c:1979:append_value_to_blob: assertion failed: (g_utf8_validate (v, -1, &end) && (end == v + len))
 Aborted (core dumped)
```


I have tried uninstalling Evolution and re-installing, purging, full uninstall via synaptic...  Makes no odds.  It does the same each time.

ANy ideas, please?:popcorn::(

---

### Post by Jonners59 on 2012-05-11
OK, seem to have resolved the crashing.

I first ran these commands


```
evolution ~~force-shutdown
```
```
sudo apt-get purge evolution
```
```
dpkg -l|grep -i evolution
```
```
sudo apt-get autoremove
```

I then went in to Synaptic Package Manager and types in Evolution in to the search window
I then deleted anything with Evolution mentioned in it except - and this is important: 
evolution-data-server and evolution-data-server-common.  Deleting these would completly screw up the PC....

I then rebooted and then reinstalled Evolution via synaptic.

It started with the setup wizard, so I entered an account, when it opened all my old accounts and settings still existed.  This was partly good as it meant I had little to do but delete the temporary account I had created.  The down side is that the it **[COLOR=Black]had NOT purged the install and the old configs still exist[/COLOR]**.  I **still have an issue with a contacts** account.  I now need to find out how to delete it.....  New thread as this subject is now closed and solved.

---

