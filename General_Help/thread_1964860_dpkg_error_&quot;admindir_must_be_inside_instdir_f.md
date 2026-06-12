---
title: "dpkg error: &quot;admindir must be inside instdir for dpkg to work properly&quot;"
date: 2012-04-24
forum: General Help
---

### Post by dpdonny on 2012-04-24
Relatively new to embedded Linux, so be kind. :)

My goal is 'install' the arm-linux-gnueabi ARM toolchain package binaries into a directory other than /usr. Why would I want to do that? Good question. The answer is control over our embedded applications build environment. My company would like to keep the toolchain binaries stored in git repositories to be used when building our embedded application.

I'd rather download the arm-linux-gnueabi binaries that downloading and building the source. Why? Because the binaries exist.

I wish there was an 'apt-get install <package> instdir=XXX', but there isn't, so I am trying to use dpkg to dowload the package and install in my own directory. It worked OK for a few of the packages,but getting the following error in a couple of them.

My questions: 
Why am I getting the error below? 
Am I properly using dpkg to 'install' a package in a different directory other than /usr? 
Is there another option?

Thanks for any help you can provide.
I get the same error for either of these commands
# sudo dpkg -i --instdir=./mydir gcc-4.5-arm-linux-gnueabi_4.5.2-8ubuntu3cross1.47_i386.deb
# sudo dpkg --instdir=./linaro --unpack g++-4.5-arm-linux-gnueabi_4.5.2-8ubuntu3cross1.47_i386.deb

(Reading database ... 134070 files and directories currently installed.)
Unpacking gcc-4.5-arm-linux-gnueabi (from gcc-4.5-arm-linux-gnueabi_4.5.2-8ubuntu3cross1.47_i386.deb) ...
dpkg (subprocess): admindir must be inside instdir for dpkg to work properly
dpkg: error processing gcc-4.5-arm-linux-gnueabi_4.5.2-8ubuntu3cross1.47_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 gcc-4.5-arm-linux-gnueabi_4.5.2-8ubuntu3cross1.47_i386.deb

---

### Post by bacalfa on 2012-12-20
Hey there!

Did you get a solution to your problem? I have the same problem. I downloaded an .rpm file, converted it to .deb with alien and then tried to install it in a specific directory. But I got the same error message as you did.

Couldn't find any answers after googling about this.

Thanks!


Bruno

---

