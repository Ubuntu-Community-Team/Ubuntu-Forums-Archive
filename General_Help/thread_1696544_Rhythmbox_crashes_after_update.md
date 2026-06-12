---
title: "Rhythmbox crashes after update"
date: 2011-02-27
forum: General Help
---

### Post by Leed on 2011-02-27
I've been using Rhythmbox for a long time without problems. 

Came back from holiday last week, used it again, no problem. Later installed the standard ubuntu updates.

Now when I start Rhythmbox it closes again after a few seconds. In the Terminal I get :

```

(rhythmbox:2156): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
Segmentation fault


```

It's very annoying, as I really want the program to run.... does this error make any sense to anybody?

---

### Post by Leed on 2011-02-28
Am I the only one experiencing this problem?

---

### Post by Leed on 2011-02-28
What I've noticed so far is, that when clicking on Last.fm it immediately crashes. But disabling last.fm doesn't solve the problem... it still crashes after a few seconds of usage

--Edit
Banshee also crashes on load.


It seems the Problem is with last.fm. 
In case anyone else is interested. I managed to keep Rhythmbox alive by closing the last.fm and the "Contex Pain" Plugins. Works ok for now.

---

### Post by FabianN on 2011-03-02
I have the exact same issue.

Finally got Rhythmbox working by disabling the Last.fm plugin, banshee is still crashing.

Once other thing I noted is that running as root will not have any issues. The last.fm plugin functions just fine under Rhythmbox and Banshee will run without any issues.

---

### Post by alexis44 on 2011-03-03
I'm having a problem with crashes, too.  I was looking for a program that might play various radio stations, and I found it with this program.  i was able to find the Internet Radio Browser plug-in and started using the program.  I may listen to it for about 20 or 30 minutes, and it crashes.  Could there be a conflict with another program? 

In my Log File, I received this message last:

rhythmbox[7205]: segfault at 0 ip 0086c8b9 sp bff91130 error 4 in librhythmbox-core.so.1.1.0[815000+12b000]

---

### Post by Leed on 2011-03-03
Altho not impossible, I doubt that it is the same issue. 20 minutes is a long time compared with the 10-20 seconds Rhythmbox gives me. 

I assume they changed something on the last.fm Site and Rhythmbox ist still trying to get information about the Band, Singer or whatever on the site, but it's not finding what was expected to be found. So Rhythmbox/Banshee just closes with an error, perhaps even as protection to prevent something unexpected to happen.

---

### Post by martinwebster on 2011-03-18
I use Banshee 1.8 and it recently started crashing as soon as play starts. I thought I'd give Rhythmbox a go and that crashes as soon as I try to add my password to the last.fm plugin. Without last.fm it seems to play fine.

I returned to Banshee, pressed <Ctrl>+U to disable scrobbling and it plays. No crashes. Press <Ctrl>+U again and a crash occurs within a few seconds. Related or a coincidence?

Rhythmbox:

```
$ rhythmbox

(rhythmbox:17403): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::row-ending-details' of type `gboolean' from rc file value "((GString*) 0x9f7ca20)" of type `GString'

** (rhythmbox:17403): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Mint-X-Metal/gtk-2.0/Rhythmbox/Treeview/row-middle.png,
borders don't fit within the image
Segmentation fault

```

Banshee:

```
$ banshee
[Info  19:32:39.505] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  19:32:41.194] Updating web proxy from GConf
[Info  19:32:41.258] All services are started 1.553383
[Info  19:32:42.632] nereid Client Started
[Info  19:32:42.874] AppleDeviceSource is ignoring unmounted volume Windows 7
[Warn  19:32:42.886] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Info  19:32:43.006] AppleDeviceSource is ignoring unmounted volume Data
[Warn  19:32:43.006] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Info  19:32:45.511] Uncached artwork size 175 requested
[Info  19:32:45.523] Uncached artwork size 37 requested
[Info  19:35:56.139] Uncached artwork size 175 requested
[Info  19:35:56.145] Uncached artwork size 37 requested
Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <0x00038>
  at System.Net.ServicePoint.get_HostEntry () <0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <0x0010b>
  at System.Net.WebConnection.InitConnection (object) <0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0x00046>

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xc6740c]
	/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xa986d61f]
	/lib/libc.so.6(gethostbyname2_r+0x1c5) [0x4161a5]
	/lib/libc.so.6(+0xa782c) [0x3d582c]
	/lib/libc.so.6(getaddrinfo+0x165) [0x3d73b5]
	banshee-1() [0x8158c93]
	[0x416bfa3]
	[0x416bec1]
	[0x416bce0]
	[0x416b71c]
	[0x416b3e2]
	[0x2300bf]
	banshee-1() [0x8061328]
	banshee-1(mono_runtime_invoke+0x40) [0x813c890]
	banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
	banshee-1() [0x814266e]
	banshee-1() [0x81d2341]
	banshee-1() [0x81d2858]
	banshee-1() [0x81b11db]
	banshee-1() [0x81e8e4e]
	banshee-1() [0x8214f85]
	/lib/libpthread.so.0(+0x5cc9) [0xdbccc9]
	/lib/libc.so.6(clone+0x5e) [0x3fe69e]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

These messages made me think about problems with Samba and Rhythmbox. Consequently, I removed winbind and the problems were resolved:

```
$ sudo apt-get remove winbind
```

---

### Post by DuckHook on 2011-03-19
Good detective work. Removing <winbind> solves the problem for me too. Have you reported this as a bug?:)

---

### Post by martinwebster on 2011-03-19
> **DuckHook said:**
> Good detective work. Removing <winbind> solves the problem for me too. Have you reported this as a bug?:)

I have raised two bugs; one each for Banshee and Rhythmbox.

Rhythmbox: [#738140]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/738140")

Banshee: [#738142]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/738142")

---

### Post by Leed on 2011-03-29
Cool, I just had the problem apear again, this time crashing faster than before, not leaving me enough time to resolve it. 

Then I tried removing winbind, and it worked, giving me a message, that it couldn't read the Audio CD in my drive.

Reinstalled winbind and took the CD out, works fine....

I guess the Plugin that should get info's on CD (probably from Amazone or FreeDB) is not that good anymore.

---

### Post by dschaller on 2011-04-13
For me Rhythmbox segfaults immediately on startup when trying to load an Audio CD and winbind is installed. When winbind is removed, everything okay.

---

