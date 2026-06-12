---
title: "Tomboy WebDAV sync error"
date: 2010-05-02
forum: General Help
---

### Post by dadrc on 2010-05-02
Since the 10.04 update, both my Ubuntu and Xubuntu box won't sync my tomboy notes using WebDAV (worked fine with 9.10). The error is as follows:

```
[WARN 21:55:11.384] Getting configuration from the GNOME keyring failed with the following message: The keyring daemon is not available
[WARN 21:55:27.977] Saving configuration to the GNOME keyring failed with the following message: The keyring daemon is not available
```Checked my running processes, I found a running keyring daemon:

```
drc@pepper:~$ ps aux | grep keyring
drc       1839  0.0  0.1  69640  2720 ?        Sl   21:14   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
```Did some googling, apparently some other folks had similar issues they fixed by running the following:

```
eval `gnome-keyring-daemon` && export GNOME_KEYRING_SOCKET  && export GNOME_KEYRING_PID && tomboy &#8211;search
``` Tried that, got the same error message. Reinstalled tomboy and gnome-keyring, no effect.

Anyone with a clue as to what might be wrong here?

tomboy 1.2.1-0ubuntu1
gnome-keyring 2.92.92.is.2.30.0-0ubuntu3

---

### Post by shrodi on 2010-05-03
Exact same problem here. I rely much on that Tomboy feature, so this is a major drawback for me. I hate it when things stop working after an upgrade! :(

---

### Post by dadrc on 2010-05-04
Came up with the idea of this issue being apparmor-related, but found no tomboy or gnome-keyring profile, so that probably isn't the case.

Anything else I could check?

---

### Post by dadrc on 2010-05-05
Today gnome-keyring 2.92.92.is.2.30.1-0ubuntu1 was pushed to proposed, unfortunately it didn't fix the problem for me. Did it for you, shordi?

---

### Post by shrodi on 2010-05-12
No... I've filled a bug here, but so far it didn't attract much interest: [https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061)

---

### Post by dadrc on 2010-05-12
Marked it as affecting me, too.

---

### Post by neoblitz on 2010-05-12
Affects me too. Its quite frustrating since I depend heavily on Tomboy. Is this only a Ubuntu specific issue? Or affecting other distros too?

---

### Post by dadrc on 2010-05-12
Did some digging a week ago, seems to affect Ubuntu only. Feel free to prove me wrong, though. But this only happening since I upgraded to 10.04 would suggest it's a 10.04 bug.

---

### Post by cacheuk on 2010-05-29
it seems that TomBoy looks in the ENV for 'GNOME_KEYRING_SOCKET'

```
tomboy-1.2.0/Tomboy/Gnome.Keyring/Ring.cs:89:
filename = Environment.GetEnvironmentVariable ("GNOME_KEYRING_SOCKET");
```

which doesn't seem to be set in Ubuntu 10.x (or Mint 9)

gnome-keyring-daemon does not appear to output them any more either:

```
~ $ gnome-keyring-daemon 
GNOME_KEYRING_CONTROL=/tmp/keyring-OWkYIp
SSH_AUTH_SOCK=/tmp/keyring-OWkYIp/ssh
GNOME_KEYRING_PID=9981
```

on Unbuntu 9 (and Mint 8 ):
```
~ $ gnome-keyring-daemon 
GNOME_KEYRING_SOCKET=/tmp/keyring-xMzdEc/socket
SSH_AUTH_SOCK=/tmp/keyring-xMzdEc/socket.ssh
GNOME_KEYRING_PID=7925
```

there is a socket at: $GNOME_KEYRING_CONTROL/socket

exporting it as

```
export GNOME_KEYRING_SOCKET=$GNOME_KEYRING_CONTROL/control
```

 and running TomBoy again causes it to crash with 'Connection reset by peer' when editing the preferences and selecting WebDav:


```
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Net.Sockets.SocketException: Connection reset by peer
  at System.Net.Sockets.Socket.Receive (System.Byte[] buf) [0x00000] 
  at Gnome.Keyring.Ring.GetInt32 (System.Net.Sockets.Socket sock) [0x00000] 
  at Gnome.Keyring.Ring.SendRequest (System.IO.MemoryStream stream) [0x00000] 
  at Gnome.Keyring.Ring.Find (ItemType type, System.Collections.Hashtable atts) [0x00000] 
  at Tomboy.Sync.WebDavSyncServiceAddin.GetConfigSettings (System.String& url, System.String& username, System.String& password) [0x00000] 
  at Tomboy.Sync.WebDavSyncServiceAddin.CreatePreferencesControl () [0x00000] 
  at Tomboy.PreferencesDialog.OnSyncAddinComboChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tomboy.GnomeApplication.StartMainLoop()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)
```

---

### Post by dadrc on 2010-05-30
The crash is reproducable, but at least here there is no socket in /tmp/keyring-<something>/:
```
drc@pepper:/tmp/keyring-cr0XwJ$ ls
control  pkcs11  ssh
```Guess that's why Tomboy crashes.

Found the following bug filed for libgnome-keyring1.0-cli: [launchpad bug 536925]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring-sharp/+bug/536925") . Seems to describe exactly the problem we are having. Bad news: version 1.0.0-2 was supposed to fix that, but apparently didn't.```

Package: libgnome-keyring1.0-cil
Version: 1.0.0-3
```

---

### Post by Hichhiker on 2010-10-14
So, its been 5 months, several versions of all the involved software and a new version of Ubuntu - and still exactly the same problem. 

Has anyone figured this out, or did people just move on to another product? (and if so, what product?)

Thanks.

-HH

---

### Post by dietervh on 2010-11-15
Just explored Tomboy and was very satisfied until I wanted to try and use it. 

I've got the same problem as Hichhiker
Hope it will be fixed asap.

---

### Post by Hichhiker on 2010-11-15
> **dietervh said:**
> Just explored Tomboy and was very satisfied until I wanted to try and use it. 

I've got the same problem as Hichhiker
Hope it will be fixed asap.

For what its worth, I started using Tomboy with UbuntuOne for sync - its not what I wanted, but it is the only sync for Tomboy that works, and it even works with Tomdroid client for Android - which comes in handy. 

-HH

---

