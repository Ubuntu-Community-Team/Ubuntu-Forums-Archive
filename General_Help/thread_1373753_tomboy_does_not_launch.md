---
title: "tomboy does not launch"
date: 2010-01-06
forum: General Help
---

### Post by prconnor@gmail.com on 2010-01-06
Hello,

I am attempting to use tomboy and it does not launch giving me the following:```
~$ tomboy

(/usr/lib/tomboy/Tomboy.exe:3602): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/tomboy/Tomboy.exe:3602): GLib-WARNING **: g_set_prgname() called multiple times
[INFO]: Initializing Mono.Addins

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Tomboy.AddinManager.InitializeMonoAddins (System.String old_conf_dir) [0x00000] 
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir, System.String old_tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

```

I did ```
sudo apt-get purge mono-runtime tomboy
``` and ```
sudo apt-get install tomboy
``` installing all the packages again without comment or error, but the problem persists with exactly the same error as above.

Thank you for your time/effort in helping.

Phil

---

### Post by prconnor@gmail.com on 2010-01-07
bump.

Is there another similar application that can work with Ubuntu One?  I just read about the service and am interested in trying it.

---

### Post by prconnor@gmail.com on 2010-01-07
I uninstalled tomboy using apt, and successfully installed tomboy 1.0.1 from source.  Spell check does not work.  gtkspell is installed on my computer and was located by the configure script.  Is there something I can do to make it work?

---

### Post by prconnor@gmail.com on 2010-01-09
Got it!

tomboy uses gtkspell, which uses aspell.  Although I had gtkspell I did not have asepell installed.  Once I did a ```
sudo apt-get install aspell
``` and restarted tomboy I was in the money.

Now if I could just figure out how to mark this solved ...

---

