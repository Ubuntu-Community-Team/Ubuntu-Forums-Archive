---
title: "Program won't install due to missing dependencies"
date: 2011-06-04
forum: General Help
---

### Post by Projector on 2011-06-04
I'm trying to install a program (A vpn gui) and when I run the installation file I get this output:```
guan@guan ~/Desktop/HMAGUI-Ubuntu-Release/bin $ sudo ./Install.sh 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for WebKit.WebView ---> System.DllNotFoundException: libwebkit-1.0.so.2
  at (wrapper managed-to-native) WebKit.Download:webkit_download_get_type ()
  at WebKit.Download.get_GType () [0x00000] in <filename unknown>:0 
  at GtkSharp.WebkitSharp.ObjectManager.Initialize () [0x00000] in <filename unknown>:0 
  at WebKit.WebView..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at HMAGUIMonoUbuntu.ViewCountrySelection..ctor () [0x00000] in <filename unknown>:0 
  at MainWindow..ctor () [0x00000] in <filename unknown>:0 
  at HMAGUIMonoUbuntu.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```I looked up the dependency in question and I can't find it using  synaptic or aptitude.  When I google searched for it all I could find  where mentions of it for Fedora as a .rpm file.  Is there a comparable  file for our OS or am I going to need to repackage something?

---

### Post by Projector on 2011-06-06
I've done a bit of digging since my last post and I found the package  it's calling out for in the debian squeeze repository.  However when I  tried to install it I saw it would uninstall a whole slew of  applications.  Apparently Mint 11 (and probably Ubuntu 11.04) use the  package "libwebkitgtk-1.0.-0" instead of the "libwebkitgtk-1.0.2-so"  that the vpn client is calling out for.  I'll get in contact with the  makers of the client and see if they can do anything.  Meanwhile, does  anyone know of any alternatives to get this client running using the  packages that Mint uses?  I know that i'm posting on the Ubuntu boards, but since Mint and Ubuntu are quite similar I thought you guys might have the same issue and maybe the same solution.

---

### Post by FormatSeize on 2011-06-06
> **Projector said:**
> I looked up the dependency in question and I can't find it using synaptic or aptitude. When I google searched for it all I could find where mentions of it for Fedora as a .rpm file. 
 
Get the .rpm file anyway, and then get Alien.
If you have an .rpm file for a package you wish to install, and if you cannot find a .deb debian package in any of the Ubuntu repositories or elsewhere, you can use the Alien package converter application to install the .rpm file.
 
Alien is a program that converts between the .rpm, dpkg, stampede slp, and slackpkg file formats.

---

### Post by Projector on 2011-06-06
I did manage to find the .deb lib file that that vpn client calls out for in the debian squeeze repository.  Problem was that when I tried to install it, it required a dependency (libwebkitgtk-common).  To install that dependency would have un installed many other dependencies for many web based programs I have installed, and I imagine it would have broken them.  Perhaps somebody who know more about how dependencies work can tell me otherwise.

---

### Post by babltiga on 2012-03-23
fastest way just do
```

cd /usr/lib
sudo ln -s libwebkitgtk-1.0.so.0 libwebkit-1.0.so.2

```

---

