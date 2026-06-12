---
title: "I cant install anything"
date: 2010-12-03
forum: General Help
---

### Post by endo911 on 2010-12-03
dallas@dallas-laptop:~$ sudo apt-get -f install
[sudo] password for dallas: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dallas@dallas-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libfreebob0 nvidia-185-libvdpau mplayer-skins libsvga1 mplayer
  libmyth-0.22-0 mencoder libmysqlclient15off ruby1.8 libx264-67 ruby libcelt0
  gtk2-ex-formfactory-perl libjline-java libffado1 libxml++2.6-2 rhino
  libqt4-phonon mplayer-nogui libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fancontrol (1:3.1.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fancontrol (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenjpeg2 (1.3+dfsg-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenjpeg2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libprotoc5 (2.2.0a-0.1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libprotoc5 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of protobuf-compiler:
 protobuf-compiler depends on libprotoc5 (= 2.2.0a-0.1ubuntu1); however:
  Package libprotoc5 is not configured yet.
dpkg: error processing protobuf-compiler (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 fancontrol
 libopenjpeg2
 libprotoc5
 protobuf-compiler
E: Sub-process /usr/bin/dpkg returned an error code (1)
dallas@dallas-laptop:~$ 1sb_release -a
No command '1sb_release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
1sb_release: command not found
dallas@dallas-laptop:~$ 1sb_release -a
No command '1sb_release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
1sb_release: command not found
dallas@dallas-laptop:~$

---

### Post by Zimmer on 2010-12-03
Suggest you try the Synaptic Package Manager.. Edit>Fix Broken Packages.
Quoting from Man Apt-Get
>        -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.

Try through Synaptic and if there are problems identify the packages and follow advice above(read the complete man entry) to remove them and then re install them..

---

### Post by endo911 on 2010-12-03
Setting up fancontrol (1:3.1.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fancontrol (--configure):

I tryed all i can with synaptic but the above shows up no matter what i try doing

---

### Post by Zimmer on 2010-12-04
Use Synaptic to completely remove fancontrol,  then check for broken packages(look at the info at the bottom of the Synaptic window.) fix if necessary (Edit>fix broken packages) then try installing fancontrol on its own via Synaptic.... see what messages it generates then.

I am Googling(hate that made up word !) your error messages to look for more clues.

---

### Post by endo911 on 2010-12-04
Im new to ubuntu. Synamptic cant find anything wrong with my computer no broken packages. I had the lucid repository on twice and fixed that. I cant remove fancontrol from synaptic or command line. If i try installing or removing anything i get the same error messages. 


dallas@dallas-laptop:~$ sudo aptitude -S fancontrol purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
The following partially installed packages will be configured:
  fancontrol libopenjpeg2 libprotoc5 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up fancontrol (1:3.1.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fancontrol (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenjpeg2 (1.3+dfsg-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenjpeg2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libprotoc5 (2.2.0a-0.1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libprotoc5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 fancontrol
 libopenjpeg2
 libprotoc5
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libopenjpeg2 (1.3+dfsg-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenjpeg2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libprotoc5 (2.2.0a-0.1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libprotoc5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libopenjpeg2
 libprotoc5
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

dallas@dallas-laptop:~$

---

### Post by Zimmer on 2010-12-05
Looks like dpkg has got itself in a twist somehow (you gave no details of how you might have arrived at this state, never mind, ).

If it were me I would back up my important data files and re install as it could take longer to try and fix whatever got broke. There are SOLVED bits and pieces out there of a similar nature but oft preceded by things like > I managed to fix it. Read on for how I did it.

Precaution: The process can break your system if not followed as mentioned (you may get into problems even if you follow the process). Please proceed at your own risk.
You might have a look here, but I would back up any data you do not want to lose before you launch into another potential solution (including the re install solution.)
see [http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html](http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html)

Out of interest , would you like to tell how you might have ended up this way? What distribution you are running, was it an upgrade? What exactly were you installing? Were you trying apt-get on the command line whilst you had Synaptic or the Software Centre running ? (Synaptic and Software centre are graphical front ends for Apt). ..) etc.

---

### Post by endo911 on 2010-12-05
I started out with 9.04 koala, i think. I upgraded to 10.04 that i downloaded off the net from somewhere. When it installed there were error messages don't remember what they were. But everything seemed to work so i didnt think about it. When i tried to install google earth it came up with these error messages and google earth wont start. I thought it was a problem with google earth and finally gave up. I am now trying to install istanbul desktop session recorder so i can make some how to videos for my mom. and im getting these same errors. I made a 10.10 upgrade cd but i was hoping to use it only as a last resort. Thanks for all the help by the way. And yes i had synaptic on when I tryed running apt as you can see in my first post. Oops, i guess thats what happens when you dont open up a command line for 15 years.

---

### Post by endo911 on 2010-12-06
That link worked i'm error free thank you so much!!!

---

### Post by Zimmer on 2010-12-06
Just a bit of persistent searching with the error messages in various forms will often turn up the answer.

What Linux and Ubuntu has really showed me over the last 5 years is that by storing my documents,music and photos on a separate partition (not a separate /home partition) I can safely install and re-install any Linux distribution to a partition and use it to access the data and I can try out a new one by installing that alongside it in a fresh partition without uninstalling the original.

I also back up my data partition to an external drive.... I do not worry about the OS partition because I know I can re-install it quite quickly (probably quicker than it would take to diagnose and repair ...:)  )

Don't forget to mark this thread as SOLVED (option in the Thread Tools at top of the post)

---

