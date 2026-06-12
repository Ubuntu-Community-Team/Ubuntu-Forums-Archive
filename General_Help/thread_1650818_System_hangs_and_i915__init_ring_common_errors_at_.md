---
title: "System hangs and i915 / init_ring_common errors at tty1 - tty6"
date: 2010-12-22
forum: General Help
---

### Post by AngelDE98 on 2010-12-22
I had a lot of problems to date but this is my biggest : 

Everytime I just launch an Game / Program like " Armagetron Advanced " / Blender , my Laptop almost freezes / " hangs " . 
If I change from Desktop Mode / X Server to ttyX , I get only an LOOP of thousands of errors . I made some screens with my Mobile phone and I noticed it just happened after installing the " 200 Line Kernel Patch That Does Wonders Alternative " at such programs . One error line is : 

```
[drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed ... GPU hung
```

I tried to get the other ones too . 

```
[drm:i915_do_wait_reguest] *ERROR* i915_do_wait_request returns -5 (awaiting XXXXXX at XXXXXX)
[drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[drm:init_ring_common] *ERROR render ring head forced to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
```

My mobile phone cam has only 3 megapixel and no blur-fix ... 
But at least I think it is good enough ... 

Can someone PLEASE help me ? I do not want to format Ubuntu ! 
And is it really the Kernel Patch ? I tried to remove it and I think I removed it but ... it is still there . 

PS : The ERROR is from " Armagetron Advanced " because I tought it is an Blender error ...

Edit 1 : It is DRM not DRN

---

### Post by AngelDE98 on 2010-12-23
Bump ...

And reinstalling the linux_image_ XXX was not helping . I try to completly remove it and install it from scratch and report my newest state .

---

### Post by AngelDE98 on 2010-12-23
Even this could not help !!! At least it happens a little later than just at starting the application but it is still going on nerves !!! Please help !!! :confused: :( :cry: [-o<

---

### Post by AngelDE98 on 2010-12-27
Bump.

---

### Post by AngelDE98 on 2010-12-29
Bump

---

### Post by AngelDE98 on 2010-12-30
THIS SUX !!! REALLY !!! I DO NOT WANT TO REINSTALL UBUNTU !!! I GOT SO FAR AND THIS LITTLE ERROR IS F**KING ME UP ... Calm down ... Calm down ... AAARGH !!!! 

Sorry for this above but can someone really please help me ? Thanks a lot .

---

### Post by AngelDE98 on 2010-12-31
Can someone really help me ? 

And happy new year :D 

I think I give up ... It is already 2011 !!!

---

### Post by AngelDE98 on 2010-12-31
:lolflag: I just gave up and it works properly ... I can play Armagetron Advanced again ! But what was causing it ? :confused: 

Still OMG ... New Year , New Wonders ...

---

### Post by Habeouscorpus on 2010-12-31
I've had a few of these errors myself, just at a different time. It's a graphics problem, I've found. Haven't gotten it fixed yet, though.

---

### Post by AngelDE98 on 2011-01-01
Edit : Everything removed because I looked even more closely ...
It says in expert mode that i915 is on my Display ... You were right . But I still unmarked some 915 things in DRIconf . I do not know what fixed it but I think my ...
> Mesa DRI Mobile Intel(R) GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2 (Tungsten Graphics, Inc)
... is not from Intel or it is not supported well in Linux because in Windows it had more than MMX and SSE2 such as SSE3 ... I just create another Topic ... YES :lolflag:

Edit : No new topic ...

---

