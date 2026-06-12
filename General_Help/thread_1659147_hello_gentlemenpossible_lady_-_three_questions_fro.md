---
title: "hello gentlemen/possible lady - three questions from a  newbie!"
date: 2011-01-03
forum: General Help
---

### Post by JuicyCouture on 2011-01-03
im really impressed with the OS so far, exactly what i've been looking for. the install was a little rough, it hung up on "getting the time from the server" for almost 15 minutes even though i was connected to the internet. then for the first few bootups, the ubuntu boot screen was a box that only took up 1/4 of the screen. but that went away. anyway - im in now and its all looking good, but theres a few things i would like to be able to know how to do.

#1 - how do i set up evolution to access my hotmail account?

#2 - just noticed this while uploading an avatar to this site, the box that pops up that lets you browse your files - theres no view change? i have to click each individual picture to see what it is; can this be changed?

#3 - what is currently the best way to get an expose-like feature going in ubuntu? 


thanks for the help fellas we'll probably be seeing a lot more of each other.

regards,

---

### Post by Verbeck on 2011-01-03
1.
> 
**POP server**: pop3.live.com (Port 995)   
**POP SSL required**? Yes
**User name**: Your Windows Live ID, for example [EMAIL="yourname@hotmail.com"]yourname@hotmail.com[/EMAIL]
**Password**: The password you usually use to sign in to Hotmail or Windows Live
**SMTP server**: smtp.live.com (Port 25)   
**Authentication required?** Yes (this matches your POP username and password)
**TLS/SSL required?** Yes
edit: instructions with screenshots [[LINK]]("http://pricklytech.wordpress.com/2010/05/01/ubuntu-10-4-lucid-configuring-evolution-to-connect-to-hotmail-windows-live-mail/")

2. dunno

3. install *compizconfig-settings-manager *(search for *ccsm* and install the advanced one if you use the software center) and *compiz-fusion-plugins-extra*,
then open the compizconfig settings manager from system>preferences

from there, play around till you get what you need
eg1: enable the plugin 'scale' and press the 'windows key' + w to see all open windows
eg2: enable Expo and press the 'windows key' + E to see all workspaces

---

### Post by JuicyCouture on 2011-01-03
thank you

one other thing, i remember from watching linux mint installation tutorials that you needed to set a home partition, a root partition, even a swapfile.

but none of that was asked when installing 10.10 - anyone know if these simply arent used or if they are set to some default? in which case what are they set to?

thanks again

---

### Post by lithopsian on 2011-01-03
10.10 installation does give you the option of setting these things but it isn't exactly obvious.  Remember the screen with the orange and green line?  Just pressing the buttons at each stage will not do it.  I think you get a swap partition by default, but maybe I'm wrong about that.

It is not essential that you have these things and Ubuntu will work just fine in one partition without even a swap partition.  You can type sudo swapon -s to see what sort of swap you have.  A separate /home partition can be useful if you want to overwrite with a new version or distro without affecting your settings and personal data.

---

### Post by cipherboy_loc on 2011-01-03
Do you NEED to set a /home partition? I don't use one, while it might be nice for when you run multiple OSes, such that you have a separate place for your /. Then, if you have to re-install, your data is already separated from your OS that you want to replace.

As for a swapfile, some might argue whether a swap file is better than a swap partition, but overall, if you want to hibernate, you should have a swap (file/partition) one to two times the size of your RAM. I would argue that if you could ensure that you will always have a USB flash drive (not an external hard drive, but actual flash media) plugged in, you should format some of that as Swap, just because seek time on flash is much less than a HDD.

In other words, you have encountered one of the many choices in GNU/Linux and Ubuntu. Do you want to be a "power" user that customizes your system to the ends of the Earth (separate /, /usr, /tmp, /var, and /whatever/directory/you/want/separated), or do you want a more basic configuration that will work for most users.

As for question 2 on your original post, I would imagine there would be a way, but where it is, I don't know.

--EDIT--
If you did not get a swap partition and or a swap file, follow this tutorial (on the ubuntuforums) to create a swap file (you can create it any where, just make sure that what ever media you put it on 1) has enough room and 2) will always be attached to the system at boot (so if you always want to boot with a USB drive attached, you could put it there)).
--/EDIT--

Cipherboy

> **JuicyCouture said:**
> thank you

one other thing, i remember from watching linux mint installation tutorials that you needed to set a home partition, a root partition, even a swapfile.

but none of that was asked when installing 10.10 - anyone know if these simply arent used or if they are set to some default? in which case what are they set to?

thanks again

---

### Post by Verbeck on 2011-01-03
> **JuicyCouture said:**
> 
one other thing, i remember from watching linux mint installation tutorials that you needed to set a home partition, a root partition, even a swapfile.

but none of that was asked when installing 10.10 - anyone know if these  simply arent used or if they are set to some default? in which case what  are they set to?

you'll get the choice if you select 'manually partition' from the installer (both mint and ubuntu)

but if you choose 'use entire disk', the defaults are X2 Ram size swap and the rest as the root partition. no separate /home

---

### Post by JuicyCouture on 2011-01-03
wow this no view change in the file selection panes are gonna be a big issue for me as i spend a lot of time on 4chan constantly uploading pictures

someones gotta know a way to add a view change to that

---

### Post by JuicyCouture on 2011-01-03
are they planning on combining the bottom window bar into the top bar? doesnt seem like they have to have both

they have a dock like app launcher on the top bar, if they combined the icons to manage windows like windows 7 does we could get a lot more screen real estate

though this is linux im sure all that is modifiable as it is

---

### Post by Verbeck on 2011-01-03
> **JuicyCouture said:**
>          are they planning on combining the bottom window bar into the top bar? doesnt seem like they have to have both

they have a dock like app launcher on the top bar, if they combined the  icons to manage windows like windows 7 does we could get a lot more  screen real estate

they'll be doing some changes to the default desktop UI in the next release. 
you can see how it looks like at the moment on the netbook edition
[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)
[http://www.google.com/images?hl=en&source=imghp&biw=1440&bih=751&q=ubuntu+unity&gbv=2&aq=f&aqi=g10&aql=&oq=&gs_rfai=](http://www.google.com/images?hl=en&source=imghp&biw=1440&bih=751&q=ubuntu+unity&gbv=2&aq=f&aqi=g10&aql=&oq=&gs_rfai=)

> **JuicyCouture said:**
> 
though this is linux im sure all that is modifiable as it is           
yep , right click>add to panel if you want to add an applet
and right click the applet>un-check 'lock to panel' > remove from panel

---

### Post by piquat on 2011-01-04
> **JuicyCouture said:**
> #2 - just noticed this while uploading an avatar to this site, the box that pops up that lets you browse your files - theres no view change? i have to click each individual picture to see what it is; can this be changed?

I knew this was going to be a pain for someone as soon as I saw it.  It's not really an option to use a different file manager since it will open in nautilus anyway.  And changing that association isn't an option, I don't think anyway.

---

