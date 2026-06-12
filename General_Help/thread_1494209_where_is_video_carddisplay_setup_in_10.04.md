---
title: "where is video card/display setup in 10.04?"
date: 2010-05-26
forum: General Help
---

### Post by n-alexander on 2010-05-26
kubuntu 10.04.

1. in the user I used for system installation, my monitor works fine

2. in the user I created later - same rights - monitor is set for 60Hz. This is the only option in System Settings/Display

3. there's only xorg.conf.failsafe in /etc/X11, which seems to what the second user is using

Where is the display/video card set up in Kubuntu 10.04?

Why are different users use different settings? Can I copy from one to the other?

Thanks,
Alex

---

### Post by ankspo71 on 2010-05-27
Hi,
Is there any differences between each user's /home/<user>/.local/screen-configurations.xml?  What kind of graphics card are you using? It is possible for nvidia card users to have user-specific nvidia settings using a ~/.nvidia-settings.rc file.

---

### Post by n-alexander on 2010-05-28
> **ankspo71 said:**
> Hi,
Is there any differences between each user's /home/<user>/.local/screen-configurations.xml?  What kind of graphics card are you using? It is possible for nvidia card users to have user-specific nvidia settings using a ~/.nvidia-settings.rc file.

I didn't know about these files, thanks.

They are different, but nothing looks like a resolution/rate setting. There's just a lot of this:

```
 <configuration primary="0" modifiable="false" name="single" >
  <screen id="0" >
   <bottom-of>-1</bottom-of>
   <privacy>false</privacy>
   <right-of>-1</right-of>
  </screen>
 </configuration>

```

The card is an Intel built-in.

---

