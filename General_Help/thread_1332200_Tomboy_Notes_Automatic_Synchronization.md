---
title: "Tomboy Notes Automatic Synchronization???"
date: 2009-11-20
forum: General Help
---

### Post by cyanide on 2009-11-20
Hi,
   Does anyone know how to make Tomboy Notes synchronize automatically to a folder after a change/addition/deletion is made to the notes??

I am tired of clicking the synchronize notes buttons when ever I want to update my notes on Dropbox, I was hoping some one could help me automate the synchronization.

If anyone could give me a guide to do that it would be most appreciated.

Any help is appreciated.

PS: I use Tomboy Notes in Windows as well, if anyone know the windows hack, kindly include that as well.

---

### Post by sharm on 2009-11-20
No way to do that with the built-in synchronization, but if you disable that there is a way.

If you are using Tomboy 1.0, go to preferences->add-ins and enable the Note Directory Watcher add-in.  Then use symlinks to link your notes directory (defaults to ~/.local/share/tomboy ) to a directory in dropbox.  Do the same thing on Windows (I'm not familiar with the right way to do symlinks on windows but I'm sure if you google you'll figure it out).

Now, when you modify a note in Tomboy one computer, since both computers are sharing a note directory, and both have the Note Directory Watcher add-in enabled, the second computer will notice the change when Dropbox syncs it over, and it will update your note automatically.

---

### Post by cyanide on 2009-11-21
Thanks sham!! The instructions you provided worked flawlessly.

---

### Post by sharm on 2009-11-21
Glad I could help, cyanide.

For anyone else reading this thread, I should mention that automatic synchronization is planned for Tomboy 1.2, so those of you using Ubuntu One and other official sync backends, you will get autosync in Lucid if everything goes according to plan.

---

