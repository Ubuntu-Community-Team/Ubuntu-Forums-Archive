---
title: "Crontab"
date: 2009-10-29
forum: General Help
---

### Post by aabrego on 2009-10-29
Hi:

I'm trying to run a crontab job using a Perl script. Inside the Script the program calls for execution a C Shell script. The execution of the perl part works fine but the C Shell script does not work. I have a log file and is reads: sh:sh_gamit: command not found (where sh_gamit is my C Shell script)

Is it because I'm mixing Perl and C Shell? What I do not understand is that if I run the very same Perl script (calling the C Shell script) from a terminal windows, it works fine.

Any suggestion?

---

### Post by laceration on 2009-10-29
I have had similar problems with crontab where one script is not able call another script or program.  Cron is just a bitch, sometimes you have to rewrite a script just so it will work with cron.
You might first check to see that the path to C script is in a path statement in your crontab -- it could be that.  Something like this:
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/bin
```
The way I solved the problem was to break it into 2 scripts and have a crontab for each 1 minute apart if nec.
I did one script where I had to put it into 3 crontabs!

---

### Post by aabrego on 2009-10-29
Thanks for your help. I solved my issue. The problems was that the C Shell script had in the first line the option -f which prevented the shell to read the .cshrc file, which already contained the path for a symbolic link required by the C Shell script.

Regards,

Antonio

---

