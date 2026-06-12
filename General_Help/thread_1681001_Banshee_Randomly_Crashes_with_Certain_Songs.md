---
title: "Banshee Randomly Crashes with Certain Songs"
date: 2011-02-03
forum: General Help
---

### Post by Joseph Schwenker on 2011-02-03
When I opened Banshee today and tried to play a certain song, the player crashed. When I opened the player again, it continued to crash for only the same songs. Here's the output:

```
[Info  11:19:22.275] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  11:19:22.620] Starting collection of anonymous usage data
[Info  11:19:23.353] Updating web proxy from GConf
[Info  11:19:23.397] All services are started 0.900266
[Warn  11:19:23.553] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
[Info  11:19:24.110] nereid Client Started
[Warn  11:19:24.252] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
Stacktrace:


Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xb789140c]

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

I temporarily fixed this by disabling all extensions, reenabling them, then restarting Banshee, but the problem came back a few minutes later.

---

### Post by Joseph Schwenker on 2011-02-03
This is the output of playing the same song, this time with all extensions disabled.

```
[Info  11:23:25.024] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  11:23:25.348] Starting collection of anonymous usage data
[Info  11:23:26.072] Updating web proxy from GConf
[Info  11:23:26.087] All services are started 0.873857
[Warn  11:23:26.229] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
[Info  11:23:26.656] nereid Client Started
[Warn  11:23:39.696] Caught an exception - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.Run () [0x00000] in <filename unknown>:0 


```

---

### Post by DarthScape on 2011-02-03
Might want to try the banshee ppa, because 1.8.1 is out and also some preview releases.

---

### Post by Joseph Schwenker on 2011-02-03
Thanks, though I got Banshee working again by only reenabling the extensions that I use. It must have been a certain extension causing the problem. Thanks for your advice, though.

---

