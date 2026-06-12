---
title: "Banshee crashes after updating compiled version"
date: 2011-10-01
forum: General Help
---

### Post by mkborregaard on 2011-10-01
I am new to Ubuntu, and thus unsure about whether this is the correct forum. I think the problem is general (i.e. not related to Banshee specifically) so I post here. 
I was eager to try out Banshee 2.2, but could not find it in the Banshee ppa. So I downloaded the source from the Banshee website, and installed it on my machine using ./configure; make; sudo checkinstall. I had to run each command several times to get all the necessary dependencies (dev-libs) installed. I also try to compile and install the banshee-2.2 community extensions, but the install failed, so I gave up.

I subscribe to the banshee ppa, and when running sudo apt-get dist-upgrade it automatically downloaded and installed banshee 2.2.1. There were several error messages during the install (sorry, I do not know where to find the install log - will post if you can direct me to where it is). Now, banshee crashes upon launch, with the following message:
```

michael@ubuntu:~$ banshee
[Info  13:19:52.209] Running Banshee 2.2.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-09-27 10:02:56 UTC]
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::link-color' of type `GdkColor' from rc file value "((GString*) 0x8f669a0)" of type `GString'


```

I have tried removing the app (using both complete removal in Synaptic, and autoremove) and reinstalling. Now, the install gives fewer error messages, though still the message:
```
Udpakker banshee-extension-soundmenu (fra .../banshee-extension-soundmenu_2.2.0-1ubuntu2~hyper1+natty_i386.deb)...
Behandler udløsere for shared-mime-info ...
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Behandler udløsere for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Behandler udløsere for desktop-file-utils ...
Behandler udløsere for python-gmenu ...
Rebuilding /usr/share/applications/desktop.da_DK.utf8.cache...
Behandler udløsere for hicolor-icon-theme ...
Behandler udløsere for menu ...
Behandler udløsere for man-db ...
Behandler udløsere for python-support ...
Sætter banshee (2.2.0-1ubuntu2~hyper1+natty) op...
Sætter banshee-extension-soundmenu (2.2.0-1ubuntu2~hyper1+natty) op...
Behandler udløsere for menu ...

```

Reinstalling does not solve the problem, and I cannot run banshee anymore. Any help would be greatly appreciated!
Thanks,

---

### Post by mkborregaard on 2011-10-01
I have reposted this question at the Banshee forum, since it looked more appropriate.

---

### Post by flipper T on 2011-10-01
2.2 comes as standard in 11.10

wait 9 days ?

---

### Post by mkborregaard on 2011-10-01
I would be happy to wait for the oneiric upgrade, but I do not believe this will solve the problem. Banshee 2.2 is already now on the banshee community ppa. The problem is that it will not run, and I believe it is because I have broken something, maybe in the dependencies, that cannot be remedied by a renewed install of banshee. Of course I could reinstall Ubuntu from scratch with the 11.10 iso, but surely there must be less drastic ways?

---

### Post by mkborregaard on 2011-10-03
The solution seems to be that banshee 2.2 is built against the mono-addin library version 0.6-2, which is standard in oneiric, not 0.4-8, which I have on my natty narwhal. So waiting for oneiric should indeed do the trick.

---

