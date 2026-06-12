---
title: "f-spot error at startup"
date: 2010-11-30
forum: General Help
---

### Post by RastaManPower on 2010-11-30
hello guys i have just installed f-spot and it loads up and crashes. i tryed changing the theme but it doesnt work.also tryed a reinstall but no luck. this is the output
:~$ f-spot
[Info  00:04:31.806] Initializing Mono.Addins
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

---

### Post by irwan_up on 2010-12-08
mine too. we have exactly the same problem. help us, please... thanks

---

