---
title: "Help with installing a driver with a makefile"
date: 2009-07-15
forum: General Help
---

### Post by RobertQQ on 2009-07-15
Hi all!!

I am trying to install a driver for my wireless card on a desktop computer with ubuntu 9.04 but am having problems. I downloaded the package the driver is in and unpacked it. It created two folders and a makefile. I've tried and googled just about everything I can think of to get this to run but with no success. Here are some things I have tried:

I made sure I had Build essentials and Linux Headers.

I've used ./ , make, and make install in about everyway imaginable.

Tried these commands, sudo chmod +x filename, and sudo chmod +x configure.

I know I'm probably just doing something wrong or not doing something right but I am out of things to try. Any help on this will be greatly appreciated. Also, below is a copy of the makefile. Thanks!!


# $Id: Makefile_kbuild_portsrc,v 1.1.2.4 2008/05/02 18:33:39 Exp 


$obj-m              

+= wl.owl-objs            

:= wl-objs            

+= src/wl/sys/wl_linux.owl-objs            

+= src/wl/sys/wl_iw.owl-objs            

+= src/shared/linux_osl.oEXTRA_CFLAGS       

:=EXTRA_CFLAGS       

+= -I$(src)/src/includeEXTRA_CFLAGS       

+= -I$(src)/src/wl/sysEXTRA_LDFLAGS      

:= $(src)/lib/wlc_hybrid.o_shipped


Thanks Again!

---

