---
title: "Getting back to pure gnome."
date: 2010-11-18
forum: General Help
---

### Post by Artemis Fowl on 2010-11-18
EDIT: The way the ubuntu forums formatted it made it easier to understand, and I installed the misisng packages.

So I installed  kubuntu plasma desktop, so that I could try KDE, and decided I didn't like it. So I followed the  psycho cat tutorial here on [http://www.psychocats.net/ubuntu/puregnome ]("http://www.psychocats.net/ubuntu/puregnome")"Getting back to pure gnome on Ubuntu"

So, I copy and paste the code there, and it starts uninstalling, but then I get this:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages

```I have absolutely no idea what to do. I know it has something to do with missing dependencies (anyone could, if they read the code) but I don't know what to do.

---

### Post by 13½% on 2010-11-18
sudo apt-get install -y libaccess-bridge-java

Then try the remove routine.

---

### Post by nigo92 on 2010-11-29
I have the same problem but typing "sudo apt-get install -y libaccess-bridge-java" didn't help. Any other ideas :?

--- Edit ---
I found a solution here [http://ubuntuforums.org/showthread.php?t=1579169&page=2]("http://ubuntuforums.org/showthread.php?t=1579169&page=2")

---

