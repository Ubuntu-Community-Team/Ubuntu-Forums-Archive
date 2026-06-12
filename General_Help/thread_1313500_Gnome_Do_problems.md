---
title: "Gnome Do problems"
date: 2009-11-03
forum: General Help
---

### Post by ricky0319 on 2009-11-03
I just installed 9.10 on my Macbook 2,1. I posted this in the Apple Users section, but still have not received a response. i figured this could be filed under general Ubuntu problems since it is not hardware related. First I want to say this is by far the best release and I am loving karmic. I just have a problem with Gnome Do. I have installed Gnome Do and it does not open. When I click on it nothing happens. I have tried deleting several times and reinstalling it still nothing. I have tried from the software center, synaptic and a .deb file. Any suggestions?

When I try to run gnome do in the terminal this what happens -

ERROR: Unexpected error in setup process
System.Exception: System.NullReferenceException: Object reference not set to an instance of an object
at Mono.Addins.Database.AddinDatabase.InternalScanFol ders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
at Mono.Addins.Database.AddinDatabase.ScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
ERROR: Add-in scan operation failed
Stack overflow in unmanaged: IP: 0x81a64ec, fault addr: 0xbf4edffc
ERROR: The add-in database could not be updated. It may be due to file corruption. Try running the setup repair utility

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Do/Service
at Mono.Addins.ExtensionContext.AddExtensionNodeHandl er (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
at Do.Platform.Services.Initialize () [0x00000] 
at Do.Core.PluginManager.Initialize () [0x00000] 
at Do.Do.Main (System.String[] args) [0x00000] 


I am still new at linux and I am not sure what all this is.

---

### Post by Unknown Pirate on 2009-11-03
1. Install Gnome Do

2. Reboot your machine

3. Try to open again

---

### Post by ricky0319 on 2009-11-03
The reboot about installing Gnome Do does not work. The same thing is happening. I click on the application and nothing happens.

---

### Post by Unknown Pirate on 2009-11-03
I am sorry I can't help you this time try to add question to the Gnome DO team

[https://answers.launchpad.net/do/+addquestion/+login](https://answers.launchpad.net/do/+addquestion/+login)

**Best regards!**

---

### Post by directhex on 2009-11-04
Remove your Do config folder ~/.config/gnome-do and try again. Old versions of Do used to copy the plugins to your config folder, and those are going to be old (probbaly incompatible) versions

---

### Post by ricky0319 on 2009-11-04
How can I find that folder?

---

### Post by bedhead75 on 2009-11-04
[https://bugs.launchpad.net/do/+bug/325106](https://bugs.launchpad.net/do/+bug/325106)

I don't think that folder exists.  Check here instead.

---

### Post by ricky0319 on 2009-11-05
Thanks I deleted that folder in  ~/.local/share/gnome-do then reinstalled. It worked.

---

