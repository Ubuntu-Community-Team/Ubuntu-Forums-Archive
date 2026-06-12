---
title: "startupmanager cannot start"
date: 2011-08-15
forum: General Help
---

### Post by pko76 on 2011-08-15
i have a problem startupmanager cannot start on ubuntu 10.04.i run gksudo startupmanager but it cannot start without error message.

---

### Post by dino99 on 2011-08-15
close all your apps and try again

---

### Post by pko76 on 2011-08-15
> **dino99 said:**
> close all your apps and try againi already restart my system but nothing the same problem

---

### Post by dino99 on 2011-08-15
open synaptic and remove/purge it then reinstall it

---

### Post by pko76 on 2011-08-15
> **dino99 said:**
> open synaptic and remove/purge it then reinstall iti do that but the same problem

---

### Post by hakermania on 2011-08-15
Post the error message here please

---

### Post by pko76 on 2011-08-15
> **hakermania said:**
> Post the error message here please
there is no error message

---

### Post by hakermania on 2011-08-15
> **pko76 said:**
> there is no error message
Oh I got it wrong here. Can you run on gdb to see what's wrong here?

---

### Post by pko76 on 2011-08-15
> **hakermania said:**
> Oh I got it wrong here. Can you run on gdb to see what's wrong here?
i don't know how to use gdb.
i run again the gksudo startupmanager command.it gives these results
```
gksudo startupmanager
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 166, in __init__
    self.resolution = utils.get_resolution()
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 159, in get_resolution
    return matches.group(1) + 'x' + matches.group(2)
AttributeError: 'NoneType' object has no attribute 'group'

```

---

### Post by hakermania on 2011-08-16
Does it have to run using gksudo?

---

### Post by pko76 on 2011-08-16
> **hakermania said:**
> Does it have to run using gksudo?
when i try to run it from the system menu the same problem.i use gksudo in order to show me the error message.

---

### Post by Mark Phelps on 2011-08-16
I used to use StartupManager all the time -- and then upgraded to 11.04, with the GRUB 1.99RC upgrade, and it didn't work properly anymore.  So, I quit using it and went over to Grub-customizer.

My guess, from the messages you're getting, is that there is a default resolution set in startupmanager that is invalid -- and thus, it won't display.

Since uninstalling and reinstalling doesn't help, you should consider going over to Grub-customizer as an alternative.

---

### Post by pko76 on 2011-08-17
> **Mark Phelps said:**
> I used to use StartupManager all the time -- and then upgraded to 11.04, with the GRUB 1.99RC upgrade, and it didn't work properly anymore.  So, I quit using it and went over to Grub-customizer.

My guess, from the messages you're getting, is that there is a default resolution set in startupmanager that is invalid -- and thus, it won't display.

Since uninstalling and reinstalling doesn't help, you should consider going over to Grub-customizer as an alternative.

i will follow your suggestion but how i can use gdb?

---

