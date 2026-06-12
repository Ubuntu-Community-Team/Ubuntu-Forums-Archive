---
title: "Need help with my school computer lab (run ubuntu)"
date: 2009-10-08
forum: General Help
---

### Post by charliehorse55 on 2009-10-08
My school (K - 12) has a System 76 computer lab, and so far it has been great. However we need a way to use the Lego Mindstorms NXT program, which is so far only available for Windows and Mac.

I'm in grade 11 and am in charge of the computer lab as such I need to get this software running. 

I've looked at Wine but it does not support the NXT system.  I then looked into VM's but the complexity of the UI would confuse the 10 yr olds that have to use the NXT program. 

Thus, I'm looking for a way to run the VM without the GUI, or the windows screen. IE if it ran like Wine did, running the program in it's own window, that would be great. 


The lab is working great other than that though, if anyone wanted to know. It's filled with 15 of the System 76 Net tops. I've set up Open Office to always save files as .doc. The computers "nuke" themselves overnight, deleting firefox cache and documents folder. (Students aren't allowed to store data on the computers.)

But anyways, I really need to find a way to make this work.

Thanks in Advance,

--Evan

---

### Post by jbrown96 on 2009-10-08
Your best bet is virtualization. You can set up Windows in Kiosk mode and have NXT automatically start. This way they can't close the app or open new ones. Then use virtualbox and set up the VMs. Virtualbox can be run from the command line. I don't know the syntax, but you can find it online. Then create a bash script that just runs a virtualbox command that will launch the VM. You can create links on the desktop to it. This should be fairly straightforward.

My only concern is the nettop part. Will these be able to run virtualized windows? How much ram? While they CPUs don't need to support virtualization, it greatly helps performance.

---

### Post by alphaniner on 2009-10-08
There's also a legal issue.  Strictly speaking I think you need a license for each Windows VM, although I'm not sure how it works in an educational setting.

---

### Post by ajgreeny on 2009-10-08
Could you start the VM of windows with this Lego Mindstorms NXT program auto-running as a startup program, and maximised in the window's window, if you see what I mean.  That way when the windows VM starts all that would be seen would be the NXT window.

I hasten to add that I have never heard of NXT, nor Lego Mindstorms, so don't really know if this is possible, but it is certainly possible to have programs start automatically when windows boots normally, so I presume it must be possible in a VM as well.

---

### Post by Bradj47 on 2009-10-08
My parents are the leaders for the Lego Robotics club at my old elementary school and they use the very same NXT stuff. They tried finding ways to get it to run on both Solaris and Ubuntu under many different virtual machines and emulators but they had no success. They resorted to using Windows XP. But I would definitely use MacOS over Windows so if you have Macs available you won't have to use Windows. But as for getting it to run on Linux or Unix, I don't think there's any easy way.

---

### Post by charliehorse55 on 2009-10-08
thanks for all of the great ideas....

we have an site liscense for windows for the admin and other computers around the school, legally it's not a problem. 

The Net tops have 2 GB RAM, a Dual core hyperthreaded cpu @ 1.6 GHz and 80 GB HD.

I also need a way to pass a USB device straight to windows as it uses proprietary windows device drivers to connect to the NXT module. Or could I do it throught bluetooth? (NXT support it!)

jbrown96 you idea seems like the best. Could you point me at some resources on how to do this? While I have ~2 Yrs Experience with linux I've never used VMs. (I run windows 7 for games on my desktop along with Ubuntu 9.04 and arch)

Thanks,

--Evan

---

### Post by Sub101 on 2009-10-08
As someone who has tried to use the NXT software I have been unable to get it working in Linux.

On a side note I would take a look at the LabVIEW kit [here]("http://zone.ni.com/devzone/cda/tut/p/id/4435")

---

### Post by vancouverite on 2009-10-08
As a side note: if you haven't already, you should email LEGO and tell them about your problem.  Ubuntu is growing as an educational tool and they should be moving to support it.  I see a couple of people in this thread alone who have face the same challenge and LEGO needs to be made aware of that.  In fact, you should have everyone in your IT team email them!

These companies are service driven and will/do (or should) respond to customers.  This forum is certainly the best place for you to look for help, but with your ubuntu ([link]("http://en.wikipedia.org/wiki/Ubuntu_(philosophy)")) you can make life better for those that follow.

[http://service.lego.com/en-US/Contactus/Email.aspx](http://service.lego.com/en-US/Contactus/Email.aspx)

Van

---

### Post by macabrem on 2009-10-08
> **charliehorse55 said:**
> My school (K - 12) has a System 76 computer lab, and so far it has been great. However we need a way to use the Lego Mindstorms NXT program, which is so far only available for Windows and Mac.

I'm in grade 11 and am in charge of the computer lab as such I need to get this software running. 

I've looked at Wine but it does not support the NXT system.  I then looked into VM's but the complexity of the UI would confuse the 10 yr olds that have to use the NXT program. 

Thus, I'm looking for a way to run the VM without the GUI, or the windows screen. IE if it ran like Wine did, running the program in it's own window, that would be great. 


The lab is working great other than that though, if anyone wanted to know. It's filled with 15 of the System 76 Net tops. I've set up Open Office to always save files as .doc. The computers "nuke" themselves overnight, deleting firefox cache and documents folder. (Students aren't allowed to store data on the computers.)

But anyways, I really need to find a way to make this work.

Thanks in Advance,

--Evan

Have you tried posting this question in the System 76 support?  
[http://ubuntuforums.org/forumdisplay.php?f=341](http://ubuntuforums.org/forumdisplay.php?f=341)

Even though it isn't really a problem with System 76, they are really great about helping with all questions relating to System 76 over there.

---

### Post by charliehorse55 on 2009-10-08
I just found this. My problems have been solved. (this should still work in jaunty right?)

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by jbrown96 on 2009-10-09
Wow. Just spent a lot of time writing up a nice guide for Virtualbox. Seamless Virtualization is much better. Just make sure to do the host networking only, so there aren't any security repercussions.

---

### Post by M0nk3yM4n on 2010-07-13
How do you have the computers nuke themselves? And can you do it from the Ubuntu server? I need help managing computers at the university community center I work at and was wondering if I could use the method you used?

---

