---
title: "package dependencies"
date: 2012-06-11
forum: General Help
---

### Post by keith234 on 2012-06-11
Hi Everyone

I'm running Ubuntu 12.04 and have started getting problems loading software - always getting package dependencies errors. This happened when I tried to load Audacity:
  
The following packages have unmet dependencies:

audacity: Depends: audacity-data (= 2.0.0-1) but 2.0.0-1 is to be installed
          Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
          Depends: libavformat-extra-53 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
          Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
          Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
          Depends: libflac++6 (>= 1.2.1) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.32.1-0ubuntu2 is to be installed
          Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is to be installed
          Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113-2~) but 19+svn20111121-1 is to be installed
          Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.12.1) but 2.8.12.1-6ubuntu2 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.12.1) but 2.8.12.1-6ubuntu2 is to be installed

I have tried google searching this but am getting more confused...any help appreciated

---

### Post by forrestcupp on 2012-06-11
In the terminal, have you tried
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by keith234 on 2012-06-11
Hi Forestcupp

Thanks for replying...just tried that but still getting same problem. 

Cheers
Keith

---

