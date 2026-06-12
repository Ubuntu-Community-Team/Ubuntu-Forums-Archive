---
title: "4 media players crushing on startup (bus error)"
date: 2011-09-27
forum: General Help
---

### Post by geo909 on 2011-09-27
Dear all,

I'm having a weird problem on my lubuntu 11.04 desktop: when 
I'm trying to run any of my 4 media players, they crush. Only
banshee shows a grey window for a while, all the others don't
even start.. Here's what I get from the command line for:


1.Rhythmbox:
```

jorge@Office-Desktop:~$ rhythmbox
Bus error
jorge@Office-Desktop:~$ 

```

2.Exaile:
```

jorge@Office-Desktop:~$ exaile 
INFO    : Loading Exaile 0.3.2.1...
INFO    : Loading settings...
WARNING : Failed to import gtk.glade, interface will not be fully translated.
Bus error
jorge@Office-Desktop:~$ 

```

3.Banshee:
```

jorge@Office-Desktop:~$ banshee 
[Info  15:26:58.241] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
Stacktrace:

  at (wrapper managed-to-native) Banshee.GStreamer.Service.gstreamer_initialize (bool,Banshee.GStreamer.Service/BansheeLogHandler) <0x00004>
  at (wrapper managed-to-native) Banshee.GStreamer.Service.gstreamer_initialize (bool,Banshee.GStreamer.Service/BansheeLogHandler) <0x00004>
  at Banshee.GStreamer.Service.Banshee.ServiceStack.IExtensionService.Initialize () <0x00050>
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode) <0x00107>
  at Banshee.ServiceStack.ServiceManager.Run () <0x0017c>
  at Banshee.ServiceStack.Application.Run () <0x00046>
  at Banshee.Gui.GtkBaseClient.Initialize (bool) <0x0027e>
  at Banshee.Gui.GtkBaseClient..ctor (bool,string) <0x00023>
  at Banshee.Gui.GtkBaseClient..ctor () <0x00017>
  at Nereid.Client..ctor () <0x00010>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this__ (object,intptr,intptr,intptr) <0x00040>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at System.Reflection.MonoCMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0018b>
  at System.Reflection.MonoCMethod.Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x00027>
  at System.Reflection.ConstructorInfo.Invoke (object[]) <0x00042>
  at System.Activator.CreateInstance (System.Type,bool) <0x00184>
  at System.Activator.CreateInstance (System.Type) <0x00012>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00015>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x00089>
  at Banshee.Gui.GtkBaseClient.Startup<object> () <0x0005c>
  at Banshee.Gui.GtkBaseClient.Startup<object> (string[]) <0x000d8>
  at Nereid.Client.Main (string[]) <0x00015>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0x00043>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x0002e>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00067>
  at System.AppDomain.ExecuteAssembly (string) <0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0x00057>
  at Booter.Booter.BootClient (string) <0x00069>
  at Booter.Booter.Main () <0x001a0>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>

Native stacktrace:

	banshee() [0x80dbc5b]
	banshee() [0x81136eb]
	[0x89240c]
	/usr/lib/libgstreamer-0.10.so.0(gst_registry_binary_read_cache+0x5ad) [0x4ad1f8d]
	/usr/lib/libgstreamer-0.10.so.0(gst_update_registry+0x199) [0x4aa84b9]
	/usr/lib/libgstreamer-0.10.so.0(+0x19e74) [0x4a53e74]
	/lib/i386-linux-gnu/libglib-2.0.so.0(g_option_context_parse+0x3c8) [0x3204f8]
	/usr/lib/libgstreamer-0.10.so.0(gst_init_check+0xe6) [0x4a549b6]
	/usr/lib/libgstreamer-0.10.so.0(gst_init+0x32) [0x4a54ab2]
	/usr/lib/banshee/libbanshee.so(gstreamer_initialize+0x42) [0x380e1b2]
	[0x8af2e09]
	[0x8af2d41]
	[0x8af2a90]
	[0xe95475]
	[0xe9211f]
	[0x546cb7]
	[0x5469ac]
	[0x546970]
	[0x546941]
	[0x4c7329]
	banshee() [0x8062bc8]
	banshee(mono_runtime_invoke+0x3e) [0x8192eee]
	banshee(mono_runtime_invoke_array+0x5c8) [0x8196ac8]
	banshee() [0x814a098]
	[0x4c7250]
	[0x4c6e8c]
	[0x4c6cf8]
	[0x4c6cb3]
	[0x4c59bd]
	[0x4c5823]
	[0x5468ee]
	[0x5467ba]
	[0x5466ed]
	[0x4d3269]
	[0x4d30e6]
	[0x4d313c]
	banshee() [0x8062bc8]
	banshee(mono_runtime_invoke+0x3e) [0x8192eee]
	banshee(mono_runtime_exec_main+0xe0) [0x81959e0]
	[0x4d3077]
	[0x4d2f37]
	[0x4d2e06]
	[0x4d2db0]
	[0x4d2d32]
	[0x4d2ce8]
	[0x4d2aea]
	[0x4b9351]
	[0x4b944b]
	banshee() [0x8062bc8]
	banshee(mono_runtime_invoke+0x3e) [0x8192eee]
	banshee(mono_runtime_exec_main+0xe0) [0x81959e0]
	banshee(mono_runtime_run_main+0x11d) [0x8195ced]
	banshee(mono_main+0x1676) [0x80b7706]
	banshee() [0x8059355]
	/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0xc7de37]
	banshee() [0x8059291]

Debug info from gdb:


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
jorge@Office-Desktop:~$ 

```

