---
title: "F-spot 0.8.0 crashes after import - Maverick x64"
date: 2010-11-25
forum: General Help
---

### Post by bpack on 2010-11-25
Hi everyone. 

I'm having a very frustrating issue with F-spot Photo Manager, version 0.8.0-1. I've scanned the forums for days but have not happened upon a solution thus far. The application always crashes after importing photos --without moving the original files-- and will continue to crash after repeated attempts to launch the application. 

The only suitable work-around to open F-spot again is to delete the config folder in /home/username/.config/f-spot. But I can't seem to be able to "import" any photos into the library without the same process repeating itself. 

I've tried "importing" photos with "Detect Duplicates" turned off, but the same process occurs. 

Here is the output when launching F-spot from the terminal:

[I][Info  17:14:20.634] Initializing Mono.Addins
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Argument is out of range.
  at System.DateTime.DaysInMonth (Int32 year, Int32 month) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndexDescending (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndex (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.TickLabel (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.GroupSelector.HandleAdaptorChanged (FSpot.GroupAdaptor adaptor) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) FSpot.GroupAdaptor/ChangedHandler:invoke_void__this___GroupAdaptor (FSpot.GroupAdaptor)
  at FSpot.TimeAdaptor+<DoReload>c__AnonStorey19.<>m__6B () [0x00000] in <filename unknown>:0 
  at FSpot.Driver+<RunIdle>c__AnonStorey11.<>m__50 () [0x00000] in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)
[/I]
After deleting the f-spot folder in /.config and launching F-spot from the terminal again, F-spot launches properly and presents me with the usual "Import" dialogue. This is the terminal output thus far:

[I][Info  17:15:33.873] Initializing Mono.Addins

(f-spot:2969): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.[/I]

And after choosing my folders to import and selecting the option to write metadata to the files, I click "Import", and the process seems to complete properly, but as soon as the import is finished, the application crashes with this output: 


[I][Warn  17:19:56.510] Metadata of file file:///media/05ded4ad-5542-4e60-a2c3-67db3c6c6744/blaine-ubuntu/Pictures/Photos/2010/05/09/P5090002.JPG may be corrupt, refusing to write to it, falling back to XMP sidecar.
[Warn  17:19:59.527] Metadata of file file:///media/05ded4ad-5542-4e60-a2c3-67db3c6c6744/blaine-ubuntu/Pictures/Photos/2010/05/15/P5150104.JPG may be corrupt, refusing to write to it, falling back to XMP sidecar.
TAGLIB# DEBUG: Added ns1 prefix for [http://ns.adobe.com/illustrator/1.0/](http://ns.adobe.com/illustrator/1.0/) namespace (XMP)
TAGLIB# DEBUG: Added ns2 prefix for [http://ns.adobe.com/xap/1.0/sType/ResourceRef#](http://ns.adobe.com/xap/1.0/sType/ResourceRef#) namespace (XMP)
[Error 17:20:13.611] Error syncing metadata to file
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Jobs.SyncMetadataJob.WriteMetadataToImage (FSpot.Photo photo) [0x00000] in <filename unknown>:0 
  at FSpot.Jobs.SyncMetadataJob.Execute () [0x00000] in <filename unknown>:0 
[Warn  17:20:21.277] Metadata of file file:///media/05ded4ad-5542-4e60-a2c3-67db3c6c6744/blaine-ubuntu/Pictures/2010/05/08/P5080023.JPG may be corrupt, refusing to write to it, falling back to XMP sidecar.
[Warn  17:20:22.512] Metadata of file file:///media/05ded4ad-5542-4e60-a2c3-67db3c6c6744/blaine-ubuntu/Pictures/2010/05/15/P5150085%20(Modified).JPG may be corrupt, refusing to write to it, falling back to XMP sidecar.
[Error 17:20:38.884] Error syncing metadata to file
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Jobs.SyncMetadataJob.WriteMetadataToImage (FSpot.Photo photo) [0x00000] in <filename unknown>:0 
  at FSpot.Jobs.SyncMetadataJob.Execute () [0x00000] in <filename unknown>:0 
Marshaling destroy signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Widgets.CollectionGridView.OnDestroyed () [0x00000] in <filename unknown>:0 
  at Gtk.Object.NativeDestroy (System.Object o, System.EventArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
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
   at Gtk.Object.gtk_object_destroy(IntPtr )
   at Gtk.Object.Destroy()
   at Gtk.Widget.Destroy()
   at FSpot.UI.Dialog.ImportDialog.OnControllerStatusEvent(ImportEvent evnt)
   at FSpot.Import.ImportController+ImportEventHandler.invoke_void__this___ImportEvent(ImportEvent )
   at FSpot.Import.ImportController+<FireEvent>c__AnonStorey8.<>m__24()
   at FSpot.Driver+<RunIdle>c__AnonStorey11.<>m__50()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)

[/I]
As seen in the output above, the problem appears to be because of a failure to sync the metadata with the photo files. 

Repeating the above process with the option to "Store metadata separately" produces the same crashing result with this output:

[I][Info  17:25:40.738] Initializing Mono.Addins

(f-spot:3067): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Argument is out of range.
  at System.DateTime.DaysInMonth (Int32 year, Int32 month) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndexDescending (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndex (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.TickLabel (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.GroupSelector.HandleAdaptorChanged (FSpot.GroupAdaptor adaptor) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) FSpot.GroupAdaptor/ChangedHandler:invoke_void__this___GroupAdaptor (FSpot.GroupAdaptor)
  at FSpot.TimeAdaptor+<DoReload>c__AnonStorey19.<>m__6B () [0x00000] in <filename unknown>:0 
  at FSpot.Driver+<RunIdle>c__AnonStorey11.<>m__50 () [0x00000] in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)[/I]

I've tried to eliminate all the different variables I can think of, but I haven't found a solution. This issue is present not only in Ubuntu, but also in openSuse 11.3 and Linux Mint 10.

Thank-you for your patience and my apologies for the very long post. 

Can anyone come up with a solution?


Many thanks.

---

### Post by directhex on 2010-11-25
Definitely file a bug about this - the F-Spot developers will never know there's a problem if it's kept on Ubuntuforums

---

### Post by bpack on 2010-11-25
Thanks for the suggestion.

The bug is now reported.

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/681266](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/681266)

---

### Post by parsim on 2010-12-13
Looks like it was previously reported in this bug:

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/669472](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/669472)

... which was fixed here:

[https://bugzilla.gnome.org/show_bug.cgi?id=631333](https://bugzilla.gnome.org/show_bug.cgi?id=631333)

... scheduled for 0.8.1.

---

### Post by parsim on 2010-12-14
Here is the workaround, btw:
```
cd ~/.config/f-spot
cp photos.db photos.db.incaseiwannarecover
sqlite3 photos.db "select * from photos where time < 0;"
sqlite3 photos.db "delete from photos where time < 0;"
```
The second-last line above just gives you a list of what will be affected; you can skip it.

It makes F-Spot resync its metadata for those pics. In my case F-Spot did not lose any of the imported pictures, but timestamped them as 1/1/1970.

---

### Post by bpack on 2010-12-19
Thank you very much parsim.

It seems to work now with no other side effects.

I'll look forward to this feature being fixed permanently.

Thanks everyone.;)

---

### Post by fussl on 2011-01-08
Great, I had been looking for a solution to this problem for ages and had given up for the last 2 month. Thanks for this!!

---

### Post by borobudur on 2011-05-02
Thanks [parsim]("http://ubuntuforums.org/member.php?u=276785")! Solved my problem too!

---

