---
title: "Ubuntu 10.04 Firefox and Java vs. Formula1"
date: 2010-07-02
forum: General Help
---

### Post by taylorkh on 2010-07-02
I though this was a 64 bit issue - I rebuilt my PC with Ubuntu 10.04 32 bit and I still have the same issue.

The issue - Formula1.com has a feature called Live Timing which runs a java applet to show track timing and commentary during qualification and races. When I attempted to launch it in the 64 bit Ubuntu I got a blank window and that was it.

The apple does run on my netbook running Ubuntu 9.04 with the Icedtea plugin v.6b14-1.4.1 and Firefox v. 3.0.19.

It runs in Firefox v.3.6.6 on Win XP with Sun Java 1.6.0_20.

It will not run on Ubuntu 10.04 with Firefox v.3.6.6. I created a VMWare Virtual machine to do some testing. Here is what I tried:

1 - Installed the Icedtea package and it dependencies from Ubuntu repositories - about : plugins in Firefox shows java installed (essentially the same as the 9.04 netbook) but the app does not run.

2 - Replaced the virtual machine with a fresh copy and installed sun java from the Ubuntu repositories. Linked Firefox to the java plugin thusly
> cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.20/jre/plugin/i386/ns7/libjavaplugin_oji.so
about : plugins in Firfox does not show the java plugin and of course the applet does not run.

3 - Installed Icedtea package on top of the results of #2 - about : plugins shows Icedtea java plugin present but the applet does not run.

I am at a loss. Can anyone suggest anything else to try? I would like to follow the Silverstone race next weekend without having to run an XP VM

TIA,

Ken

p.s. Just did a little more testing - created a Jaunty (9.04) 32 bit VM - same as the netbook - and attempted to pull up Live Timing.  Firefox indicated a plugin was required but did not say what plugin. I installed the Icetea-pluigin package from the Ubuntu repositories and tried again. The Live Timing app works just fine.

What has broken in 10.04???

---

### Post by Wilf999 on 2010-07-24
I have exactly the same problem, except I'm trying to watch qualifying for the German grand prix.

I don't seem to have any working Java applets in 10.04, as I had a similar problem with the viewing results of the Le Mans 24 Hours on Autosport.com, which was also presented in a Java applet.

Guess which sports I like :D

Wilf

---

### Post by taylorkh on 2010-07-24
Hi Wilf999,

I have the German GP qualifying running in Firefox on my XP virtual machine. I will be interesting to see if Lewis Hamilton can pull off another miracle given that he lost a good part of practice after modifying his car against the tire wall on Friday.

Ken

---

