---
title: "64bit strace hanging while tracing 32-bit java"
date: 2009-12-28
forum: General Help
---

### Post by gmoore777 on 2009-12-28
When running 64bit strace on 64 bit HardyHeron (or LucidLynx)
it hangs when following 32-bit java.(an Ant build process)

I've narrowed down the problem to these basic steps:

The command I run is:
export JAVA_HOME=/opt/jdk1.6.0_16_32;
strace -f -F  -e open,chdir,fchdir,fork,vfork,exit_group,execve,_exit <path_to_ant>/bin/ant -f build.xml target1;

------------------------------------------
build.xml:

<project name="main" default="target1">
<target name="target1">
    <echo message="Inside ant target of target1."/>
    <exec executable="make"  failonerror="true" dir=".">
      <arg line="-f Makefile makeTarget"/>
    </exec>
  </target>
</project>
------------------------------------------
Makefile:
makeTarget:
        @echo "Inside Makefile doing the target of makeTarget.\n"

----------------------------

If I change JAVA_HOME to a 64 bit java, then strace completes
successfully.
Otherwise it hangs, until I `kill -9` the java process.


(I don't want to use 64 bit java since we have other C code we compile that is not 64-bit-ized and that opens up another can of worms.)
----------------------------
I've searched the forums and found only one other pertinent
post about how 64 bit strace could not follow vforks, but
that has been fixed in a version of strace that is available and installed on my LucidLynx machine, and my problem exists as well on LucidLynx.
----------------------------
(I also would have posted this tothe 64 bit forum but
for some reason the "new thread" button does not appear
on that forum page for me.)
----------------------------
I'll take any ideas on how to proceed as i am at a dead end.

---

### Post by gmoore777 on 2009-12-29
I narrowed down problem a bit more.
In that above build.xml file. If I change from running `make`, to running `ls`, I get the same hanging problem.

But if I copy a 32-bit "ls" from another machine and run
that instead then strace completes successfully.

Meaning, the 64-bit strace command can't trace a 32 bit java application (ant)that spawns off 64-bit binaries.
Everything needs to be all 32-bit. (or all 64 bit)

I just logged this as a bug against strace on 64-bit hardyHeron:
[https://bugs.launchpad.net/ubuntu/+source/strace/+bug/501454](https://bugs.launchpad.net/ubuntu/+source/strace/+bug/501454)

---

