---
title: "Problem Compiling a Program in Another Partition"
date: 2010-01-19
forum: General Help
---

### Post by FaBioW114 on 2010-01-19
Hi,

I'm trying to compile a c++ program under Ubuntu 9.04 and have had some problems with it. A long time ago, I installed this OS and everything was fine. However, for some reason, I had to reinstall it and then the problem begun: I could not compile programs anymore (the exact messages will be shown in a little). To make the system read the old files (which were in another partition), I changed the fstab file, adding the following line:

/dev/sda4	/home	ext3		defaults,user	0	0

With that, I could access all my files and stuff, but couldn't compile anymore. After a while, I realized that I could compile a program if the files were in my pen-drive.

Few days ago I reinstalled the OS and got to compile! But that was before I add that line to the fstab file. When I added it (the line), again I was not able to compile. I tried Ubuntu 9.10 and it worked, I could compile, but I didn't like this version so I went back to 9.04. And then I can't compile again ¬¬ That is: if I add that line to fstab, compilation can't be done anymore.

Here are the messages shown when I try to compile:

Through terminal, it generates the executable, but it doesn't run. It says:
"bash: ./<filename>: Permission denied"

Through Code::blocks:
"sh: <path>: Permission denied"

Note that it's not written "bash" here, just "sh", which is different from compiling through the terminal.

Here are the permissions of the file and the corresponding path:
-rwx--xr-x  1 fabiow fabiow     9730 2010-01-19 14:11 <filename>
drwxr-xr-x  8 fabiow fabiow     4096 2010-01-19 14:11 desktop
drwxr-xr-x 52 fabiow fabiow     4096 2010-01-19 14:50 fabiow
drwxr-xr-x  4 root   root       4096 2010-01-10 14:16 home

The path: /home/fabiow/desktop/

Even as a root:
sudo: unable to execute ./<filename>: Permission denied

Sorry if my story was too long, but I think these are all important information. I'm not exactly an expert in linux, much of that work was done by a friend of mine, I've learned a lot, but still there's a way to go.

Thanks a lot for your patience and good will!

---

