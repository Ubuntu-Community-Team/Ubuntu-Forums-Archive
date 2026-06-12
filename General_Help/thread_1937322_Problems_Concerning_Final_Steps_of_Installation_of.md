---
title: "Problems Concerning Final Steps of Installation of MATLAB"
date: 2012-03-07
forum: General Help
---

### Post by Alcidious on 2012-03-07
Hi,

I am a new linux user (finally took the plunge), and I am still uncomfortable installing programs manually.  I purchased MATLAB for school, i followed installation instructions, but i can't run the program. No icon is on a desktop, matlab doesn't come up in the dash, and I can't run it calling "matlab" in the terminal, within the directory it was placed.  I keep getting "command not found".  I have tried changing the working directory several times with no results.

I think the problem has something to do with where I installed the program : i began by downloading zip files in my user folder ( /home/myname/mathworks_downloads)after unpacking and installing (following instructions), the matlab installation gui tried to make a directory in /usr/local but was unable. So I created /home/myname/mathworks_downloads/MATLAB and the installation gui completed.  There are a number of files and folders in that particular directory.  The instructions said I should be able to call "matlab" in the terminal, in the "matlabroot" directory I created (but I am unsure which is the correct one).  

Is this caused by my failure to create a proper "matlabroot" directory somewhere in /usr/local??? Thanks

FYI- using ubuntu 11.10, intel x86 based, installed Matlab 2012a

---

### Post by ofnuts on 2012-03-07
> **Alcidious said:**
> Hi,

I am a new linux user (finally took the plunge), and I am still uncomfortable installing programs manually.  I purchased MATLAB for school, i followed installation instructions, but i can't run the program. No icon is on a desktop, matlab doesn't come up in the dash, and I can't run it calling "matlab" in the terminal, within the directory it was placed.  I keep getting "command not found".  I have tried changing the working directory several times with no results.

I think the problem has something to do with where I installed the program : i began by downloading zip files in my user folder ( /home/myname/mathworks_downloads)after unpacking and installing (following instructions), the matlab installation gui tried to make a directory in /usr/local but was unable. So I created /home/myname/mathworks_downloads/MATLAB and the installation gui completed.  There are a number of files and folders in that particular directory.  The instructions said I should be able to call "matlab" in the terminal, in the "matlabroot" directory I created (but I am unsure which is the correct one).  

Is this caused by my failure to create a proper "matlabroot" directory somewhere in /usr/local??? Thanks

FYI- using ubuntu 11.10, intel x86 based, installed Matlab 2012a
You may be able to run matlab by adding the directory where you put matlab in your PATH environment variable.

You may also want to redo the installation properly. On Linux you need system privileges to install things. These are obtained temporarily by using "sudo". Instead of issuing just "command" you use "sudo command". You are prompted for your password, and then the command executes with "root" privileges (that include the write access to /usr, in particular).

---

### Post by Alcidious on 2012-03-09
I decided to start over, and used   sudo ./install  in the appropriate working directory.  Everything worked, MATLAB was successfully installed and activated.  However, I am having trouble running the program. There are no "icons" that I can find, and searching "matlab" in the dash turns up nothing.  I was finally able to run the program when I located the "matlab" file/command in /usr/local/MATLAB/etc (I used the mouse to click 'run in terminal'); here is the printout:

  /usr/local/bin/MATLAB/R2012a_Student/bin/util/oscheck.sh: 605: /lib/libc.so.6: not found

Wrongly assuming MATLAB was running from the terminal, i typed "2+2" and then the program started.  Help is very much appreciated! (Bit of a steep learning curve...)

---

### Post by ofnuts on 2012-03-09
> **Alcidious said:**
> I decided to start over, and used   sudo ./install  in the appropriate working directory.  Everything worked, MATLAB was successfully installed and activated.  However, I am having trouble running the program. There are no "icons" that I can find, and searching "matlab" in the dash turns up nothing.  I was finally able to run the program when I located the "matlab" file/command in /usr/local/MATLAB/etc (I used the mouse to click 'run in terminal'); here is the printout:

  /usr/local/bin/MATLAB/R2012a_Student/bin/util/oscheck.sh: 605: /lib/libc.so.6: not found

Wrongly assuming MATLAB was running from the terminal, i typed "2+2" and then the program started.  Help is very much appreciated! (Bit of a steep learning curve...)
This likely not the proper way to start matlab., because executables don't go in /usr./local/etc.

The Matlab startup command could be in /usr/local/bin/MATLAB/ but on the whole, assuming it is now properly installed, start a terminal session and enter "matlab". You light even get it started by entering m-a-t-[tabkey] and discover the auto-ompletionfeature of your terminal session. If you can start "matlab" from a terminal, entering "which matlab" in a terminal session will tell you where the matlab executable is.

Program that are installed in Linux don't usually create startup icons. Linux has always been a multi-user system and putting icons by default clutters the desktop of those that don't use the program (I share a Windows computer with a teenage boy...). But you can make your own startup icons..

---

### Post by |{urse on 2012-03-09
@Alcidious
You just need a symlink to it.

From: [http://morganbye.net/blog/2011/05/matlab-ubuntu-1104](http://morganbye.net/blog/2011/05/matlab-ubuntu-1104)

For 64 bit:
> 
sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
 

For 32 bit:
> 
sudo ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6

---

### Post by |{urse on 2012-03-09
If your version of ubuntu is newer than 11.04 then

[http://morganbye.net/blog/2011/10/matlab-ubuntu-1110](http://morganbye.net/blog/2011/10/matlab-ubuntu-1110)

---

### Post by Alcidious on 2012-04-21
Thanks for the help! MATLAB works and is amazing!

---

