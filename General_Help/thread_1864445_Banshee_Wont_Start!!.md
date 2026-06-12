---
title: "Banshee Wont Start!!"
date: 2011-10-19
forum: General Help
---

### Post by Pen16 on 2011-10-19
I updated to 11.10 and im running 64-bit.  My original problem was that every time i would try and open a file it would open banshee instead so to fix that i deleted banshee from the file association and got nautilis back but now everytime i wanna listen to music, banshee wont open at all!

It starts to open and then it stops and disappears. What's goin on?

---

### Post by Pen16 on 2011-10-19
I've tried un-installing it and reinstalling it but still doesn't start.

---

### Post by techvish81 on 2011-10-19
ditch it and use rhythmbox, banshee is not much reliable in 11.10

---

### Post by Pen16 on 2011-10-19
Really? I'd like to try and fix it but i guess if thats what this communities offering.

[Info  14:10:11.778] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Height (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.sizeallocated_cb(IntPtr widget, IntPtr allocation)
   at Gtk.Widget.gtksharp_widget_base_show(IntPtr )
   at Gtk.Widget.OnShown()
   at Nereid.PlayerInterface.OnShown()
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
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

Thats what im gettin in terminal (sorry couldn't find scroll box)

---

