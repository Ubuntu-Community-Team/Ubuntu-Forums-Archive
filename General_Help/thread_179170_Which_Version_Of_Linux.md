---
title: "Which Version Of Linux?"
date: 2006-05-19
forum: General Help
---

### Post by Signsoflife on 2006-05-19
Hiya. 

Basically i'd like to run linux from an external drive but i'm unsure which version would be most suitable and lightest on resources on my laptop, which i use for music(1.6ghz m,1gb ram). I have run the live cd twice but eah time its been 45 minutes to an hour apparently installing. Is this normal? If it is i'll run it again, i'm just concerned about it not working or having bugs and time is an issue right now. 

My pc is down so i'm having to use the laptop till i can get it fixed and i'm trying to finish a project which has reached it's deadline for completion.

So which one would give me the most trouble free operation and is most laptop friendly in your experience?

Ubuntu seems ideal but with three different versions:-? 

Thanks in advance.

SOL.

It would be for wordprocessing, graphics and possibly video. Cheers.

---

### Post by Sef on 2006-05-19
> (1.6ghz m,1gb ram)

That is not a lightweight laptop.  Ubuntu will do just fine.

> I have run the live cd twice but eah time its been 45 minutes to an hour apparently installing. Is this normal?

That is not normal at all.  I should take under 5 minutes to be up and running.  This may indicate you have a problem installing.  It depends on what is causing the problem: the download, the burn,  the cd, or is it hanging up on some hardware.  What version are you using:  Breezy, Dapper or other?  Dapper will be stable in less than two weeks, and it has much better support.

> Ubuntu seems ideal but with three different versions

Go with Ubuntu which has a Gnome interface.  It has more support in the forums.

---

### Post by Signsoflife on 2006-05-19
Thanks Sef. It is breezy. I just realised, i downloaded the image from the european mirror instead of uk. Would this make a difference? It was stuck on a screen in dos for ages with a repeating message but with a different code in brackets on each line. I think the cd had completed the live install prior to this. I'd have to run it again to tell you exactly what the message said. Also, i used iso recorder to burn the image and the disc used is an imation cd-r. 

I'll rerun the cd if you want to know what the message is.

Cheers.

SOL.

---

### Post by Signsoflife on 2006-05-19
Here is the message:

[4294843.771000]r8169:eth0:PHYreset until link up

This repeats itself continually(?)

The cd gets to the stage where the ubuntu logo appears and the processes appear underneath it. However when it gets to Starting hotplug subsystem it switches to the dos screen still saying Starting hotplug subsystem. Followed by the above message.

What would cause this?

I ran the cd rom integrity utility and the result said the cd is 'valid'.
So i guess the cd is fine.

So assuming i can't get it to work what's a good alternative to ubuntu? I really need to get on with my thing. It never seems to be straightforward, oh well.



Sol

---

### Post by skippy81 on 2006-05-19
The error message is network related.  

8139 = realtek network card model
eth0 = the name linux gives to a working network interface.  

Do you have the network connected? If so try removing it.

Any chance you could post the exact model number of your laptop and also tell us whether the network card is built in, or is slotted into a pmcia slot.

Thanks

---

### Post by Signsoflife on 2006-05-19
I have two network adapters.

But i recognise it now,it's the ethernet and it's built in. Full name: Realtek RTL8169/8110 Family Gigabit Ethernet NIC.

The laptop is an M551G and it's made by fortune technology([http://www.fortunetechnology.co.uk/)](http://www.fortunetechnology.co.uk/)). When you say remove it do you mean if its external or uninstall/disable it? I'll try ubuntu again with it disabled and unplug the net. I'll get back to you with the results.

Sol.

---

### Post by Signsoflife on 2006-05-19
I went into the bios when i rebooted and removed the network adapter from the boot order but to no avail. Is there a work around/command line to ignore the adapter when running the live cd?

What else could i run, even temporarily. Is this the right place to ask? This is taking up far too much time. I need to crack on with it. Technology, meh!

Thanks

Sol

---

### Post by confused57 on 2006-05-19
You could try Ctrl+C, which should skip the step it's hanging on.

---

