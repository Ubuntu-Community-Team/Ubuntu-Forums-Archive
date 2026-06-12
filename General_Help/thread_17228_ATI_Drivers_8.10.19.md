---
title: "ATI Drivers 8.10.19 ?"
date: 2005-02-27
forum: General Help
---

### Post by ernstp on 2005-02-27
You guys were really quick with packaging the first 8.X release but I'm still waiting for 8.10.

What's up?

---

### Post by daniels on 2005-02-27
We're well past the Upstream Version Freeze, so it won't go in for Hoary.

---

### Post by ernstp on 2005-02-27
[QUOTE=daniels]We're well past the Upstream Version Freeze, so it won't go in for Hoary.[/QUOTE]

Oh! Never, ever, in the official repository? Or after release as an update perhaps?

Ok, guess I have to try and install it myself then...

---

### Post by daniels on 2005-02-27
Not in Hoary at all, no.

---

### Post by Kareema on 2005-02-27
[QUOTE=daniels]Not in Hoary at all, no.[/QUOTE]

I understand that it won't be in the repositories until Hoary final is out - but why not after the release? 

Graphics drivers are a central component of a working system, many users want/need 3D acceleration and there are many bugs eliminated in each update of the ATI drivers.

IMHO there should be the possibility for the next stable system (Hoary) to get these drivers as an update in the Ubuntu repositories (to improve overall stability and usability of users' productive systems).

---

### Post by daniels on 2005-02-27
Once a release is out, that's it -- it only receives critical bugfix and security updates.  Otherwise, there's no real point to a 'release'.

As for the newer == better argument, well, just look at nVidia for proof of that -- going from 1.0.6111 to 1.0.6629 regressed all support for cards < GeForce2; they just lock up solid.  8.8.25 is a known quantity and actually has very few bugs (certainly no showstoppers), so I'm happy to stick with what we know for Hoary.

---

### Post by Kareema on 2005-02-27
> **daniels]Once a release is out, that's it -- it only receives critical bugfix and security updates.  Otherwise, there's no real point to a 'release'.
[/QUOTE]
Understood - regarding the short time span between two releases it's the only way to go.

[QUOTE=daniels]
As for the newer == better argument, well, just look at nVidia for proof of that -- going from 1.0.6111 to 1.0.6629 regressed all support for cards < GeForce2 said:**
> 
Sometimes this is a valid argument - sometimes not (as in the case of NVidia this time).

[QUOTE=daniels]
8.8.25 is a known quantity and actually has very few bugs (certainly no showstoppers), so I'm happy to stick with what we know for Hoary.
Right, 8.8.25 is working good and it's a 'must have'. As for 8.10.19, there are some things worth updating (see release notes):
[list]
[*]fglrxconfig now produces a proper xorg.conf X Server configuration file
[*]Running certain 3D applications no longer result in system hangs on x86_64 systems with RADEON™ 9100/8500 series or FireGL™ 8800 installed
[*]XVideo support now available in dualhead configuration
[*]3D geometry corruption no longer occurs with Celestia and other 3d apps
[*]and some other bugfixes mentioned at the Rage3D forums that are not mentioned in the release notes
[/list]
But that's probably not enough to justify an update while past Upstream Version Freeze and maybe risk some other problems while there are enough things to do for the final release.

Thank you for answering and make me understand some of the things that lead to this decision. And thank you for your efforts and your good work.

---

### Post by daniels on 2005-02-28
No worries.  Normally I'm not quite so queasy -- I'm taking time out of pulling the entire i810 driver from HEAD, after having done the same for the Via unichrome driver -- but binary-only drivers don't allow anyone any visibility to what's going on.  There's only one real bug with the i810 stuff from HEAD, and I have a fairly good idea where that lies.  Not so with the nVidia thingo.  That's the biggest problem; no-one has any idea what the changes are, so managing them becomes nigh on impossible.

---

### Post by MadMan2k on 2005-04-02
but could you at least tell, how you made the 8.8.25 package?
Since there are several problems you run in doing it via alien:
1) conflicts with mesa
2) build warning: 
```
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
 make[1]: Leaving directory `/usr/src/<your kernel>'

```
3) the driver is indetifying itself as not dri capable, when running glxinfo with
"export LIBGL_DEBUG=verbose"

which results in the absence of 3d support  :-?

---

