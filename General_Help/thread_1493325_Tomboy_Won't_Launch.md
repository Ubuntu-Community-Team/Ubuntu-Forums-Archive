---
title: "Tomboy Won't Launch"
date: 2010-05-25
forum: General Help
---

### Post by Jason Cook on 2010-05-25
I am trying to launch Tomboy and it won't launch. Deleting my ```
~/local/share/tomboy
``` directory solved the problem but I don't have my notes anymore. Is there a way to salvage my notes or fix the problem?
This is the output I receive when I run tomboy.
```
[INFO 18:12:16.270] Initializing Mono.Addins
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.IOException: Invalid handle to path "/home/jason/.local/share/tomboy/0308544f-f0a0-4ef1-a184-0b7caf1f78c3.note"
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string,System.Text.Encoding)
  at Tomboy.NoteArchiver.ReadFile (System.String read_file, System.String uri) [0x00000] 
  at Tomboy.NoteArchiver.Read (System.String read_file, System.String uri) [0x00000] 
  at Tomboy.Note.Load (System.String read_file, Tomboy.NoteManager manager) [0x00000] 
  at Tomboy.NoteManager.LoadNotes () [0x00000] 
  at Tomboy.NoteManager.Initialize () [0x00000] 
  at Tomboy.Tomboy+<Main>c__AnonStorey1.<>m__0 () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tomboy.GnomeApplication.StartMainLoop()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)
```

---

### Post by tgalati4 on 2010-05-25
Open a terminal and run:

tomboy --debug

Only post the interesting bits.

You can always try a reconfigure:

sudo dpkg-reconfigure tomboy

---

### Post by Jason Cook on 2010-05-25
Reconfiguring tomboy doesn't work.

As I don't know what is of interest I have posted the entire output here.
```

** Running Mono with --debug    **
[DEBUG 20:51:08.093] NoteManager created with note path "/home/jason/.local/share/tomboy".
[DEBUG 20:51:10.216] EnableDisable Called: enabling... True
[DEBUG 20:51:10.244] Binding key '<Alt><Shift>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG 20:51:10.423] Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/open_recent_changes'
[INFO 20:51:10.649] Initializing Mono.Addins
[DEBUG 20:51:11.569] AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG 20:51:11.704] 	       Name: Tomboy.Tomboy,0.10
[DEBUG 20:51:11.705] 	Description: 
[DEBUG 20:51:11.706] 	  Namespace: Tomboy
[DEBUG 20:51:11.707] 	    Enabled: True
[DEBUG 20:51:11.709] 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG 20:51:16.627] AddinManager.OnAddinLoaded: Tomboy.WebSyncServiceAddin
[DEBUG 20:51:16.629] 	       Name: Web Sync Service Add-in
[DEBUG 20:51:16.629] 	Description: Synchronize Tomboy Notes with Tomboy Online and other compatible web services
[DEBUG 20:51:16.630] 	  Namespace: Tomboy
[DEBUG 20:51:16.630] 	    Enabled: True
[DEBUG 20:51:16.631] 	       File: /usr/lib/tomboy/addins/WebSyncServiceAddin.dll
[DEBUG 20:51:16.634] AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG 20:51:16.636] 	       Name: WebDav Sync Service Add-in
[DEBUG 20:51:16.636] 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG 20:51:16.646] 	  Namespace: Tomboy
[DEBUG 20:51:16.646] 	    Enabled: True
[DEBUG 20:51:16.647] 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG 20:51:16.704] Unable to locate 'gnomesu' in your PATH
[DEBUG 20:51:16.705] Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG 20:51:16.705] Successfully found all system tools
[DEBUG 20:51:16.706] Unable to locate 'wdfs' in your PATH
[DEBUG 20:51:16.708] AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG 20:51:16.710] 	       Name: Local Directory Sync Service Add-in
[DEBUG 20:51:16.711] 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG 20:51:16.712] 	  Namespace: Tomboy
[DEBUG 20:51:16.719] 	    Enabled: True
[DEBUG 20:51:16.719] 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.IOException: Invalid handle to path "/home/jason/.local/share/tomboy/0308544f-f0a0-4ef1-a184-0b7caf1f78c3.note"
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string,System.Text.Encoding)
  at Tomboy.NoteArchiver.ReadFile (System.String read_file, System.String uri) [0x00000] 
  at Tomboy.NoteArchiver.Read (System.String read_file, System.String uri) [0x00000] 
  at Tomboy.Note.Load (System.String read_file, Tomboy.NoteManager manager) [0x00000] 
  at Tomboy.NoteManager.LoadNotes () [0x00000] 
  at Tomboy.NoteManager.Initialize () [0x00000] 
  at Tomboy.Tomboy+<Main>c__AnonStorey1.<>m__0 () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tomboy.GnomeApplication.StartMainLoop()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)

