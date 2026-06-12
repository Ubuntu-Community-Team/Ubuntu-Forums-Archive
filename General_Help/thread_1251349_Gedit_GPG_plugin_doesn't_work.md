---
title: "Gedit GPG plugin doesn't work"
date: 2009-08-27
forum: General Help
---

### Post by j_arquimbau on 2009-08-27
I activated the GPG GPG plugin for Gedit, but when I select the text to encode it, it shows:

<<No se encontraron claves de cifrado con las que realizar la operación que solicitó. Ahora se iniciará el programa Contraseñas y claves de cifrado para que puede crear una clave o importarla.>>

which means:

<<No encoding keys for doing this operation were found. Now the programs of Passwords and encoding keys (seahorse) is going to be launched so you can create a key and import it>>

Then the program is launched but my keys are already created. In fact, I can encode-decode the text file if I close it and select it with the right button of the mouse and choose the encoding option in nautilus. But even in this case, it shows the message I've just posted, and I have to close seahorse and then I can choose the key with which I want to encode the files.

Any help so far?

Thank you!

---

### Post by gpghelp on 2009-09-06
I'm having the same issue and I've spent like three hours trying to get it work and am getting really frustrated. Does anyone have any ideas?

---

### Post by mobusby on 2009-10-15
Same issue here.  The plugin has worked before, but for now it is completely useless to me.

As a temporary work around, I use the command line to decrypt files:
```
gpg -d /path/to/encrypted/file
```

Encrypting is much less fun, since by default gpg want to perform a binary encryption of the file, instead of an ascii encryption of the contents.

---

### Post by j_arquimbau on 2009-10-17
I got an answer, quite late though:

In jaunty youhave to encode a file first, then you will be able to encode text inside gedit.

In karmic (trying beta) all this has benn solved.

---

