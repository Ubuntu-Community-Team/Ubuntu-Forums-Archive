---
title: "nvidia 290.10 and Google chrome aero snap"
date: 2012-02-12
forum: General Help
---

### Post by ubrox on 2012-02-12
Yes, weird combination of things.


A couple of days ago I moved up to Nividia 290.10 on my HP dv7 laptop, ubuntu 11.10. I use ubuntu-x (swat) repository to update to the new driver.


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


 nvidia-current                         290.10-0ubuntu1~oneiric~xup1            NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                 285.05.09-0ubuntu0.1                    NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        290.10-0ubuntu1~oneiric~xup1            Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                285.05.09-0ubuntu0.1                    Tool of configuring the NVIDIA graphics driver
xorg                                   1:7.6+7ubuntu7.1                        X.Org X Window System
 google-chrome-stable                   17.0.963.46-r119351                     The web browser from Google

Since I upgraded, I seem to have some quirkiness wrt to aero snap and its limited to Google chrome. Everything worked as expected till I updated. Since I update, chrome refuses to snap to the edges. When I fiddle with (preferences->personal stuff->) (use system title bar & borders, Hide system title bar ...) options, just select the other and come back etc., it starts working fine. It snaps to edges, maximizes at the top etc ...

AFAIK, it started after update to the new driver. And its limited to Chrome. Terminal etc snap fine.

---

