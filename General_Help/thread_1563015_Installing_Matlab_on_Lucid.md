---
title: "Installing Matlab on Lucid"
date: 2010-08-28
forum: General Help
---

### Post by evenrelation on 2010-08-28
Hello

I hope this is the correct spot for this question.

From my university intranet I downloaded an ISO file which I mounted into a folder:

```
mkdir mount_matlab
sudo mount -o loop linux64.iso mount_matlab/
cd mount_matlab/
```but
```
./install
```gives me
```
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/user/matlab_temp/mount_matlab/update/install/main.sh: 178: /home/user/matlab_temp/mount_matlab/update/bin/glnx86/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


```I have execute permission nonetheless:
```
-r--r--r-- 1 root root    3262 2009-07-24 18:06 activate.ini
-r-xr-xr-x 1 root root   43320 2010-01-18 21:18 install
-r--r--r-- 1 root root 1110371 2010-01-15 22:32 inst_doc.pdf
-r--r--r-- 1 root root   73937 2010-01-18 21:18 license.txt
-r--r--r-- 1 root root    5839 2010-01-25 16:09 readme.txt
dr-xr-xr-x 6 root root    2048 2010-03-17 13:25 update
```Also, ./install* -t won work either.

Any ideas what I need to do to get the installer running?

---

### Post by kelvinho on 2010-08-28
Hi there ... I am not a demon coder by any means, but I have noticed that there is a difference between my Debian setup, and Ubuntu, in that I have to make files that do not have the .deb extension executable through the Properties pane before I can run it.

You could also try dragging the binary into a Super-user terminal.

The file looks suspiciously like a 64bit jobby - do you need the 32bit version?

If I have been of help, then please "Get on with your homework!"

All the best

---

### Post by evenrelation on 2010-08-28
I'm a Linux newbie (numpty) so most of your post is in a language I'm not familiar with.

But I got the 64 bit version since my processor is 64 bit. What 64 vs 32 bit means is beyond me as well.

The installation instructions on my university intranet said get the 32 bit, so perhaps I need to downnload the 1.9 gb again.

Thanks anyway.

---

### Post by kelvinho on 2010-08-28
Hey do not worry ... I would not claim to be any kind of computer genius. If you are using Matlab, you should have some kind of natural talent for investigation. 

The properties pane ... by that I mean "right click .... and then select Properties, at the bottom of the panel that comes up with options such as "delete" etc

Select Properties, then another panel shoots up on the screen. Click on the Permissions tab in this panel, and there should be a tick box, which enables the execute command to be run.

I have posted a picture of the window here. Remember to right-click and select Properties to get there, then Permissions.

If this still doesn't work, try copying the files from the cd image to your drive or usb pen, and trying again.

Sorry if my language was unclear. Here is the image that I made.

[http://linuxanswers.yolasite.com/ubuntu-answers---changing-file-permissions.php](http://linuxanswers.yolasite.com/ubuntu-answers---changing-file-permissions.php)
Feel free to post again. I am trying to help you get there =)

---

### Post by evenrelation on 2010-08-29
Well, turns out the problem was the architecture.

I downloaded the 32-bit version, the installation worked and Matlab is up and running.

Thanks anyway.

---

### Post by firefox66 on 2010-09-15
I got this problem so how can i fix it :

[email]xxx@xxx-laptop:~/Downloads/Mathworks.Matlab.R2010b.UNIX.ISO[/email]-TBE/install$ ./install
Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_4095/java/jre/glnxa64/jre/bin/java: Permission denied
Finished
[email]xxx@xxx-laptop:~/Downloads/Mathworks.Matlab.R2010b.UNIX.ISO[/email]-TBE/install$

I use ubuntu 10.04 x64

---

### Post by Raptorista on 2010-10-05
Hi! I got the same problem.
Did you find anything out?

Please let me know!

---

### Post by matt_symes on 2010-10-05
Hi,
 
If you want a free matlab clone try octave
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)
Compatible with matlab
 
Might save you the hassle with matlab. Dont use it myself so... (this might be a silly reply)

---

### Post by qubits1 on 2010-10-11
@firefox66

I had the same problem and here is how I fixed it.
Go to terminal and get to the base directory with all the installation files.
Then go to "install files dir"/java/jre/glnx86(or glnxa64 for 64-bit)/jre/bin/
Now, add the permission to execute "java" file using
: sudo chmod +x java

The installation should work now.

---

