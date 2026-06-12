---
title: "Pkg to Update is Greyed Out - Can't Update"
date: 2012-03-19
forum: General Help
---

### Post by hbnmgr on 2012-03-19
In Update Mgr I only have 1 pkg. - [COLOR=Red]MULTIMEDIA PLAYER server, encoder, transcoder (ffmpeg)[/COLOR],
but it is greyed out and I can't select it. There are security issues it addresses so would like the update, but it will not/can not update due to it being greyed out.

Running: Ubuntu 11.10 - oneiric

Any suggestions?
Thanks!
hbnmgr

---

### Post by ajgreeny on 2012-03-19
Try ```
sudo apt-get update
sudo apt-get upgrade
``` in terminal and see if that solves the problem.

---

### Post by hbnmgr on 2012-03-19
Did that already. 
This Pkg is only one left but won't update because it is greyed out in the Update Manager window.

???

---

### Post by raja.genupula on 2012-03-19
yeah do that as above friend said . when you type 
```
sudo apt-get upgrade
```

look at the list of available updates for your system and check that are they similar with your update manager ? 

Let us know what you got . all the best .

---

### Post by hbnmgr on 2012-03-19
Here is the output;

```

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ffmpeg
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

That's the program alright. How do I get it to update/upgrade? 
It is still greyed out ?!?!?!?

FYI - this is what is state in Update Manager, under Changes,
for FFMPEG.

Changes for the versions:
Installed version: 4:0.7.2-1ubuntu1
Available version: 4:0.7.3-0ubuntu0.11.10.1

Version 4:0.7.3-0ubuntu0.11.10.1: 

  * Update to 0.7.3 to fix multiple security issues (LP: #911811):
    - SECURITY UPDATE: denial of service and possible code execution via
      malformed file containing QDM2 stream
      - CVE-2011-4351
    - SECURITY UPDATE: denial of service and possible code execution via
      malformed file containing VP3 stream
      - CVE-2011-4352
    - SECURITY UPDATE: denial of service and possible code execution via
      malformed file containing VP5 or VP6 streams
      - CVE-2011-4353
    - SECURITY UPDATE: denial of service and possible code execution via
      malformed VMD file
      - CVE-2011-4364
    - SECURITY UPDATE: denial of service and possible code execution via
      malformed file containing svq1 stream
      - CVE-2011-4579

-----------------------------------

---

### Post by raja.genupula on 2012-03-19
hi ok now do this and let us know what you got 

```
sudo apt-get dist-upgrade
```

all the best .

---

### Post by hbnmgr on 2012-03-19
Output;

```

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ffmpeg
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```Same!?!

---

### Post by hbnmgr on 2012-03-19
So,   What does "Kept Back" mean?

---

### Post by raja.genupula on 2012-03-19
ok do this 

```
sudo apt-get install ffmpeg
```

If its said already installed then do as 

```
sudo apt-get install --reinstall ffmpeg
```

---

### Post by hbnmgr on 2012-03-20
Did not say already installed, but here is output;

```

sudo apt-get install ffmpeg
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ffmpeg : Depends: libavcodec53 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libavcodec-extra-53 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavdevice53 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libavdevice-extra-53 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavfilter2 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libavfilter-extra-2 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavformat53 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libavformat-extra-53 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavutil51 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libavutil-extra-51 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libpostproc52 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libpostproc-extra-52 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libswscale2 (>= 4:0.7.3-0ubuntu0.11.10.1) but it is not going to be installed or
                   libswscale-extra-2 (>= 4:0.7.3) but 4:0.7.2.1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Broken Pkgs ???

---

### Post by raja.genupula on 2012-03-20
yeah now in terminal do as 
```
sudo apt-get install -f
```

---

### Post by hbnmgr on 2012-03-20
Here is the output;

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```But still don't know what that gets me? Should I Remove the Headers?
I hate being a Linux dumba**, what book do you recommend?

---

### Post by hbnmgr on 2012-03-20
No Reply, so - tried it anyway. This is my Output;

```

apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

``` 

I believe I'm Root - but - Now What???  I'm stumped ! ! !

---

### Post by ajgreeny on 2012-03-20
You seem to have the unstripped** libav*-extra-##** packages installed and the version of ffmpeg you are using (which version do you have installed?) seems to depend on the standard versions, ie the packages without the "extra" in the name.

It surprises me that this is happening as I thought the two versions of the libav* were interchangeable, but perhaps they are not.  I don't have ubuntu 11.10 running to try this out on at the moment, but I might try it on my xubuntu 11.10 later and will try to report back.

PS: Have you enabled the **medibuntu** repos in the past but now have them disabled?  The unstripped libav* packages come from medibuntu, or they do for Lucid which I am using, and if you have disabled the medibuntu repos it is possible that ffmpeg can not be updated as the unstripped libav* packages are not available to the system any more.

---

### Post by hbnmgr on 2012-03-20
> **ajgreeny said:**
> 
PS: Have you enabled the **medibuntu** repos in the past but now have them disabled?  The unstripped libav* packages come from medibuntu, or they do for Lucid which I am using, and if you have disabled the medibuntu repos it is possible that ffmpeg can not be updated as the unstripped libav* packages are not available to the system any more.

Answer: NO, but I am running Ubuntu Studio installed from DVD, and recently updated.
Also, FYI - I'm running XFCE Desktop as it seems to be the only one available, but I like it anyway.

---

### Post by ajgreeny on 2012-03-21
> **hbnmgr said:**
> Answer: NO, but I am running Ubuntu Studio installed from DVD, and recently updated.
Also, FYI - I'm running XFCE Desktop as it seems to be the only one available, but I like it anyway.
Something strange going on in that case, perhaps more related to ubuntu-studio repos, which I assume are different to standard ubuntu.

I have just looked at my installation of Xubuntu 11.10, and installing both ffmpeg and the various libav*-extra packages went with no problems at all.
The package versions I installed were:-
```
ffmpeg_4%3a0.7.3-0ubuntu0.11.10.1_i386.deb
libavcodec-extra-53_4%3a0.7.3ubuntu0.11.10.1+medibuntu1_i386.deb
libavdevice-extra-53_4%3a0.7.3ubuntu0.11.10.1+medibuntu1_i386.deb
libavfilter-extra-2_4%3a0.7.3ubuntu0.11.10.1+medibuntu1_i386.deb
libavformat-extra-53_4%3a0.7.3ubuntu0.11.10.1+medibuntu1_i386.deb
libavutil-extra-51_4%3a0.7.3ubuntu0.11.10.1+medibuntu1_i386.deb
```
all of which appear to be one version above those you have available.

Perhaps it is worth enabling the [medibuntu]("http://www.medibuntu.org/") repos for your system to see if that helps.

---

### Post by hbnmgr on 2012-03-21
Unacceptable !!!

---

### Post by hbnmgr on 2012-03-21
Perhaps it would help to move this thread to the Ubuntu Studio thread ! ! !

Can someone / moderator accomplish this for us please ? ? ?

Thanks!

---

### Post by ajgreeny on 2012-03-21
> **hbnmgr said:**
> Unacceptable !!!
What is unacceptable?

---

### Post by hbnmgr on 2012-03-21
Your answer was unacceptable. 

Tried it in Synaptic - and That worked, apparently that version needed to be removed. Selected a few others and installed them instead.

SOLVED.

---

### Post by whiskers751 on 2012-03-22
Try using aptitude!
```
sudo apt-get install aptitude
sudo aptitude
```
That should show your problems...

---

