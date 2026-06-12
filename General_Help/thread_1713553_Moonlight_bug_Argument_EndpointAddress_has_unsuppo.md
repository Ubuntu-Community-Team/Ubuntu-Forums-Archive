---
title: "Moonlight bug: Argument EndpointAddress has unsupported URI scheme: https"
date: 2011-03-24
forum: General Help
---

### Post by Charybdisz on 2011-03-24
Hi,

I have Novell Moonlight 3.99.0.2 with Firefox. But if the application loads from https, I get the following error:
[B]
Argument EndpointAddress has unsupported URI scheme: https[/B]

  at System.ServiceModel.Channels.HttpChannelFactory`1[System.ServiceModel.Channels.IRequestChannel].OnCreateChannel (System.ServiceModel.EndpointAddress address, System.Uri via) [0x00000] in <filename unknown>:0 
  at System.ServiceModel.Channels.ChannelFactoryBase`1[System.ServiceModel.Channels.IRequestChannel].CreateChannel (System.ServiceModel.EndpointAddress remoteAddress, System.Uri via) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (System.Reflection.MonoMethod,object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 


How could I solve this problem? This prevents the application from working properly.

---

