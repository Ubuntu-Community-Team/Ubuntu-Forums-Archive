---
title: "Console login fails - cannot execute -G"
date: 2011-11-11
forum: General Help
---

### Post by Carbs70 on 2011-11-11
Have been using Ubuntu for about 18 months now, although I'm far from a guru on the command line....although I do try to get my hands dirty when need arises. As I have an NVIDIA graphics card I'm forced to reinstall the drivers with every kernel or Xserver update. But recently, something unusual has started happening...

When booting into the console, or dropping into console by stopping gdm. 
I enter my ID and password....it welcomes me, tells me about last login...
Then comes up with a message something like "cannot execute -G no such file or directory", then drops back to prompting me for logon ID and password again!

I can access sudo OK...but of course can't install graphics drivers that way.... so really need to be able to login to console.

I'm not sure where to start looking to debug this one? :confused:

---

### Post by Carbs70 on 2011-11-12
OK....been spending a while reading through all the various bash scripts that I'm aware of that run when logging into console.

If anyone could inform me which scripts might be executed AFTER the system response about "Welcome xxxx last login xx-xx-xx" etc etc.... then I would be greatly appreciative.

---

### Post by Carbs70 on 2011-11-12
Sorted it myself.... after much reading I know a bit more about the Linux login process...

The problem was that in the etc/passwd file, the end of the line for my root user that should have read "/bin/bash" instead read "-G"

Not sure how on Earth that got corrupted, but glad that I've fixed it!!
NVidia drivers now installed and back to normal!

---

