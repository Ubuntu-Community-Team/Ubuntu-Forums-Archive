---
title: "cannot find -lstdc++"
date: 2011-01-27
forum: General Help
---

### Post by masali on 2011-01-27
Hi everyone, 
I am a linux newbie and i am facing a  bit trouble running a function in one application. 

My application is giving me this error:

/usr/bin/ld: cannot find -lstdc++

How can I fix it?
I used this but didnt work 

user@user-OptiPlex-GX280:/bin$ sudo apt-get install libstdc++6-4.3-dev
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6-4.3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.

My current gcc version is 4.4.5

I appreciate your help 

MAS

---

### Post by regala on 2011-01-27
> **masali said:**
> Hi everyone, 
I am a linux newbie and i am facing a  bit trouble running a function in one application. 

My application is giving me this error:

/usr/bin/ld: cannot find -lstdc++


what is the exact command you typed ?
(it should be obvious that only one of the two essential pieces of information needed is never enough)

---

### Post by muteXe on 2011-01-27
didnt read it properly :)

---

### Post by masali on 2011-01-30
> **regala said:**
> what is the exact command you typed ?
(it should be obvious that only one of the two essential pieces of information needed is never enough)

In matlab I try to comile a mex function from C code by the following command:
mex filename.c

and this is what i get:

Warning: You are using gcc version "4.4.4-14ubuntu5)".  The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)

/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

    mex: link of ' "timestwo.mexglx"' failed.

??? Error using ==> mex at 222
Unable to complete successfully.

---

### Post by Perfect Storm on 2011-01-30
This may help you: [http://realsuddenlike.wordpress.com/category/usrbinld-cannot-find-lstdc/](http://realsuddenlike.wordpress.com/category/usrbinld-cannot-find-lstdc/)

---

### Post by masali on 2011-01-30
> **Artificial Intelligence said:**
> This may help you: [http://realsuddenlike.wordpress.com/category/usrbinld-cannot-find-lstdc/](http://realsuddenlike.wordpress.com/category/usrbinld-cannot-find-lstdc/)
This is what i have done:
sudo ln -s /usr/lib/libstdc++.so.6.0.14 /home/user/Matlab/sys/os/glnx86/libstdc++.so.6.0.9

however, error message of matlab didnt change:
Warning: You are using gcc version "4.4.4-14ubuntu5)".  The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)

/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

    mex: link of ' "timestwo.mexglx"' failed.

??? Error using ==> mex at 222
Unable to complete successfully.

then i followed it with these commands but didnt work:
user@user-OptiPlex-GX280:/$ sudo ln -s /usr/lib/libstdc++.so.6.0.14 /home/user/Matlab/sys/os/glnx86/libstdc++.so.6.0.9
user@user-OptiPlex-GX280:/$ sudo mv /home/user/Matlab/sys/os/glnx86/libstdc++.so.6 /home/user/Matlab/sys/os/glnx86/libstdc++.so.6_backup
user@user-OptiPlex-GX280:/$ sudo ln -s /usr/lib/libstdc++.so.6.0.14 /home/user/Matlab/sys/os/glnx86/libstdc++.so.6
user@user-OptiPlex-GX280:/$ sudo mv /home/user/mlab/sys/os/glnx86/libstdc++.so.6 /home/user/mlab/sys/os/glnx86/libstdc++.so.6_backup
user@user-OptiPlex-GX280:/$ sudo ln -s /usr/lib/libstdc++.so.6.0.14 /home/user/mlab/sys/os/glnx86/libstdc++.so.6
user@user-OptiPlex-GX280:/$ sudo mv /home/user/mlab/sys/os/glnx86/libstdc++.so.6.0.9 /home/user/mlab/sys/os/glnx86/libstdc++.so.6.0.9_backup
user@user-OptiPlex-GX280:/$ sudo ln -s /usr/lib/libstdc++.so.6.0.14 /home/user/mlab/sys/os/glnx86/libstdc++.so.6.0.9

I wanted to add is that 'cannot find -lstdc++' error didnt appear until I tried to downgrade my gcc version to get rid of the warning matlab was giving me. I followed this:
[http://ubuntuforums.org/showthread.php?t=1413330](http://ubuntuforums.org/showthread.php?t=1413330)

However, I restored my original version of gcc and the error remained

---

