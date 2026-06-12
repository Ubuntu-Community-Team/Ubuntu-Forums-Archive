---
title: "Help a n00b with installing ADOM please."
date: 2011-11-02
forum: General Help
---

### Post by baconstrips on 2011-11-02
Hello, I just recently installed Ubuntu 11.10 from Windows and I am trying to adjust. The main problem I've come across is installing programs not in the software centre, such as ADOM. Here are the steps I have taken, please help me with whatever I did wrong
1) download file from [www.adom.de]("http://www.adom.de")
2) In terminal:
gunzip adom-111-elf.tar.gz
tar xf adom-111-elf.tar
3) copy file from downloads to home folder
I then try to run ADOM by typing 'adom' when in its folder, but it gives me 'adom: command not found'. I even checked it was there with the 'ls' command, and it lists adom with green text. Thank you for any help.

---

### Post by Telengard C64 on 2011-11-02
Try like this:

```
./adom
```

The reason for the **./** is because the current working directory is not automatically searched for executables. **./** is shorthand for *the current working directory*.

---

### Post by Telengard C64 on 2011-11-02
> **baconstrips said:**
> 2) In terminal:
gunzip adom-111-elf.tar.gz
tar xf adom-111-elf.tar

If I may offer a bit of unsolicited advice, it should have been possible to extract the archive in a single step. The following single command should do the same job as the above two commands:

```
tar xvzf adom-111-elf.tar.gz
```

Here's what happened when I tried it:

```
$ tar xvzf adom-111-elf.tar.gz
adom/
adom/adom
adom/manual.doc
adom/readme.1st
adom/adomfaq.txt

```

:guitar:

---

### Post by baconstrips on 2011-11-02
Thank you very much both for the reply and the advice. Worked great!

---

### Post by Telengard C64 on 2011-11-02
You're welcome. Glad to know that worked for you.  :)

---

