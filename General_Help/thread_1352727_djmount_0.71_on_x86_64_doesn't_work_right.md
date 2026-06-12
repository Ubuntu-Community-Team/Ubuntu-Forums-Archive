---
title: "djmount 0.71 on x86_64 doesn't work right"
date: 2009-12-11
forum: General Help
---

### Post by jimbolaya on 2009-12-11
I ran into a bit of a problem today.  I wanted to get djmount running on my 64-bit installations, so I went and grabbed the source from sourceforge (since there doesn't seem to be any packages) and built it from source.

The problem is, once I "djmount <directory>" and look in the directory, I can only see my UPnP servers.  The servers themselves have no directory entries.  I know it works perfectly on 32-bit since I have a 32-bit installation using the same version (Jaunty).  

I would really like to be able to get to my UPnP servers through djmount on my 64-bit machines.  Am I not compiling it correctly?  Should I only be using 32-bit options?

James

---

### Post by shoeman22 on 2010-01-26
I'm in the same boat.  I have a 32 bit karmic install that mounts upnp just fine, but the 64 bit just shows the folders.

I can't seem to get XBMC or Boxee to read upnp either as of late, so I've had to use my PS3 for streaming.  This works fine, but I'd much rather be able to do everything from within Boxee or XBMC if I can.

---

### Post by GixerPoD on 2010-04-18
I had exactly the same problem. It is a fault with the version of the libupnp source that is included with the dpmount download. 

A description of the fault and the fix (worked for me - 64-bit Karmic) is on [http://sourceforge.net/projects/djmount/forums/forum/475926/topic/1686772](http://sourceforge.net/projects/djmount/forums/forum/475926/topic/1686772)

The latest version of the libupnp source can be found in [http://sourceforge.net/projects/pupnp/files/](http://sourceforge.net/projects/pupnp/files/)

I had to also run "sudo ldconfig" after installing the new libupnp and djmount before djmount would run - it was reporting that it couldn't find the libupnp.so.3 file.

The sequence that worked for me was:
Download and unpack latest libupnp source.
Go to libupnp directory
./configure
make
sudo make install

Download and unpack djmount source
Go to djmount directory
./configure --with-external-libupnp --with-libupnp-prefix=/usr/local/lib/
make
sudo make install
sudo ldconfig

After that I could run djmount /media/upnp and it showed all of the device contents, not just the devices themselves.

---

### Post by spazzeri on 2013-03-26
I have another problem with djmount 0.71 on ubuntu 12.10, 64-bit.
It segfaults when I try to access a file; syslog contains something like:

djmount[13401]: segfault at 7fbc000001f0 ip 00007fbcc0684f0b sp 00007fbcba7299f0 error 4 in libupnp.so.6.3.1[7fbcc0674000+34000]

It used to work; the machine was running 12.04 ubuntu at the time.

---

### Post by wildmanne39 on 2013-03-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

