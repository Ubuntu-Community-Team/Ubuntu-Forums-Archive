---
title: "linux command path / register"
date: 2009-12-13
forum: General Help
---

### Post by stdcinout on 2009-12-13
hi guys i know there is manual to this but just wondering 

say you install something that you can call as a command in terminal 

for example something / some softwares like vboxgtk 

then you can call vboxgtk in the terminal 

but where does the vboxgtk resides? i type in whereis vboxgfk it shows the path to usr/bin/some/where/in/

but is there any file or something that control the PATH of this?or something? 

THANKS

---

### Post by lloyd_b on 2009-12-13
> **stdcinout said:**
> hi guys i know there is manual to this but just wondering 

say you install something that you can call as a command in terminal 

for example something / some softwares like vboxgtk 

then you can call vboxgtk in the terminal 

but where does the vboxgtk resides? i type in whereis vboxgfk it shows the path to usr/bin/some/where/in/

but is there any file or something that control the PATH of this?or something? 

THANKS

Just add the directory that command is in to your PATH.  Edit the file "~/.bashrc", and at the end add a line:```
PATH="$PATH:/usr/bin/some/where/in"
``` (with the real directory, of course).

Note that you'll need to close and reopen the terminal window before this change takes effect.

Lloyd B.

---

### Post by SPr on 2009-12-13
From the manual
> 
whereis then attempts to locate the desired program  in  a list of standard Linux places.

The places are hardcoded into the binary.
```

strings /usr/bin/whereis| grep /

```
reveals them.

---

### Post by lloyd_b on 2009-12-13
"whereis" is a bit limited.  Try "which {filename}" to see where a given executable file resides - this *does* search the PATH.

Lloyd B.

---

### Post by stdcinout on 2009-12-13
thank you guys !

---

