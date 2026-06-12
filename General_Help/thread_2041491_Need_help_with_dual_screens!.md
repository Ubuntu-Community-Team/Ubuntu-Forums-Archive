---
title: "Need help with dual screens!"
date: 2012-08-12
forum: General Help
---

### Post by zack6849 on 2012-08-12
Im having troubles applying my Second screeen to ubuntu, i recive the following error

The selected configuration for displays could not be applied
requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 0), size=(1920, 1080), maximum=(1920, 1920)

Failed to apply configuration: %s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 0), size=(1920, 1080), maximum=(1920, 1920)

My xort.conf is here: [http://pastebin.com/dzgj2FEi](http://pastebin.com/dzgj2FEi)
and my system specifications are as follows

os [Linux 3.2.0-29-generic-pae i686]
distro[Ubuntu "precise" 12.04] 
cpu [4 x AMD Athlon(tm) II X4 640 Processor (AuthenticAMD) @ 800MHz] 
memory [Physical: 11.8GB, 93.4% free] disk[Total: 206.5GB, 83.5% free] 
video[ Advanced Micro Devices [AMD] nee ATI Barts XT [ATI Radeon HD 6800 Series]
sound [HDA-Intel - HDA ATI SB1: HDA-Intel - HD-Audio Generic]

I was told to follow the guider here : [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)
however it helped none, i've been trying to get this functioning on and off for about 3 days, any help would be GREATLY appreciated!

---

### Post by QIII on 2012-08-12
Did you install the driver by following the instructions to create a .deb?

What can you tell me about your monitors themselves?

---

### Post by GeneralCody on 2012-08-12
In the Nvidia driver there is an option for Cinerama, which when activated helps me configure my two monitors. Is there anything like that available for your ATI driver perhaps?

---

