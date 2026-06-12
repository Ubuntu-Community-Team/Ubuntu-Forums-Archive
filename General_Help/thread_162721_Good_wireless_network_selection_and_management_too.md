---
title: "Good wireless network selection and management tool?"
date: 2006-04-19
forum: General Help
---

### Post by apsalyers on 2006-04-19
Not to invoke the unholy name of Microsoft, but is there a wireless network management tool for Linux similar to the one in Windows?  Simply a tool which displays all available wireless networks within range and allows the user to select?

---

### Post by joelito on 2006-04-19
I use gtkwifi. It's in the forums ([http://www.ubuntuforums.org/showthread.php?t=18466](http://www.ubuntuforums.org/showthread.php?t=18466)) 

Note that for all I know it only works with Gnome.

---

### Post by elamericano on 2006-04-19
[QUOTE=apsalyers]Not to invoke the unholy name of Microsoft, but is there a wireless network management tool for Linux similar to the one in Windows?  Simply a tool which displays all available wireless networks within range and allows the user to select?[/QUOTE]

Unholy is right. I liked the Windows Zero Config tool well enough when it was a hotfix to SP1, but now it is an atrocious, oversized, network selector, and if you go around it to advanced settings, you don't get the ssid list anymore.

Anyway, some people have been able to compile newer versions of NetworkManager to have WPA support, but it hasn't worked out for me. I'll try again when I move to Dapper.

You're using encryption, right?

---

### Post by threethirty on 2006-04-19
i tried to run that prog from the commandline and got this
```
three@raptor:~$ gtkwifi
WARNING: GTKWifi is not intended to be run directly from the command line.
Use 'gtkwifi run-in-window' to run GTKWifi in a window.

(:18453): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed

```
how do i go about running this

---

### Post by threethirty on 2006-04-19
nevermind i found it, but i cant figure out how to use it

---

