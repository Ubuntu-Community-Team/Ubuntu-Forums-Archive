---
title: "Vmware Workstation disappears"
date: 2011-04-29
forum: General Help
---

### Post by Dr. Friday on 2011-04-29
Well my problem is with Vmware Workstation after upgraded from Ubuntu 10.10 to 11.04. Vmware dissapears when i do anything in it. I have posted a video for those who want to see the problem in action
Oh and i don't know if this is revlant but i have a syncmaster t240HD as my monitor but Ubuntu says its an Unknown Monitor.

Video
[http://www.youtube.com/watch?v=INn90e98Mbk](http://www.youtube.com/watch?v=INn90e98Mbk)


Update: Catalyst Control Center reports my monitor and the settings correctly.

---

### Post by craigni on 2011-04-30
I have *exactly* the same problem.  I've tried everything, to no avail.  It's really frustrating.

---

### Post by Dr. Friday on 2011-05-01
Nobody can  help me? :( thats depressing...

---

### Post by buckmaster60 on 2011-05-01
Having the same issue.  Searching for an answer.

---

### Post by buckmaster60 on 2011-05-01
Try this.  [http://ubuntuforums.org/showthread.php?t=1744378](http://ubuntuforums.org/showthread.php?t=1744378)

So far it has helped my situation.

---

### Post by Dr. Friday on 2011-05-02
> **buckmaster60 said:**
> Try this.  [http://ubuntuforums.org/showthread.php?t=1744378](http://ubuntuforums.org/showthread.php?t=1744378)

So far it has helped my situation.
ok it will let me open it now... but as soon as i start the virtual machine it vanishes like harry houdini.. it is very frustrating

By open i mean once i open the virtual machine in vmware i can edit the VM's settings and such.. i couldn't do that before.

---

### Post by Dngoins on 2011-05-02
I had the same problem, the link above worked for me...

I had to modify vmware instead of vmplayer.

Just follow the link and change /usr/bin/vmware for vmware workstation, change vmplayer for vmware player...

HTH

---

### Post by Dr. Friday on 2011-05-03
I did follow the instructions... Vmware workstation now closes when i start a virtual machine.it closes due to an unknown error.

---

### Post by Jarret on 2011-05-26
You have to edit the file "/usr/bin/vmware" in addition to "/usr/bin/vmplayer" 

So add "export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0" after the copyright notice in both and you should be good to go.

This problem was driving me nuts all day..

---

