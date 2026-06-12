---
title: "Pure-ftpd installation problems"
date: 2012-09-04
forum: General Help
---

### Post by Zammmo on 2012-09-04
I just wanted to install a simple ftpd so I can access my media archives from my other pc's... but it has now turned into a 6 hour ordeal... this is my last hope so I don't have to dig out my Win7 disk. 

I have installed pure-ftpd many times before but it has always been on dedicated servers running debian. I would shell in, download pure, ./configure, add a line to inetd and run it. I could log in from root and access everything I needed to in minutes. I figured doing it on ubuntu would be even simpler... 

First tried installing from the software centre. There is no documentation available, just the message that is it run from the command line and a couple commands. I would never run a ftpd on port 21, so first thing I want to do is change that. I can't find a conf file or any command to change the configuration at all.  Yes, I can log in and access all my files, but on port 21 and there doesn't seem to be anyway to change it. Normally pure-ftpd is started from the command line and you can add the port you want the daemon to run in the command, but with this, the daemon is already running so it won't let me run it again and I can't find a way of stopping it. I have checked 'ps x' and the inetd conf but nothing is there.

So i uninstalled it and downloaded the binaries for a manual install via the terminal. ./configure everything seems fine but when it comes to running it the pure-ftpd executable isn't anywhere it should be. /usr/local/sbin and /usr/sbin have no sign of it. find -name pure-ftpd doesn't shed any light on its whereabouts.

I gave up on pure-ftpd and tried some other options

vsftpd was useless. I couldn't find anywhere I could configure the port or file/dir access

proftpd seemed like it was going to be great. A nice gui, everything laid out, a tonne of configuration options. Everything was going fine. I go to log in, the server is running but for some reason it tries to give me anonymous access and as anonymous access is disabled it fails. The only access I could give my user account was /dev/null now I don't if that is important, but when I changed it to like /sh or /bash it would crash the server and revert back to /dev/null

So I am back to pure-ftpd. I have the download centre version that will install and run but I can't configure it and the binary version that I can configure but it won't run.

Please help me! :(

---

