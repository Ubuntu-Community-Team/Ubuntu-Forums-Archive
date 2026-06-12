---
title: "`GLIBC_2.11' not found (required by /bin/sh)"
date: 2010-06-13
forum: General Help
---

### Post by iWarior on 2010-06-13
Hello!

In some software (OS: Ubuntu Server) I get error:

```
`GLIBC_2.11' not found (required by /bin/sh)
```

But there is symbolic link in **/lib/** : **/lib/libc.so.6 -> libc-2.11.1.so** => as I can understand it's mean that in my system present GLIBC_2.11.1 ...

How can I fix this error?

Many thanks in advance!

---

### Post by gzarkadas on 2010-06-13
Open a terminal window (menu Applications|Accessories|Terminal) and enter the following command (it will list the dependencies of your sh executable):
```
ldd -v /bin/sh
```Then select the output text with the mouse, press Ctrl+Shift+C to copy it and paste it here.

---

### Post by iWarior on 2010-06-13
Thanks for your reply!

> **gzarkadas said:**
> Open a terminal window (menu Applications|Accessories|Terminal) 

I use Ubuntu server.

When I run this command => error:
> The program 'ldd' is currently not installed.

Now in my Ubuntu Server 9.04 I have broken libc6 2.11 from Ubuntu Server 10.4 (now i know, that it was bad idea install it on 9.04)... When I try downgrade (with aptitude) to normal jaunty-version of libc6 -> error from my 1st topic massage.

Now my aim - downgrade libc6 to normal for Ubuntu 9.04 and upgrade my OS to 9.10 and then to 10.4

---

### Post by gzarkadas on 2010-06-14
I believe ldd is part of glib, thus you should have it; but I didn't make a server install before and maybe I am wrong here. Anyway, I don't know how you installed your new libc, but if your /bin/sh is broken, chances are low that you will manage to do this task through aptitude. You may try:

    * To download the jaunty libc deb for your architecture from [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/) and perform a local install using dpkg.

    * To completely uninstall the package directly using dpkg with the appropriate force options and then install the older version. 

Use `man dpkg' to browse available options. If anything of this works, then you can proceed to the upgrades.

Another option, if you have trouble to fix this error, which I haven't yet tried -**be warned**- but I believe is sound, is to perform a clean install of Lucid + a copy of your config/data as follows:

