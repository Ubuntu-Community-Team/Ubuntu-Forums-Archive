---
title: "how to script lftp to test if a file/directory exists"
date: 2010-05-28
forum: General Help
---

### Post by bsenftner on 2010-05-28
I need to test if a file exists on a remote ftp server within a bash script via lftp.

Of course, interactively, this is trivial, but the end user is not at all technical. The bash script is being called by a perl/tk gui, and the end user can not use a command line at all. 

At first, I simply tried to 'ls' the remote file, but if the file does not exist, lfpt attempts a retry, with default retries set to 4096 times... kinda useless.

So I tried setting net:max-retries to 1, via this:

[INDENT]lftp -u "username,password" ${remoteServer} -e "set ftp:ssl-protect-data true; set net:max-retries 1; debug 3; ls ${remoteFile}; exit" &> ${tempFile} 
ret=`cat ${tempFile}`
...parsing logic looking for ls error...
[/INDENT] 

However, the retry setting seems to be ignored, and it retries anyway. 

This seems so trivial... 

I thought of maybe getting a listing of the file's parent directory, and parsing that for the file, but I'd have to individually traverse and verify each directory in the file's path from start to end, and if the root directory in that path does not exist I'm back in 4096-retry hell.

Any suggestions? Remember, it's an ftp server, so scp and such can't be used...

---

