---
title: "A couple NVIDIA driver issues"
date: 2009-08-18
forum: General Help
---

### Post by johnjust on 2009-08-18
I used the following guide to set up a shell script that would automatically update my drivers when a new kernel was installed, but it's hurting more than helping.

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

It failed the first time (gave me an error about being unable to install), but it still installed the kernel (2.6.28-13).

Then, when 2.6.28-14 came out, it failed again (same error), but still installed it.

Now, every time I try to install new applications through Synaptic, it always tries to configure those 2 kernels and gives me more errors.  However, all the applications still install.  Is there a way to remove those "failed" packages, so they don't show up anymore?

I've now completely removed that script.  If anyone knows a way to change the script so it works without errors, please share (I had some shell scripting experience in college, but nothing as in-depth as this).

For the time being, I have no problem reinstalling my drivers manually when a new kernel comes out.  Thanks for any assistance!

---

### Post by kpkeerthi on 2009-08-18
DKMS is the way to do.
[http://ubuntuforums.org/showthread.php?t=1036788]("http://ubuntuforums.org/showthread.php?t=1036788")

---

