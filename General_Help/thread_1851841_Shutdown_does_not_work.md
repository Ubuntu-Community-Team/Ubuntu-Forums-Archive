---
title: "Shutdown does not work"
date: 2011-09-29
forum: General Help
---

### Post by zashuna on 2011-09-29
Hi,

I am running xubuntu 11.04 amd64 on my netbook. Recently, I don't know why, whenever I click the shutdown or restart button from the panel, I get a window asking me whether I want to shutdown/reboot and when I click yes, nothing happens. Every time, I'm forced to power off from the terminal. I've read at least other instance of this problem. If anyone has any ideas, it would be greatly appreciated. Thanks!

---

### Post by raja.genupula on 2011-09-29
Hi i can provide you a alternative solution 
sudo shutdown -h 0

this is the command for shutdown your system . use this as temporary solution upto some one gonna help you to fix this.

---

### Post by Toz on 2011-09-29
Which groups do you belong to?
```
groups
```

What happens when you try to shutdown using these methods:
```
xfce4-session-logout -h
```
```
dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Does it work? Any error messages?

Also, look in ~/.xsession-errors for error messages when you try to shutdown by clicking the shutdown button.

---

### Post by zashuna on 2011-09-29
Hi, thanks for your help. When I type "quote", I get:

```
shunan adm dialout cdrom plugdev lpadmin admin sambashare
```

When I type:

```
xfce4-session-logout -h
```

Nothing happens. If I try typing it again, I get a window saying: "Session manager must be in idle state when requesting a shutdown"

However, "xfce4-session-logout -h" does work and it does shutdown the computer. The last few lines of my .xsession-errors file are:

```
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1973):invoke_NPP_GetValue: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```

---

### Post by zashuna on 2011-09-30
bump :(

---

### Post by Toz on 2011-09-30
Are you fully updated? 

Can you post back the results of running this command?
```
ps -ef | grep xfce | tr -s ' ' | cut -d' ' -f8
```
...and
```
ps -ef | grep xcfe4-session | grep -v grep
```

Do you have anything in your ~/.xinitrc file?

And if possible, post back the entire contents of your .xsession-errors file after a failed shutdown attempt.

I'm thinking there is something wrong with the xfce4-session on your computer.

---

