---
title: "sudo access denied, karmic"
date: 2009-11-13
forum: General Help
---

### Post by moominboy8668 on 2009-11-13
hi guys! 

im sure a few people have either had or read about some shutdown/restart problems in Karmic?

my workaround was to create 2 launchers on the desktop and run the terminal commands from those icons but i was annoyed with it asking for the sudo password every time.

so i had a good read about passwordless sudo-ing and had a few trial runs using visudo.

now i've accidentally removed or commented myself out of the sudoers file!

can't use sudo as "dave is not in the sudoers file"

can't use root as root is not installed?

and obviously can't gt back into visudo to correct my mistake

any help or direction would be greatly appreciated folks. thank you!

---

### Post by mihaiv on 2009-11-13
Boot from the Ubuntu installation CD and fix the problem.
Use visudo with the -f option to specify your installed sudoers file (see man visudo).

---

### Post by moominboy8668 on 2009-11-13
i have the 8.04 live disc, just about to burn the karmic one but out of interest would it matter?

---

