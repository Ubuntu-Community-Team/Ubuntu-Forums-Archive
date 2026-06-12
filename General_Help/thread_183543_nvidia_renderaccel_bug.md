---
title: "nvidia renderaccel bug"
date: 2006-05-28
forum: General Help
---

### Post by starkes on 2006-05-28
Hey

i found this on the wiki and tried taking it seriously to fix my problems with ut2004 freezing brutally all the time, and it worked.

```

Note: RenderAccel has a bug. Memory leak and crashes. Disable it in /etc/X11/xorg.conf in the section "Device".

Option          "RenderAccel"   "false"

```

Can anyone tell me what the problem is anyway, or what exactly this renderaccel option does?

---

### Post by starkes on 2006-05-28
bump

(i've found that nobody replies until theres enough views that they think they'll be able to throw a useless post in to up their count, but hopefully someone out there ACTUALLY knows things and can help.)

---

### Post by Simon Bridge on 2006-06-06
[QUOTE=starkes]Hey

i found this on the wiki and tried taking it seriously to fix my problems with ut2004 freezing brutally all the time, and it worked.

```

Note: RenderAccel has a bug. Memory leak and crashes. Disable it in /etc/X11/xorg.conf in the section "Device".

Option          "RenderAccel"   "false"

```

Can anyone tell me what the problem is anyway, or what exactly this renderaccel option does?[/QUOTE]NIce, I shall try that myself (dapper+nvidia=freeze for multimedia).

To see what is ahppening, you can enable renderaccel and watch your CPU load and your RAM/swap use.

---

### Post by tseliot on 2006-06-06
[QUOTE=starkes]Can anyone tell me what the problem is anyway, or what exactly this renderaccel option does?[/QUOTE]
Usually RenderAccel makes your desktop a bit faster.

If you use the latest driver (8762) you "shouldn't" have any problems with renderaccel.

---

### Post by starkes on 2006-06-08
i seem to get crashes that take the system down on average within 10 minutes in ut2004 if i have frenderaccel on. but then again, i get some of these crashes on a system using an ATI card anyway, so it could be ubuntu or ut2004...

---

### Post by Simon Bridge on 2006-06-09
Well, I got the nvidia driver off the repo - I don't get to see which one this is since I'm not at that computer now. However, turning render-acceleration off fixed my issues here.

Except when trying to play a dvd with xine ... then it all returns, and only goes away after reboot + restarting gdm. (Reboot alone won't do it.)

It is a wonderful puzzle and 100% reproducable.

Unfortunately - I cannot investigate further for a while as the machine exhibiting this issue has experienced a power surge and blown up. Literally - flame, smoke, everything. This, naturally, has a very bad effect on 3D acceleration :) Forunately I had just backed up everything preparatory to installing dapper <sigh of releif>

---

### Post by starkes on 2006-06-10
oh man, wait until you use xgl/compiz on dapper. theres quite a few reproducable ridiculously weird bugs.

---

### Post by Simon Bridge on 2006-06-11
The obvious thing to do next is file a bug report?

---

### Post by Jason_25 on 2006-06-11
[QUOTE=Simon Bridge]The obvious thing to do next is file a bug report?[/QUOTE]
Or maybe try dapper and see if it works.

---

### Post by Simon Bridge on 2006-06-11
[quote=Jason 25]Or maybe try dapper and see if it works.[/quote]What will that tell you? Dapper Desktop uses the xorg (non-3D) "nv" driver. Of course it works. It is the *nvidia* driver which has the issue!

---

### Post by Jason_25 on 2006-06-11
[QUOTE=Simon Bridge]What will that tell you? Dapper Desktop uses the xorg (non-3D) "nv" driver. Of course it works. It is the *nvidia* driver which has the issue![/QUOTE]
No I mean install dapper.

---

### Post by Simon Bridge on 2006-06-13
[QUOTE=Jason_25]No I mean install dapper.[/QUOTE]But... that's what we've *done*!

---

### Post by Jason_25 on 2006-06-13
My mistake.  You posted in the breezy forum BTW.

---

### Post by Simon Bridge on 2006-06-16
[QUOTE=Jason_25]My mistake.  You posted in the breezy forum BTW.[/QUOTE]
That's right Jason, if you read from post #1 you'll see we started in breezy and continued in dapper ... it's this little thing about adding to existing threads before considering starting a new one ... and conversations can meander.

If this would genuinely be better in a dapper forum... perhaps a moderator can shift it?

---

### Post by starkes on 2006-06-16
guess it doesnt really matter, as i've had this problem with breezy, dapper, and a few pre-releases of dapper. so its more or less a universal problem.

i dont understand how you can partially accelerate something though, like how do you turn off renderaccel and then still have acceleration, but apparently not as good.

I can say that when im rocking a GeForce 5-anything, i should get better performance than i did with a GeForce 4 Ti 4200, and thats not what i'm seeing, RenderAccel's fault or not.

---

### Post by Jason_25 on 2006-06-16
[QUOTE=starkes]
I can say that when im rocking a GeForce 5-anything, i should get better performance than i did with a GeForce 4 Ti 4200, and thats not what i'm seeing, RenderAccel's fault or not.[/QUOTE]
Why do you think that? 

For example, the Ti 4200 is clearly a much stronger card than an FX5200.  But the FX5200 has DX9 features and better AA/AF which are largely useless because of the speed of the card.

---

### Post by starkes on 2006-06-16
well, the card im using i believe is a 5600. Its not my card, i had to fix the heatsink for a buddy and it just somehow ended up in my comp, but im pretty sure its a 5600

I know for sure it is a much better card than a ti 4200 because ive seen them working side by side and it kicks the shit out of the 4200

---

### Post by Jason_25 on 2006-06-18
As you can see from [this]("http://www.digital-daily.com/video/nvidia-nv31/index02.htm") and other benchmarks the results are not that cut and dry.  The TI4200 even competes with the mid-range 5-series.  Personally, for a linux-only computer I would choose the TI4200.

---

### Post by starkes on 2006-06-18
i guess its too bad that the 4200 isnt around anymore.

I came home one day and thought the monitor was off until i tried turning it on and there was still no video. Took a look at the 4200 and the fan wasnt spinning anymore. it got fried.

---

### Post by Jason_25 on 2006-06-18
I hear you on that.  I have a gainward TI4800SE overlocked to TI4800 speeds that's loaned to a friend and the fan died a couple years back.  i ziptied an 80mm fan to it and that was that.  It is happily running dapper i386 right now.

---

