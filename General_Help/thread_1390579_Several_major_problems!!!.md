---
title: "Several major problems!!!"
date: 2010-01-25
forum: General Help
---

### Post by Futile10 on 2010-01-25
Hi all,
 
I have a Vaio CS36GJ notebook with Ubuntu 9.10 (32 bit) installed.  Everything seems to be fine except for the following problems (which I consider to be a major headache):
 
1. When I suspend from the menu or when I close my laptop the keyboard freezes (sometimes the mouse as well).
 
2. My camera does not work (the touch pad that controls it does not work as well - this includes volume control, play - stop - pause, and capture (for taking stills via the built-in camera).
 
3. The function keys for volume work fine, but not for brightness, LCD external monitor, etc...
 
I have searched for my notebook model to find out solutions to the above, but after spending the past week searching I could not find anything.  This is really frustrating as I do not want to revert back to using Winblows.  I have always been a big supporter of open source!  
 
Please, I am not a geek and have little knowledge (basically none) of Linux and specifically the OS I am using (Ubuntu 9.10 32 bit).
 
By the way, I have a 64 bit machine, but ran into snags with my nvidia graphics card...but funnily enough the 32 bit version works fine...well...aside from the above problems!
 
PLEASE!  I really need some help!  I do not know where else to turn...
 
Thanks so much!

---

### Post by Rocket2DMn on 2010-01-25
This looks like a newer model laptop, is that correct?  Sometimes the support for new hardware lags a bit since the release cycles need to freeze the kernel version at some point before a new Ubuntu version comes out.  For these types of problems, I would suggest filing bug reports on Launchpad - the sooner you do this, the better.  This allows more time for these problems to be fixed before the next Ubuntu release.

There is a link in my signature for information about filing bug reports.  It includes some background information, so don't be afraid of all the text.  In your case, you will want to file a separate report for each problem you listed, and file them against the "linux" package, which is for the kernel.  If you post links here to the reports you file, I would be happy to perform the bug triage for you to help expedite the process of reaching a developer.

If you want to get a head start, most of these are problems you can test with a LiveCD of the current development release of Ubuntu, Lucid Lynx.  The Alpha2 version is availabe [here]("http://www.ubuntu.com/testing/lucid/alpha2").  The advantage of using a LiveCD is that you don't need to make changes to your existing install.  If you do test this out, be sure to include the results in your bug reports.

I am happy to help you with this process, so please don't hesitate to ask!

---

