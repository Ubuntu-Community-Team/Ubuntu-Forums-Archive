---
title: "Mouse pointer not working properly in VMware Workstation"
date: 2011-08-24
forum: General Help
---

### Post by Bit Hacker on 2011-08-24
Hey guys. I installed Ubuntu 11.04 today in vmware workstation 7.1.3 build-324285, with Windows 7 as host. My mouse is not working properly in it. It won't point at where it should be pointing. I installed vmware tools and that also didn't help. Googling did result in something related to 'vmmouse' [VMwareKB]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=5739104") but Ubuntu 11.04 doesn't use xorg.conf so I donno how to solve this. Any idea? Here is the video of the problem. [http://www.youtube.com/watch?v=F_WQHm5Oabc](http://www.youtube.com/watch?v=F_WQHm5Oabc)

---

### Post by duke.tim on 2011-08-24
Sounds like a vmware driver problem, I'll see if I get the error after installing 11.04 ...time to reboot!
What is the hosting OS?

---

### Post by searchfgold6789 on 2011-08-24
I also have the same problem.
Workaround:

[LIST=1]
[*]Un-Capture the mouse.
[*]Hover the mouse pointer directly over the place where it is in the VM.
[*]Capture the mouse.
[/LIST]
I hope this helps!

---

### Post by duke.tim on 2011-08-24
I do not get a mouse error. Maybe like mentioned above you need to change some settings

[IMG]http://i816.photobucket.com/albums/zz83/duke_tim/Capture.jpg[/IMG]

---

### Post by Bit Hacker on 2011-08-25
The host is Windows 7. Take a look at the video of the problem. [http://www.youtube.com/watch?v=F_WQHm5Oabc](http://www.youtube.com/watch?v=F_WQHm5Oabc) . This problem occurred even when I booted into ubuntu live.

---

### Post by Bit Hacker on 2011-08-27
bump?

---

### Post by duke.tim on 2011-08-27
Try changing the screen resolution, i've seen this problem in ubuntu when using multiple screens... it might help in VMware too.

If VMware has an option to set the screen resolution try changing that too (preferably to match Ubuntu)

---

### Post by duke.tim on 2011-08-30
Check this thread out looks like you may have a similar problem
[http://communities.vmware.com/message/775050#775050](http://communities.vmware.com/message/775050#775050)

---

