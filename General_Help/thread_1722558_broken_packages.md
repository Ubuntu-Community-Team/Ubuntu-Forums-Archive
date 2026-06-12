---
title: "broken packages"
date: 2011-04-05
forum: General Help
---

### Post by Johnny420 on 2011-04-05
I was trying to install ffmpeg and keep getting this return and I dont understand what I need to do to fix this.

~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libavdevice52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libavfilter0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libavformat52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavformat-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libavutil49 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavutil-extra-49 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libpostproc51 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libpostproc-extra-51 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libswscale0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libswscale-extra-0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
E: Broken packages

---

### Post by plucky on 2011-04-06
This is a bug with update-manager

See [Launchpad Bug Report](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114)

Good Luck

p.s. Launchpad is going down for maintenance in 8 minutes.

---

### Post by Johnny420 on 2011-04-07
Thanx 

Today my update manager gave me the updates I needed

---

