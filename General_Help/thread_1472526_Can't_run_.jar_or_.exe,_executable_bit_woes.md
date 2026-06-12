---
title: "Can't run .jar or .exe, executable bit woes"
date: 2010-05-04
forum: General Help
---

### Post by zuperxtreme on 2010-05-04
So it looks like this is a new type of protection, but I can't seem to run executables even with "Allow executing file like as program" checked.

Running it as sudo doesn't work either. 

Is there a way to turn this off? HALP.

Screen shot of properties attached.

EDIT: Java and Wine installed, btw.

---

### Post by mb_webguy on 2010-05-04
The ".exe" files are Windows executables, which you can't run under linux without installing [Wine]("http://www.winehq.org/download/deb").

The ".jar" files are Java archives/applets, so you need to have Java installed.

EDIT:  From the screenshot, it looks like you don't have ownership of the files.  Open the terminal, cd to the directory containing the file(s), and type "sudo chown *username*:*username* *filename*", where *username* is your username, and *filename* is the name of the file.

---

### Post by lechien73 on 2010-05-04
Odd...I had a similar problem running executable files from a CD, but haven't had any issues with .exe files that have the executable bit set.

If you try to run it from a terminal window:

```
sudo wine <path and filename of executable>
```

What happens?

---

### Post by zuperxtreme on 2010-05-04
Weird, from the GUI I get the execute bit error, but if I do:

java -jar <file> 

it works fine this way, same with wine.

"sudo chown username:username filename" didn't, though. :/

---

### Post by zuperxtreme on 2010-05-04
Bump for long-term solution???

---

### Post by mc4man on 2010-05-04
> long-term solution???

Your best bet for a wine solution would be to either use Wine Team PPA - 
according to  post 18 the cautious-launcher has been disabled in their builds
[http://ubuntuforums.org/showthread.php?t=1467914&page=2](http://ubuntuforums.org/showthread.php?t=1467914&page=2)

Otherwise you could create a custom launcher for wine or edit the default launch command  - described in posts 10 and 13 in above link.

As far as java you could edit the launch command in the appropriate .desktop depending on what java you have installed, the manner in which to edit would be the same as shown in post 10 for wine


edit
wine team  ppa (i believe this is the one
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by zuperxtreme on 2010-05-05
Thanks a lot mc4man, works perfectly. :) 

(Still, it seems dumb, there shouldn't even need to be a problem)

---

### Post by dmolony on 2010-05-21
I have a similar problem with 10.04. I use ant to build my .jar files (from a mac) which puts the jar in a dropbox folder. This file then appears on my Ubuntu machine, with a symlink on the desktop to the jar file in the dropbox folder.

In 9.10 I was able to build a jar, then go to the Ubuntu box, double-click the desktop link and it would work. In 10.04 however, it now complains about the executable bit not being set. So I click properties on the desktop icon, make the file executable, and it now works. Yippee!

Until I do the next build that is!! That resets the execute permission, and I have to go through the procedure all over again. Every time!!

Is this an Ubuntu issue, or a Dropbox issue? Or both?

---

### Post by dcstar on 2010-05-21
> **dmolony said:**
> I have a similar problem with 10.04. I use ant to build my .jar files (from a mac) which puts the jar in a dropbox folder. This file then appears on my Ubuntu machine, with a symlink on the desktop to the jar file in the dropbox folder.

In 9.10 I was able to build a jar, then go to the Ubuntu box, double-click the desktop link and it would work. In 10.04 however, it now complains about the executable bit not being set. So I click properties on the desktop icon, make the file executable, and it now works. Yippee!

Until I do the next build that is!! That resets the execute permission, and I have to go through the procedure all over again. Every time!!

Is this an Ubuntu issue, or a Dropbox issue? Or both?

When files are created they usually are done with a default umask value, this may well be different in 10.04 - in fact defaulting with the execute bit set may well have been deemed a security issue.

The process of creating any executable file should specifically set the execute bit and not just assume that it will be set.

---

### Post by mc4man on 2010-05-22
> Is this an Ubuntu issue, or a Dropbox issue? Or both?

It is solely an ubuntu issue - the sercurity team decided on a policy that in theory may have merit but in practice is mis-implemented, misguided and of no actual value.

There was and is no need for .exe's and .jar's to have the bit set and depending on their source no expectation that it would or could.

Many solutions for wine, for java just edit the launch command and be done with it.

---

### Post by dmolony on 2010-05-22
Just edit the launch command?

This is exactly why linux hasn't killed off windows, and why I do all my development work on a Mac. WTF?

---

### Post by mc4man on 2010-05-23
> This is exactly why linux hasn't killed off windows,...
I seriously doubt this or anything related has much to in that area at all.

while I think this is a policy that needs to be redone or reverted there may be others who are in a position to correctly think differently.

On the positive side without knowing all that much it would only take me about 20 sec's to revert this locally - I don't think the same can be said for windows or mac Os (as far as modifying the behavior of programs to suit

---

### Post by UnstableAfliction on 2010-09-09
my problem is a little different, because i made a personalizated command, i change the wine protocol, i try to change premission, but i cant! the problem is when i right click on the .exe file, there is not a permissions tab where to change it. 

i know this is because i use xubuntu. please if you know about this help, i know the answer must be an easy thing, but for now, i am about give up.

---

### Post by linuxfreak777 on 2011-01-27
TRY DOING THIS......i take a .jar file as an example....move it to your home directory and then change the permissions .....like chmod 700 filename..........doing this did the thing for me...

---

### Post by JNieto on 2011-06-02
> **linuxfreak777 said:**
> TRY DOING THIS......i take a .jar file as an example....move it to your home directory and then change the permissions .....like chmod 700 filename..........doing this did the thing for me...

Thanks for the hint !!!

For me the same file:
a) On NTFS local file system appears as -rwxrwxrwx  root, and does not run. :(
 
b) copied to /home/mysuser appears as -rwxrwxrwx  myuser and RUNS !!!  :D (simply copied, no owner or protections changed!!!)

The run method is the desktop one : right click; "Open with Sun Java 6 runtime".
The terminal method "java -jar myjar.jar" works on both places.

---

