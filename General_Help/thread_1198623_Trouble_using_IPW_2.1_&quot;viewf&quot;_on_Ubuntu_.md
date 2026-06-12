---
title: "Trouble using IPW 2.1 &quot;viewf&quot; on Ubuntu 9.04"
date: 2009-06-27
forum: General Help
---

### Post by steve_akh076 on 2009-06-27
Dear Ubuntu users,

I am trying to run Image Processing Workbench (IPW 2.1, [https://www.nmepscor.org/trac/IPW/wiki/Version2.1](https://www.nmepscor.org/trac/IPW/wiki/Version2.1)) on 32-bit Ubuntu version 9.04. IPW consists of C-binaries created using a ANSI-C compiler. I am running the IPW functions from a bash shell and IDL (spawn). Everything works fine except the IPW function "viewf." This function attempts to create a bunch of directories for storing temporary files. The function exits with an error about unable to create directories due to permissions (command and start of error are given below). The IPW and working directories all have read, write and execute permissions to everyone. I cannot figure out how to set the permissions so that the IPW viewf function is able to create the required directories. Can anyone help me? This problem exists when I have the current directory set to either my ntfs or ext3 partitions.

I would really appreciate any help I can get. This sounds like it may relate to setting the permissions, so I decided to post the question here. Does anyone out there use IPW 2.1? Thanks.

Steve


Command:

viewf dem.ipw > test


Error comments (truncated):

mkdir: cannot create directory `/viewf.22823': Permission denied
/usr/local/ipw-2.1/ipw-2.1.0b3/bin/viewf: 61: cannot create /viewf.22823/horz.e: Directory nonexistent
/usr/local/ipw-2.1/ipw-2.1.0b3/bin/viewf: 62: cannot create /viewf.22823/horz.w: Directory nonexistent
/usr/local/ipw-2.1/ipw-2.1.0b3/bin/viewf: 66: cannot create /viewf.22823/sxt1: Directory nonexistent

/usr/local/ipw-2.1/ipw-2.1.0b3/aux/horizon/hor1d: ERROR:
/usr/local/ipw-2.1/ipw-2.1.0b3/bin/viewf: 69: cannot create /viewf.22823/horz.ssw: Directory nonexistent
    can't open "/viewf.22823/sxt1"
    (UNIX error is: No such file or directory)


transpose: ERROR:
    can't read basic image header
    (File: (stdin))
    (IPW error is: invalid IPW image (no header))


/usr/local/ipw-2.1/ipw-2.1.0b3/aux/horizon/hor1d: ERROR:
    can't open "/viewf.22823/sxt1"
    (UNIX error is: No such file or directory)

---

