---
title: "Openoffice not starting"
date: 2010-07-05
forum: General Help
---

### Post by sksingh on 2010-07-05
I am using 10.04 LTS. Earlier openoffice was working fine but since yesterday, its not working i.e when i try to open openoffice spreadsheet, presentation or any other programs of openoffice, its not starting up. Even splash screen is not coming up. Its also not displaying any errors.
I also tried running from terminal by giving command **ooffice -writer**. But its giving following errors.

/usr/lib/openoffice/program/../basis-link/ure-link/bin/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/oosplash.bin: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory

After that i tried to reinstall using **sudo aptitude reinstall ~nopenoffice**, but still same problem exists. PLEASE HELP

---

### Post by AlphaLexman on 2010-07-05
try:```
oowriter -norestore
```you may have had a faulty shutdown.

---

### Post by sksingh on 2010-07-05
No change, when i gave above command its giving same errors

/usr/lib/openoffice/program/../basis-link/ure-link/bin/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/oosplash.bin: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory

---

### Post by AlphaLexman on 2010-07-05
The oosplash.bin gives me concern. Try
```
oowriter -nologo
```

---

### Post by sksingh on 2010-07-05
Status quo. This was the error given by command oowriter -nologo

/usr/lib/openoffice/program/../basis-link/ure-link/bin/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory

---

### Post by gansvv on 2010-07-05
Post the result of:

```

locate libuno_sal.so.3

```

---

### Post by sksingh on 2010-07-05
This is the result

/usr/lib/libuno_sal.so.3
/usr/lib/ure/lib/libuno_sal.so.3

---

### Post by AlphaLexman on 2010-07-05
post the result of:
```
locate javaldx
```
and
```
loacte oosplash.bin
```

---

### Post by sksingh on 2010-07-05
For locate javaldx

/usr/lib/ure/bin/javaldx

& for locate oosplash.bin

/usr/lib/openoffice/program/oosplash.bin

---

### Post by AlphaLexman on 2010-07-05
> **sksingh said:**
> /usr/lib/openoffice/program/../basis-link/ure-link/bin/javaldx

is two links [shortcuts] to > /usr/lib/openoffice/ure/bin/javaldx

on my system I do have /usr/lib/openoffice/ure

but I don't have a bin directory there only a lib directory

post the output of ```
ls /usr/lib/openoffice/ure/
```

---

### Post by sksingh on 2010-07-05
Here is the output

cannot access /usr/lib/openoffice/ure/: No such file or directory

---

### Post by AlphaLexman on 2010-07-05
what does the parent directory look like?

---

