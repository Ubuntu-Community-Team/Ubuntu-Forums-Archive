---
title: "Possible corrupt library"
date: 2009-11-10
forum: General Help
---

### Post by blackcabbage on 2009-11-10
Hi,

I think I may have a corrupt library that trashes my current session whenever I run either gmsh or paraview. is there anyway to check all the libraries they depend on/reinstall them?

I can't give too much output from my system when I run them because the xterm closes and trying to run any other programs after the 'crash' doesn't work. However, the messages I get are along the lines of:

'assertion botched'
'malloc clobbered'

and then I can't even run the simplest of command line options (ls, etc).

The problem only appears to be related to these programs as far as I can tell, but will update if any other programs give rise to  similar output.

Any help would be great.

---

### Post by Giblet5 on 2009-11-10
You can reconfigure all the packages via
```
sudo dpkg-reconfigure -a
```

That'll take a while to run, but it may fix this problem.

---

### Post by blackcabbage on 2009-11-10
Thanks for the suggestion - I've since tried reinstalling the dependencies but with no luck - the system either freezes up or breaks.

Are there any suggestions for how I could best trace the source of the error when I start up gmsh?

---

### Post by Giblet5 on 2009-11-10
> **blackcabbage said:**
> Thanks for the suggestion - I've since tried reinstalling the dependencies but with no luck - the system either freezes up or breaks.

Are there any suggestions for how I could best trace the source of the error when I start up gmsh?

Your system is unstable, based on your description. The best-case scenario is that gmsh will be as, or more, unstable.

It's like arguing over the best way to saddle a dead horse.

Focus on stabilizing the system, then revisit gmsh problems.

---

### Post by blackcabbage on 2009-11-10
But the system at large is stable. I only have problems when I start gmsh or paraview. Everything else (firefox/thunderbird/vlc/python/etc) works fine.

If there is a way I can get ltrace or the logs to display what went wrong at the time of the crash, I could probably track down the problem, however the ltrace output doesn't get written before the crash when running it with gmsh. Can I get the output to be written more regularly? ie after every n lines of output rather than at the end of it's execution?

---

### Post by Giblet5 on 2009-11-10
> **blackcabbage said:**
> But the system at large is stable. I only have problems when I start gmsh or paraview. Everything else (firefox/thunderbird/vlc/python/etc) works fine.

If there is a way I can get ltrace or the logs to display what went wrong at the time of the crash, I could probably track down the problem, however the ltrace output doesn't get written before the crash when running it with gmsh. Can I get the output to be written more regularly? ie after every n lines of output rather than at the end of it's execution?

About all you can do is start it from the command line and redirect its streams to a log file.

```
anycommand > the.log 2>&1
``` will grab the stdout and stderr streams from any command you start in the shell. Unfortunately, you can't change the command's output buffering...

If/when that doesn't work, you can grab the source and create a debug build. That implies skills that you might or might-not have, so think it over before rushing off to grab the source.

---

