---
title: "Tomboy Notes Fails to Start"
date: 2011-09-20
forum: General Help
---

### Post by ltnemo2000 on 2011-09-20
Although it seems to be able to start for a split second and then instantly closes. the pencil and pad next to my battery icon pops up and then goes away instantly. this is a huge problem because all of my notes for psychology and calculus are in this program as well as those from previous classes. i kind of need them. re-installation didn't work.
much appreciated,
     >G

---

### Post by scarleo on 2011-09-20
Not sure what can cause that, anyway your notes are probably safe in /home/user/.local/share/tomboy if you need them before you solve this

---

### Post by ltnemo2000 on 2011-09-20
thanks. i've actually been wondering where tomboy stores its files so i can give them to friends. at least now i can study for an exam.

---

### Post by patryk77 on 2011-09-20
Try running it from the terminal

$ tomboy

This *might* print some useful information.

---

### Post by ltnemo2000 on 2011-09-20
ok. so I ran it from terminal and the most notable line was:
```
System.IO.IOException: Invalid handle to path "/home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note"
```

I'm not sure exactly what this means and i have even less idea how to fix it. here's the whole output though.

```
grant@grant-VPCEF22FX:~$ tomboy
[INFO 16:57:12.229] Initializing Mono.Addins
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.IOException: Invalid handle to path "/home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note"
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] in <filename unknown>:0 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] in <filename unknown>:0 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string,System.Text.Encoding)
  at Tomboy.NoteArchiver.ReadFile (System.String read_file, System.String uri) [0x00000] in <filename unknown>:0 
  at Tomboy.NoteArchiver.Read (System.String read_file, System.String uri) [0x00000] in <filename unknown>:0 
  at Tomboy.Note.Load (System.String read_file, Tomboy.NoteManager manager) [0x00000] in <filename unknown>:0 
  at Tomboy.NoteManager.LoadNotes () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteManager.Initialize () [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy+<Main>c__AnonStorey2.<>m__0 () [0x00000] in <filename unknown>:0 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Tomboy.GnomeApplication.StartMainLoop()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)

```

the only code i know is a little python. this is greek to me.

---

### Post by patryk77 on 2011-09-20
> System.IO.IOException: Invalid handle to path "/home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note"

ls -l /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note

It will probably complain that the file doesn't exist... If that's the case:
touch /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note

And try it again

---

### Post by ltnemo2000 on 2011-09-22
hmm... still nothing. 
```
grant@grant-VPCEF22FX:~$ ls -l /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note
-rw-r--r-- 1 grant grant 0 2011-09-16 19:19 /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note
grant@grant-VPCEF22FX:~$ touch /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note
touch: cannot touch `/home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note': Input/output error

```

---

### Post by patryk77 on 2011-09-22
```
-rw-r--r-- 1 grant grant 0 2011-09-16 19:19 /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note
```

Actually says the file already existed, and had 0 bytes. If I create a 0 byte file in my folder, Tomboy still works though.

You can try to remove it. Since it's 0 bytes you can always recreate with touch after.

Try:
rm /home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note

I don't like the I/O error though. If it says it can't remove it, you might want to run fsck from a live CD.

---

### Post by directhex on 2011-09-22
```
touch: cannot touch `/home/grant/.local/share/tomboy/b3d1b3e9-e169-493b-9291-9878c27308f1.note': Input/output error
```

Smells like file system corruption to me. Definitely run fsck.

---

### Post by barraclm on 2011-10-19
I have a similar problem (Tomboy doesn't run after upgrade).  I was one of the (too) many who had problems with the upgrade and had to create the /run and /run/lock structure and link to /var/run and /var/lock.  I saw something about the dbus being an issue there.

Here is my output from $tomboy.  Amy help would be appreciated.

===============================================================

Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0

---

### Post by directhex on 2011-10-20
> **barraclm said:**
> I have a similar problem (Tomboy doesn't run after upgrade).  I was one of the (too) many who had problems with the upgrade and had to create the /run and /run/lock structure and link to /var/run and /var/lock.  I saw something about the dbus being an issue there.

Here is my output from $tomboy.  Amy help would be appreciated.

===============================================================

Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0

Looks like a corrupted Mono install - try aptitude reinstall libmono-corlib2.0-cil

---

