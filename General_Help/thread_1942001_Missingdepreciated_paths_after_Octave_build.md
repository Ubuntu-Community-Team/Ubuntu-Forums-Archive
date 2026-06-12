---
title: "Missing/depreciated paths after Octave build"
date: 2012-03-16
forum: General Help
---

### Post by dwdarkstar on 2012-03-16
Hello, I compiled Octave 3.6.1 in my 10.04 platform, however when I run Octave there is a sizeable list of errors pertaining to missing paths for the various basic call functions within Octave.  Stranger still is that it's apparently missing them repeatedly for two fairly outdated versions of Octave, 3.0 and 3.0.5  ...?

Before building 3.6.1 from source I installed Octave 3.2 via apt-get but got the exact same errors regarding missing paths ??

What's going on here???  See post build terminal output below.  Thanxs!!

```
Octave successfully built.  Now choose from the following:

   ./run-octave    - to run in place to test before installing
   make check      - to run the tests
   make install    - to install (PREFIX=/usr/local)

make[3]: Entering directory `/home/farstar/octave-3.6.1'
Makefile:2486: warning: overriding commands for target `check'
Makefile:2077: warning: ignoring old commands for target `check'
make[3]: Nothing to be done for `install-exec-am'.
/bin/mkdir -p /usr/local/share/octave/site/m /usr/local/share/octave/site/api-v48+/m /usr/local/share/octave/3.6.1/site/m /usr/local/lib/octave/site/oct/x86_64-unknown-linux-gnu /usr/local/lib/octave/site/oct/api-v48+/x86_64-unknown-linux-gnu /usr/local/lib/octave/3.6.1/site/oct/x86_64-unknown-linux-gnu /usr/local/libexec/octave/site/exec/x86_64-unknown-linux-gnu /usr/local/libexec/octave/api-v48+/site/exec/x86_64-unknown-linux-gnu /usr/local/libexec/octave/3.6.1/site/exec/x86_64-unknown-linux-gnu
test -z "/usr/local/include/octave-3.6.1/octave" || /bin/mkdir -p "/usr/local/include/octave-3.6.1/octave"
 /usr/bin/install -c -m 644 config.h '/usr/local/include/octave-3.6.1/octave'
test -z "/usr/local/share/octave/3.6.1/etc" || /bin/mkdir -p "/usr/local/share/octave/3.6.1/etc"
 /usr/bin/install -c -m 644 NEWS '/usr/local/share/octave/3.6.1/etc'
make[3]: Leaving directory `/home/farstar/octave-3.6.1'
make[2]: Leaving directory `/home/farstar/octave-3.6.1'
make[1]: Leaving directory `/home/farstar/octave-3.6.1'

farstar@go-bot:~/octave-3.6.1$ ./run-octave

GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

warning: addpath: /usr/local/share/octave/site-m: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/physicalconstants-0.1.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/linear-algebra-1.0.7: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/testfun: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/test: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/graceplot-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/graceplot-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/io-1.0.8: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/general-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/general-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/3.0.5/oct/x86_64-pc-linux-gnu: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/specfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/finance: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/quaternion: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/audio: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/elfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/time: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/path: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/special-matrix: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/tests: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/models: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/distributions: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/strings: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/startup: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/polynomial: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/plot: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/set: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/linear-algebra: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/sparse: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/general: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/signal: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/io: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/testfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/hinf: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/system: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/obsolete: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/util: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/image: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/optimization: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/pkg: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/deprecated: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/geometry: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/miscellaneous: No such file or directory
octave:1> exit

error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found

farstar@go-bot:~/octave-3.6.1$

```

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> Hello, I compiled Octave 3.6.1 in my 10.04 platform, however when I run Octave there is a sizeable list of errors pertaining to missing paths for the various basic call functions within Octave.  Stranger still is that it's apparently missing them repeatedly for two fairly outdated versions of Octave, 3.0 and 3.0.5  ...?

Before building 3.6.1 from source I installed Octave 3.2 via apt-get but got the exact same errors regarding missing paths ??

What's going on here???  See post build terminal output below.  Thanxs!!

It looks like you might have an old configuration file (like ~/.octaverc) leftover from a previous version of octave somewhere in octaves default path that is being run at start up.

Did you uninstall the 3.2 package using "apt-get remove" or "apt-get purge"?
"apt-get remove" can leave configuration files for the program you are uninstalling but "apt-get purge" will remove them as well.

Have you ever built any other versions of octave from source?
If you did and you installed them did you uninstall them (make uninstall) before building and running octave 3.6.1?

Try running this command and post the result here.
```
octave --verbose
```
This will make octave give more detailed information about what it its doing and may show what file(s) are causing these error messages.

---

### Post by dwdarkstar on 2012-03-16
Thanks arclance, i did not run apt-get purge, but it seems like the issue is with some previous version.  i don't recall if i built octave from source previously... but here is the output from octave --verbose

```
farstar@go-bot:~$ octave --verbose
GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

