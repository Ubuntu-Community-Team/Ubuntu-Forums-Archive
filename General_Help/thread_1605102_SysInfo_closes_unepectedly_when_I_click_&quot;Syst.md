---
title: "SysInfo closes unepectedly when I click &quot;System&quot;"
date: 2010-10-24
forum: General Help
---

### Post by 98cwitr on 2010-10-24
I like using sysinfo to make sure I'm clocked correctly and to get other system information. I open it and click anything other than "System" it works fine, but when I click "System" I get this [in terminal when run from terminal]

> 

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)


Correction por favor?

---

### Post by 98cwitr on 2010-10-26
bump

---

### Post by todak on 2010-10-26
It is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727").

---

