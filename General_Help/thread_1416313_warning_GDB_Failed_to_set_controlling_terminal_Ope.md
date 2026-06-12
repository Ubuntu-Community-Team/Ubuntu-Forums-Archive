---
title: "warning: GDB: Failed to set controlling terminal: Operation not permitted"
date: 2010-02-25
forum: General Help
---

### Post by Stephen90 on 2010-02-25
I am running Ubuntu 9.10 Karmic Koala, and I am having problems with GDB.  When I attempt to debug a C program in kdbg or codeblocks, the output terminal will display this message: "warning: GDB: Failed to set controlling terminal: Operation not permitted"  I have searched quite a bit and I have not found a fix that works.  Anybody have any fixes or ideas?  Thanks for your help.
Stephen

I am running the latest stable versions of all my software supplied by the ubuntu repositories
My system meets all the dependencies for KDBG and Codeblocks
I am running gnome, but the KDE files installed by Synaptic are version 3.5.10
I have KDBG version 2.1.1
I have GDB version 7.0-0ubuntu1
I have CodeBlocks 8.02-0ubuntu4

If anybody needs any more information in order to give ideas or knowledge on how to fix this just let me know

Thanks

---

### Post by Stephen90 on 2010-03-23
This has been posted for 3 weeks with over 209 views and 0 responses.  I'm reporting this to ubuntu as a bug.

---

### Post by Stephen90 on 2010-03-24
I wish to report this bug, but I am currently having trouble finding the package causing the issue, and I would like anyone's advice/assistance that can help.
I **KNOW** this issue must be affecting other users because:

I normally the gnome desktop environment, so last night I figured I would try running KDBG's "native" desktop environment, KDE.  

I booted 'Kubuntu' 9.10 from the live CD i downloaded/burned, ran the software manager application, and installed KDBG, and all of its dependencies/suggested packages.  I wrote a short simple program, compiled it using the -g flag (to create debugging info for GDB) and opened it using KDBG.  

The 'Program Output' window in KDBG gave me the same warning/error:
"warning: GDB: Failed to set controlling terminal: Operation not permitted"
this was when running from the Kubuntu 9.10 live CD so this must be a 'Distribution Wide' issue on some package that is installed with the operating system.


Anybody have any clues as to which packages are faulty/any fixes for the problem?

---

### Post by Stephen90 on 2010-03-24
P.S. I am running on the i386 architecture

I am currently downloading previous versions of ubuntu: 9.04 and 8.10 to test if the the same error/warning occurs.

---

### Post by OntO on 2010-03-27
I have the same problem:

[IMG]http://i070.radikal.ru/1003/d6/030bb31b7eb6.png[/IMG]
[IMG]http://s003.radikal.ru/i203/1003/af/efd41dd16d37.png[/IMG]

---

### Post by ArKanjo on 2010-04-10
Same on Kubuntu 9.10 and 10.4beta1
using codeblocks and netbeans

started when upgrade from GDB 6.8 to 7.0 and 7.1 ...

---

### Post by pbrane on 2010-04-10
I assume gdb runs from the command line in a terminal? 
```

$ gdb progname

```
Does this only happen in an IDE. I mainly use gdb from the command line so I won't be much help. I tried using Nemiver ( which uses gdb as a back end ) and it ran fine.

---

### Post by v.cecchetto on 2010-05-04
Other threads on same topic:

[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005)

[http://forums.netbeans.org/topic15797.html](http://forums.netbeans.org/topic15797.html)

In Netbeans:

Project > Properties > Run > Console Type > External Terminal

for information you can have far less problem in Netbeans if you disable automatic profiling (especially if you are using threads):

Select the project > Click Dx > Properties > Profile > Show profiling indicators during run (uncheck)

---

### Post by Stephen90 on 2010-05-07
This also occurs in Ubuntu 10.04.  I have recently tested this bug in both KDE and Gnome, and I have come to the conclusion that this is an issue between the GDM and KDM display managers.  Although I have not extensively tested this, I did not get the warning message when running KDE with KDM.  Only in Gnome with GDM or KDE with GDM.

To avoid this warning you could just completely switch display managers, or somehow configure GDM and KDM to play nicely and run Gnome programs with GDM and KDE programs with KDM (or at least the debugging programs that seem to be having issues).  

Also, as an alternative to those of you who don't with to get too deeply involved with KDM and GDM settings and scripts, DDD (Data Display Debugger) seemed to function properly and did not display any "terminal control" warnings.

---

### Post by crypticlynx on 2010-09-13
I installed KDE logged out and started a KDE session. Also I used:
```
 sudo dpkg-reconfigure gdm
```
to change to kdm still I'm getting the same "warning" message as before using the Code::Blocks IDE. The console output also still doesn't work :-(
Any idea how to solve this problem? 

PS: I also tried to downgrade to gdb 6.8, which got rid of the warning message, but the console output was still missing...

---

### Post by hikui on 2010-12-31
Same problem on Kubuntu 10.10
using codeblock and netbeans.

---

### Post by abraxas334 on 2011-03-23
My system:
Ubuntu 10.10
gdb 7.2
netbeans 6.9

I recently upgraded from Netbeans 6.8 to 6.9. I already had the warning in 6.8 but debugging worked ok

Now using the same project, in the upgraded version still runs, but debugging no longer works. 
I made a test program and it seems to have something to do with command line arguments, can anyone else confirm this? 
A program without commandline arguments is still debuggable even with the warning appearing, but as soon as I trying to do something like this, it cannot run/debug anymore. It behaves as if there were no commandline arguments.
extract of my main.cpp

[PHP]
  if(argc!=4)
    {
        std::cout<<
                "************************Warning********************\n"
                "You are not using the right number of  arguments try: \n"
                "./executable configFile.dat TASKID ChainLength\n"
                "*******This siumulation will now terminate*********"<<std::endl;
        return(EXIT_FAILURE);
    }
    else
    {
       //run the program
    }


[/PHP]
arguments are right because the program still runs fine in runmode!
Has anyone else observed this? Is there a fix? 
One of the suggestions I found was playing with the output window/terminal regardless which combination I use I still encounter the same problem!

---

### Post by hamilleton on 2012-05-10
My environment:
Ubuntu 12.04
GDB 7.3
Code::Blocks r7955

got the same problem,
warning: GDB: Failed to set controlling terminal: Operation not permitted
anyone could help?
Thanks in previous.

---

### Post by chronop on 2012-06-08
Xubuntu 12.04
Code::Blocks 10.04

Same problem, however my console output still works so it is more of an annoyance.

---

### Post by oldos2er on 2012-06-08
Old thread closed.

---

