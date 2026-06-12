---
title: "Apache2, php, and the COM1 port"
date: 2010-03-15
forum: General Help
---

### Post by tbirchall on 2010-03-15
Not really sure where to post this, so here goes...  I installed apache2, php and MySQL via LAMP and everything seems to work fine but when I try to open the COM1 port to do serial communication via PHP, I get a permission denied error.

'mode com1: BAUD=9600 PARITY=N data=8 stop=1 xon=off';
$fp=fopen("COM1:","w+");

I've also tried using /dev/ttyS0 instead of COM1: but no luck.  Anyone out there know what I'm doing wrong?  I don't know if I need to set something up in apache2 or php or if the code is just wrong.  I'm on an Acer Aspire One with Ubuntu's LNR 9.10.

Thank you and sorry if this is the wrong place to post this!

Tom

---

### Post by blueridgedog on 2010-03-15
Do you have a com1 in /dev?

What are the permission on com1?

Current syntax is to call it ttyS0 and the default permission will not let just anyone use it.  See:

crw-rw---- 1 root dialout 4, 64 2010-03-02 13:17 ttyS0

You can create a symbolic link called com1, and add the user that is trying to connect to the dialout users group...or just grant others permission to use it (slight security risk).

---

### Post by tbirchall on 2010-03-16
Thank you so much for responding.  I changed the COM1 to ttyS0 now I get an error which says no such file exists.  There is a file dev/ttyS0 and I am part of the dialout group which has read/write access.  Do I need to give the full pathname to this file?  Will writing to that file send serial data out the port or actually change the file?  All the examples I've found of writing serial code for php don't show a full path.

$fp=fopen("ttS0","w");

Any additional help is greatly appreciated.  I'm (obviously) new to linux and php, so getting stuck is pretty easy.  :-)

-Tom

---

### Post by blueridgedog on 2010-03-16
I would try the full path name, and test it with a sudo to make certain you are not hitting a permission issue.

---

### Post by tbirchall on 2010-03-16
I checked the permissions on dev/ttyS0 and there is a group named dialout.  I am part of that group and it has read/write permissions.  From the warning below, it looks like it is still trying to find the file in the home... structure. I also tried root/dev/ttyS0 as a path. You mentioned using sudo - can you do that from within php?
[B]
Warning[/B]:  fopen(File System/dev/ttyS0) [[function.fopen]("http://localhost/function.fopen")]: failed to open stream: No such file or directory in **/home/tom/public_html/arduino_03.php** on line [B]13
[/B]
Thanks again,
Tom

---

### Post by blueridgedog on 2010-03-16
I suspect that apache is operating in a chroot environment and has no access to the serial ports.

Take a look at post 4 and on here:

[https://www.linuxquestions.org/questions/linux-server-73/php-exec-issue-with-chrooted-lighttpd-559438/](https://www.linuxquestions.org/questions/linux-server-73/php-exec-issue-with-chrooted-lighttpd-559438/)

Search google and here for apache chroot and serial port.

I may be misleading you, but it is my best guess at the moment.  An apache or PHP forum may get you closer to the answer.

---

### Post by junapp on 2010-03-16
I suspect you may need to make www-data (or whoever you have apache running as) part of the dialout group, not your user account.

---