1. Backup everything in these directories (lets call it backup #1):[INDENT]/home
    /etc
    /root
    /var
    /srv
    /usr/local
[/INDENT]2. Get a list of all your additional packages. You can use this code snippet to get a list of all your currently installed packages; replace <filename> with the path of the actual file to store the list.
```

sudo -i
cd /var/lib/dpkg
cat status | awk 'BEGIN{RS="";FS="\n";ORS="\n"}{if($2~/ok installed|Essential: yes/) print substr($1,10,length($1))}' > <filename>
exit

```Save this file; you 'll need it after the Lucid install.

3. Make the clean install of Lucid.

4. Then in your freshly installed system you can install all packages in a batch from the saved list; replace <filename> with the path of the actual file where the list was stored and <logfile> with the path to a logfile which you can later open to review the process:
```

sudo -i
touch <logfile>
while read package; do apt-get install ${package} | tee -a <logfile> ; done < <filename>
exit

```Read the logfile and fix any errors before going to next step.

5. Make a backup of the same directories of your newly installed system (lets call it backup #2). You may need it if things get broken.

6. Then restore every file that makes sense from your backup #1, on top of the existing ones (ie do not remove them before). These will probably be:[INDENT]All of /home
All of /etc that you have changed yourself. If you can't figure out what you have changed, just copy them all.
    All of /root
    All of /var/log , /var/www , /var/mail , /var/local ; other directories inside /var should not be needed and better not override the newly installed ones.
    I don't know about /srv; probably all, but you 'll have to judge yourself.
    All of /usr/local
[/INDENT]7. Test your new system. Note that since you upgrade 2 OS versions, there may be significant changes in the conf settings of some packages, both in /etc and in /home and you may have to manually arrange things. But I believe this would also be the case in the upgrade process anyway. If something is broken you have backups from both your old data and settings (backup #1) and the new ones (backup #2) and thus a way to compare versions and fix things.

Let me repeat once again (it never harms to do so :)) that the alternative is to be considered _experimental_. If you have a production server, first try to fix things; only if you can't fix it start experimenting.

---

### Post by iWarior on 2010-06-15
Thanks for your time **gzarkadas**! :grin:

Today i have solved all my problems - with the help of your tips! :guitar:

1st and main |-> Mix packages from different Ubuntu ver. rep. - very-very bad idea :)

In my situation -> i have libc6 from lucid and all other packages - from jaunty. Aptitude try downgrade libc6, but process failed... And libc6 does't completely remove. That's why I have't ldd and many others software, such as locale etc. =)

So. In same situation - better downgrade packages directly with **dpkg** - step by step, until dependences will not are permitted.

I have done it, after reinstalling libc6.

PS: reinstalling - IMHO it's not solution for work-server, in the last resort - Live CD can help.

---

### Post by VISTA_USER on 2010-08-27
> **gzarkadas said:**
> I believe ldd is part of glib, thus you should have it; but I didn't make a server install before and maybe I am wrong here. Anyway, I don't know how you installed your new libc, but if your /bin/sh is broken, chances are low that you will manage to do this task through aptitude. You may try:

    * To download the jaunty libc deb for your architecture from [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/) and perform a local install using dpkg.


I couldn't find GLIBC_2.11' at [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/). Any advice?

thank you

---

### Post by gzarkadas on 2010-08-27
No, you cannot, because this version is a security update for lucid and is located in .../e/eglibc. The link in previous post regarded how the OP could restore the (older) original version.

Use the download link at the bottom of page [http://packages.ubuntu.com/lucid/libc6](http://packages.ubuntu.com/lucid/libc6) to find how to get it (best IMO is to set your software sources as described there and use synaptic or apt-get).

---

### Post by Jonathanchen on 2011-01-31
Hello,

I encountered same problem. Below is my ldd query information. What can I do??

    linux-gate.so.1 =>  (0x00e18000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00110000)
    /lib/ld-linux.so.2 (0x00d3c000)

    Version information:
    /bin/sh:
        libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.1.1) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
    /lib/tls/i686/cmov/libc.so.6:
        ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2

---

### Post by gzarkadas on 2011-02-01
Please specify in more detail what your actual problem is. The ldd output looks ok at first glance (note that 2.1.1 is not 2.11); for example, apart the hex numbers inside parentheses it is the same with that of my system, which works all right.

---

### Post by jp10 on 2011-04-09
I re-install GCC using synaptic package

on command line - I'm getting this

$gcc
gcc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by gcc)


$ ldd -v /usr/bin/gcc
/usr/bin/gcc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /usr/bin/gcc)
    linux-gate.so.1 =>  (0xb7721000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb75ad000)
    /lib/ld-linux.so.2 (0xb7722000)

    Version information:
    /usr/bin/gcc:
        libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.11) => not found
        libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
    /lib/tls/i686/cmov/libc.so.6:
        ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2


What am I missing or forget to do

Thanks

---

### Post by clockworker on 2011-07-05
Hi there,
i recently set up Ubuntu 11.04 on my laptop. I installed salome_meca 2010.2. When i want to run it i get the following error. Is that the same error as described by OP?

/SALOME-MECA-2010.2-LGPL-i386$ ./runSalomeMeca
python: relocation error: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
python: relocation error: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
python: relocation error: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
dirname: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by dirname)
python: relocation error: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
/bin/bash: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /bin/bash)
/bin/bash: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: version `GLIBC_2.8' not found (required by /bin/bash)
/bin/bash: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: version `GLIBC_2.11' not found (required by /bin/bash)
/bin/bash: /home/clockworker/Dokumente/SALOME-MECA-2010.2-LGPL-i386/SALOME/SALOME5/V5_1_4/../Prerequis/etchForSalome/lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /lib/libncurses.so.5)

the ldd command gives the following:

clockworker@clockworkerLT:~/Dokumente/SALOME-MECA-2010.2-LGPL-i386$ ldd -v /bin/sh
    linux-gate.so.1 =>  (0xb7755000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb75dd000)
    /lib/ld-linux.so.2 (0xb7756000)

    Version information:
    /bin/sh:
        libc.so.6 (GLIBC_2.4) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.3.4) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.2) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.1) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.11) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.1.1) => /lib/i386-linux-gnu/libc.so.6
        libc.so.6 (GLIBC_2.0) => /lib/i386-linux-gnu/libc.so.6
    /lib/i386-linux-gnu/libc.so.6:
        ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2
Can i solve this problem by following the above described routine?

Thank you very much for any advice
(not totally but pretty new to linux)
clockworker

---

