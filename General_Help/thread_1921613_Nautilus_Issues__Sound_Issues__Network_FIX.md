---
title: "Nautilus Issues / Sound Issues / Network FIX"
date: 2012-02-07
forum: General Help
---

### Post by Plasma_NZ on 2012-02-07
[COLOR="Red"]Nautilus issue is resolved, so is the Networkfix (still avaliable - pm me)[/COLOR]


Ok so i upgraded my mobo/cpu and reinstalled ubuntu 11.10_64bit


i have noticed using the on-board audio, every 5 seconds i get this strange sound, repeats every 5 seconds... 

Did the obvious and removed pulse audio, didnt solve it, checked alsamixer and muted all mic/input fields, didn nothing, so muted everything.

Made the repeating sound quieter but could still hear it, then i signed into skype and all of a sudden the sound clicks like a mic being muted and all is well with the repeating sounds now gone..... strange... (no i dont like pulseaudio and wont use it, its crap)



some additional info, use's a  alsa-info.sh script...

This is the output AFTER i've run skype which fixes the sound problem..

```

!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfd100000 irq 16
 1 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:13.2-5.4, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1022:780d (rev 01)
	Subsystem: 1043:836c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
-ne 	
bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne 	
beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne 	
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne 	
enable_msi : -1
-ne 	
id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne 	
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne 	
model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne 	
patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne 	
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne 	
power_save : 0
-ne 	
power_save_controller : Y
-ne 	
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne 	
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne 	
single_cmd : N

!!Module: snd_usb_audio
-ne 	
async_unlink : Y
-ne 	
device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne 	
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne 	
id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne 	
ignore_ctl_error : N
-ne 	
index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne 	
nrpacks : 8
-ne 	
pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne 	
vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


```

Cheers

---

### Post by Plasma_NZ on 2012-02-08
Bump

---

### Post by Plasma_NZ on 2012-02-22
bump

---

### Post by roelforg on 2012-02-22
May i ask what nautilus and Network have to do with this?

---

### Post by Plasma_NZ on 2012-02-22
They were part of my original post, but have been solved via other threads... so only have the sound problem now..

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> They were part of my original post, but have been solved via other threads... so only have the sound problem now..
Ah,
but you should've created seperate threads in the first place.
That's easier to read, much better then 3 different topics together

---

### Post by Plasma_NZ on 2012-02-22
no need to troll man...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> no need to troll man...
Sorry,
i didn't mean it that way, i just told you what the Code of Conduct says.
I really didn't mean to troll.

---

### Post by roelforg on 2012-02-22
To get back on topic.

Would you run and post the output of:
```

sudo lshw -C sound

```

---

### Post by Plasma_NZ on 2012-02-22
```
[ physics: ~ ]$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: Hudson Azalia Controller
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:fd100000-fd103fff
[ physics: ~ ]$ 

```

---

### Post by roelforg on 2012-02-22
Try reinstalling skype as it appears to be connected with this...

---

### Post by Plasma_NZ on 2012-02-22
skype is what stops this horrible sound... i believe alsa is the issue.. on a fresh install without skype being installed the sound was there.... and it was only dumb-luck that i noticed when i signed into skype that it did something to sound/mic to "fix" it...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> skype is what stops this horrible sound... i believe alsa is the issue..
I mean, that if skype stop's it, than maybe it's what's causes it;
you'd be amazed what some programs run at startup.

---

### Post by Plasma_NZ on 2012-02-22
Skype doesnt cause it as i stated... fresh install + default updates, there was this repeating sound..... install skype, then login and it "clicks" the soundcard/mic and the repeating sound stops... skype cannot be the cause because this problem was around before skype was installed.... 

seems rather logical its alsa related... im just no pro with alsa


Muting all input etc in alsamixer doesnt do jack...

Normally i never had these problems as i used creative soundcards, but since cross-firing/sli with my pci-e cards there's no room for a pci card... so im stuck trying to solve this problem...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> Skype doesnt cause it as i stated... fresh install + default updates, there was this repeating sound..... install skype, then login and it "clicks" the soundcard/mic and the repeating sound stops... skype cannot be the cause because this problem was around before skype was installed.... 

seems rather logical its alsa related... im just no pro with alsa


Muting all input etc in alsamixer doesnt do jack...
I'd try it anyhow,
alsa is controlled by loads of other programs, as a result, they could interfere.
As skype has the ability to en-/disable the mic, i just suspect skype.
I once had my network down because CUPS wouldn't start, looks totally unrelated, yet is all true.

---

### Post by Plasma_NZ on 2012-02-22
i hear what your saying, but your not listening to what im saying... i had this problem BEFORE skype was even installed... and since skype seems to be able to temp-fix it screams of a alsa problem with controlling my hda-sound..... i cannot see how you think me removing skype will remedy this problem when its clearly not related to "causing" the glitch, can just merely over-ride some alsa-settings...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> i hear what your saying, but your not listening to what im saying... i had this problem BEFORE skype was even installed... and since skype seems to be able to temp-fix it screams of a alsa problem with controlling my hda-sound..... i cannot see how you think me removing skype will remedy this problem when its clearly not related to "causing" the glitch, can just merely over-ride some alsa-settings...
SORRY!

I just didn't get the time line here.
Now i do.

I just wanted to say that alsa isn't some program, it's part of the kernel.

---

### Post by Plasma_NZ on 2012-02-22
Im aware its part of the kernel...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> Im aware its part of the kernel...
Most people don't, that's why i posted that.

I'd love to help but i can't seem to find anything that could cause this.
Tried older kernels? It's the last thing i can think off.

---

### Post by Plasma_NZ on 2012-02-22
doesnt matter which kernel i use under 11.10_64bit.. still the same problem..

Im thinking the problem is alsamixer isnt disengaging the mic/line in or something... 

and when skype loads its does a quick audio-check resulting muted mic correctly...

---

### Post by roelforg on 2012-02-22
> **Plasma_NZ said:**
> doesnt matter which kernel i use under 11.10_64bit.. still the same problem..

Im thinking the problem is alsamixer isnt disengaging the mic/line in or something... 

and when skype loads its does a quick audio-check resulting muted mic correctly...

As we both just agreed ALSA is part of the kernel,
so, maybe there's a bug in one of the kernel's modules.
If you didn't upgrade it, just say so (i didn't).

---

### Post by Plasma_NZ on 2012-02-23
Going to marked this as solved but its still a bug....


Un-muting the rear mic and setting the level to 00 - stops the repeating sound... so clearly a bug with alsa and this chipset..

---

