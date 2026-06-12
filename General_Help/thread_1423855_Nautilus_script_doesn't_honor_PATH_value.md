---
title: "Nautilus script doesn't honor PATH value"
date: 2010-03-07
forum: General Help
---

### Post by HiSiskin on 2010-03-07
On our Ubuntu 9.10 which has Nautilus 2.28.1 file manager, we have a line on a Nautilus script:

java -jar $filename 2>naut-err.txt

We have set the PATH variable value for our jdk/bin path in the $HOME/.bashrc file and we can run the above command line from gnome-terminal on the same directory where the $filename file does reside.  However, the Nautilus script emits error saying 'java not found' for the above line.

What could be the cause and the cure for the weird error?

On Fedora systems(Fedora 10 and 12), the same script does run just normally. Why Ubuntu does have the problem?

---

### Post by geirha on 2010-03-07
.bashrc is only sourced for interactive non-login shells. Set PATH in .profile instead, then log out and back in to have it sourced.

---

### Post by HiSiskin on 2010-03-07
> **geirha said:**
> .bashrc is only sourced for interactive non-login shells. Set PATH in .profile instead, then log out and back in to have it sourced.
Problem solved all too soon thanks to your precise answer. Fedora/Red Hat doesn't hava .profile file. The Debian, for which I am a sheer newbie, is a different culture.

---

