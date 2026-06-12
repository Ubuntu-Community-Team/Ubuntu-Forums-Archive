---
title: "Ubuntu 10.04 netbook version freezes on installation."
date: 2010-08-06
forum: General Help
---

### Post by pooriak on 2010-08-06
Ubuntu 10.04 freezes on installation.
When I try to install Ubuntu 10.04 for netbook it will freeze when it starts the installation.
Generating locales...
   en_US.UTF-8...

and nothing happens, it will be freezed here?
what can i do?

---

### Post by mikewhatever on 2010-08-06
You can do two things:
1. Check the downloaded iso.
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)
2. Reveal the hardware specs and computer model.

---

### Post by pooriak on 2010-08-06
I checked the iso with md5sum and it was correct.
My system sepc is:
Manufacturer: ASUS
Model: Eee PC
Processor: Intel(R) Atom(TM) CPU 330 @ 1.60GHz 
Installed memory(RAM): 3.00GB

That iso file was correct, so where is the problem? what can I do now?

---

### Post by pooriak on 2010-08-06
When I tried to install in text mode, again that was same:
Begin: Addling live session user... ...
Done.
Begin: Configuring fstab... ...
Done.
Begin: Setting up swap... ...
Done.
Begin: Setting up locales... ...
Generating locales...
  en_US.UTF-8...

it freezes here, and nothing happens. and after I press some keys it will be shown:
(process:331): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
(process:331): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans 12', text='The qui\xfbk brown fox jumps over the lazy\xbfdog.'
*** glibc detected *** /sbin/plymouthd: free(): invalid next size(fast): 0x09978f00 ***

---

### Post by mikewhatever on 2010-08-07
Not quite sure what's wrong here. Have you tried any of the non-Ubuntu or even non-Debian distros on that machine? Would be interesting to see how they did.

---

