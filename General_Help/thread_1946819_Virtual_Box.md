---
title: "Virtual Box"
date: 2012-03-25
forum: General Help
---

### Post by Spewed on 2012-03-25
So after discovering that it's nearly impossible to access your existing installation of Windows using Virutal Box or VMware Machine I suppose I will set up a new installation, but I have a few n00b questions. 

1. Does setting up a virutal machine of Windows 7 permanently take up hard drive space, or this is only temporary while using the virutal machine? 

2. Does it have to be installed on any specific hard drive? I have my dual boot configuration set up on one 500GB hard drive(hence the question about taking up space). However, I do have another 500GB hard drive that I use specifically to store media and things alike, could I simply store it on that hard drive, so long as it's mounted? 

3. Do I constantly have to authenticate the new installation of Windows every time I use a virtual machine?

---

### Post by Pand5461 on 2012-03-25
1. You'll have to create a file which serves as a virtual hard disk. In VirtualBox, you can create an image with dynamical size, so the amount of space taken will depend on how much data you store in the VM.

2. The virtual hard disk file can be located anywhere, no restrictions.

3. Why? Virtual machine behaves just like real computer. You don't have to re-authenticate your Windows installation every time you reboot, do you?

---

### Post by Jagoly on 2012-03-26
> **Pand5461 said:**
> 3. Why? Virtual machine behaves just like real computer. You don't have to re-authenticate your Windows installation every time you reboot, do you?

But you do need to be careful when changing settings in virtualbox for the VM. Windows in my experience has a tendency to deactivate itself. So be careful. I ended up resorting to a crack to stop it from deactivating.

---

### Post by HermanAB on 2012-03-26
Howdy,

I have a WinXP VM that I have been using for tax returns and other special software since about 2002.  It has been copied numerous times to new machines.  Having a Windows VM is FAR better than a native installation.  So by all means, go ahead and make a VM, then learn how to make a copy of it and you'll never look back.

---

### Post by Jagoly on 2012-03-26
^ the last word is minecraft xd ^

---

### Post by haqking on 2012-03-26
> **Spewed said:**
> **So after discovering that it's nearly impossible to access your existing installation of Windows using Virutal Box or VMware Machine I suppose I will set up a new installation, but I have a few n00b questions.** 

1. Does setting up a virutal machine of Windows 7 permanently take up hard drive space, or this is only temporary while using the virutal machine? 

2. Does it have to be installed on any specific hard drive? I have my dual boot configuration set up on one 500GB hard drive(hence the question about taking up space). However, I do have another 500GB hard drive that I use specifically to store media and things alike, could I simply store it on that hard drive, so long as it's mounted? 

3. Do I constantly have to authenticate the new installation of Windows every time I use a virtual machine?

You can take a clone of your existing and clone it into a VM using clonezilla or similar tool.

Cheers

---

### Post by Jagoly on 2012-03-26
Have you ever tried that? It may be possible with a relitivaly clean standard install, but its often not feasible for OEM installs.

---

### Post by haqking on 2012-03-26
> **Jagoly said:**
> Have you ever tried that? It may be possible with a relitivaly clean standard install, but its often not feasible for OEM installs.

yes i have done it many times.

---

### Post by Jagoly on 2012-03-26
Oh, alright then, I failed miserably when I tried to do it a while ago with an old dell running win7. Though that was ages ago when I still used mint, so I was a pretty big n00b back then (the ancient past of mid 2010). I didnt remove any of the yucky dell stuff first so that probably didn't help.

But a clean install in a VM is still better, I think that the clone to a vm method is actually ilegal.

---

### Post by haqking on 2012-03-26
> **Jagoly said:**
> Oh, alright then, I failed miserably when I tried to do it a while ago with an old dell running win7. Though that was ages ago when I still used mint, so I was a pretty big n00b back then (the ancient past of mid 2010). I didnt remove any of the yucky dell stuff first so that probably didn't help.

But a clean install in a VM is still better, I think that the clone to a vm method is actually ilegal.

legality is a seperate issue, and depends on licensing of course.

the actual cloning itself to a VM is not illegal in itself, it depends on the licencing and whether or not a OEM install etc.

The actual cloning can be done though, of course a clean install is better but i was just answering the OP in terms of not being able to use a existing install.

Peace

---

### Post by Adrian98 on 2012-03-26
No it doesnot occupy a permanent space on your hard drive until you uninstall the O.S.  Try it with backup!! :p

---

### Post by Spewed on 2012-03-26
While we're on this subject I've successfully gotten things working with Virtual Box, but not with an existing installation on a physical drive like I had hoped to achieve. I'm just using an old Windows XP copy for a virtual drive. 

Anyway, I'm primarily doing this for the use of Netflix, as well as any other future reason I may want to use Windows without having to log off and switch over. But, since we're on the subject of Netflix, I've noticed the viewing experience is a bit choppy and and dips in frame rates as opposed to if I were running my Windows 7 drive. Is this just problematic of the virtual drive or is there a certain amount of Vram I should appropriate to the Windows XP vritual drive? 

Also, I do have 3d acceleration enabled.

---

