---
title: "Cannot run mono!"
date: 2006-03-01
forum: General Help
---

### Post by joined on 2006-03-01
Hi to all.

I have tried to install "mono" on a SUSE 10 distro to test a my little .NET WinForms project. On SUSE 10 all works fine.

So I have tried to run it on my preferred distro (Ubuntu)! ;)

But I received always the following VERY LONG error, why?

Note: I have installed mono via mono univerlas installer and via Ubuntu repository but always with the same bad resutls. :(

```
fabio@ubuntu:~$ mono Desktop/test.exe

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.Form ---> System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.Drawing.GDIPlus ---> System.DllNotFoundException: gdiplus.dll
in (wrapper managed-to-native) System.Drawing.GDIPlus:GdiplusStartup (ulong&,System.Drawing.GdiplusStartupInput&,System.Drawing.GdiplusStartupOutput&)
in <0x000fa> System.Drawing.GDIPlus:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x001a5> System.Drawing.Image:InitFromStream (System.IO.Stream stream)
in <0x00107> System.Drawing.Bitmap:.ctor (System.Runtime.Serialization.SerializationInfo info, StreamingContext context)
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0008d> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x0010e> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x0001a> System.Reflection.MethodBase:Invoke (System.Object obj, System.Object[] parameters)
in <0x001e1> System.Runtime.Serialization.ObjectRecord:LoadData (System.Runtime.Serialization.ObjectManager manager, ISurrogateSelector selector, StreamingContext context)
in <0x00110> System.Runtime.Serialization.ObjectManager:DoFixups ()
in <0x00042> System.Runtime.Serialization.Formatters.Binary.ObjectReader:ReadNextObject (System.IO.BinaryReader reader)
in <0x000b4> System.Runtime.Serialization.Formatters.Binary.ObjectReader:ReadObjectGraph (System.IO.BinaryReader reader, Boolean readHeaders, System.Object result, System.Runtime.Remoting.Messaging.Header[] headers)
in <0x0011f> System.Runtime.Serialization.Formatters.Binary.BinaryFormatter:NoCheckDeserialize (System.IO.Stream serializationStream, System.Runtime.Remoting.Messaging.HeaderHandler handler)
in <0x0000f> System.Runtime.Serialization.Formatters.Binary.BinaryFormatter:Deserialize (System.IO.Stream serializationStream)
in <0x00035> System.Resources.ResourceReader:ReadNonPredefinedValue (System.Type exp_type)
in <0x00321> System.Resources.ResourceReader:ReadValueVer1 (System.Type type)in <0x0017b> System.Resources.ResourceReader:ResourceValue (Int32 index)
in <0x00028> System.Resources.ResourceReader+ResourceEnumerator:get_Value ()
in <0x0008c> System.Resources.ResourceSet:ReadResources ()
in <0x00049> System.Resources.ResourceSet:GetObject (System.String name, Boolean ignoreCase)
in <0x000c8> System.Resources.ResourceManager:GetObject (System.String name, System.Globalization.CultureInfo culture)
in <0x00010> System.Resources.ResourceManager:GetObject (System.String name)
in <0x00017> System.Windows.Forms.Locale:GetResource (System.String name)
in <0x00011> System.Windows.Forms.Form:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x0000b> Test.MainForm:.ctor ()
in (wrapper remoting-invoke-with-check) Test.MainForm:.ctor ()
in <0x00018> Test.MainForm:Main (System.String[] args)
```

--
Best regards...

Fabio Dell'Aria.

---

### Post by mostwanted on 2006-03-01
Mono doesn't support Windows Forms yet.

---

### Post by joined on 2006-03-01
[QUOTE=mostwanted]Mono doesn't support Windows Forms yet.[/QUOTE]
And why the same .NET WinForms project run well on SUSE 10? :)

---