```

---

### Post by tgalati4 on 2010-05-25
Try disabling the websync add-in.

---

### Post by Jason Cook on 2010-05-25
> **tgalati4 said:**
> Try disabling the websync add-in.
How can I do that if the app won't launch?

---

### Post by tgalati4 on 2010-05-25
Sorry, I just thought of that!  The error seems to occur at the point that the web syncronization code looks for the local sync file.  It can't find it and dies a horrible death.

If you are running gnome, then tomboy shows up in your toolbar as a yellow stickie.  You can right click on it to get to preferences.  So I presume that tomboy won't even load to the toolbar?

Try:

sudo apt-get purge tomboy
sudo apt-get install tomboy

---

### Post by Jason Cook on 2010-05-26
> **tgalati4 said:**
> Sorry, I just thought of that!  The error seems to occur at the point that the web syncronization code looks for the local sync file.  It can't find it and dies a horrible death.

If you are running gnome, then tomboy shows up in your toolbar as a yellow stickie.  You can right click on it to get to preferences.  So I presume that tomboy won't even load to the toolbar?

Try:

sudo apt-get purge tomboy
sudo apt-get install tomboy

The icon shows in the notification area for less than a second. Purging and reinstalling doesn't work. As deleting my config fixed the problem I don't think that there is something wrong with tomboy, it's somthings with my config.

---

### Post by Jason Cook on 2010-05-26
It appears that there is an Input/output error with a few of the files. Removing the fixes the problem. Is there anyway to recover the files.

---

### Post by tgalati4 on 2010-05-26
Do you still have the tomboy note files in .tomboy?

They look like:

tgalati4@tpad-Gloria7 ~/.tomboy $ ls
0094b9e9-7005-441e-87c7-5b7d31a4aef2.note
5e227d63-2cba-491d-bd87-afb434de4e85.note
6d490e07-2af0-48b3-9a4c-9791397c8259.note
8ca30a64-f73d-4d92-a451-e64c99281d57.note
95c4cff5-f887-4b3c-b669-edb82cf178f2.note
addin-db-001
addins
cc943332-af4b-4072-8156-4b39b02795fb.note
d4f0c602-b542-48ce-ba23-140d38bb53dc.note
dd89b979-a379-45ae-8baf-6841667c3137.note
def574f4-d31e-4ff3-924f-6594069552f5.note
fb969323-5726-4b63-8998-5e6cb7b91afe.note
manifest.xml

If you moved them to Trash, then they would be in the Trash folder.  If you used the rm (remove) command, then you need to use photorec (sudo apt-get install testdisk) to perform the recovery.  I'm not sure if photorec knows what *.note files are, you will have to do some research on that.

---

### Post by Jason Cook on 2010-05-26
Thanks. I've got my notes back!

---

### Post by zakb on 2010-08-18
> **Jason Cook said:**
> The icon shows in the notification area for less than a second. Purging and reinstalling doesn't work. As deleting my config fixed the problem I don't think that there is something wrong with tomboy, it's somthings with my config.

I had a similar problem.  It started after I re-sized all my partitions with gparted using the live cd.  After combing through the forums I saw your post above about deleting the config file.  That worked for me too.

Here is what I did. 
 Went to /home/zak/.config  
Re-named the file 'tomboy' to 'tomboyconfig.bak' (just in case...)
Opened tomboy from the 'Applications' menu and everything seems fine.  
When I went back in to the '.config' folder there was a nice, new, shiny 'tomboy' folder, so I deleted the 'tomboyconfig.bak'  

If you are new at this, please note that in order to see the '.config' file you will have to open your /home folder and then  go to the menu at the top of the window--click 'View/Show Hidden Files..."

So if anyone is still paying attention to this thread, can we mark it "Solved"?  And if so, how do we do that?  

Thanks...

---

