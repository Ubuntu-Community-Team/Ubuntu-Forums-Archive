---
title: "Stuck at checking battery state"
date: 2012-02-03
forum: General Help
---

### Post by ALF102 on 2012-02-03
Hi there, I've managed to get my hands on a Dell Inspiron 1545 and replace its internal HDD with my HDD that has Ubuntu 11.10 in it. Apparently the laptop has broke its LCD screen so I plug in an external monitor and then start it all up. During the startup, it got stuck at the "Checking Battery State". So I pressed Ctrl+Alt+F1 and manually start the lightdm with 'sudo lightdm', then these error messages came out:

[172.331137] [drm:i9xx_crtc_mode_set] *ERROR* Couldn't find PLL setttings for mode! 

[172.331146] [drm:drm_crtc_helper_set_config] *ERROR* Failed to set mode for [CRTC:4]

[172.724690][drm:i9xx_crtc_mode_set] *ERROR* Couldn't find PLL setttings for mode! 
[172.724697][drm:drm_crtc_helper_set_config] *ERROR* Failed to set mode for [CRTC:4]

[172.724844][drm:i9xx_crtc_mode_set] *ERROR* Couldn't find PLL setttings for mode! 
[172.724850][drm:drm_crtc_helper_set_config] *ERROR* Failed to set mode for [CRTC:4]

[172.746806][drm:i9xx_crtc_mode_set] *ERROR* Couldn't find PLL setttings for mode! 
[172.746932][drm:drm_crtc_helper_set_config] *ERROR* Failed to set mode for [CRTC:4]

---

