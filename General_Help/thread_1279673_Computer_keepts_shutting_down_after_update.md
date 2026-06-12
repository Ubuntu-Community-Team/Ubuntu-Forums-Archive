---
title: "Computer keepts shutting down after update"
date: 2009-10-01
forum: General Help
---

### Post by 12jewels on 2009-10-01
My friend who has a suse machine call me last week because as soon as his computer enter into the X desktop it shut itself down. It sounded kinda funny so I told him to bring his computer over to me.

Before I could get to his computer, the next day I updated my computer with the suggested updates in the update manager, rebooted my computer and now my computer which is a ubuntu computer, also shuts down after I enter into the X desktop. I did notice that there was a kernel headers update I believe in the update manager that got updated.

Does anyone else have this problem?

How do I fix this problem? I tried rolling back on the kernel with no luck.

I don't have a dust problem or a heat problem either.


Thanks

---

### Post by AndyCee on 2009-10-01
One thing to try is to boot into recovery mode, drop to a root shell with networking and run

apt-get update
apt-get upgrade

I have occasionally had an update which partially failed and caused me grief. This fixed it for me.

---

### Post by 12jewels on 2009-10-01
I solved the problem. I have a nVidia card and when the last kernel update happen the video driver I was using was causing a panic in the kernel. I had to go to the nVidia website to get the driver from there because the one in the install software area of ubuntu is still not up to date.

So if you have a nVidia card and your computer keeps resetting or shutting down, that is what the problem is, especially if you know your computer is not overheating or dusty.

Thanks

---

### Post by 12jewels on 2009-10-05
Actually the problem is not solved.

Here is my take on what happened.

After my friend and I who by the way have two different versions of linux distros, updated our computers to the new linux kernel headers. i believe that there was something inside those headers patches that also patch the video card itself. Whatever it was it ruined my video card.

I can used the box on low graphics just fine as long as I don't try to use the nvidia drivers. I of course didn't like that, so I wiped my computer out and reinstalled windows. Now here is why I say that it was something in the kernel header files that patched my video card firmware or something, it is because I get the same exact errors in windows too. I am fine until I try to use the nvidia drivers then the computer goes back to restarted or shutting itself down. My computer has never done that before until i use the recommended updates on the kernel.

I have another computer exactly like the one that is messed up and the system is again asking me to update that computer with the new kernel stuff. I have not done it because I know that same thing will happen again. I am tempted to do it just so I can prove my theory. If fact, I may just do that. Worst case I just have to buy a new video card and disable the onboard one.

Has anyone else noticed this problem? If so, how was it fixed?

---

