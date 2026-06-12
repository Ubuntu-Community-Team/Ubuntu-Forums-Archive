---
title: "Google Earth major problem"
date: 2011-02-09
forum: General Help
---

### Post by leviathan8 on 2011-02-09
Hi. I've been toying around with the packages provided in the medibuntu repository, and saw the Google earth package. So I installed it and when I start it, it all works fine, but whenever I try to modify a setting or put myself in street view mode, my screen starts flickering, then immediately after that it goes blank, showing some weird lines and finally I lose signal with monitor. The only thing I can do is to restart... This is what my syslog tells about the event:

```
Feb  8 19:58:10 nubuntu-desktop kernel: [  297.864043] [drm:radeon_fence_wait] *ERROR* fence(f0911620:0x0001F457) 508ms timeout going to reset GPU
Feb  8 19:58:10 nubuntu-desktop kernel: [  297.864053] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:10 nubuntu-desktop kernel: [  297.864060] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA53004A4
Feb  8 19:58:10 nubuntu-desktop kernel: [  297.864066] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x000F0002
Feb  8 19:58:10 nubuntu-desktop kernel: [  297.864073] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x20003CC0
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.040072] radeon 0000:01:00.0: Wait for MC idle timedout !
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.040079] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.040136] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.040199] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000C02
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.089116] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.089122] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.089128] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.145254] [drm:radeon_fence_wait] *ERROR* fence(f0911620:0x0001F457) 796ms timeout
Feb  8 19:58:10 nubuntu-desktop kernel: [  298.145262] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F457)
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656185] [drm:radeon_fence_wait] *ERROR* fence(f0911160:0x0001F458) 504ms timeout going to reset GPU
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656195] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656202] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656209] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656215] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656227] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656284] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.656347] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.705264] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.705270] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.705276] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.760649] [drm:radeon_fence_wait] *ERROR* fence(f0911160:0x0001F458) 616ms timeout
Feb  8 19:58:12 nubuntu-desktop kernel: [  300.760657] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F458)
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272051] [drm:radeon_fence_wait] *ERROR* fence(f09caec0:0x0001F45B) 504ms timeout going to reset GPU
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272061] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272068] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272075] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272081] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272093] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272149] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.272213] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.321132] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.321138] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.321144] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.376418] [drm:radeon_fence_wait] *ERROR* fence(f09caec0:0x0001F45B) 616ms timeout
Feb  8 19:58:15 nubuntu-desktop kernel: [  303.376427] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F45B)
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889058] [drm:radeon_fence_wait] *ERROR* fence(ec4ec100:0x0001F462) 504ms timeout going to reset GPU
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889069] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889076] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889082] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889089] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889100] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889157] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.889221] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938160] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938166] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938172] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938185] [drm:radeon_fence_wait] *ERROR* fence(f09115c0:0x0001F45F) 508ms timeout going to reset GPU
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938189] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938191] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938194] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938196] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938210] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.938269] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.987231] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.987233] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:18 nubuntu-desktop kernel: [  305.987235] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:18 nubuntu-desktop kernel: [  306.040881] [drm:radeon_fence_wait] *ERROR* fence(ec4ec100:0x0001F462) 664ms timeout
Feb  8 19:58:18 nubuntu-desktop kernel: [  306.040889] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F462)
Feb  8 19:58:18 nubuntu-desktop kernel: [  306.109139] [drm:radeon_fence_wait] *ERROR* fence(f09115c0:0x0001F45F) 732ms timeout
Feb  8 19:58:18 nubuntu-desktop kernel: [  306.109142] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F462)
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624063] [drm:radeon_fence_wait] *ERROR* fence(f0911c00:0x0001F465) 508ms timeout going to reset GPU
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624072] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624079] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624086] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624092] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624104] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624160] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.624224] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.673142] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.673148] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.673154] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.725996] [drm:radeon_fence_wait] *ERROR* fence(f0911c00:0x0001F465) 616ms timeout
Feb  8 19:58:20 nubuntu-desktop kernel: [  308.726005] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F465)
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240051] [drm:radeon_fence_wait] *ERROR* fence(f0911f40:0x0001F468) 508ms timeout going to reset GPU
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240061] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240067] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240074] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240080] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240092] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240148] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.240212] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.289131] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.289137] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.289143] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.344511] [drm:radeon_fence_wait] *ERROR* fence(f0911f40:0x0001F468) 620ms timeout
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.344527] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F468)
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352545] [drm:radeon_fence_wait] *ERROR* fence(ec4ecea0:0x0001F46E) 620ms timeout going to reset GPU
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352553] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352559] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003028
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352565] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352571] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352582] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352639] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.352702] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.401614] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.401620] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.401626] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.456977] [drm:radeon_fence_wait] *ERROR* fence(ec4ecea0:0x0001F46E) 732ms timeout
Feb  8 19:58:23 nubuntu-desktop kernel: [  311.456986] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F46E)
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856102] [drm:radeon_fence_wait] *ERROR* fence(f0911160:0x0001F46F) 504ms timeout going to reset GPU
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856112] radeon 0000:01:00.0: GPU softreset 
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856118] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856125] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856132] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856143] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856199] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.856263] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.905232] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.905238] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.905244] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.961129] [drm:radeon_fence_wait] *ERROR* fence(f0911160:0x0001F46F) 616ms timeout
Feb  8 19:58:26 nubuntu-desktop kernel: [  313.961137] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x0001F46F)
Feb  8 19:58:26 nubuntu-desktop kernel: Kernel logging (proc) stopped.
```

Note that I do not have video graphics driver enabled.

---

### Post by dino99 on 2011-02-09
the way to follow:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by leviathan8 on 2011-02-10
Oh, didn't thought about that. Thanks.

---

