---
title: "Enable WebGl in Chrome"
date: 2012-03-25
forum: General Help
---

### Post by aura7 on 2012-03-25
I am able to enable it in firefox using the following method :

sudo apt-get install libosmesa6

and 

After installing above package open your browser and type about:config address bar and search for webgl.osmesalib now you need to add string type as /usr/lib/libOSMesa.so.6


WebGL is now enabled in firefox but not in chrome.


HOW TO ENABLE WEBGL IN CHROME.....?

---

### Post by imachavel on 2012-03-25
[LIST=1]
[*]Just run Chrome from a terminal enabling WebGL: *./google-chrome --enable-webgl*
[*]You can also **right-click** on your Google Chrome icon and choose **Properties**. Then, at the end of your target line, add *--enable-webgl*
[/LIST]


I am going to assume firefox is somehow set as the default browser and when you

sudo apt-get install libosmesa6
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libosmesa6
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,130 kB of archives.
After this operation, 10.1 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libosmesa6 i386 7.11-0ubuntu3 [1,130 kB]
Fetched 1,130 kB in 6s (168 kB/s)                                              
Selecting previously deselected package libosmesa6.
(Reading database ... 339499 files and directories currently installed.)
Unpacking libosmesa6 (from .../libosmesa6_7.11-0ubuntu3_i386.deb) ...
Setting up libosmesa6 (7.11-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

it installs webgl for firefox (is web gl something that works with plug ins to help opengl work with flash and other related codecs or something? Sorry, not familiar with it).

Now when I open google chrome(because right click and properties only works in windows)............ well, no webgl in the google wrench icon in under the hood, or any settings that I can find. Ok I see webgl DOES have something to do with your video api library. What a pain.... I'm reading through this:

[http://catchvar.com/webgl-in-chrome-10-on-ubuntu-1010](http://catchvar.com/webgl-in-chrome-10-on-ubuntu-1010)

and actually trying this all out right now:

glxinfo | grep render
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
danel@danel-Dimension-4700:~$ about:gpu
about:gpu: command not found
danel@danel-Dimension-4700:~$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms execstack ia32-libs sudo sh ati*.run  
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ia32-libs' has no installation candidate
E: Unable to locate package sh
E: Unable to locate package ati*.run
E: Couldn't find any package by regex 'ati*.run'


and as you can see it's not going to well. Well, my best guess is there is a config file somewhere that needs to be set so that google chrome opens by default. In windows whenever you open a new browser, windows asks if you'd like to set it as default. However you upgraded you video driver, and set webgl to work, it must have set it for fire fox. I always say I like Linux better then windows, but in some ways windows and mac are much simpler. My best estimate is to google how to set a config file somewhere that Ubuntu OS uses to set the default web browser you use. I only assume if you open a web page link and google chrome pops up, then when you enable webgl it will be set in a google.conf file instead of a firefox.conf file. If I'm wrong I'm wrong

best of luck

Also it'd be nice to know what version of Ubuntu you are using:

lsb_release -a in the terminal please, and please post return output syntax

---

### Post by aura7 on 2012-03-25
Thanks for the reply.

As of the version of ubuntu I am using 
**lsb_release -a **
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

**glxinfo | grep render**

direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2


WebGL is working perfectly fine in Firefox... I have checked some games too...

But, In Chrome I tried the method after reading the same URL
[http://catchvar.com/webgl-in-chrome-10-on-ubuntu-1010](http://catchvar.com/webgl-in-chrome-10-on-ubuntu-1010)
that you mentioned but I am still not getting webgl in chrome.

**about:gpu** on chrome url  is giving the following output
Graphics Feature Status
Canvas: Software only. Hardware acceleration disabled.
HTML Rendering: Hardware accelerated
3D CSS: Hardware accelerated
WebGL: Hardware accelerated
WebGL multisampling: Hardware accelerated

but in the log messages display in the same window under is giving the following errors
[3090:3090:726026434:ERROR:gl_surface_glx.cc(257)] : glXChooseFBConfig failed.
[3090:3090:726026574:ERROR:gpu_info_collector.cc(25)] : gfx::GLContext::CreateOffscreenGLSurface failed
[3090:3090:726026614:INFO:gpu_child_thread.cc(110)] : gpu_info_collector::CollectGraphicsInfo complete. success = 0
[3090:3090:728843726:ERROR:gl_surface_glx.cc(257)] : glXChooseFBConfig failed.
[3090:3090:728845445:ERROR:gl_surface_glx.cc(257)] : glXChooseFBConfig failed.

This is the error i am getting on the terminal too when I am starting chrome with the following parameters.
google-chrome --enable-webgl --allow-file-access-from-files --ignore-gpu-blacklist 

[3090:3090:728845445:ERROR:gl_surface_glx.cc(257)] glXChooseFBConfig failed.
[37:37:728845613:ERROR:command_buffer_proxy.cc(136)] Failed to initialize command buffer service.


The above error is what i am getting on terminal... 

The chrome version I am using is 17.0.963.83 (Official Build 127885)

In Windows I just updated the Intel Drivers and everything works fine in both the browsers but here I am getting problems. I too prefer linux but sometimes getting basic things done in linux like enabling graphics drivers becomes really messy.

---

