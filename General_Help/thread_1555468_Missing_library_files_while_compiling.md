---
title: "Missing library files while compiling"
date: 2010-08-18
forum: General Help
---

### Post by derek71 on 2010-08-18
I have tried to compile several programs from source code and have into a similar error in each case.  I try make the program and I get an error like: fail program confsdefs.h.

Reading further into the log file, I see there is a long list of missing library files when I compile something like Samba 3.5.x:
vararg.h,
unix.h,
mode.h,
filio.h,
s5param.h,
minix/config.h,
standards.h,
filesys.h,
acl.h,
libacl.h,
capability.h,
id.h,
compat.h,
priv.h,
security.h,
termio.h,
dl.h,
direct.h,
windows.h,
winsock2.h,
ws2tcpip.h,
in_p.h,sockio.h,
rpc_nettype.h,
dustat.h,
libxfs.h,
netgrouph,
CFStringEncodingConverter.h,
valgrind.h,
memcheck.h,
nss_common.h,
nsswitch.h,
ns_api.h,
attributes.h,
extattr.h,
ea.h,
proplist.h,
readline.h,
history.h,
libexc.h,
libunwind.h,
gpfs_gpl.h,
isi_version.h,
giconv.h,
fam.h,
ldap.h,
lber.h,
keyutils.h,
pam_appl.h,
pam_modules.h,
vx_quota.h,
devnm.h,
ctdb.h,
ctdb_private.h,
nss_dbdefs.h,
usersec.h,
watch.h,
client.h.

I have searched for dependency information and used apt-get to add anything I can find.

How can I identify and find the dependencies for source?  I have checked the source documentation though typically does not list required packages.

My other question is how to check the path used to locate the libraries?  Given the length of the missing library list, I think the problem may be configuring make.

---

### Post by Bachstelze on 2010-08-18
Any reason you want to compile Samba?  That's probably asking for some headaches.

---

### Post by derek71 on 2010-08-18
I agree, trying to compile from source is a headache.

For Samba, I want to use the more advanced versions in order to store Windows file timestamp information, which the older versions don't do.

Generally, I would rather use the repositories to add software, though I find more recent versions in source only on occasion that I would like to use.

---

