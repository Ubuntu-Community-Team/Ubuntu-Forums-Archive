---
title: "FreeCCA / Mono"
date: 2011-10-16
forum: General Help
---

### Post by K-4U on 2011-10-16
Hello everybody.

At school, we have a <snip> program called Cisco NAC.
This program is used to only allow people on the wifi, who have the latest windows updates and a virus scanner installed.

Needless to say, this doesn't work under Ubuntu.
Now, i've stumbled upon a program called FreeCCA. However, i run into some problems.

I have first downloaded the .deb file provided at the website. However, when i run this:
> Missing method System.Reflection.Assembly::op_Inequality(Assembly,Assembly) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Reflection.Assembly.op_Inequality'.
  at NDesk.DBus.TypeImplementer.GetImplementation (System.Type declType) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.BusObject.GetObject (NDesk.DBus.Connection conn, System.String bus_name, NDesk.DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Connection.GetObject (System.Type type, System.String bus_name, NDesk.DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Connection.GetObject[IBus] (System.String bus_name, NDesk.DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at NDesk.DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at freecca.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Reflection.Assembly.op_Inequality'.
  at NDesk.DBus.TypeImplementer.GetImplementation (System.Type declType) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.BusObject.GetObject (NDesk.DBus.Connection conn, System.String bus_name, NDesk.DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Connection.GetObject (System.Type type, System.String bus_name, NDesk.DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Connection.GetObject[IBus] (System.String bus_name, NDesk.DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at NDesk.DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at freecca.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0 


No idea on how to fix this.
So, i decided to download their latest source, and try to compile that:
> Making all in .
make[1]: Map '/home/koen/freecca-1.1.0' wordt binnengegaan
mkdir -p bin/Release
gmcs -noconfig -codepage:utf8 -warn:4 -optimize+ "-main:freecca.MainClass"  -out:bin/Release/freecca.exe -target:winexe './gtk-gui/generated.cs' './gtk-gui/MainWindow.cs' './src/AssemblyInfo.cs' './src/Certificate.cs' './src/Cipher.cs' './src/Client.cs' './src/Keyring.cs' './src/Main.cs' './src/MainWindow.cs' './src/NetworkManager.cs' './src/Settings.cs' './src/HTMLParser/Attribute.cs' './src/HTMLParser/AttributeList.cs' './src/HTMLParser/Parse.cs' './src/HTMLParser/ParseHTML.cs' './src/Notifications/Notifications.cs' './src/Notifications/LibNotifyNotifications.cs' './src/Systray/Systray.cs' './src/Systray/Menu.cs' './src/Systray/About.cs'  '-resource:./gtk-gui/gui.stetic'    -r:System    -r:/usr/lib/pkgconfig/../../lib/cli/pango-sharp-2.0/pango-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/atk-sharp-2.0/atk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gdk-sharp-2.0/gdk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gtk-sharp-2.0/gtk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/glib-sharp-2.0/glib-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/glib-sharp-2.0/glib-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/glade-sharp-2.0/glade-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/pango-sharp-2.0/pango-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/atk-sharp-2.0/atk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gdk-sharp-2.0/gdk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gtk-sharp-2.0/gtk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/glib-sharp-2.0/glib-sharp.dll    -r:Mono.Posix    -r:/usr/lib/cli/gconf-sharp-2.0/gconf-sharp.dll    -r:/usr/lib/cli/Gnome.Keyring-1.0/Gnome.Keyring.dll    -r:/usr/lib/cli/notify-sharp-0.4/notify-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/pango-sharp-2.0/pango-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/atk-sharp-2.0/atk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gdk-sharp-2.0/gdk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/gtk-sharp-2.0/gtk-sharp.dll    -r:/usr/lib/pkgconfig/../../lib/cli/glib-sharp-2.0/glib-sharp.dll    -r:/usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll    -r:/usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll    -r:/usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll  
./src/Systray/Systray.cs(71,52): error CS0176: Static member `freecca.Systray.GetIcon(string)' cannot be accessed with an instance reference, qualify it with a type name instead
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [bin/Release/freecca.exe] Fout 1
make[1]: Map '/home/koen/freecca-1.1.0' wordt verlaten
make: *** [all-recursive] Fout 1


Now, here's the big question. Who can help me?
I really want to be able to bypass those damn ICT guys at school and be able to internet on my Ubuntu.

---

### Post by K-4U on 2011-11-09
*bump*

---

### Post by nothingspecial on 2011-11-09
While it is unfortunate that your schools internet security system does not work with Ubuntu, we can not support circumventing it here.

Closed.

---

