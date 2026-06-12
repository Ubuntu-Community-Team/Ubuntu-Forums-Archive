---
title: "can't get canon pixma ip1500 to work in 9.10"
date: 2009-11-02
forum: General Help
---

### Post by ucbts on 2009-11-02
i'm trying to follow the instructions laid out here: [http://ubuntuforums.org/showthread.php?t=487890](http://ubuntuforums.org/showthread.php?t=487890), but i'm unable to install pstocanonbj.  i get an error message saying 
The following packages have unmet dependencies:
  pstocanonbj: Depends: libcupsys2 (>= 1.2.3)

any ideas what do do from here?

---

### Post by b3125312k on 2009-11-12
I'll tell you my story, as I struggled with this problem.
0. install libcups2-dev: sudo aptitude install libcups2-dev
1. add to the sources.list "deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./" and "deb-src http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./"
2. install libcnbj and bjfilter: sudo aptitude install libcnbj-2.5 bjfilter-2.5
3. install dpkg-dev: sudo aptitude install dpkg-dev
4. get sources of pstocanonbj: apt-get source pstocanonbj
5. set current dir to pstocanonbj-3.3/ : cd pstocanonbj-3.3/
6. configure it: ./configure
7. make it: make
8. install it: sudo make install
9. copy or link pstocanonbj filter from "/usr/local/lib/cups/filter/pstocanonbj" to "/usr/lib/cups/filter/pstocanonbj"
enjoy!

---

### Post by DanInKtown on 2009-12-15
**bravo!**

---

### Post by Kunomad on 2010-01-19
Thank you so much!

I'm now fiddling around with Linux for 2 years and have never got my iP1500 to work - not even with takushi's instructions... 

Googling the pstocanonbj-install error above, i found this thread and just followed your steps.

**It Works!!!!**

---

### Post by b3125312k on 2010-02-04
I'm glad I could help.

---

### Post by sosky on 2010-02-08
hi,

I get this error:

jordan@jordan-desktop:~$ sudo apt-get source pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/mambo.kuhp.kyoto-u.ac.jp_%7etakushi_ubuntu_._Sources - open (2: No such file or directory)
jordan@jordan-desktop:~$

---

### Post by aboud on 2010-03-17
Not over here ..
after I went through all steps, the driver is finialy in the list but the printer isn't working.

---

### Post by Jonodaigle on 2010-03-23
Hi there, again I am not to savy with ubuntu but quickly learning, i am getting the identical error as sosky, but I am also fussy on the rest of the steps after there... any help would be much appreciated.

---

### Post by thane1 on 2010-06-17
> **b3125312k said:**
> I'm glad I could help.


You Certainly Did!!!!!!!!!!  I'm getting lucid running here on my parents' computer with their old Canon Pixma MP130.  Was having no success with the installation as I couldn't get the iP1500 driver installed.  Your solution worked great!  Many thanks.

---

### Post by TheCrema on 2010-08-18
Many thanks mate, I was about to give up on my mp130 and thanks to your ip1500 installation guide it works like a charm now :D

---

### Post by boxie on 2010-08-18
I am using 64bit 10.04LST and I am not able to install the drivers using the steps in this thread.

at step:
4. get sources of pstocanonbj: apt-get source pstocanonbj

I get an error:
E: Could not open file /var/lib/apt/lists/mambo.kuhp.kyoto-u.ac.jp_%7etakushi_ubuntu_._Sources - open (2: No such file or directory)


hope that someone can help me, lest I get a printer that has proper support on linux.

:KS

---

### Post by jerimiahgentry on 2011-02-08
Hello! Thanks for the detailed instructions. I am still having some trouble here:

I say:

sudo aptitude install libcnbj-2.5 bjfilter-2.5

and it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  libcnbj-2.5 
0 packages upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
Need to get 0B/5,983kB of archives. After unpacking 10.8MB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libcnbj-2.5 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":

And I say: Yes

And it says:

Writing extended state information... Done
(Reading database ... 129138 files and directories currently installed.)
Unpacking libcnbj-2.5 (from .../libcnbj-2.5_0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcnbj-2.5_0-1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/bjlib/bjfilterpixmaip1500.conf', which is also in package bjfilter-pixmaip1500 0:2.50-3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 /var/cache/apt/archives/libcnbj-2.5_0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done



What's my next point of action? 

Thank you for your assistance.

Jerimiah

---

### Post by szydra on 2012-02-19
[FONT=Arial Black]b3125312k>> Thank you so much! It works for me perfectly in Oneiric 32 bit.

jerimiahgentry>> Remove the package bjfilter-pixmaip1500--it should help.[/FONT]

---

