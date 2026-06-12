---
title: "Eclipse errors after installing GlobalMenu"
date: 2010-06-13
forum: General Help
---

### Post by neojames on 2010-06-13
Whenever I start Eclipse I get the splash screen, until the loading bar starts then it crashes. When I run it in terminal I get the following error:-

** (Eclipse:3847): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb731ea8e, pid=3847, tid=3075954368
#
# JRE version: 6.0_18-b18
# Java VM: OpenJDK Client VM (14.0-b16 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.8
# Distribution: Ubuntu lucid (development branch), package 6b18-1.8-0ubuntu1
# Problematic frame:
# C  [libglib-2.0.so.0+0x3ea8e]  g_main_context_prepare+0x16e
#
# An error report file with more information is saved as:
# /home/james/hs_err_pid3847.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted


If anyone could help it would be appreciated! Thanks in advance!

---

### Post by vnkatesh on 2010-06-13
Hi. Even I had the same problem. I just randomly arrived here after searching..
So, I was able to solve *my* specific problem.

It was almost exactly same as yours. Eclipse stopped working (it was working fine till about 1-2 hour ago and the same SIGSEGV crash with libglib being the problematic frame)

So, the thing was, I did an upgrade to my comp within the past launches and I immediately realized that something in the upgrade broke it.

I'd advise you the same, did you recently install any new package? 

So, this is what *I* did to get rid of the problem: In short: I removed/purged the indicator-datetime package, autoremove-the remaining non-required packages, removed the canonical-dx-team/une launchpad ppa, and did update/dist-upgrade.

  434  eclipse &
  435  clear
  436  eclipse &
  437  sclear
  438  ls
  439  clear
  440  eclipse 
  441  eclipse -clean
  442  eclipse &
  443  eclipse 
  444  which java
  446  java -v
  447  ls
  449  cat hs_err_pid*
  450  ls
  451  rm hs_err_pid*
  452  clear
  474  vi New.java
  475  javac New.java 
  476  vi New.java
  477  javac New.java 
  478  java New 
  479  java -version
  480  ls
  481  eclipse 
  482  sudo apt-get update
  483  sudo apt-get dist-upgrade 
  484  sudo apt-get remove indicator-datetime 
  485  sudo apt-get purge indicator-datetime  //UNITY related package.
  486  sudo reboot
  487  eclipse 
  488  sudo apt-get dist-upgrade 
  489  sudo apt-get update
  490  sudo apt-get dist-upgrade 
  491  sudo apt-get update
  492  sudo apt-get dist-upgrade 
  493  sudo apt-get install -f
  494  sudo apt-get autoremove //after removing the indicator-datetime, the remaining package.
  495  sudo vim /etc/apt/sources.list //REMOVE THE CANONICAL-DX-TEAM-UNE PPA
  496  sudo apt-get dist-upgrade 
  497  sudo apt-get update 
  498  sudo apt-get dist-upgrade 
  499  sudo apt-get install -
  500  sudo apt-get install -f

---

### Post by neojames on 2010-06-14
redshift is working again (I realised it had died earlier on today and it gave a smiler error to eclipse), however eclipse still doesn't run! :(

---

### Post by defrex on 2010-06-15
Same here, for what it's worth. 

I tried vnkatesh's potential solutions, but I didn't have that repo installed, I didn't have indicator-datetime installed, I had already autoremoved, and a dist-upgrade didn't help.

It seems a recent update killed it. Yesterday I remember installing a very long list of updates though.

Since Android development is my job and it relies on Eclipse, I really need a solution for this. I'll post back if something works.

---

### Post by defrex on 2010-06-15
There seems to be a bug about this here:

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474)

---

### Post by defrex on 2010-06-15
quick-fix: run it with sudo

Clearly no good long-term, but it'll let me get back to work.

---

### Post by vnkatesh on 2010-06-15
Seems like a serious bug that they've pushed to the repos.

Try removing appmenu-gtk. I remember that being 'autoremoved' after I took down indicator-datetime.

---

### Post by neojames on 2010-06-16
Thank you! It works! Now I can go back to learning Java!

---

### Post by kelvinator on 2010-08-13
The solutions suggested here did not work for me. Instead I downloaded the most current version of Eclipse from their website (eclipse.org). That app is working without any problems so far.

3.6 from eclipse.org is newer than the version in Synaptic.

[QUOTE=neojames;9454021]Whenever I start Eclipse I get the splash screen, until the loading bar starts then it crashes. When I run it in terminal I get the following error:-

** (Eclipse:3847): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed

---

