---
title: "No menus and &quot;working&quot; icon displayed indefinitely"
date: 2011-08-25
forum: General Help
---

### Post by tech242 on 2011-08-25
Hi,

I'm having some problems starting Gnome. Everything was working fine until I ran out of disk space on my system partition. Then all menus (top and bottom) disappeared. I freed up some disk space (back to the same 6GB it had free before) but menus did not return. I tried restarting but only thing that happens when Gnome starts is that my Wine programs that are set to autorun start. Nothing else happens, the mouse icon just keeps indicating that the system is working. No menus are displayed, and none of the usual keyboard commands (Alt-F1, Alt-F2) work. I have tried rebooting to failsafeX but the result is the same.

Anyone have any ideas what the problem might be and how I might resolve it? Running 11.04 BTW.

---

### Post by akoskm on 2011-08-25
If by freeing up some disk space you mean dropping files into the Trash, you have to empty it to actually get the free space.

---

### Post by fdrake on 2011-08-25
post the results:
```

df -ah
less ~/.xsession-errors
dmesg | less

```

---

### Post by tech242 on 2011-08-25
I used "rm -rf" to remove the files.

df -ah
```

Filsystem            Storlek Anvnt Tillg Anv% Monterat pÃ¥
/dev/sdg1              56G   46G  6,3G  88% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
fusectl                  0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  3,9G  768K  3,9G   1% /dev
none                     0     0     0   -  /dev/pts
none                  4,0G  1,1M  4,0G   1% /dev/shm
none                  4,0G  500K  4,0G   1% /var/run
none                  4,0G     0  4,0G   0% /var/lock
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
nfsd                     0     0     0   -  /proc/fs/nfsd
none                  0,0K  0,0K  0,0K   -  /proc/fs/vmblock/mountPoint 
```

less ~/.xsession-errors
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=sv_SE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-CU0jHw
GNOME_KEYRING_PID=3335
GNOME_KEYRING_CONTROL=/tmp/keyring-CU0jHw
SSH_AUTH_SOCK=/tmp/keyring-CU0jHw/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-CU0jHw
SSH_AUTH_SOCK=/tmp/keyring-CU0jHw/ssh
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
gnome-session[3281]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (Filen eller katalogen finns inte)
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x548024
** (nm-applet:3367): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3367): DEBUG: foo_client_state_changed_cb
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/jonas/.compiz/session/102c181d321837cd20131426281128704800000032810037"
Initializing session options...done
Starting unity-window-decorator
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a068,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a088,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a0a8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a0c8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a0e8,): stub
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fe00, (null), (null), 0x100a108,): stub
fixme:win:RegisterDeviceNotificationW (hwnd=0x12cd98, filter=0x54e93c,flags=0x00000001) returns a fake device notification handle!
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

** (process:3365): WARNING **: recent-manager-provider.vala:125: Desktop file for vmplayer was not found
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} not registered
err:ole:create_server class {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} not registered
err:ole:CoGetClassObject no class object {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} could be created for context 0x5
fixme:systray:wine_notify_icon unhandled tray message: 4
fixme:dwmapi:DwmIsCompositionEnabled 0x32fa20
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x41d041d, 0000: semi-stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x41d041d, 0000: semi-stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x41d041d, 0000: semi-stub! 

```

dmesg | less
[http://pastebin.com/AD8bGaY5]("http://pastebin.com/AD8bGaY5")

---

### Post by fdrake on 2011-08-25
did you try to free your tmp folder?

```


sudo rm -r /tmp/*
```
reboot

---

### Post by tech242 on 2011-08-25
> **fdrake said:**
> did you try to free your tmp folder?

```


sudo rm -r /tmp/*
```
reboot

Just tried it, doesn't seem to change anything...

---

