---
title: "Nvidia resolution for different users"
date: 2009-10-16
forum: General Help
---

### Post by momist on 2009-10-16
Hi there,

I have a clean install of Jaunty on which I have just installed two extra users.  I have my Nvidia graphics Display resolution set to 1024 x 768 by the proprietary drivers, and this works OK.  However, the two new users always login to find that their display is set to 1280 x 1024, which is just about usable, but not comfortable, on my old fuzzy monitor.

They can change the Display resolution in the 
System : Preferences : Display : Driver Vendor's Tool : Nvidia X-Server Display Resolution - interface, but cannot save this.  The save function tries to re-write the relevant /etc/xorg file, for which they have no permissions. Their home directory does not contain any .config files.

How can individual users save their preferred display resolution please?

Thanks

Ian

---

### Post by Giblet5 on 2009-10-16
The only way I know of to do this is to edit your xorg.conf file and provide multiple resolution defs in the "Screens" section. Then, each user can start X manually at the resolution they prefer, OR, they can cycle through the defined resolutions with CtrlAlt+ and CtrlAlt- (numeric pad).

It's complicated. Unfortunately.

A lot of this over-complication is due to the absence of a solid standard for determining a given monitor's capabilities. Not all monitors handle multiple resolutions well at all.

**[COLOR="DarkRed"]Be warned[/COLOR]**: messing with xorg.conf can cause your display to go blank and can actually ruin your monitor.

---

### Post by momist on 2009-10-16
> **Giblet5 said:**
> The only way I know of to do this is to edit your xorg.conf file

Wow - thanks for the answer, but that's not an answer for these users (non computer literate, and Windows centric).  

Maybe the best thing would be to try and set it up for the same resolution for us all. We'd all be happy at the reduced 1024 x 768.  How can I limit the resolution permanently - for all?

Cheers.

---

### Post by mocoloco on 2009-10-16
Easy, just go to System > Preferences > Display.  It will ask you if you want to use your vendors tool instead, just say "no" to that.  Changes made in there are saved per user.  Just tested it myself.

---

### Post by momist on 2009-10-17
> **mocoloco said:**
> Easy, just go to System > Preferences > Display.  It will ask you if you want to use your vendors tool instead, just say "no" to that.  Changes made in there are saved per user.  Just tested it myself.

Thanks mocoloco.  Apart from crashing my system the first time I tried it (total lockup - don't know why), that has now worked for me.  I'm now limited to the lower scan rates, but I can live with that.  I'm getting a new monitor in a few days, and will be changing everything again then anyway.

---

### Post by anaconda on 2009-10-17
another solution would be to run
sudo nvidia-settings 
for each user, and change the resolution from there.

the resulting settings file ".nvidia-settings-rc" is stored in each users  home directory. And it should be loaded each time the user logs in. If not you can add the 
nvidia-settings -l
line to eg. .xinitrc file.....

Havent tried that with different users, but I do use it myself..

---

### Post by momist on 2009-10-18
> **anaconda said:**
> another solution would be to run
sudo nvidia-settings 
for each user, and change the resolution from there.


Thanks anaconda,  that sounds exactly what I needed.  When I have some time, I'll give it a go.

---

