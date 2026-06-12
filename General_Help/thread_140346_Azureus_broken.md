---
title: "Azureus broken?"
date: 2006-03-06
forum: General Help
---

### Post by patsissons on 2006-03-06
Tried to boot up azureus today and was given a strange error message that caused azureus to crash violently.  Here is the error report, maybe someone can make some sense of it?

```

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGILL (0x4) at pc=0xb156808f, pid=18485, tid=3084749024
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libgtk-x11-2.0.so.0+0x1f408f]  gtk_tree_view_column_set_reorderable+0x65
#
# An error report file with more information is saved as hs_err_pid18485.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
./azureus: line 112: 18485 Aborted                 ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

```

---

### Post by WretchedSpawn on 2006-03-06
it seems to be complaining about a part of one of your libgtk-2.0 libraries.  you might simply try running a search for libgtk-2.0 in synaptic and seeing if:
a. there are any new versions of ones you already have, or 
b. install any of the 'official' libgtk libraries you don't already have.

---

### Post by patsissons on 2006-03-06
I guess for anyone who runs into this issue (seemed to happen after I upgraded to the latest KDE, which would be 3.5.1) the simple fix is to re-install the following packages:
libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common

I'm sure you could get away with just reinstalling (or possibly reconfiguring) just one of those packages (if you knew the right one), but I did all three and now azureus works fine :)

---

### Post by moffa on 2006-03-06
sorry, but how do I reinstall them without also removing the other 20 or so other packages?

edit: I figured it out (install --reinstall) but it is still not working.

Any other suggestions?

---

### Post by patsissons on 2006-03-09
I just used synaptic and marked those 3 packages for reinstallation.  One other thing I did do (which may or may not have helped) was I installed the latest version of java as per this wiki page
[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca")

Give that a shot and see if it helps.  Don't forget that last step, it's very important.
sudo update-alternatives --config java

---

