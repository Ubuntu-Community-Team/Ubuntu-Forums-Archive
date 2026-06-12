---
title: "AWN problems"
date: 2009-11-27
forum: General Help
---

### Post by CRF450R on 2009-11-27
Hi, this is my first post and I've only been running Ubuntu for about 3 days.

My problem is with AWN. I installed it through Ubuntu Software Center and opened it to configure it once. After that it would no longer load. I've tried removing it through Terminal and SPM to no avail.

I've tried various commands in Terminal with zero results. My latest looks like this:

tritonv8@Ubuntu:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up avant-window-navigator (0.3.2.1-4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing avant-window-navigator (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libawn-extras0 (0.3.2.2-2ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libawn-extras0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-alsaaudio (0.2-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-alsaaudio (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-dateutil (1.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-dateutil (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 avant-window-navigator
 libawn-extras0
 python-alsaaudio
 python-dateutil
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've also googled to no end with no luck. Your help is much appreciated.

---

### Post by CRF450R on 2009-11-27
bump

---

### Post by raktarok on 2009-11-27
Try deleting the awn config files left in the home folder, if it exists.
Open the home folder, press ctrl+h (it shows hidden files) and navigate to .config. Then delete the awn folder there.
Or do this from a terminal.
 ```
rm -r ~/.config/awn/
```
Then see if awn loads. 

You can also try this to remove the package, but proceed with caution. Try without the force option first. I don't think this is going to help but you could try..
sudo dpkg -r --force avant-window-navigator

And can you remove/install other packages?

---

### Post by CRF450R on 2009-11-27
I haven't tried installing/uninstalling other software yet. I'm a bit nervous to try it as I don't have much experience with Ubuntu or any Linux based OS. I just don't want to screw things up. I have a tendency to make things crash. Of course I guess I try on purpose. I'd like to fix this first and then move on. I'll give those suggestions a try and post back. I'm also unfamiliar with the file system so I appreciate the suggestion for the .config tip. I'm a little more comfortable graphically than from a command line.

---

### Post by CRF450R on 2009-11-27
Ok, here's the result of an attempt to remove awn from the terminal:

tritonv8@Ubuntu:~$ sudo rm -r ~/.config/awn
[sudo] password for tritonv8: 
rm: cannot remove `/home/tritonv8/.config/awn': No such file or directory

And here is the result of the other:

tritonv8@Ubuntu:~$ sudo dpkg -r --force avant-window-navigator
dpkg: unknown force/refuse option `avant-window-navigator'

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

Hmmm, I know it's there because I get errors with the other commands.

---

### Post by raktarok on 2009-11-27
ok, try these three in order:
cd /var/lib/dpkg/info/
sudo rm avant-window-navigator.*
sudo apt-get remove avant-window-navigator

I am posting commands here, because its much faster and easier this way. It could be done via graphical, but it would take way more time and efforts. (and I would have to type more too :)) So bear with me now.
Don't be worried if you don't understand what these commands do. The first one just changes the directory to the specified one, the second deletes a bunch of files that may be conflicting with the removal, and the third, you know what it does: it removes the package.You can do all of these in graphical mode too, but this way,it is faster. At least I think so)

---

### Post by CRF450R on 2009-11-28
Great! A portion worked as you can see. There are still 3 things left that didn't get removed with that as follows:

tritonv8@Ubuntu:~$ cd /var/lib/dpkg/info/
tritonv8@Ubuntu:/var/lib/dpkg/info$ sudo rm avant-window-navigator.*
[sudo] password for tritonv8: 
tritonv8@Ubuntu:/var/lib/dpkg/info$ sudo apt-get remove avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avant-window-navigator
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 336kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `avant-window-navigator' missing, assuming package has no files currently installed.
(Reading database ... 140770 files and directories currently installed.)
Removing avant-window-navigator ...
Setting up libawn-extras0 (0.3.2.2-2ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libawn-extras0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-alsaaudio (0.2-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-alsaaudio (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-dateutil (1.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-dateutil (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libawn-extras0
 python-alsaaudio
 python-dateutil
E: Sub-process /usr/bin/dpkg returned an error code (1)
tritonv8@Ubuntu:/var/lib/dpkg/info$ 

I can only assume these last three items are related but maybe not?

---

### Post by raktarok on 2009-11-28
You are right in assuming that the three items are related. Repeat the same process for these too:
```
cd /var/lib/dpkg/info/
sudo rm libawn-extras0* python-alsaaudio* python-dateutil*
sudo apt-get remove avant-window-navigator
```

This should fix the problem. By using * here, you are deleting all files starting with the prefix, but actually, since you are getting an error that says "unable to execute installed post-installation script", you can only delete the files ending in **postinst**. So, instead of the second line above, this should work too:
```
sudo rm libawn-extras0.postinst python-alsaaudio.postinst python-dateutil.postinst

```

Now you should see three other warnings similar to "files list file for package `avant-window-navigator' missing, assuming package has no files currently installed", while removing avant-window-navigator. Then you should be able to install it again.  

Also, if this is not too much of a trouble, can you please post the contents of one of the files ending in .postinst? I am asking this just out of curiosity...your problem seems to arise from that file, and since it says "Exec format error", I think that the file may be missing one important line.

Good luck, and hope this helped!

---

### Post by CRF450R on 2009-11-29
Awesome! That did the trick. Thank you Raktarok. 

Pardon my ignorance but I can't find that .postinst file anywhere. I'd happily display it if I could. I did a search for ".postinst" through file browser and returned nothing. Is there another way?

---

### Post by raktarok on 2009-11-29
oh..I meant one of the files libawn-extras0.postinst OR python-alsaaudio.postinst OR python-dateutil.postinst in the directory /var/lib/dpkg/info/. (If you are at the home folder, you can hit up two times in the file manager and then, you will see a folder named var. From there, you can navigate to the specified directory) These were the files that were causing error, and I just wanted to have a look at one of them. 

But you have already deleted these files, and by now, you must have installed a working copy of avant-window-navigator. The files causing the error are no longer there, so forget what I asked. I should have been more clear, and asked you to post the contents of those files before deleting them. 

Anyway, no harm done...and glad to hear that this worked! Its a bit unfortunate that you had to face such an ugly problem so early on and I hope this does not ruin your impressions of ubuntu and linux in general...

---