4.Clementine:
```

^Tjorge@Office-Desktop:~$ clementine 
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - gnome settings daemon not registered 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Couldn't load icon "find" 
Application asked to unregister timer 0x1f00000a which is not registered in this thread. Fix application.
Bus error
jorge@Office-Desktop:~$ 

```

Please, any ideas about that? Seems that there is some "bus error".. Would that suggest that there's a hardware issue? 

Many thanks in advance for your time..

---

### Post by TeoBigusGeekus on 2011-09-27
Patrioti, does it also happen with serious media players (vlc, mplayer)?

---

### Post by geo909 on 2011-09-27
> **TeoBigusGeekus said:**
> Patrioti, does it also happen with serious media players (vlc, mplayer)?

Hey Kopeli,

No, serious media players incl. mplayer, vlc are fine.. Audacious
also works. But I'd rather stick with something more bloated for
my big shinny music collection.. And anyway, there is something 
fishy here.. *Four* applications won't even open!

---

### Post by TeoBigusGeekus on 2011-09-27
Just a thought: reinstallation/reconfiguration of mono?

---

### Post by geo909 on 2011-09-27
> **TeoBigusGeekus said:**
> Just a thought: reinstallation/reconfiguration of mono?

So, what package in particular? 

However (and I'm not sure if I'm missing something)
I'm pretty sure that for instance Exaile and clementine 
(my two preferred applications) do not use mono.. And 
all their error messages say something about this bus..

[CENTER][IMG]http://www.theinjurylawyers.co.uk/injury-lawyers-blog/wp-content/uploads/2008/07/bus-crash1.jpg[/IMG]
There really must be a bus error..
[/CENTER]

---

### Post by geo909 on 2011-09-28
bump

---

### Post by SeijiSensei on 2011-09-28
Does lubuntu use [dbus]("http://www.freedesktop.org/wiki/Software/dbus") like GNOME and KDE do?  I've not used LXDE as a desktop environment, but I wouldn't be surprised to learn that a "lightweight" DE doesn't use dbus.

---

### Post by geo909 on 2011-09-28
> **SeijiSensei said:**
> Does lubuntu use [dbus]("http://www.freedesktop.org/wiki/Software/dbus") like GNOME and KDE do?  I've not used LXDE as a desktop environment, but I wouldn't be surprised to learn that a "lightweight" DE doesn't use dbus.

No, I really don't think that is the case; the dbus package
is installed anyway..

The funny thing (which I just realized) is that all of them
start properly if I run them as root (except exaile which
says that "running as root is not supported" ?!?!).

So it seems that there's something with permissions..

---

### Post by geo909 on 2011-09-28
> **SeijiSensei said:**
> Does lubuntu use [dbus]("http://www.freedesktop.org/wiki/Software/dbus") like GNOME and KDE do?  I've not used LXDE as a desktop environment, but I wouldn't be surprised to learn that a "lightweight" DE doesn't use dbus.

How can I check if dbus runs properly, actually?

---

### Post by SeijiSensei on 2011-09-29
If I run "ps ax | grep dbus" I get half a dozen entries, but the most important one I suspect is the one with the lowest pid:

```
 1142 ?        Ss     0:00 dbus-daemon --system --fork
```

That's the initial instance of the daemon from startup.

---

### Post by geo909 on 2011-09-29
> **SeijiSensei said:**
> If I run "ps ax | grep dbus" I get half a dozen entries, but the most important one I suspect is the one with the lowest pid:

```
 1142 ?        Ss     0:00 dbus-daemon --system --fork
```

That's the initial instance of the daemon from startup.

I get this:

```

jorge@Office-Desktop:~$ ps ax | grep dbus
  632 ?        Ss     0:00 dbus-daemon --system --fork --activation=upstart
  971 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startlubuntu
  974 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startlubuntu
  975 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 1890 pts/0    S+     0:00 grep --color=auto dbus


```

So, what does that mean? I don't really understand much..

Thanks!

---

### Post by geo909 on 2011-10-02
Now I have the same problem with other applications as well!
For instance gpodder:

```
jorge@Office-Desktop:~$ gpodder
Bus error
jorge@Office-Desktop:~$ 

```

..but again "sudo gpodder" will fire up the application..

Please, *any* help?! After extensive google search and 
asking in forums, I've yet to find the solution.. I'm so busy 
at the moment and it seems that I either have to solve this 
or do a format, which I'd really like to avoid.. Any help 
would be greatly appreciated..

---

### Post by TeoBigusGeekus on 2011-10-02
Could it be a permissions problem?
It's a desperate measure, but try
```
sudo chown -R yourusername: /home/yourusername
```

---

### Post by geo909 on 2011-10-02
> **TeoBigusGeekus said:**
> Could it be a permissions problem?
It's a desperate measure, but try
```
sudo chown -R yourusername: /home/yourusername
```

Thanks, but I don't think so.. I'm the owner of everything
under $HOME.. I did that and didn't change anything..

Any other ideas?

---

### Post by geo909 on 2011-10-02
I sort of solved the problem: I created another user
and logged in again as this user.. Everything worked
perfectly..

So, I'll just change the user, it seems that this is 
a better and faster way instead of dealing with the 
bus error..

Thanks to TeoBigusGeekus and the others who spent 
time on this!

---

### Post by TeoBigusGeekus on 2011-10-02
It was something in your home folder that was causing this.
Another approach would be to backup your home folder and start deleting files and folders one by one. A painful procedure (I had to do it once and I know) but it would help pinpoint the culprit...

---

