---
title: "rpm-build package missing and halted LTIB build under Ubuntu 10.04"
date: 2010-07-23
forum: General Help
---

### Post by yliu000 on 2010-07-23
I am trying to build LTIB under Ubuntu 10.04, and I have installed  the following packages:
apt-get install m4
apt-get install  bison
apt-get install patch
apt-get install build-essential
apt-get  install libncurses5-dev
apt-get install zlib1g-dev
apt-get  install rpm
 
But I still have this problem message saying I  missed rpm-build package when I tried to build:
ltib cannot be  run because one or more of the host packages needed
to run it are  either missing or out of date.

Please install/upgrade these  packages and then re-try.

Package                Minimum ver    Installed info
-------                -----------   ---------------
[COLOR=#99cc00]rpm-build              0             not installed[/COLOR]
Died  at ./ltib line 1241.
traceback:
 main::host_checks:1241
   main:489


Started: Fri Jul 23 16:53:26 2010
Ended:   Fri  Jul 23 16:53:26 2010
Elapsed: 0 seconds


Build Failed

Exiting  on error or interrupt
 
Could anyone help me to solve this  please?
 
Thanks,
yliu

---

### Post by zuikway on 2010-07-23
rpmbuild should install with rpm. type:

whereis rpmbuild

If it exists, then rpmbuild is present and maybe you can just comment out the line in ltib under pre_install_deps  => ...

Wayne

---

### Post by yliu000 on 2010-07-23
Thanks for your help Wayne.

Here is the response:
yliu@ubuntu:~$ whereis rpm-build
rpm-build:
yliu@ubuntu:~$ whereis rpmbuild
rpmbuild: /usr/bin/rpmbuild /usr/share/man/man8/rpmbuild.8.gz

I am new to LTIB, could you please provide me some detail instructions  on how to comment out the line in LTIB? Thank you again.

Best regards,
yliu

---

### Post by yliu000 on 2010-07-24
I have tried to comment out the line in ltib file, but it gave me more errors ...

Could anyone help please? Thank you.

Kind regards,
yliu

---

### Post by yliu000 on 2010-07-26
I found out the cause of previous problem was that the LTIB doesn't
support the latest version of RPM 4.7.0, so I have installed the downgrade
version 4.4.2.3, and now the LTIB doesn't report rpm-build package missing
error, however I still can not build LTIB which gives me the error message
in
host_config.log file. I have attached this file in this email. I also
downgraded my ubuntu to 9.10 version. Please help me to solve this
problem. Thank you.

---

### Post by mphoenix on 2010-12-31
I am having the same problem too. Anyone find a solution to this? Thanks.

---

