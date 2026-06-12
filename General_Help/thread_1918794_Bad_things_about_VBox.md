---
title: "Bad things about VBox?"
date: 2012-02-01
forum: General Help
---

### Post by layers on 2012-02-01
I couldn't find anything on this topic online - what is bad about running VBox's guest OS as your main OS for your usage, on top of Ubuntu?

Being a laptop, I guess battery performance will be terrible. I haven't noticed any lag, but would the temperatures inside go higher => higher fan speed and more overheating => hardware parts would last a year less? What are some other negatives?

---

### Post by Dave_L on 2012-02-01
It's too easy to accidentally destroy large amounts of data.  Once my finger slipped while I was using the VBox menus and I deleted a VM, which was annoying. I think the interface needs more confirmation prompts for destructive actions.

---

### Post by QIII on 2012-02-01
You would typically want to do it the other way around.  Run VBox from your primary OS with the other OS inside it.  

Be that as it may.

When running VBox you have resources being consumed by the primary and by the virtual machine.  That doesn't exactly mean you are expending the same wattage as two separate machines because the host is handling a lot of the work.  But it's more than either alone, so you would be drawing more power and, therefore, running your battery down more quickly.

If you run your primary as host, then you can shut down the virtual when you don't need it and spare your battery.

---

### Post by layers on 2012-02-01
I see.

I guess, my question can also be rephrased as: Would the life of the electronic devices inside your machine be lessened if your CPU usage is on a higher average?

---

### Post by QIII on 2012-02-01
The simplistic answer is "Yes", but I don't think it would be easy to quantify.

All things mechanical and electronic are subject to a shorter service life when used more/faster/longer/under higher load conditons.

I have several machines I run distributed scientific applications on.  Rosetta@home, for instance.  I toasted the mobo on that machine a month or so ago and had to replace it because I had been running the quad core CPU full throttle 24x7 for about 6 months.  Blew a couple of caps.  Thankfully, the CPU survived.  I have a massive hsf on it and whatever damage happened to the mobo didn't get to the CPU in a way that would have toasted it regardless of the hsf.

---

### Post by ingramproductions on 2012-02-01
I don't think the opensource edition has usb support

---

### Post by ottosykora on 2012-02-02
At work , we replaced 8 physical servers (big HP machines) with one single physical machine running all our servers in virtual mode, well vmware to be honest.

Transfer did happen within 7hrs and some of the servers are for security purposes. All works perfect.

I remember that we had laptops at some time, booting to linux, but then starting virtual machine with w2k as standard system. There were reasons behind it, some mail tasks were not possible then with windows, connect to special server etc.
All worked well, but in such setup (laptop, people work on it) was more likely to break, we had to restore the vm often from backup, as it is easy to break it in such operation.

---

### Post by sudodus on 2012-02-02
> **layers said:**
> I couldn't find anything on this topic online - what is bad about running VBox's guest OS as your main OS for your usage, on top of Ubuntu?

Being a laptop, I guess battery performance will be terrible. I haven't noticed any lag, but would the temperatures inside go higher => higher fan speed and more overheating => hardware parts would last a year less? What are some other negatives?
I will add the primitive answer, because I think it is the main drawback of virtual machines:

It will be ***slower*** than running 'your main OS for your usage' directly on the physical machine. A virtual machine will be slower because it is using software to some actions, that are more efficient when used directly on the hardware. It is very easy to notice the difference if you run a video clip (unless you have a lot of horsepower, but even then you would probably have issues playing 1920x1080/50p high definition video)

---

