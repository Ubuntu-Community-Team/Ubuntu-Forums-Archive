---
title: "Gnome-Do Errors"
date: 2010-04-15
forum: General Help
---

### Post by winchendonsprings on 2010-04-15
Gnome-Do stopped working and I uninstalled/reinstalled through synaptic. Now it still will not launch. Here is the Terminal printout.

(/usr/lib/gnome-do/Do.exe:6180): GLib-WARNING **: g_set_prgname() called multiple times
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.801] [SystemService] Could not initialize dbus: Unable to open the session message bus.
[Error 01:17:24.809] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
[Error 01:17:24.809] [NetworkService] Could not initialize dbus: Unable to open the session message bus.

System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.ExtensionNodeEventArgs.get_ExtensionObject () [0x00000] 
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
[Error 01:17:24.812] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.814] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.826] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.838] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.840] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
[Error 01:17:24.840] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.843] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.844] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Fatal 01:17:24.848] [Services] Service of type INetworkService not found. Using default service instead.
[Error 01:17:24.854] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

(/usr/lib/gnome-do/Do.exe:6180): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Error 01:17:24.903] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 01:17:24.913] [NetworkService] Could not initialize dbus: Unable to open the session message bus.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

(/usr/lib/gnome-do/Do.exe:6180): libdo-WARNING **: Binding '<Super>space' failed!

Tomboy.NotesItemSource "Tomboy Notes" encountered an error in UpdateItems: An exception was thrown by the type initializer for Tomboy.TomboyDBus.
Could not read Gnome Bookmarks file /root/.gtk-bookmarks: Could not find file "/root/.gtk-bookmarks".
  [COLOR=SeaGreen][B]
[SIZE=3]
Any ideas would be great[/SIZE][/B][/COLOR]

---

### Post by kalaka on 2010-05-13
I am having the same problem. Maybe we should file a bug report?

Does anyone have a solution? :)

---

