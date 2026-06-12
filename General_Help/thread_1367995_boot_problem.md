---
title: "boot problem"
date: 2009-12-30
forum: General Help
---

### Post by aminmatrix on 2009-12-30
hi$
 ihave a ubuntu 9.10
when i boot on gerneriic 9.10 -16 it shows "Kernel panic - not syncing :VFS unable to mount root ,tried :ext3 ext4 ext2

---

### Post by Johnny B on 2009-12-30
we need more information.

did you recently install ubuntu or make any changes that could have caused this?
did you try to boot recovery mode?

---

### Post by ajgreeny on 2009-12-30
I assume you have recently done an update and a new kernel was installed.  If you get a grub menu at boot time try booting to a previous kernel (2.6.31-14?) and if that is OK, just delete the 2.4.31-16 kernel and keep using that instead.  If you see no grub menu hold shift a boot to see it appear.

There seem to have been a few cases of the 2.6.31-16 kernel causing panic at boot time.

---

### Post by aminmatrix on 2009-12-30
> **Johnny B said:**
> we need more information.

did you recently install ubuntu or make any changes that could have caused this?
did you try to boot recovery mode?


yes my friend i tried to create a usb startup disc

---

### Post by aminmatrix on 2009-12-30
> **ajgreeny said:**
> I assume you have recently done an update and a new kernel was installed.  If you get a grub menu at boot time try booting to a previous kernel (2.6.31-14?) and if that is OK, just delete the 2.4.31-16 kernel and keep using that instead.  If you see no grub menu hold shift a boot to see it appear.

There seem to have been a few cases of the 2.6.31-16 kernel causing panic at boot time.


yes ihave the previous kernel but can i repaire th new kernel ????and how i can remove the new kernel??
and what's the diffresce between them???

---

### Post by AsianSpanker on 2009-12-30
I have found several postings, like the one I posted that seem to have disappeared!
I donwloaded all the updates and turned my computer off for the night. The next morning and thereafter I got [2.199098]kernel panic-not syncing:VFS unable to mount root fs on unknown-block(0,0).. 
When I posted this, I had found many others with the same problem.
Now I can't find their posts.
or mine.
So, I tried booting from disk, but the same thing came up.
Is there anyone out there that can help?

---

### Post by AsianSpanker on 2009-12-30
If all I can get is a screen that shows kernel panic, and trying to boot from a Canonical disk can't be done, is there anyone out there that can help me? It has been days and I see no answers. Bump 
How does one get to the grub menu to erase the last kernel or whatever happened in the last update? 

There were many asking that, I can't find any answers. Is there a way to retrieve my files? Someone posted an answer, but now I can't find that either.
Bump

---

### Post by AsianSpanker on 2009-12-30
> **ajgreeny said:**
> I assume you have recently done an update and a new kernel was installed.  If you get a grub menu at boot time try booting to a previous kernel (2.6.31-14?) and if that is OK, just delete the 2.4.31-16 kernel and keep using that instead.  If you see no grub menu hold shift a boot to see it appear.

There seem to have been a few cases of the 2.6.31-16 kernel causing panic at boot time.

Yes, and how would one do that?

What is shift-a-boot? Where do you hold the the shift key down at?

---

### Post by AsianSpanker on 2009-12-30
> **aminmatrix said:**
> hi$
 ihave a ubuntu 9.10
when i boot on gerneriic 9.10 -16 it shows "Kernel panic - not syncing :VFS unable to mount root ,tried :ext3 ext4 ext2

It seems that we are supposed to shift-a-boot? and select another kernel? I don't know what that means..Shift-a-boot?

---

### Post by AsianSpanker on 2009-12-30
> **ajgreeny said:**
> I assume you have recently done an update and a new kernel was installed.  If you get a grub menu at boot time try booting to a previous kernel (2.6.31-14?) and if that is OK, just delete the 2.4.31-16 kernel and keep using that instead.  If you see no grub menu hold shift a boot to see it appear.

There seem to have been a few cases of the 2.6.31-16 kernel causing panic at boot time.

Could you PPlease explain how to do this? F12 at startup and go where?

---

### Post by ajgreeny on 2009-12-30
> **AsianSpanker said:**
> Could you PPlease explain how to do this? F12 at startup and go where?
I am so sorry but that was a typo error, and should have said "hold shift at boot" ie press the capital key, not Caps Lock, but shift, and a grub menu should appear.

I hope that helps you boot to the older kernel which should be in the menu list.  When booted from that use synaptic to search for 2.6.31-16 and remove it.  Next time you boot you will automatically be booted to the remaining kernel, 2.6.31-14.

Good luck!

---

### Post by AsianSpanker on 2009-12-30
Slowed down and did as suggested and am now on line again!!! Thank you thank you. I feel renewed. Now I went into Synaptic package manager and typed in 2.6.31-16 and tons o stuff came up. I marked for deletion 2.6.31-16 Linux image. It was 64 bit.
So, Thank you again for slowing down and speaking a language I understand. Simple things throw me. Like you hold down the shift key and press Esc and then you get the grub menu.
Then you can load from the kernel you want. I have about 7 kernels in there. Should I delete all but 2.6.31-16?
That was the basic elegant answer that I wanted. I knew that someone would have one.

---

### Post by AsianSpanker on 2009-12-30
Now my fan seems to be going faster and faster and I am not doing anything on the computer. Could this be another 9.10 glitch?

---

### Post by AsianSpanker on 2009-12-30
Wow my computer is running again. ajgreeny had the solution. 
Start up holding the shift key, then when black screen comes up
and says hit Esc to get grub menu, hit Esc. 
You get the grub menu that shows all the kernels. go to 2..6.31-14 and 
highlight it. Then the computer boots from that. Then go to Synaptic Package Manager and type in 2.6.31-16 and it will show you that kernel.
Delete it. 
You are back in business. I haven't shut er down yet. So I don't know if this is a perminant fix. But I think it is.

---

