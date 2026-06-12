---
title: "VLC won't reinstall, help?"
date: 2011-05-06
forum: General Help
---

### Post by Moga1 on 2011-05-06
I am fairly new to Linux :) 

I have VLC 1.1.9 installed from package. I accidently deleted the /usr/bin/vlc executable manually, which naturally made the program not work anymore - but even though I reinstalled the package (several times, and also uninstalled and installed fresh) - the file won't come back.  

Before this happened I was compiling the newest unstable version of VLC (1.2.0) and making symbolic links for the new version (hence the mistake thinking I was deleting a link), but even this version of the program won't run anymore even though it still has it's executable - it says: 
"./usr/local/bin/vlc-1.2.0/vlc: error while loading shared libraries: libvlccore.so.5: cannot open shared object file: No such file or directory" - but the libvlccore package is installed!

I even downloaded the VLC 1.1.9 .deb package file but it doesn't contain a /usr/bin/vlc file (!)

I want VLC back!!! help please? :KS

---

### Post by Moga1 on 2011-05-06
Ah, apparently it was in the vlc-nox package. VLC 1.1.9 now runs but the 1.2.0 still gives me the same error message, any ideas? (it used to run fine before I messed with the 1.1.9 executable)

---

