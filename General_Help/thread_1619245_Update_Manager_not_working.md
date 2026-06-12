---
title: "Update Manager not working"
date: 2010-11-11
forum: General Help
---

### Post by HandyAndy on 2010-11-11
I'm using Ubuntu 10.10 with Fluxbox as my window manager. Update Manager was working fine in 10.04, but now, when updates are available and I click "install", nothing happens. Using 10.04 I used to get the password prompt; now nothing other than the window sort of flickers.

I've tried uninstalling and re-installing Update Manager - didn't work.

I can update upgradeable packages without a problem using Synaptic and Update Manager works fine if I log into a Gnome session and use it from there. So I'm wondering if it's something to do with the latest Update Manager and Fluxbox.

I'd be grateful if anyone's got any ideas.

Andy

---

### Post by dark.generic on 2010-11-11
in terminal try

```
sudo apt-get update

```then

```
sudo apt-get upgrade
```

---

### Post by 73ckn797 on 2010-11-12
> **dark.generic said:**
> in terminal try

```
sudo apt-get update

```then

```
sudo apt-get upgrade
```

This fixed update manager constantly listing the same updates after they  were already installed. Update manager would prompt for password but  then would not update. Terminal reinstalled the updates and now they are not being listed as current updates.

Is there a file that would need to be deleted or edited to prevent this if it happens again? It might help others.

I could easily turn off update manager and use terminal in the future.

---

### Post by dark.generic on 2010-11-13
I'm still pretty new to ubuntu...

All I do is when the Update Manager notifies me about new updates i just update through terminal...

---

### Post by HandyAndy on 2010-11-14
Thanks for the suggestions, but it's not that I need a work-around; I can update by other means without Update Manager. What I'm trying to do is get something working again that was working before I upgraded to 10.10.

Another related problem is that I can no longer install new programs through the Software Centre. Again, when I click "install" nothing happens. Again Synaptic or apt-get install work fine and again Software Centre works fine in a Gnome session. So the problems seems to be something to do with using apt through the latest versions of Ubuntu's Gnome applications under Fluxbox.

---

### Post by HandyAndy on 2010-11-18
Bump

---

### Post by 73ckn797 on 2010-11-18
> **HandyAndy said:**
> So the problems seems to be something to do with using apt through the latest versions of Ubuntu's Gnome applications under Fluxbox.
Have you searched for other people having this problem using Fluxbox? I do not use it so I cannot help.

---

### Post by HandyAndy on 2010-11-18
> **73ckn797 said:**
> Have you searched for other people having this problem using Fluxbox? I do not use it so I cannot help.

I have and I haven't found anything like it or anything that provides any clues.

---

### Post by amsterdamharu on 2010-12-09
Have you started synaptic from a terminal? 
```
gksu synaptic
```
Maybe that will give you some errors.

One thing I usually do when a program breaks down is re-installing it. This works for apps like pidgin but I'm not sure it'll work for synaptic package manager as it could seriously screw up stuff.

Here is how to uninstall package manager/synaptic
```
sudo apt-get purge synaptic
sudo apt-get install synaptic
```

If you have your home dir in a separate disk/partition and it seriously brakes you can re-install without losing personal data.

After reading some horror stories about the updates I'd rather just re-install a newer version when needed (using mint 8 now and happy with it so no need yet).
Install everything on one partition -> the system partition will have a home folder and a newly created user folder, I boot up with tinycore and have ubuntu mount my home partition instead of the newly created one. This in case the install would destroy something in home.

---

