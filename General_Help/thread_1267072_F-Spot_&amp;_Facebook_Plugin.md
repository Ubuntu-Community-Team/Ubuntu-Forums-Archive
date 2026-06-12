---
title: "F-Spot &amp; Facebook Plugin"
date: 2009-09-15
forum: General Help
---

### Post by ukblacknight on 2009-09-15
I'm having trouble with the Facebook export option in F-Spot.  I'm trying to upload some pictures to Facebook, however after clicking Login and then OK on the dialog, F-Spot crashes.  It does open an instance of Firefox and take me to Facebook, to allow F-Spot access.

I've got a terminal output as below:

```

tom@blacknight:~$ f-spot
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:95: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:96: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:330: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:376: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:482: error: invalid string constant "panel", expected valid string constant
[Info  15:59:09.320] Initializing DBus
[Info  15:59:09.416] Initializing Mono.Addins
[Info  15:59:09.531] Starting new FSpot server
[Info  15:59:10.143] Starting DBusService
[Info  15:59:10.146] Starting BeagleService
[Info  15:59:10.146] Hack for gnome-settings-daemon engaged

(f-spot:25930): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:95: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:96: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:330: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:376: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/tom/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:482: error: invalid string constant "panel", expected valid string constant
Marshaling clicked signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: There is an error in XML document. ---> System.InvalidOperationException: <friends_get_response xmlns='http://api.facebook.com/1.0/'> was not expected
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot (System.Xml.Serialization.XmlTypeMapping rootMap) [0x00000] 
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot () [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.IO.Stream stream) [0x00000] 
  at Mono.Facebook.Util.GetResponse[FriendsResponse] (System.String method_name, Mono.Facebook.FacebookParam[] parameters) [0x00000] 
  at Mono.Facebook.FacebookSession.GetFriends () [0x00000] 
  at FSpot.Exporter.Facebook.FacebookExport.HandleLoginClicked (System.Object sender, System.EventArgs args) [0x00000] 
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
   at FSpot.Driver.Main(System.String[] args)

```

Anyone else experiencing this problem?  Or know of a way to fix this?

Thanks :)

---

### Post by ukblacknight on 2009-09-15
Oops, it appears that someone already posted this problem here:

[http://ubuntuforums.org/showthread.php?t=922560](http://ubuntuforums.org/showthread.php?t=922560)

---

