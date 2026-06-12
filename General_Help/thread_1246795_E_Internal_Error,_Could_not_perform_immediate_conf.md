---
title: "E: Internal Error, Could not perform immediate configuration (2) on libc6"
date: 2009-08-22
forum: General Help
---

### Post by jwmollman on 2009-08-22
When I try to perform a system update via "sudo apt-get update" followed by "sudo apt-get upgrade" I get this error:

[http://ubuntu.pastebin.com/f7a967312](http://ubuntu.pastebin.com/f7a967312)

I tried to opened Synaptic but was presented with an error message saying I have around 23 broken packages on my system. I went to "Edit > Fix Broken Packages" then clicked "Apply" but I am given the error of:

> 
E: Internal Error, Could not perform immediate configuration (2) on libc6
When I run "sudo dpkg --configure -a" I get:

> 
john@john-eeepc:~$ sudo dpkg --configure -a
john@john-eeepc:~$ 
After that, I tried to run "sudo apt-get update" and then "sudo apt-get upgrade -f" but was given this:

[http://ubuntu.pastebin.com/f71d3323c](http://ubuntu.pastebin.com/f71d3323c)

I feel like I keep running in circles and I don't know what to do. I've tried looking on numerous forums, including the Ubuntu Forums, but all solutions for others have failed me. Any help would be greatly appreciated.

Thanks,
John

---

### Post by lazy adventurer on 2010-04-09
This happened to me when I accidently started installing again after one installation of debian, and aborted the second installation midway. But this can be repaired.

First try to install libc6 manually using dpkg. Do

```
cd /var/cache/apt/archives
sudo dpkg -i libc6-xxxx.deb
```

where xxxx represents whatever latest version apt has downloaded.
If installation fails in this way, then you will at least see a more detailed reason. If the reason is related to dependency, try

```
sudo dpkg --force_depends -i libc6-xxxx.deb
```

If it still fails, and shows some error like 'a non-dpkg version of the package has been found on your system' then what you do is:

1. Find the existing libc6 libraries present on your system:
```
find /lib -name "libc6-*.so*"
```
2. Here is the tricky part -- you have to remove these libraries in order for the new installation of libc6 to succeed. But libc6 is a very basic library for your system, and if it is not present, even basic commands like ls and cp won't work. So you back-up your libc6 libraries by changing their names to libc6.so.bak or something like that. 

After that, use the LD_PRELOAD environment variable for each and every command you issue, until you have installed the new libc6. Set the value of this variable to the full path to any of the libaries you have backed up. For example, if you have backed up libc6.so to /lib/libc6.so.bak then you install libc6 with

```
LD_PRELOAD=/lib/libc6.so.bak sudo apt-get install libc6
```

or (for csh)

```
setenv LD_PRELOAD /lib/libc6.so.bak
sudo apt-get install libc6
```

3. If you have done step 2. correctly, you can now unset LD_PRELOAD, and go back to

```
sudo apt-get install -f
```

for fixing the dependencies.

---

