---
title: "Working directory changing"
date: 2009-12-31
forum: General Help
---

### Post by mdmann00 on 2009-12-31
Aloha All,

I am experiencing a weird issue on 9.10, 64-bit. I am accessing this problem system remotely via VNC. On the remote system, I mount a Windows share using smbfs, cd into some subdirectory within that filesystem and start doing work. The command prompt ALWAYS indicates that my current directory is the subdirectory I expect, but after a while (the time seems to vary), I notice that commands aren't working properly anymore (for example, I execute bash scripts that are manipulating files in what I think is my working directory, but I get results that indicate I am not where I am supposed to be). If I do an ls, the output suggests I am some four or five directories up in the filesystem, even though I never requested a directory change. If I do a pwd, though, it indicates I am still where I expected to be (what the command prompt indicates is my current directory). If I do 'cd `pwd`' I get taken back to the directory I'm supposed to be in. It isn't persistent, though.

The local system does not behave this way, though, and it is the same version of Ubuntu at the same update level. Current working directories don't change on their own. This leads me to believe that it is either a VNC issue or an smbfs issue. I've not been able to find information to suggest anyone else is having this problem, and I have no idea what to do to troubleshoot it since it appears to be related to no particular action on my part.

Has anyone seen this, heard of this, or have any ideas about what might be happening?

Thanks in advance for any help.

---

### Post by xifer on 2009-12-31
Can only suggest looking for dodgy symbolic links in the directory structure.
Also have you done a low level file system check in case of corruption?

---

### Post by mdmann00 on 2010-01-01
Thank you for the response, xifer. Unfortunately, there are no symbolic links in any of the affected directories. I have not done a filesystem check of that filesystem. I can't as I don't have administrative access to that filesystem.

---

### Post by xifer on 2010-01-01
> **mdmann00 said:**
> Thank you for the response, xifer. Unfortunately, there are no symbolic links in any of the affected directories. I have not done a filesystem check of that filesystem. I can't as I don't have administrative access to that filesystem.

Only other thing is could it be related to spaces in directory names?  I couldn't account for this behaviour otherwise. Need to study also exactly what commands etc you issue when you are connected and the nfs is mounted.  Sometimes you can stare at something for hours and not see the obvious.

---

### Post by iTrascurato on 2010-01-01
> **xifer said:**
> Only other thing is could it be related to spaces in directory names?  I couldn't account for this behaviour otherwise. Need to study also exactly what commands etc you issue when you are connected and the nfs is mounted.  Sometimes you can stare at something for hours and not see the obvious.

Yeah... 

Can the OP post some example commands and outputs?

---

### Post by nixxin on 2010-02-25
I am experiencing exactly the same thing. I first thought it was related to my setup (Ubuntu running on a VMware virtual machine with shell accessed via "screen"). The problem might be related to smbfs as it in my case only appears when the current working directory is on a windows share. The working directory changes suddenly and unexpectedly. It happens both in the middle of a running python script (the script fails as the directories become unavailable) and during a normal interactive shell session. Strangely pwd shows the name of the expected directory while ls lists the contents of a directory some levels higher. No spaces in the directory names. It does not seem to be related to any external reasons (network problems or activity on the host machine).

---

