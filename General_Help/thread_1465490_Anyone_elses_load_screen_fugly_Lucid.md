---
title: "Anyone elses load screen fugly? Lucid"
date: 2010-04-29
forum: General Help
---

### Post by Shakz on 2010-04-29
Load screen after install and bounce has been coming up in like 400X300 huge and pixelated and fugly. Is this happening still with your upgrades or fresh installs of the latest iso is this WAE? Is it just me? When I booted from iso (before perminant install) it looked fine....after install though it comes up uuuuuugly.
Boot only takes a few seconds so I can live with it. Poor presentation though when showing it to someone outside of the nix community.

EDIT: The load screen was very pretty in Karmic for me.....Lucid is dorked up though.

---

### Post by Rasa1111 on 2010-04-29
I did notice that also,
when trying to get the liveCD to work properly. 

I wondered why it was all big and pixelated...

---

### Post by jrothwell97 on 2010-04-29
This is down to the fact the proprietary drivers don't usually support KMS.

Cheer up, though, it's not as ugly as it was, and it could certainly be uglier :D

---

### Post by themusicalduck on 2010-04-29
If you installed proprietry drivers then it will look like this unfortunately :/

If you want it not to look like that then you have to stick with open source drivers.

---

### Post by PhoHammer on 2010-04-29
> **themusicalduck said:**
> If you installed proprietry drivers then it will look like this unfortunately :/

If you want it not to look like that then you have to stick with open source drivers.

+1

That's when it happened on my machine. So is there a reason to use proprietary drivers? It seemed like the open-source driver was doing fine. I think I shall switch back...

---

### Post by WinterRain on 2010-04-29
> **PhoHammer said:**
> So is there a reason to use proprietary drivers? 

Yeah, if you need 3D support for games or whatnot. I don't reboot very often, so I can live with it.

---

### Post by undecim on 2010-04-29
I can't play any full-screen games on the FOSS drivers, so I'm stuck with an ugly screen myself.

---

### Post by PhilGil on 2010-04-29
I switched to the proprietary drivers then back to nouveau, but my boot screen is still ugly.  Is there any way to fix it?  Curiously, my shutdown screen looks fine.

---

### Post by cgroza on 2010-04-29
I have the same problem ,but it does not matter for me because once its booted I have no problems.

---

### Post by DasFox on 2010-04-29
> **themusicalduck said:**
> If you installed proprietry drivers then it will look like this unfortunately :/

If you want it not to look like that then you have to stick with open source drivers.


Ahh sounds like our great FREEDOM in open source is working great! LMAO  

See people this is why we need more FREE software so things work properly! ;)

---

### Post by LowSky on 2010-04-29
Just install start up manager. You edit the slash screen size That should clean it up

---

### Post by cariboo on 2010-04-29
Please ask support questions in the support forums.

---

### Post by Shakz on 2010-04-29
If the reason is propitiatory drivers then why does it look great in Karmic?

---

### Post by Shakz on 2010-04-29
> **cariboo907 said:**
> Please ask support questions in the support forums.

*salute*

---

### Post by themusicalduck on 2010-04-30
I found this post the other day and it worked perfectly to make the bootscreen at normal resolution. In fact it looks pretty much as it did with the open source driver - [http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html](http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html)

Although in step 2, I found gfxmode=${GRUB_GFXMODE} twice in the file, but I just added that line underneath both and it seemed to work.

edit: Apparently doing this causes problems for some people. It didn't for me, but best not to try unless you know how to fix it.

---

