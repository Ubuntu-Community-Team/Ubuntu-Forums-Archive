---
title: "hipo not detecting IPOD"
date: 2010-11-14
forum: General Help
---

### Post by krishnatry on 2010-11-14
hi,

I have just started using this forum. I am trying to synch my IPOD 3 using HIPO but HIPO is unable to detect my IPOD. when I connect my IPOD while HIPO is already running I get the below given error. Please somebody help as I need to take some backup on my IPOD.

[B]  at Hal.IDeviceIPodProxy.PropertyExists (System.String ) [0x00000] 
  at Hal.Device.PropertyExists (System.String key) [0x00000] 
  at IPod.HalClient.HalDeviceManager.IsIPod (Hal.Device device) [0x00000] 
  at IPod.HalClient.HalDeviceManager.OnDeviceAdded (System.Object o, Hal.DeviceAddedArgs args) [0x00000] 
  at Hal.Manager.OnDeviceAdded (System.String udi) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
::End of inner stack trace::
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at NDesk.DBus.Connection.HandleSignal (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.DispatchSignals () [0x00000] 
  at NDesk.DBus.PendingCall.get_Reply () [0x00000] 
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.BusObject.SendMethodCall (System.String iface, System.String member, System.String inSigStr, NDesk.DBus.MessageWriter writer, System.Type retType, System.Exception& exception) [0x00000] 
  at Hal.IDeviceIPodProxy.PropertyExists (System.String ) [0x00000] 
  at Hal.Device.PropertyExists (System.String key) [0x00000] 
  at IPod.HalClient.HalDeviceManager.IsIPod (Hal.Device device) [0x00000] 
  at IPod.HalClient.HalDeviceManager.OnDeviceAdded (System.Object o, Hal.DeviceAddedArgs args) [0x00000] 
  at Hal.Manager.OnDeviceAdded (System.String udi) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
::End of inner stack trace::
at System.Reflection.MonoMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0011f>
at System.Reflection.MethodBase.Invoke (object,object[]) <0x0002a>
at System.Delegate.DynamicInvokeImpl (object[]) <0x0017b>
at System.MulticastDelegate.DynamicInvokeImpl (object[]) <0x0003b>
at System.Delegate.DynamicInvoke (object[]) <0x00015>
at NDesk.DBus.Connection.HandleSignal (NDesk.DBus.Message) <0x0012f>
at NDesk.DBus.Connection.DispatchSignals () <0x00047>
at NDesk.DBus.Connection.Iterate () <0x00033>
at NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0003b>
at (wrapper native-to-managed) NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00077>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00052>
at Gtk.Application.Run () <0x0000b>
at Gnome.Program.Run () <0x0000b>
at Hipo.HipoMainWindow.CreateWindow (string[]) <0x01bdb>
at Hipo.HipoMain.Run (string[]) <0x000bb>
at Hipo.HipoMain.Main (string[]) <0x0003f>
[/B]

---

