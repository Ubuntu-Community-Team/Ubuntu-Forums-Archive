---
title: "Automating sshfs in expect script is not working"
date: 2012-09-19
forum: General Help
---

### Post by sumanthr on 2012-09-19
Hello,

I am using Ubuntu 12.04 64-bit version and sshfs and fuse of below versions
################
sumanth@ubuntu:~$ sshfs --version
SSHFS version 2.3
FUSE library version: 2.8.6
fusermount version: 2.8.6
using FUSE kernel interface version 7.12
#################################

When i manually execute the command "/usr/bin/sshfs  -o reconnect -C -o workaround=all -o allow_other [email]sumant@remote.host.com[/email]:/remote_directory /local directory". It works fine and i am able to access the remote folder through my local folder.
However when i tried to automate it using expect script, the mounting seems to happen ( I mean expect script does not return any error) but the file permission seems to be messed up. ( See below)
###################################################
ls -l
drwxr-xr-x  2 sumanth sumanth   4096 Sep  5 21:52 Music
d?????????  ? ?       ?            ?            ? ABCD
##################################################

Accessing the mounted folder gives the below error
################################################
sumanth@ubuntu:~$ cd ABCD
bash: cd: ABCD: Transport endpoint is not connected
#################################################

The expect script i am using is as below. Not sure if it is the problem with the expect script or permissions for sshfs/fuse.
###############################################
#!/usr/bin/expect -f
set timeout 20
spawn /usr/bin/sshfs -o reconnect -C -o workaround=all -o allow_other remote_machine:/remote_directory local_directory
expect "sumant@XXXX;s password:"
send "password\r"
###############################################

Any help would be greatly appreciated. I know we can use autofs instead of sshfs, but i am just curious as to why the automation is not working.

---

### Post by marisdembovskis on 2013-09-10
did you find solution?

---

