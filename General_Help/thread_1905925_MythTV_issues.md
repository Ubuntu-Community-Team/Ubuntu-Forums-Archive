---
title: "MythTV issues"
date: 2012-01-08
forum: General Help
---

### Post by Brian- on 2012-01-08
Hi, I am stuck installing MythTV.
I had a half installed version 022 at one point but gave up on that.
Then (stupidly?) i tried to install the Trunk Verson!
Anyway i have uninstalled these now and just installed the standard version using synaptic - 2:0.24.0
Now I can't start the backend! I get the following:

/```
usr/bin/mythbackend
2012-01-08 19:23:24.701 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2012-01-08 19:23:24.702 Using runtime prefix = /usr/local
2012-01-08 19:23:24.702 Using configuration directory = /home/brian/.mythtv
2012-01-08 19:23:24.703 Application binary version (0.24.20110505-1) does not match libraries (0.25.20101127-1)
2012-01-08 19:23:24.703 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2012-01-08 19:23:24.703 MythContext, Error: Unable to allocate MythCoreContext
2012-01-08 19:23:24.703 Application binary version (0.24.20110505-1) does not match libraries (0.25.20101127-1)
2012-01-08 19:23:24.703 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2012-01-08 19:23:24.703 Failed to init MythContext.
```I tried make distclean but it failed to.
I would appreciate any assistance you can offer please...
Thanks.
B.

Update: Still not getting anywhere! I found a post that said to run dpkg... so i did and here are the results:
 
```
dpkg -l | grep myth
rc  libmyth-0.23-0                         0.23.1+fixes26437-0ubuntu1                 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                         2:0.24.0+fixes.20110908.1de0431-0ubuntu1   Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                         2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A python library to access some MythTV features
ii  libmythes-1.2-0                        2:1.2.1-1                                  simple thesaurus library
ii  libmythtv-perl                         2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A PERL library to access some MythTV features
rc  mythbuntu-bare-client                  2.0                                        Mythbuntu Bare Client
ii  mythbuntu-common                       0.63                                       Mythbuntu application support functions
rc  mythbuntu-control-centre               0.63-0ubuntu2                              Mythbuntu Configuration Application
ii  mythbuntu-lirc-generator               0.26-0ubuntu1                              Mythbuntu Lirc Configuration Generator
ii  mythtv                                 2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (client and server)
ii  mythtv-backend                         2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (server)
ii  mythtv-backend-master                  2:0.24.0+fixes.20110908.1de0431-0ubuntu1   Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                          2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (common data)
ii  mythtv-database                        2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (database)
ii  mythtv-doc                             2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (documentation)
ii  mythtv-frontend                        2:0.24.0+fixes.20110908.1de0431-0ubuntu1   A personal video recorder application (client)
ii  mythtv-status                          0.9.3-1                                    Show the status of a MythTV backend
ii  mythtv-transcode-utils                 2:0.24.0+fixes.20110908.1de0431-0ubuntu1   Utilities used for transcoding MythTV tasks
ii  mythtvfs                               0.6.1-2                                    userspace filesystem client for MythTV
ii  mythweb                                2:0.24.0+fixes.20110908.1de0431-0ubuntu1   Web interface add-on module for MythTV
```


I think the first line is the problem?
 rc  libmyth-0.23-0                          0.23.1+fixes26437-0ubuntu1                 Common library code for  MythTV and add-on modules (runtime)

It is version 0.23 and I also have version 0.24. What does the "rc" refer to? and how do i remove version 0.23 please?

---

### Post by Brian- on 2012-01-11
Is this the wrong forum for MythTV questions?
Please help...
Thanks in advance...

---

### Post by Brian- on 2012-01-11
Ok i figured out the rc once i stopped the pipe to grep.
I have now removed the 0.23 lib.

mythbackend still says:
```
2012-01-12 12:20:36.799 Application binary version (0.24.20110505-1) does not match libraries (0.25.20101127-1)
2012-01-12 12:20:36.799 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2012-01-12 12:20:36.799 MythContext, Error: Unable to allocate MythCoreContext
2012-01-12 12:20:36.799 Application binary version (0.24.20110505-1) does not match libraries (0.25.20101127-1)
2012-01-12 12:20:36.799 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2012-01-12 12:20:36.799 Failed to init MythContext, exiting.

```So How do I do a make distclean???
as i get this:```
 sudo make distclean
make: *** No rule to make target `distclean'.  Stop.

```

---

### Post by drewdin on 2012-02-20
I am also having a bunch of MythBuntu issues, i wish I could help. I keep eating Sample Rate 32000Hz not supported.

---

