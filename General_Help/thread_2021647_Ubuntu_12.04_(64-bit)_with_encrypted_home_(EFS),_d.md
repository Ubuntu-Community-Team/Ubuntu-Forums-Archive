---
title: "Ubuntu 12.04 (64-bit) with encrypted home (EFS), don't accept the login password"
date: 2012-07-09
forum: General Help
---

### Post by nodnolse1 on 2012-07-09
[FONT=Ubuntu][SIZE=3]Unfortunately I haven't saved the EFS passphrase generates automatically by Ubuntu+EFS. I just copied it on desktop but I never saved outside the home directory. Since few days, Ubuntu don't accept the right password at user login level. I also tried 'passwd' as single user mode or by Ubuntu 64-bit live CD and 'chroot', once typed 'passwd username' and pressed the enter button, it give me no error, don't ask for 'new unix password' typing 'passwd username', it does exactly like when you press enter on a prompt w/o any command or character, just return nothing. The only way to get answer is 'passwd -S username' and 'passwd -d username', in this case, it complain about locking shadow. In passwd and shadow files, my username it's present. So, seen that I will not able to decrypt/mount my home directory to at least save my important files, the only way that I have, is to get access in some manner by the login. I also created new users, one with home directory and one without, even use 'su newusername', I can't login because 'passwd' refuses to create any password. I also used 'dpkg-[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Ubuntu][SIZE=3]reconfigure locale' that seems to be the main reason about this problem, but no way. At the end I 'dpkg-reconfigure passwd' and few others security related 'services'. The only account that is working is the 'guest', that allows to navigate over the net. So, what can I do now? I very need to get back my home files. I also changed keyboard and used the on screen keyboard, but is not a keyboard problem or 'case' letters. Below I pasted few links at documentation that I tested but unsuccessfully. Thank for reading and maybe helping,, I hope ;-) Paolo[/SIZE][/FONT]
 

[SIZE=3]Ps: attached there is the output of passwd and shadow files with many other useful informations taken coping the input /output of given commands. Passwd and shadow files output are untouched, to give you the maximum staff available to diagnose it. In case it is needed, I also saved all '/var/log/*', just ask. Mine user account name is 'a'. No problem about privacy, next Ubuntu installation I'll use a different password. Please, help me[/SIZE]



 --
[FONT=Ubuntu][SIZE=2]Few error messages: [/SIZE][/FONT] 
 
 [FONT=Ubuntu][SIZE=2]"*passwd: cannot lock* /*etc/shadow*; *try again later*"[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] [FONT=Ubuntu][SIZE=2]''ecryptfs-mount-private  ERROR: Encrypted private directory is not setup properly''[/SIZE][/FONT]
 [SIZE=2]
  [/SIZE]Others errors into the attached text file
[SIZE=2]--
[/SIZE]

[SIZE=2]--
[/SIZE] List of pages where I get commands and procedures all applied w/o success:
 [FONT=Ubuntu][SIZE=2]
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html) 
[/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2][https://bbs.archlinux.org/viewtopic.php?id=50649](https://bbs.archlinux.org/viewtopic.php?id=50649)[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/[/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]https://help.ubuntu.com/community/LostPassword#The_Other_Way[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]https://answers.launchpad.net/ubuntu/+source/shadow/+question/174969[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]http://manpages.ubuntu.com/manpages/precise/en/man1/passwd.1.html[/SIZE][/FONT]
 
 [FONT=Ubuntu][SIZE=2]http://www.unix.com/red-hat/145443-shadow-file-password-policy.html
--
[/SIZE][/FONT]

---

