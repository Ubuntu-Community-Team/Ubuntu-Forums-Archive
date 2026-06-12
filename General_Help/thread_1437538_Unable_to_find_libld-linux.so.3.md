---
title: "Unable to find /lib/ld-linux.so.3"
date: 2010-03-24
forum: General Help
---

### Post by avi@nitc on 2010-03-24
Hi All,

I am using Ubuntu 9.10/Kernel 2.6.31  on Intel Core2.

While loging into my account I got an error ¨Could not update ICEauthority¨
I solved it by deleting the ~/.ICEauthority file then restarting and allowing it to create one. As suggested by this forum.

I have another problem still existing. when I open my terminal I get the below message. I cant execute any commands existing in /bin file . I can access others.

I am able to run normally as a root or other accounts [created another account It works fine]

On opening the terminal I get the below message:
/lib/ld-linux.so.3: No such file or directory
/lib/ld-linux.so.3: No such file or directory
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
/lib/ld-linux.so.3: No such file or directory
avinash@avinash-laptop:~$ 

Error when Executing commands in  /bin :
avinash@avinash-laptop:~$ ls
/lib/ld-linux.so.3: No such file or directory

No error while using other commands:
avinash@avinash-laptop:~$ pwd
/home/avinash


my /lib/ folder shows ld-linux.so.2 which is the symlink for ld-2.10.1.so

avinash@avinash-laptop:~$ sudo ls -l /lib/ld*
-rwxr-xr-x 1 root root 113320 2009-10-07 14:20 /lib/ld-2.10.1.so
lrwxrwxrwx 1 root root     12 2010-02-12 22:49 /lib/ld-linux.so.2 -> ld-2.10.1.so

I searched for similar problem but could not find one.
Please Help as to what do I do?

Regards
Avinash

---

### Post by avi@nitc on 2010-03-24
Ok!! Found the root cause of my problem. a silly mistake!!

For some reason I had extracted a tar file[ubuntu rootfs] into my home folder. and my path was set to /home/user/bin this caused the trouble .

I am not sure if I had done that mistake or if it was due to some other activity. I am sure i din change the PATH variable may be I would have extracted one of the tar file in home folder, as I was playing around with them before the problem.

I deleted the unwanted folder at home and also deleted the PATH variable leading to bin file at home. The problem seems to have gone for now. :p

export PATH=$(echo $PATH | tr ':' '\n' | awk '$0 !~ "/avinash/"' | paste -sd:)

Regards
Avinash

---

