---
title: "Banshee crashes at launch"
date: 2011-05-04
forum: General Help
---

### Post by Paqman on 2011-05-04
See bug: [774830]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/774830")

Banshee crashes at launch for me with the following output:

```
[Info  11:17:13.556] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Info  11:17:14.902] Updating web proxy from GConf
[Info  11:17:14.948] All services are started 1.145192
** (Banshee:2091): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:2091): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
Marshaling download-finished signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> GLib.GException: Error creating directory: Permission denied
  at GLib.FileAdapter.MakeDirectoryWithParents (GLib.Cancellable cancellable) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Create (System.String directory) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Create (System.String directory) [0x00000] in <filename unknown>:0 
  at Banshee.Base.PathPattern.BuildFull (System.String base_dir, Banshee.Collection.TrackInfo track, System.String ext) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseTrackInfo.CopyToLibraryIfAppropriate (Boolean force_copy) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseImportManager.ImportTrack (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
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
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

Any ideas? I've already tried clearing out Banshee's config files in /home to no avail. I enabled apport to try and catch some output for the bug report, but it hasn't popped up.

---

### Post by Paqman on 2011-05-04
Hmm, odd. Seems like i've fixed it by:

[LIST=1]
[*]Unistalling banshee-extension-ubuntuonemusic store
[*]Launch Banshee. Banshee now works fine
[*]Reinstall banshee-extension-ubuntuonemusicstore
[*]Banshee now behaves itself
[/LIST]

So the problem was some dodginess on Ubuntu One's part (or at least its Banshee plugin). Hope this helps anyone else who strikes this.

---

### Post by myjr52 on 2011-05-05
Hi, Paqman. Thanks for your solution as I have had the exactly the same problem.

Your soluton worked for me if I uninstall "banshee-extension-ubuntuonemusicstore". But, then reinstall makes the exact same problem again.

One more thing, even if banshee won't crash after unstaill the extension, it still crashes if I select Amazon MP3 Store oe Miro Guide in the online media section.

---

### Post by Paqman on 2011-05-06
Try getting rid of your Banshee config in /home/username/.config/banshee. I was starting with a completely clean config and got it to load up ok once i'd removed the extension, then I could reinstall the extension and it worked.

If that doesn't work, file a bug at bugzilla, as you probably have a different problem from me.

---

### Post by exup1000 on 2011-05-09
Hi

I am getting a similar issue, crash on open and I suspect it is the Ubuntu One extension.

I have disabled it but it make no difference.
I uninstalled Banshee and reinstalled with bare minimum extenstions
I deleted the config folder for banshee.
Run it with sudo but same problem.

Same issue it just closes on launch.
I see in a bug tracker that it make references to WINS being enabled, which I have done on my machine. Although I am not sure how to apply the patch they mention in this [link.]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714") (The thread starts off with Rythm box but changes to Banshee when Ubuntu moved to Natty.)

```
[Info  22:59:28.007] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC]
[Info  22:59:29.699] Updating web proxy from GConf
[Info  22:59:29.759] All services are started 1.457699
[Warn  22:59:30.466] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
[Info  22:59:30.669] nereid Client Started
[Info  22:59:30.766] GStreamer version 0.10.32.0, gapless: True, replaygain: False
Stacktrace:


Native stacktrace:

	banshee() [0x80dbc5b]
	banshee() [0x81136eb]
	[0xb78ba40c]

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

---

### Post by Briga on 2011-05-14
Same problem here and in fact it started after I have started using WINS. 

I have just removed wins from the host line in /etc/nsswitch.conf and banshee now runs properly. It is a bug and it is already tracked.

---

### Post by PaulW2U on 2011-05-14
> **Briga said:**
> I have just removed wins from the host line in /etc/nsswitch.conf and banshee now runs properly. It is a bug and it is already tracked.

If that's bug #529714 that you're referring to then it was fixed on 9th May. Have you updated since then? If you're still having problems I'd be very interested to know which bug you're referring to.

---

### Post by exup1000 on 2011-05-15
Hi

yes I am refering to that bug as per the link in my post. At the time of reading that bug report I saw that they had put up a proposed fix. I manually removed the WINS entry in nsswitch.conf file which has broken my backup process for the home network. But at least it has pointed to the cause of the issue, which I take it to be UbuntuOne failing to be resolved some how on open, even thought I have removed this component in Banshee.

I was going to wait for the patch to come down in Ubuntu updates rather then modify my box to get pre-release patches as per the bug tracker wiki advice.

Saying that, I may have ago though tonight, as Banshee in general is displaying other issues. I do like Banshee interface especially how it displays video controls for play back, but it does lock up, stops responding or closes quite frequently that I may end up swithcing back to Rythmbox. My skills at troubleshooting are not very good, other than looking for fixes in Google, and finding this fix proved to be more by luck than by judgement.

Cheers.

---

### Post by randolf_ambrose on 2011-07-22
> **Paqman said:**
> Try getting rid of your Banshee config in /home/username/.config/banshee. I was starting with a completely clean config and got it to load up ok once i'd removed the extension, then I could reinstall the extension and it worked.

If that doesn't work, file a bug at bugzilla, as you probably have a different problem from me.

works just fine now!!!

good post!!! :popcorn:

---

### Post by exup1000 on 2011-07-24
Yup, seems to be working for me now. Suspect updates may have fixed it for me. I now have also re-enabled WINS and it still works.

---

### Post by bkleine on 2012-01-06
thanks for the solution to remove banshee-ubuntuone extension. This worked for me, too!

---

