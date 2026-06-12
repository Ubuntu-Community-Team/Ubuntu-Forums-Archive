---
title: "SCP command execution through ITIM does not work"
date: 2010-04-02
forum: General Help
---

### Post by satish_gauns on 2010-04-02
We have two Linux box (Machine A and Machine B). Standalone application(ITIM) running on Machine A. Target file to copy is available on Machine B.
 
SSH Handshaking done between Machine A and Machine B using normal user "ssh".
 
Standalone application running on Machine A under user "root".
 
Standalone application on Machine A invokes SCP command to copy the file from Machine B to Machine A. The SCP command executes successfully but file is not copied to Machine A. Message returned by SCP command is 
"THIS IS A PRIVATE COMPUTER SYSTEM ---USAGE MAY BE MONITORED AND UNAUTHORIZED ACCESSOR USE MAY RESULT IN CRIMINAL OR CIVIL PROSECUTIONPermission denied, please try again.Permission denied, please try again.Permission denied (publickey,password,keyboard-interactive)."
 
If I manually login to Machine A and execute same SCP command I am able to copy file without any issues.
 
Any pointer on why invoking SCP command through standalone application give above message and file is not copied?
 
Thanks in Advance!
Regards,
Satish

---

