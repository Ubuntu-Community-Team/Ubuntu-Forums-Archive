---
title: "Vbox, no 64 bit option while the host is 64 bit."
date: 2010-10-14
forum: General Help
---

### Post by keljaden on 2010-10-14
So, I recently download Vbox (I tried like 3 different versions including the most recent one). on my 10.10 ubuntu 64 bit install.  To test some 3rd party apps i was going to make a 10.10 x64 vm. For some reason, I am unable to make the VM 64 bit, it's no longer an option like it was on previous releases.  I am at a lost as to what I should do.  Any reason why it's not there? I tried 3.2.x and 3.1.8 to see if it was a most recent version, but they all had that same problem so I am thinking it's a 10.10 issue. Please help.

---

### Post by CharlesA on 2010-10-14
Are you sure it's 10.10 x64?

Also, is Hardware virtualization enabled in the BIOS?

---

### Post by sendblink23 on 2010-10-14
any x64 os vm works fine over here using latest Vbox on my 10.10 x64

---

### Post by keljaden on 2010-10-14
uname -m outputs "x86_64".

And I tried the Vbox from both the site and the repos and an older version...

I install the 64 bit debs from the site, and the 64 bit universal they install.

The problem is, the gui doesn't not have the option when I am selecting the OS like it did before. I'll check my BIOS just to be sure though.

---

### Post by CharlesA on 2010-10-14
That's the right kernel. It should have the 64-bit versions listed.

---

### Post by keljaden on 2010-10-14
That's what I thought.  When I go to select the OS to install (like Ubuntu, linux 2.6, etc)  I don't see ANY 64 bit options.  Did they move where it is located?  That's the only thing I can think of.

---

### Post by CharlesA on 2010-10-14
Not that I know of.

The 64-bit version should be listed above (or below) the 32-bit versions.

---

### Post by keljaden on 2010-10-14
I will play around with it and see if i can figure anything out.  I am going to be installing on another machine soon anyways. I'll test Vbox on that machine too.

---

### Post by Quackers on 2010-10-15
I have a 64 bit MM installation and I can't have a 64 bit OS in VBox. This is because hardware virtualization is disabled in the bios and Sony very kindly lock me out of it.  Mr. Angry!

---

### Post by keljaden on 2010-10-16
I have run 64 bit vm's before on my laptop.  This is the first time I have had this problem.

---

### Post by CharlesA on 2010-10-16
Did it work in 10.04?

---

