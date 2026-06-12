---
title: "how to monitor network traffic"
date: 2011-09-11
forum: General Help
---

### Post by DataSpy on 2011-09-11
My parents have a couple computers at their house (windows) and the internet is running really slow, I'm assuming there is a virus on the network.  How can I monitor traffic to see what's going on?

Any help greatly appreciated thanks!

---

### Post by Dangertux on 2011-09-11
I'm not sure that analyzing network traffic would be the optimal way of finding a Windows virus. Have you tried running anti-malware solutions like Microsoft Security Essentials (it's free)

If you insist on monitoring the network traffic (note this can be considered an illegal wire tap without permision) You can try something like Wireshark.

---

### Post by haqking on 2011-09-11
> **Dangertux said:**
> I'm not sure that analyzing network traffic would be the optimal way of finding a Windows virus. Have you tried running anti-malware solutions like Microsoft Security Essentials (it's free)

If you insist on monitoring the network traffic (note this can be considered an illegal wire tap without permision) You can try something like Wireshark.

+1

Everything that goes wrong with windows or anything else is not necessarily a virus and rarely is in my experience.

Not to say they are not an issue of course as they are, but network performance usually comes down to the basics such as the physical layer then upwards.

Check your router, maybe reboot it.  Check what speed your router is connecting at etc, maybe line quality issues, service issues with cable company etc.

When you say lately and slow what do you mean ?

last few days, today ? etc

slow browsing, downloading etc etc.

take each system offline one by one and see what happens to the performance of other etc.

hardwaire them to router with ethernet cable where applicable to rule out wireless related issues (alot can interfere with home wireless connections)

---

### Post by DataSpy on 2011-09-11
Thanks, I'll try out Microsoft Security Essentials, I'm not worried about the whole wire tap thing, my parents don't care, they have no idea what I'm doing :)

I just thought it would be easy to see how much bandwidth was being used with some on my laptop (ubuntu).

Thanks,
Jim

---

### Post by Dangertux on 2011-09-11
> **haqking said:**
> +1

Everything that goes wrong with windows or anything else is not necessarily a virus and rarely is in my experience.

Not to say they are not an issue of course as they are, but network performance usually comes down to the basics such as the physical layer then upwards.

Check your router, maybe reboot it.  Check what speed your router is connecting at etc, maybe line quality issues, service issues with cable company etc.

When you say lately and slow what do you mean ?

last few days, today ? etc

slow browsing, downloading etc etc.

take each system offline one by one and see what happens to the performance of other etc.

hardwaire them to router with ethernet cable where applicable to rule out wireless related issues (alot can interfere with home wireless connections)

I agree with this. I would rule out technical issues first. Particularly on the ISP's end of things. I know sometimes my internet connection becomes painfully slow particularly if my provider is doing maintenance on my DSLAM. 

If you still think it's malware induced check out MSE like I mentioned in my  first reply. If that finds nothing, start investigating whatever software was most recently installed, and if Windows has decided it's time to download any major updates (this could be crippling throughput if multiple PC's are updating)

If it's none of that you might consider using Wireshark to analyze the traffic, possibly a faulty piece of network equipment is spewing garbage and bogging down the router or other network devices.

I would definitely NOT start with Wireshark though, I am almost positive there is a much more simple solution.

---

### Post by DataSpy on 2011-09-11
Thanks you very much!!!  :)

---

