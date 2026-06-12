---
title: "xorg process eating 100% cpu in ubuntu 10.04"
date: 2012-08-02
forum: General Help
---

### Post by irfan20uk on 2012-08-02
Hi guys,
I have messed up with Xorg process in Ubuntu Lucid 10.04.4 LTS 64bit. I suppose to run simulations on my Dell Precision T1500 round the clock but after certain time more than 90% CPU starts to be hang up with Xorg process. This ultimately slows down the system speed compelling me to reboot to get back the normal system. 
Does anybody has a clue to fix this bug?
Best,

---

### Post by TheFu on 2012-08-02
There must be thousands of bugs in X, X-servers, and X-clients. Nailing down the exact offender in your situation will take many hours of looking at logs for both X and the application(s).  GPU drivers are often the buggiest software out of the code involved.  Here's a few ideas to try:

* there's no need to restart the PC. Just kill off X/Windows. If you can, don't use a GUI for your simulations and you won't have any X/Windows CPU issues.  Just use the CLI interface instead.
* Try newer GPU drivers. Often these are worse, but they might fix whatever bug you are seeing.
* Try a newer X-server. Bugs are constantly corrected and have been over the last 20 yrs.
* Try a newer client application
* Of course, if you are patching your system regularly, then perhaps an older version was more stable?  

Again, there is no need to reboot a system, just because X is eating CPU, kill off the main X process, this will end all dependent processes, and restart it via **startx**.  It might be best to ssh in from a different PC to kill X.  There's a keyboard shortcut for this too, but since it changed from <cntl>-<alt>-bksp, I haven't a clue what it is. [http://blog.jdpfu.com/2010/05/20/keystroke-to-restart-x-windows-in-ubuntu-10-04-lucid](http://blog.jdpfu.com/2010/05/20/keystroke-to-restart-x-windows-in-ubuntu-10-04-lucid) explains more.

---

### Post by irfan20uk on 2012-08-02
Hi, Thank you for your advice. I appreciate this. Nevertheless it works by stopping/kill the X server but by doing so it also kills all other running processes and on restarting X server again give me login window. Is it possible that killing X server does not harm other processes.

I use the following commands to kill and restart X server.
sudo server gdm stop
or
sudo /etc/init.de/gdm stop

sudo server gdm start
or 
sudo gdm

This all works but it gives back the system from login window by killing all other processes.
any solution to keep running the other processes while restarting X server?

---

### Post by TheFu on 2012-08-03
Any GUI program needs X, so no, there is no way to keep running a GUI program if you kill X.  

If you use non-GUI tools and run them disconnected from a GUI parent process, then those will not be sent a signal to end themselves when the window is terminated.

For example, even a terminal is attached to X, so any CLI program running inside that terminal will be killed when you end X.  If you put the CLI program in to the background, that will detach it from the terminal and it will continue regardless of X running or not.

Learn to love the CLI!

I'm thinking  a little outside the box with this next thought.  Instead of starting up your software directly, go through a VNC or NX client/server connection. You'll run both the client and the server locally, but they won't be connected to X - at least not the X that your login is running under.  I've only tried this under Android connecting to a BT5 Ubuntu install running in a chroot environment under Android. It was painful, but necessary since Android doesn't support X clients or servers directly, but VNC clients do exist.  Just a thought.  This is a pretty advanced topic, so a good understanding of VNC and X will probably be necessary. [https://www.linuxquestions.org/questions/linux-mobile-81/ubuntu-on-android-938878/](https://www.linuxquestions.org/questions/linux-mobile-81/ubuntu-on-android-938878/) explains how to do it on Android - it should be much, much easier under a direct Ubuntu install.
* Install a vnc-server
* Install a vnc-cliett
* configure the server to start the WM and a program that you want - I always start an xterm for safety
* startup the VNC server
* using the VNC client, connect to the server on localhost:5901
* Use the VNC client just like you would any other desktop.

This method will have all the limitations of VNC - no sound, delayed mouse control and slow graphic, but it should work good enough.

---

### Post by irfan20uk on 2012-08-07
Thanks, I really Appreciate your explanation. 
Best.

---