executing commands from /usr/local/share/octave/site/m/startup/octaverc ... done.
executing commands from /usr/local/share/octave/3.6.1/m/startup/octaverc ... done.
executing commands from /home/farstar/.octaverc ... warning: addpath: /usr/local/share/octave/site-m: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/physicalconstants-0.1.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/linear-algebra-1.0.7: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/testfun: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/test: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/graceplot-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/graceplot-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/io-1.0.8: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/general-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/general-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/3.0.5/oct/x86_64-pc-linux-gnu: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/specfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/finance: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/quaternion: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/audio: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/elfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/time: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/path: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/special-matrix: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/tests: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/models: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/distributions: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/strings: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/startup: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/polynomial: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/plot: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/set: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/linear-algebra: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/sparse: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/general: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/signal: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/io: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/testfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/hinf: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/system: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/obsolete: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/util: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/image: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/optimization: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/pkg: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/deprecated: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/geometry: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/miscellaneous: No such file or directory
done.

octave:1>

```

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> Thanks arclance, i did not run apt-get purge, but it seems like the issue is with some previous version.  i don't recall if i built octave from source previously... but here is the output from octave --verbose

```

[COLOR=Red]executing commands from /home/farstar/.octaverc[/COLOR] ... warning: addpath: /usr/local/share/octave/site-m: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/physicalconstants-0.1.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/linear-algebra-1.0.7: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/testfun: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/test: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/graceplot-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/graceplot-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/io-1.0.8: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/general-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/general-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/3.0.5/oct/x86_64-pc-linux-gnu: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/specfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/finance: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/quaternion: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/audio: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/elfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/time: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/path: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/special-matrix: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/tests: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/models: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/distributions: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/strings: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/startup: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/polynomial: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/plot: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/set: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/linear-algebra: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/sparse: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/general: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/signal: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/io: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/testfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/hinf: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/system: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/obsolete: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/util: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/image: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/optimization: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/pkg: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/deprecated: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/geometry: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/miscellaneous: No such file or directory
done.

octave:1>

```
Yes you have obsolete entries in your ~/.octaverc (user configuration file) leftover from some previous version.  
--verbose let me see which config file had the obsolete entries so this should be easy to fix.

Looking at the error messages it looks like it is still trying to load some old Octave-Forge packages that have been uninstalled.
If you ever installed any .deb packages that installed octave packages make sure you have purged them and not removed them.

If you post the contents of your ~/.octaverc ([COLOR=Red][COLOR=Black]/home/farstar/.octaverc) here I will post a fixed version for you.[/COLOR]
[/COLOR]

---

### Post by dwdarkstar on 2012-03-16
Thanks arclance, let me know if this is what you need:

```


farstar@go-bot:~$ more .octaverc

