---
title: "shmget issue"
date: 2010-02-23
forum: General Help
---

### Post by Zaglamir on 2010-02-23
Hi all,

I've recently switched over to Ubuntu (9.10 on a secondary partition with Windows 7) in order to facilitate analysis of particle accelerator data. I've begun to dig into this, and as I've done so I've run into many issues. So far, I've been able to solve all of them by digging through your archives here, but this one has stumped both myself and my mentor. 

We are attempting to run a compiler called "doit" which will take .evt files (from the DAQ) and turn them into .rz files (histogram files). Whenever I run this compiler (which I have compared to a working version of the code, so I know this must be a local machine issue) it comes up with this:

zach@MacClelland:~/npdg/jan10/rply$ ./doit
shmget: No such file or directory
 ***** HLIMAP Error     2 mapping memory JAN1

and from there, starts to compile but ends with a secondary error which comes from the fact that it can't find the file its supposed to be compiling in the shared memory.

From what I can tell, shmget is a shared memory access program. Which I can't seem to locate or debug or anything within my machine. I've searched across the web, but so far have had little success. This is pretty much a stock version of Ubuntu (just installed and added the data and analyzer as well as a single shared object library).

Any help you can offer would be fantastic.

Cheers,

Zach

EDIT: Also, if you could... please also consider that I am just now learning anything about Ubuntu and working within Terminals. I've done little programming and whatnot... so I'm definitely a noob. So, any help that could be translated into 4 year old speak would be great as well. Thanks.

---

### Post by lloyd_b on 2010-02-23
Typically, a file is specified and then passed through the ftok() function to generate a key value to be used with shmget().  What seems to be happening is that the particular file required to generate this key doesn't exist on the machine your working on, hence "No such file or directory".

If you have access to the source code for the program (doit), try looking through it for the call to ftok(), and see what file it's referencing, and then create a file of that name in that directory (the contents of the file are irrelevant).

Lloyd B.

---

### Post by Zaglamir on 2010-02-23
Hi Lloyd,

Thanks for your time and input. I've looked through the doit code and it has no reference to a ftok(). 

I had a gentleman suggest that I need to run an "ldconfig" but I'm not exactly sure what that is (forgive the ignorance; this is quite different for me... I'm a child of Windows and Flashy GUIs). Could this be a possible solution to the memory issue? After I finish these few tasks in Windows that I need to accomplish, I will run back over to my Ubuntu and post the source code for do it in here.

Cheers,

Zach


EDIT: Source Code
> 
#
#
./p535_cond.com # setup conditon table
./replay<<replay.eof
@p535.spec
next [file_location].evt
begin
wrt [write_location].rz all
quit
replay.eof

---

### Post by lloyd_b on 2010-02-24
> **Zaglamir said:**
> Hi Lloyd,

Thanks for your time and input. I've looked through the doit code and it has no reference to a ftok(). 

I had a gentleman suggest that I need to run an "ldconfig" but I'm not exactly sure what that is (forgive the ignorance; this is quite different for me... I'm a child of Windows and Flashy GUIs). Could this be a possible solution to the memory issue? After I finish these few tasks in Windows that I need to accomplish, I will run back over to my Ubuntu and post the source code for do it in here.

Cheers,

Zach


'ldconfig' is a utility that lets the system that handles shared libraries know where various shared libraries are located.  You can try running "sudo ldconfig" in a terminal window and see if it makes any difference ('ldconfig' needs to be run as root, hence the 'sudo'), but I'm a bit skeptical that this will solve your problem (a failure to find a shared library will generate a different error message).

Your "source code" is something that I don't recognize.  What I was suggesting you look at was the source code for whichever program is trying to execute the shmget() (./p535_cond.com or ./replay is my best guess).

What I think is happening is that the two programs above need to use a shared memory segment to exchange data, and the initial programmer decided to us a "key file" to ensure that they both use the same key for the segment.  He *should* have documented which file was used for that purpose (but probably didn't because he thought he'd be the only one ever running it).

All I can suggest is asking around and see if you can find the person who originally wrote the code.  Or check to see if there's any documentation, and dig through it for a sentence like "you must have a file named xxx in order for this to work".

Lloyd B.

---

### Post by gmargo on 2010-02-24
"No such file or directory" is an **ENOENT** error.

**shmget(2)** is a system call, not a command.  See the man page for a list of error codes that **shmget(2)** can return; for ENOENT it says:

```

ENOENT      No segment exists for the given key, and IPC_CREAT was not specified.

```

---

### Post by Zaglamir on 2010-02-25
> **gmargo said:**
> "No such file or directory" is an **ENOENT** error.

**shmget(2)** is a system call, not a command.  See the man page for a list of error codes that **shmget(2)** can return; for ENOENT it says:

```

ENOENT      No segment exists for the given key, and IPC_CREAT was not specified.

```


I'm sorry, I guess I don't understand what Enoent is. Could you re-explain in a way that is more suitable for Linux idiots? I've literally been using any for of linux for all of a week and previous to this was a completely windows dependent user. Sorry.

Zach

---

### Post by gmargo on 2010-02-25
> **Zaglamir said:**
> I'm sorry, I guess I don't understand what Enoent is. Could you re-explain in a way that is more suitable for Linux idiots? I've literally been using any for of linux for all of a week and previous to this was a completely windows dependent user. Sorry.

Zach

This is basic C programming for a POSIX api, not particulary tied to Linux or Windows.  I assume your compiler is written in C.

C programs make system calls; when a system call fails typically it returns a -1 and sets the global **errno** variable to a numerical code that indicates the specific type of error.  Rather than printing the number (which would be 2 in this case), those numbers are translated into a descriptive string which is printed instead (which would be "No such file or directory" in this case.)

The **errno(3)** man page describes the error codes. These error numbers are defined in _/usr/include/errno.h_.  On Linux, if you follow the chain of includes from errno.h, you will ultimately arrive at /_usr/include/asm-generic/errno-base.h_ and _/usr/include/asm-generic/errno.h_.  You can see the default English error strings in the comments of those files.  The **errno-base.h** file has the **ENOENT** definition.

Your program at some point is calling the **shmget(3)** system call, failing, and then printing this error message.  It is probably printing the error string through one of the error string printing functions described in **err(3)**, **error(3)**, or **strerror(3)**.

---

### Post by gauravislucky on 2012-09-12
> **lloyd_b said:**
> 'ldconfig' is a utility that lets the system that handles shared libraries know where various shared libraries are located.  You can try running "sudo ldconfig" in a terminal window and see if it makes any difference ('ldconfig' needs to be run as root, hence the 'sudo'), but I'm a bit skeptical that this will solve your problem (a failure to find a shared library will generate a different error message).

Your "source code" is something that I don't recognize.  What I was suggesting you look at was the source code for whichever program is trying to execute the shmget() (./p535_cond.com or ./replay is my best guess).

What I think is happening is that the two programs above need to use a shared memory segment to exchange data, and the initial programmer decided to us a "key file" to ensure that they both use the same key for the segment.  He *should* have documented which file was used for that purpose (but probably didn't because he thought he'd be the only one ever running it).

All I can suggest is asking around and see if you can find the person who originally wrote the code.  Or check to see if there's any documentation, and dig through it for a sentence like "you must have a file named xxx in order for this to work".

Lloyd B.


Thanks a ton Lloyd...!!! even i face the same problem....but finally happy to got rid of it...

---

