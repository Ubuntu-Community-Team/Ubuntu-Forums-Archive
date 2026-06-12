---
title: "Calling expect script from bash fails. Any pointers please"
date: 2010-03-19
forum: General Help
---

### Post by springles on 2010-03-19
Hi All, 

I am using CygWin in my Windows machine.
I would need to ftp a file from my windows machine to Unix.

I wrote an expect script and when I run the script from CygWin command prompt like
./myexpect_script, it works fine and the files are ftped to the server.

But, my requirement is I need to call this from another script

So I have script A :
#/bin/bash

#Does some processing 
#Creates the expect_script file
#And then tries to call the ./myexpect_script like

 C:/path1/path2/myexpect_script


But, I keep getting the error :

./A: line 902: C:/path1/path2/myexpect_script: No such file or directory

Can somebody help.
How can I call this expect script from my bash script.

Regards, 
-SP

---

