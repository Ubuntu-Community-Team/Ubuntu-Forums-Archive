---
title: "Razer Copperhead Mouse scroll wheel not working"
date: 2010-11-08
forum: General Help
---

### Post by phr0ze on 2010-11-08
I'm on 10.10. I used to have this mouse working several kernels ago, but along the way one of the kernel updates in 10.4 stopped the wheel from working. I upgraded to 10.10 to see if this got resolved.

I'm not sure where to go. I've google'd the hell out of it, and tried several possible solutions with no luck.

Thanks

---

### Post by deus_zeus on 2010-11-22
I'm in the same boat - I just have a standard PS2 mouse - same deal. The middle scroll wheel will paste from clipboard if I have a terminal open, but doesn't scroll at all. I've tried in browsers, terminals, and an open office doc. Most frustrating of all is that this was working fine a few kernels ago.
Below, button two is when I press the mouse wheel, but if I scroll, nothing happens in xinput:
FYI - this is not hardware - mouse is 4 weeks old, and scrolling works perfectly on XP, VISTA, and WIN 7
-------------------------

root@deus4679:~# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBPS2                                  	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USBPS2                                  	id=8	[slave  keyboard (3)]
root@deus4679:~# xinput test 9
button press   2 
button release 2 
button press   1 
button release 1 
button press   3 
button release 3 
motion a[0]=357 a[1]=827 
motion a[0]=353 a[1]=829 
motion a[0]=350 a[1]=831 
motion a[0]=347 a[1]=833 
motion a[0]=346 a[1]=834 
button press   1 
button release 1 
button press   2 
button release 2 
button press   2 
button release 2 
button press   2 
button release 2 
button press   1 
button release 1 
button press   2 
button release 2 
button press   3 
button release 3 
button press   1 
button release 1 
button press   1 
button release 1 
------------------

---

### Post by deus_zeus on 2010-12-08
Working now - but not sure why.
My PS2 kbd and mouse are connected via a KVM, but as my new desktop didn't have dual PS2 plugs, I was using a belkin dual PS2 to USB adapter - I never thought to check this, because everything always worked fine when switching to my other machines. Anyway, I tested using a wireless mouse, and everything worked ok. I unplugged the belkin USB adapter, and plugged it into a different USB port - lo and behold, all my mouse functions now work. I can't explain why this worked, I'm just happy  it does now.

---

