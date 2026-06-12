---
title: "Unable install printer software"
date: 2011-05-22
forum: General Help
---

### Post by Dave T on 2011-05-22
Installed U.11.4 new H.D. Canon MP610 Printer-Scanner Deb. programs will not install. Reason missing package (libcupsys2). Available package (libcups2). Downloaded Deb. Linux programs from Canon site onto CD-R, and tried to install from CD. without success.:(

---

### Post by linuxinstalledfromhdd on 2011-05-22
You can try this in terminal:

sudo dpkg -i --force-all package.deb

---

### Post by Dave T on 2011-06-03
Admin, you may delete this thread. Save server space. Thankyou to helper but didn't work.

---

### Post by wolfen69 on 2011-06-03
There was no need to burn the files to cd first. You merely just click the deb files to install.

---

### Post by Dave T on 2011-06-04
Dear wolfen69, put files on CD-R as backup storage. Always do in case of H.D. crash. Put files in Downloads, then clicked on them to install. Got various Dependency errors; cache failure (so I inslalled extra 1G ram), Then unmet dependency no package LIBCUPSYS2-installed package LIBCUPS2. Tried moving files to Desktop but result same. Used Gdebi for package install; kept breaking apt then repairing apt and removing broken package. Used TERM to run commands given me by demonipuch (in my other string). Kept getting "could not open location (commandxxxxx) error stating file (commandxxxxxx) no such file or directory". Put a few other c commands into TERM ( ls and cd among others) but none worked. Selected "run in term", pressed ENT and TERM dialogue box vanished. I realise I can use Ubuntu printer/scanner programmes but I would prefer to use OEM .deb programmes because of the extra options available. There are scanner to print quality issues, using the Ubuntu programmes, which I wish to avoid. That's the only issue I have. Ubuntu 11.04 is totally "awesome" and I love what I've seen so far. The only problem is using TERM and installing OEM packages. Really I don't want to, and shouldn't ever nead to use TERM. cheers from Dave T.

---

### Post by Dave T on 2011-06-07
To new Ubuntu devotees like me,
Hacked around through menus. TERM from within a normal account is NOT the su "command-line", for entering "c" system commands. Go system settings/logon screen/start in SAFE MODE. Save and exit out, shutdown and restart. Login normally again and you are at the true "command line". Now pressing "alt and F2" brings up command box, enter command and you go into text-only TERM window. Now you're working directly with the O.S. and any command you enter is a SYSTEM command, so get it right! Follow the text on-screen in the TERM window, and you can still correct the results of a "doubtful" command-entry by Y/N [ent]. To return to normal "protected" account; right click on bottom bar and select your start "mode" e.g. Ubuntu Standard. Exit and shutdown. Now you're back to normal.
     If you followed my threads, you will know what I've been trying to accomplish, and this information is the successful result of my "learning curve". Print this out and go for it. Cheers from Dave T.

---

