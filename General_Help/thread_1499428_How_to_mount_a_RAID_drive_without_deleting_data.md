---
title: "How to mount a RAID drive without deleting data"
date: 2010-06-01
forum: General Help
---

### Post by jokerdave on 2010-06-01
Hi All, 

I had to recently reinstall ubuntu because 10.04 started acting up on me. I reinstalled 9.04 but I don't know how to mount my RAID drive without messing with the data that's already on there. I have the UUID for the RAID but fstab isn't able to find it. I also previously used RAID software but I don't remember which one I used. Any suggestions for how to mount my drive so that ubuntu can see it? Thanks.

---

### Post by ronparent on 2010-06-01
What flavor od raid (hardware, software, fakeraid)?

---

### Post by jokerdave on 2010-06-02
It's software based. I just forget which one I used.

---

### Post by ronparent on 2010-06-02
Mdadm is the standard package for administering software raids in ubuntu. Although that is likely what was used, if you actually have a software raid, it is not automatically installed when 9.04 is installed if you used the standard desktop version. The 'alternate' install cd would have recognized the presence of a raid on your system and assisted you in properly installing it. You probably should have reinstalled using that.

---

### Post by jokerdave on 2010-06-03
> **ronparent said:**
> Mdadm is the standard package for administering software raids in ubuntu. Although that is likely what was used, if you actually have a software raid, it is not automatically installed when 9.04 is installed if you used the standard desktop version. The 'alternate' install cd would have recognized the presence of a raid on your system and assisted you in properly installing it. You probably should have reinstalled using that.

What is this "alternate" install cd you speak of? Can I download it off the site? I'm installing via usb stick since I don't have a DVD drive on that computer.

---

### Post by ronparent on 2010-06-03
Same source as the desktop version, except the alternate install - [http://www.ubuntu.com/](http://www.ubuntu.com/)

---

