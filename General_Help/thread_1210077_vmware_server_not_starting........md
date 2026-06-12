---
title: "vmware server not starting......."
date: 2009-07-11
forum: General Help
---

### Post by brettschwartz on 2009-07-11
currently using:

Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty



recently installed patches...... did a reboot and now vmware does NOT startup.....

I do the following:
brett@ubuntu:~$ vmware
@@PRODUCT_NAME@@ is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.


I then run:

brett@ubuntu:~$ sudo  /usr/bin/vmware-config.pl
[sudo] password for brett:
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]



for the life of me, I cannot find the NEW directory where this is installed.... I could of sworn I had this installed already....... I wouldn't know where to start and check this..... (C compiler)

Assistance would greatly be appreciated!

thanks
Brett

---

### Post by Jebtrix on 2009-07-11
Did you install:

```
sudo apt-get install build-essential
```

Yet?

---

### Post by brettschwartz on 2009-07-11
yes.....see below...


brett@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for brett:
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.




I have no clue where it installed to......

---

### Post by Lampi on 2009-07-11
I assume you somehow lost the symbolic link to your header files. You can check this with 'ls -la /usr/src/'

It should look like this:

```
lampi@kubuntujaunty:~$ ls -la /usr/src/

drwxrwsr-x 13 root src      4096 2009-06-28 19:08 .
drwxr-xr-x 12 root root     4096 2009-04-24 10:34 ..
lrwxrwxrwx  1 root src        31 2009-05-12 10:10 linux -> linux-headers-2.6.28-11-generic
```
if it doesn't you can add the symlink again with this command
```
sudo ln -s linux-headers-`uname -r` linux
```

---

### Post by brettschwartz on 2009-07-11
this is what I got.... After what you stated me to do....



brett@ubuntu:~$ ls -la /usr/src/
total 32
drwxrwsr-x  8 root src  4096 2009-07-11 00:08 .
drwxr-xr-x 13 root root 4096 2009-06-08 13:43 ..
drwxr-xr-x 22 root root 4096 2009-06-08 12:56 linux-headers-2.6.28-11
drwxr-xr-x  7 root root 4096 2009-06-08 13:31 linux-headers-2.6.28-11-generic
drwxr-xr-x  7 root root 4096 2009-06-08 12:56 linux-headers-2.6.28-11-server
drwxr-xr-x 22 root root 4096 2009-07-02 08:06 linux-headers-2.6.28-13
drwxr-xr-x  7 root root 4096 2009-07-02 08:06 linux-headers-2.6.28-13-generic
drwxr-xr-x  7 root root 4096 2009-07-11 00:08 rpm
brett@ubuntu:~$

---

### Post by Lampi on 2009-07-12
@brettschwartz: stupid me ... sorry! I was right about the problem you have, but the symbolic link has to be set like this:
```
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
```

Then check again 'ls -la /usr/src' to make sure it looks like my example up there. You seem to use the same generic kernel I do.

---

### Post by brettschwartz on 2009-07-12
Ok, did what you stated...... here's my output


brett@ubuntu:~$ ls -la /usr/src
total 32
drwxrwsr-x  8 root src  4096 2009-07-12 08:31 .
drwxr-xr-x 13 root root 4096 2009-06-08 13:43 ..
lrwxrwxrwx  1 root src    39 2009-07-12 08:31 linux -> /usr/src/linux-headers-2.6.28-13-server
drwxr-xr-x 22 root root 4096 2009-06-08 12:56 linux-headers-2.6.28-11
drwxr-xr-x  7 root root 4096 2009-06-08 13:31 linux-headers-2.6.28-11-generic
drwxr-xr-x  7 root root 4096 2009-06-08 12:56 linux-headers-2.6.28-11-server
drwxr-xr-x 22 root root 4096 2009-07-02 08:06 linux-headers-2.6.28-13
drwxr-xr-x  7 root root 4096 2009-07-02 08:06 linux-headers-2.6.28-13-generic
drwxr-xr-x  7 root root 4096 2009-07-11 00:08 rpm






I executed sudo vmware-config.pl

I get the following now:



brett@ubuntu:~$ sudo vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]




note: include directory......... in your code, it requested /usr/src/linux (not w/the include)  I'm trying to change the target directory and no dice.... (<sigh>)

---

### Post by Lampi on 2009-07-12
You don't need to change the target directory - all you need is the link to the header files - /usr/src/linux/include is a directory **inside** your kernel-header directory.

I didn't notice you use a server kernel - shouldn't be a problem though. With build-essentials installed and the symlink to your running kernel-headers you should be able to compile at least something. You could check you installed the headers for the server kernel:
```
apt-get install kernel-headers-`uname -r`
```

---

### Post by brettschwartz on 2009-07-12
I can't win...... (unbelievable...)




brett@ubuntu:~$ sudo apt-get install kernel-headers-`uname -r`
[sudo] password for brett:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.28-13-server

---

### Post by Lampi on 2009-07-12
package is called linux-headers-2.6.28-13-server

if it's already installed I'm out, try kernel 2.6.28-13-generic then

---

### Post by brettschwartz on 2009-07-13
ended up doing this....


sudo apt-get install linux-headers-`uname -r`
sudo vmware-config.pl


that worked!

hey I appreciate all the time you spent w/ me.... Thank you so much!

---

### Post by Lampi on 2009-07-14
no problem, apparently you installed build-essentials and changed your kernel image *afterwards* to the server edition. That's why you were missing the kernel-headers ;)

---

### Post by brettschwartz on 2009-07-14
thanks again for your help.... I GREATLY appreciate it!

---

### Post by Jago6060 on 2009-07-23
ok I have a related problem.  VMware server just suddenly stopped working, no idea why.  Its been running for a few months without issue.  So now its telling my that its installed but not properly configured.  so I went through the steps that you all suggested and somethign curious happened...

when I tried to add the symbolic link, then ran 'ls -la /usr/src' I got one line that looked like this...

linux -> /usr/src/linux-headers-uname -r

That's not supposed to do that...right?

---