## Begin savepath auto-created section, do not edit
  path ('.:/home/farstar/Desktop/Graduate/Courses/Differential Equations:/usr/lo
cal/share/octave/site-m:/usr/share/octave/packages/3.0/physicalconstants-0.1.7:/
usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32:/us
r/share/octave/packages/3.0/linear-algebra-1.0.7:/usr/share/octave/packages/3.0/
integration-1.0.7/testfun:/usr/share/octave/packages/3.0/integration-1.0.7/test:
/usr/share/octave/packages/3.0/integration-1.0.7:/usr/lib/octave/packages/3.0/gr
aceplot-1.0.7/x86_64-pc-linux-gnu-api-v32:/usr/share/octave/packages/3.0/gracepl
ot-1.0.7:/usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32:/usr/
share/octave/packages/3.0/io-1.0.8:/usr/lib/octave/packages/3.0/general-1.0.7/x8
6_64-pc-linux-gnu-api-v32:/usr/share/octave/packages/3.0/general-1.0.7:/usr/lib/
octave/3.0.5/oct/x86_64-pc-linux-gnu:/usr/share/octave/3.0.5/m:/usr/share/octave
/3.0.5/m/specfun:/usr/share/octave/3.0.5/m/finance:/usr/share/octave/3.0.5/m/qua
ternion:/usr/share/octave/3.0.5/m/audio:/usr/share/octave/3.0.5/m/elfun:/usr/sha
re/octave/3.0.5/m/time:/usr/share/octave/3.0.5/m/path:/usr/share/octave/3.0.5/m/
special-matrix:/usr/share/octave/3.0.5/m/statistics:/usr/share/octave/3.0.5/m/st
atistics/tests:/usr/share/octave/3.0.5/m/statistics/models:/usr/share/octave/3.0
.5/m/statistics/base:/usr/share/octave/3.0.5/m/statistics/distributions:/usr/sha
re/octave/3.0.5/m/strings:/usr/share/octave/3.0.5/m/startup:/usr/share/octave/3.
0.5/m/polynomial:/usr/share/octave/3.0.5/m/plot:/usr/share/octave/3.0.5/m/set:/u
sr/share/octave/3.0.5/m/linear-algebra:/usr/share/octave/3.0.5/m/sparse:/usr/sha
re/octave/3.0.5/m/general:/usr/share/octave/3.0.5/m/signal:/usr/share/octave/3.0
.5/m/io:/usr/share/octave/3.0.5/m/testfun:/usr/share/octave/3.0.5/m/control:/usr
/share/octave/3.0.5/m/control/hinf:/usr/share/octave/3.0.5/m/control/system:/usr
/share/octave/3.0.5/m/control/obsolete:/usr/share/octave/3.0.5/m/control/util:/u
sr/share/octave/3.0.5/m/control/base:/usr/share/octave/3.0.5/m/image:/usr/share/
octave/3.0.5/m/optimization:/usr/share/octave/3.0.5/m/pkg:/usr/share/octave/3.0.
5/m/deprecated:/usr/share/octave/3.0.5/m/geometry:/usr/share/octave/3.0.5/m/misc
ellaneous');
## End savepath auto-created section

farstar@go-bot:~$ 

```

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> Thanks arclance, let me know if this is what you need:

Yes that is what I needed, here is a corrected version.
Please backup your .conkyrc first just in case there is something important  buried in that long list I missed and then change it so it contains  this.
```

## Begin savepath auto-created section, do not edit
  path ('.:/home/farstar/Desktop/Graduate/Courses/Differential Equations');
## End savepath auto-created section

```All that is left is what looks like your personal octave function folder, everything else looks like it is obsolete.
Those should have been removed when that version was uninstalled but were not for some reason (they should not really be in ~/.octaverc at all since that is the user  config file and some of those are core octave directories).

Here is a more readable list of everything I removed.
```

/usr/local/share/octave/site-m
/usr/share/octave/packages/3.0/physicalconstants-0.1.7
/usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32
/usr/share/octave/packages/3.0/linear-algebra-1.0.7
/usr/share/octave/packages/3.0/integration-1.0.7/testfun
/usr/share/octave/packages/3.0/integration-1.0.7/test
/usr/share/octave/packages/3.0/integration-1.0.7
/usr/lib/octave/packages/3.0/graceplot-1.0.7/x86_64-pc-linux-gnu-api-v32
/usr/share/octave/packages/3.0/graceplot-1.0.7
/usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32
/usr/share/octave/packages/3.0/io-1.0.8
/usr/lib/octave/packages/3.0/general-1.0.7/x86_64-pc-linux-gnu-api-v32
/usr/share/octave/packages/3.0/general-1.0.7
/usr/lib/octave/3.0.5/oct/x86_64-pc-linux-gnu
/usr/share/octave/3.0.5/m
/usr/share/octave/3.0.5/m/specfun
/usr/share/octave/3.0.5/m/finance
/usr/share/octave/3.0.5/m/quaternion
/usr/share/octave/3.0.5/m/audio
/usr/share/octave/3.0.5/m/elfun
/usr/share/octave/3.0.5/m/time
/usr/share/octave/3.0.5/m/path
/usr/share/octave/3.0.5/m/special-matrix
/usr/share/octave/3.0.5/m/statistics
/usr/share/octave/3.0.5/m/statistics/tests
/usr/share/octave/3.0.5/m/statistics/models
/usr/share/octave/3.0.5/m/statistics/base
/usr/share/octave/3.0.5/m/statistics/distributions
/usr/share/octave/3.0.5/m/strings
/usr/share/octave/3.0.5/m/startup
/usr/share/octave/3.0.5/m/polynomial
/usr/share/octave/3.0.5/m/plot
/usr/share/octave/3.0.5/m/set
/usr/share/octave/3.0.5/m/linear-algebra
/usr/share/octave/3.0.5/m/sparse
/usr/share/octave/3.0.5/m/general
/usr/share/octave/3.0.5/m/signal
/usr/share/octave/3.0.5/m/io
/usr/share/octave/3.0.5/m/testfun
/usr/share/octave/3.0.5/m/control
/usr/share/octave/3.0.5/m/control/hinf
/usr/share/octave/3.0.5/m/control/system
/usr/share/octave/3.0.5/m/control/obsolete
/usr/share/octave/3.0.5/m/control/util
/usr/share/octave/3.0.5/m/control/base
/usr/share/octave/3.0.5/m/image
/usr/share/octave/3.0.5/m/optimization
/usr/share/octave/3.0.5/m/pkg
/usr/share/octave/3.0.5/m/deprecated
/usr/share/octave/3.0.5/m/geometry
/usr/share/octave/3.0.5/m/miscellaneous

```

---

### Post by dwdarkstar on 2012-03-16
Thanks again arclance.  That cleaned up a lot of the errors, however now i'm getting this:

```

farstar@go-bot:~$ octave

GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

>>>error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: evaluating argument list element number 1
error: called from:
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 10, column 27
error: evaluating argument list element number 4
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 5, column 13

octave:1> exit
error: feval: function `unimplemented' not found

farstar@go-bot:~$




```

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> Thanks again arclance.  That cleaned up a lot of the errors, however now i'm getting this:

```

farstar@go-bot:~$ octave

GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

>>>error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: evaluating argument list element number 1
error: called from:
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 10, column 27
error: evaluating argument list element number 4
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 5, column 13

octave:1> exit
error: feval: function `unimplemented' not found

farstar@go-bot:~$

```
That was there before just hidden by the large error list.
> **dwdarkstar said:**
> 
```

octave:1> exit

error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found

farstar@go-bot:~/octave-3.6.1$

```
Please do these two things to help me try to pin down this problem.
First run
```
octave --verbose
```again but this time before you exit octave run
```
path
```to get the current Octave search path so I can compare it to my working 3.6.1 install.

You can also try running "make check" where you built octave (the same directory where you ran "make") to run some self tests on the octave you built.
Don't be suprised if you get some failed tests that is normal (I have never had no failures, some tests are expected to fail on certain processor architectures).
Let me see the result so I can determine if I those failure could be related to this error.

Post what you get here so I can see it.

---

### Post by dwdarkstar on 2012-03-16
OK arclance, here is the first bit:

```
farstar@go-bot:~$ octave --verbose
GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

executing commands from /usr/local/share/octave/site/m/startup/octaverc ... done.
executing commands from /usr/local/share/octave/3.6.1/m/startup/octaverc ... done.
executing commands from /home/farstar/.octaverc ... done.

octave:1> path

Octave's search path contains the following directories:

.
/home/farstar/Desktop/Graduate/Courses/Differential Equations

octave:2> 

```

When starting qtoctave i get this:

```
Starting Octave...
GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

>>>error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found
error: evaluating argument list element number 1
error: called from:
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 10, column 27
error: evaluating argument list element number 4
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 5, column 13
 path

Octave's search path contains the following directories:

.
/usr/share/qtoctave/scripts_octave
/home/farstar/Desktop/Graduate/Courses/Differential Equations

>>>error: feval: function `unimplemented' not found
error: evaluating argument list element number 1
error: called from:
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 10, column 27
error: evaluating argument list element number 4
error:   /usr/share/qtoctave/scripts_octave/_ide_reload_variables_list.m at lin
e 5, column 13

```

the make check results in this:

```
Summary:

  PASS   9993
  FAIL      0

There were 3 expected failures (see fntests.log for details).

Expected failures are known bugs.  Please help improve Octave
by contributing fixes for them.

There were 169 skipped tests (see fntests.log for details).
Skipped tests are features that are disabled in this version of Octave
because the needed libraries were not present when Octave was built.

243 (of 803) .m files have no tests.

38 (of 154) .cc files have no tests.

Please help improve Octave by contributing tests for
these files (see the list in the file fntests.log).

make[1]: Leaving directory `/home/farstar/octave-3.6.1/test'

```

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> OK arclance, here is the first bit:

```

octave:1> path

Octave's search path contains the following directories:

.
/home/farstar/Desktop/Graduate/Courses/Differential Equations

octave:2> 

```When starting qtoctave i get this:

First don't use qtoctave when testing I am not familiar with it and it just adds more things that can go wrong.

You are missing the path for _**EVERY**_ part of octave so they are not loading.
I read up on path and I think I figured out why it is not working.
The issue is with the way you are setting path in you .octaverc.
At some point you must have run
```
&#8212; Function File:  **savepath** (file)
Save the portion of the current function search path, that is not set during Octave's initialization process, to file.  If file is omitted, ~/.octaverc is used.  If successful, savepath returns 0.  
```which saved your current path configuration to your .octaverc.
Howver because it saved it in the format 
```
path ('.:/home/farstar/Desktop/Graduate/Courses/Differential Equations');
```it is using _**ONLY**_ the paths defined in your .octaverc and no others.
```
&#8212; Built-in Function:  **path** (...)
Modify or display Octave's load path.          
If nargin and nargout are zero, display the elements of Octave's load path in an easy to read format.          
If nargin is zero and nargout is greater than zero, return the current load path.          
If nargin is greater than zero, concatenate the arguments, separating them with pathsep.  Set the internal search path to the result and return it.          
No checks are made for duplicate elements.  
```This prevented octave from automatically setting the correct builtin function paths at startup when you changed versions.

If you change your .octaverc to contain only this it should work.
```
addpath '/home/farstar/Desktop/Graduate/Courses/Differential Equations'
```This will add your personal directory to whatever path octave sets at startup instead of what you were doing before.

For reference my path looks like this with my personal directory removed.
```

/usr/local/lib/octave/3.6.1/site/oct/x86_64-unknown-linux-gnu
/usr/local/lib/octave/site/oct/api-v48+/x86_64-unknown-linux-gnu
/usr/local/lib/octave/site/oct/x86_64-unknown-linux-gnu
/usr/local/share/octave/3.6.1/site/m
/usr/local/share/octave/site/api-v48+/m
/usr/local/share/octave/site/m
/usr/local/share/octave/site/m/startup
/usr/local/lib/octave/3.6.1/oct/x86_64-unknown-linux-gnu
/usr/local/share/octave/3.6.1/m
/usr/local/share/octave/3.6.1/m/general
/usr/local/share/octave/3.6.1/m/pkg
/usr/local/share/octave/3.6.1/m/miscellaneous
/usr/local/share/octave/3.6.1/m/sparse
/usr/local/share/octave/3.6.1/m/plot
/usr/local/share/octave/3.6.1/m/linear-algebra
/usr/local/share/octave/3.6.1/m/io
/usr/local/share/octave/3.6.1/m/elfun
/usr/local/share/octave/3.6.1/m/polynomial
/usr/local/share/octave/3.6.1/m/signal
/usr/local/share/octave/3.6.1/m/special-matrix
/usr/local/share/octave/3.6.1/m/help
/usr/local/share/octave/3.6.1/m/audio
/usr/local/share/octave/3.6.1/m/time
/usr/local/share/octave/3.6.1/m/specfun
/usr/local/share/octave/3.6.1/m/testfun
/usr/local/share/octave/3.6.1/m/prefs
/usr/local/share/octave/3.6.1/m/strings
/usr/local/share/octave/3.6.1/m/deprecated
/usr/local/share/octave/3.6.1/m/set
/usr/local/share/octave/3.6.1/m/geometry
/usr/local/share/octave/3.6.1/m/image
/usr/local/share/octave/3.6.1/m/path
/usr/local/share/octave/3.6.1/m/optimization
/usr/local/share/octave/3.6.1/m/statistics
/usr/local/share/octave/3.6.1/m/statistics/tests
/usr/local/share/octave/3.6.1/m/statistics/base
/usr/local/share/octave/3.6.1/m/statistics/distributions
/usr/local/share/octave/3.6.1/m/statistics/models
/usr/local/share/octave/3.6.1/m/startup

```> **dwdarkstar said:**
> 
the make check results in this:

It does not look like there is anything wrong there.

---

### Post by dwdarkstar on 2012-03-16
Thanks so much for your help arclance!  I changed .octavert to what it needed and all is well.  I'm going to mark this solved.  Hopefully you get some beans.  Nice work!

---

### Post by arclance on 2012-03-16
> **dwdarkstar said:**
> Thanks so much for your help arclance!  I changed .octavert to what it needed and all is well.  I'm going to mark this solved.  Hopefully you get some beans.  Nice work!
Glad I could help.
Out of curiosity what are you using Octave for?

---

### Post by dwdarkstar on 2012-03-17
Image analysis pertaining to nanofabrication of thin film aluminium oxides.  The nanostructures are imaged via FESEM and various characteristics are extracted from the PNG files using matlab/octave etc.  If I could just get my hands on a good FESEM I'd have lots more pictures to analyse :)  Thanks again!

---

### Post by arclance on 2012-03-17
Sounds cool.
I started using Octave when I wrote a deconvolution for my senior research project to complete my Chemistry and Applied Physics BS degrees.
It would have taken ~48 hours to process the 20 samples from a single experiment if I had not gotten access to my schools computational cluster letting me multi-thread the process reducing the processing time to ~2 hours.
[Then I did this just because I wanted to.]("http://www.bay12forums.com/smf/index.php?topic=87196.msg2370618#msg2370618")

---

