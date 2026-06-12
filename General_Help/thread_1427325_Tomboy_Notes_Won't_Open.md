---
title: "Tomboy Notes Won't Open"
date: 2010-03-11
forum: General Help
---

### Post by wearyroad on 2010-03-11
Hey all, I've been using Tomboy Notes on Mac and, when I recently came over to Ubuntu, was thrilled that I could use it still. However, it quit working. I cannot open it in the Applications Menu, I can't open it via terminal (this is what I get if I try:

brasel@sonny:~$ tomboy -new note

(/usr/lib/tomboy/Tomboy.exe:7009): GLib-WARNING **: g_set_prgname() called multiple times
/usr/share/themes/Human/gtk-2.0/gtkrc:85: Murrine configuration option "gradients" is no longer supported and will be ignored.

(/usr/lib/tomboy/Tomboy.exe:7009): GLib-WARNING **: g_set_prgname() called multiple times
[INFO]: Initializing Mono.Addins

Unhandled Exception: System.IO.IOException: Invalid handle to path "/home/brasel/.local/share/tomboy/8e0f2749-17a0-4771-953d-88bd6681d9f6.note"
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
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
)
I can't open it at all.
I've been trying to find help online, but all of the help lists suggest things that haven't worked. I don't have a .tomboy file in my /home directory, or in my /home/brasel directory. I've uninstalled and reinstalled, I even cleaned out my computer via the computer janitor and it still wouldn't re-install and run. 

Can someone help with this, or am I completely going the wrong way with this?

---

### Post by viralmeme on 2010-03-11
> **wearyroad said:**
> Hey all, I've been using Tomboy Notes on Mac and, when I recently came over to Ubuntu ..

Be carefull, I just tried to install it and it installed MONO. I don't want MONO on my machine ....

---

### Post by cjhabs on 2010-03-11
Your problme appears to be with accessing the file:
Unhandled Exception: System.IO.IOException: Invalid handle to path "/home/brasel/.local/share/tomboy/8e0f2749-17a0-4771-953d-88bd6681d9f6.note"

Did some files get moved or deleted?

---

### Post by wearyroad on 2010-03-11
> **cjhabs said:**
> Your problme appears to be with accessing the file:
Unhandled Exception: System.IO.IOException: Invalid handle to path "/home/brasel/.local/share/tomboy/8e0f2749-17a0-4771-953d-88bd6681d9f6.note"

Did some files get moved or deleted?

I tried to uninstall-reinstall it through the ubuntu software center. If that deleted part of my files, A: I have no idea which ones they were, B: Therefore, I have no idea how to get them back, other than uninstall-reinstall and that worked so well the last two times and C: there's a biger problem here than just Tomboy. (if ubuntu software center is deleting essential files for programs to run whenever you need to uninstall-reinstall.... I mean, I know it was low on features but now it's also a security risk/malware?)

Basically, I think I could do a clean reinstall, (and I think I really need to do a clean reinstall) but I'm not sure how to clean it up before reinstalling. Any ideas?

Edit: I found the file on my computer and it's completely blank. Also, none of the applications know how to open it. (Not even the file browser knows how, I tried to copy it and save it as something else, but the file browser returned: "Error opening file: Input/output error," like all the others.)

---

### Post by sharm on 2010-03-11
The file giving the error appears to be corrupted.  Try moving it to another directory, or simply deleting it, and then try to start Tomboy again.

Uninstalling/reinstalling Tomboy will not fix this problem; the problem is with the note files on your computer.  Hopefully only that one file is corrupted.

---

### Post by wearyroad on 2010-03-11
> **sharm said:**
> The file giving the error appears to be corrupted.  Try moving it to another directory, or simply deleting it, and then try to start Tomboy again.

Uninstalling/reinstalling Tomboy will not fix this problem; the problem is with the note files on your computer.  Hopefully only that one file is corrupted.

That worked. Two files were corrupted, and I sent them both to the trash, and now it works like a charm. It even synchronizes with the server now, so Thanks! :)

---

### Post by alfplayer on 2010-03-11
You can try gnote, a lighter tomboy clone.

---

### Post by wearyroad on 2010-03-11
Say, is there a way to make it so that Tomboy notes are all put in one window placement? I open a lot of them and they end up filling the bottom of my screen, is there a way to set it so that a specific application is always grouped?

Thanks!

---

### Post by wearyroad on 2010-03-11
> **alfplayer said:**
> You can try gnote, a lighter tomboy clone.
Does gnote port your existing tomboy notes? There are certain ones I'd rather like to not  type again... (mine tend to get really long, lol.)

---

### Post by alfplayer on 2010-03-11
> **wearyroad said:**
> Does gnote port your existing tomboy notes? There are certain ones I'd rather like to not  type again... (mine tend to get really long, lol.)

Of course, you could just do it copy/pasting. Anyway, replacing ~/.gnote with your tomboy directory ~/.tomboy worked fine last timed I checked (you may have to move out ~/.gnote first). It should work. To be sure, keep a backup of .tomboy, don't just rename the directory.

To be clear, on a terminal you can run after installing gnote:
cd
mv .gnote .gnote.backup
cp -r .tomboy .gnote

In case you don't know, ~ is your home directory, that is, /home/*yourusername*.

---

### Post by alfplayer on 2010-03-11
I've just remembered: be careful, you may lose text formatting (bold, italics, text size, etc.) if you do it copy/pasting.

---

