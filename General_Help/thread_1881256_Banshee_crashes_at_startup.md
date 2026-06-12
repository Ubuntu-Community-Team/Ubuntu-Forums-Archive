---
title: "Banshee crashes at startup"
date: 2011-11-15
forum: General Help
---

### Post by elias3 on 2011-11-15
I've installed a fresh version of Ubuntu 11.1, and whenever I launch Banshee it works 4 or 5 seconds then it crashes
Here is what i got from the terminal

```
[Info  04:39:39.774] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]
[Info  04:39:41.706] Updating web proxy from GConf
[Info  04:39:42.135] All services are started 1&#1643;930397
** (Banshee:2238): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:2238): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
[Info  04:39:43.357] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[Info  04:39:44.147] nereid Client Started
[Info  04:39:44.731] GStreamer version 0.10.35.0, gapless: True, replaygain: False
[Info  04:39:44.872] AppleDeviceSource is ignoring unmounted volume 42 GB Filesystem
[Info  04:39:44.968] AppleDeviceSource is ignoring unmounted volume 42 GB Filesystem

** (Banshee:2238): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 1041, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 640, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 781, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/elias/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:2238): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed
** (Banshee:2238): DEBUG: Loading the real store page

** (Banshee:2238): WARNING **: Got less number of items in credentials hash table than expected!

** (Banshee:2238): WARNING **: Error rescanning Purchased Music: No such file or directory

(Banshee:2238): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed
Marshaling url-loaded signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.UbuntuOneMusicStore.UbuntuOneMusicStoreSource.OnDefaultStoreUrlLoaded (System.Object o, UbuntuOne.UrlLoadedArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (System.Reflection.MonoMethod,object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

---

### Post by BillyBoa on 2011-11-15
It's a bug. Check here:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/883023](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/883023)

---

### Post by Docaltmed on 2011-11-15
In my case, it was the Live Radio extension causing the problem. I used the 5 seconds of time I had to disable the extension, and then it started up normally and worked fine.

---

### Post by elias3 on 2011-11-17
Thank you all for your help, I installed the proposed update and now 5, 10, 15 seconds... Yes it works now :p

---

