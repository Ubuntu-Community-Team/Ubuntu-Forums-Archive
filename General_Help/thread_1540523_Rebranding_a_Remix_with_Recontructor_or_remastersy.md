---
title: "Rebranding a Remix with Recontructor or remastersys?"
date: 2010-07-27
forum: General Help
---

### Post by Nick_Jinn on 2010-07-27
Lets say we want a unified custom distro of Ubuntu or Mint for a project and we all need the same tools, the same bookmarks, and some preconfigured accounts and IRC chat link......Is there a way to rebrand it easily with those tools?

Can you using a different tools, like morphing morphix to mod something other than Morphix? Like using Morphix to remake a Ubuntu spinoff or using it to combine repositories from 2 different releases?

---

### Post by bodhi.zazen on 2010-07-27
For the most part as long as you follow the GPL and do not use trademarked names, such as Ubuntu, go for it.

You can mix repositories with apt-pinning, but it is quite technical, and has been known to cause carnage.

---

### Post by Nick_Jinn on 2010-07-28
Certainly. I am not trying to create a competing distro or anything. Its intended to be very limited in scope for a smallish groups purposes. We are not trying to steal anyones fire.


I am not skilled enough to create anything too innovative or different. I just need everyone in my project to be on the same page. Rebranding isnt even essential, but it might be cool.



My question was 'how' rather than 'may I'. I know Morphix has a tool, but I have not tried it. Wasnt Ubuntu originally based on Morphix, or at least the live CD portion?

---

### Post by bodhi.zazen on 2010-07-28
There is a ton to read and know about making a live CD.

Start with the documentation for remastersys.

See also :

[LiveCDCustomizationFromScratch - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

---

### Post by Nick_Jinn on 2010-07-28
Thanks. You obviously know your stuff so I will value your suggestions.


This is a small spin-off project for activists, not really for the general public. I am not really a dev so I am looking to use the most simple GUI based tools available.

---

### Post by bodhi.zazen on 2010-07-28
> **Nick_Jinn said:**
> Thanks. You obviously know your stuff so I will value your suggestions.


This is a small spin-off project for activists, not really for the general public. I am not really a dev so I am looking to use the most simple GUI based tools available.

I understand what you want, and as I indicated, remastersys is, IMO, probably the easiest.

BUT, there is a bit of a learning curve for making a live CD / iso and I found the documentation only goes so far, you have to jump in and give it a try. It is complex and you will need to be prepared to read a fair amount, and try a few new tricks, such as a chroot.

If you run into problems, post back.

---

### Post by TNAFan on 2010-07-31
I would love to do this exact thing, however the problem I have encountered when trying to use remastersys is that one can only use a default Ubuntu installation with the extra apps you have isntalled, or create something that installs your custom settings, but unfortunately also is necessary that it copies over your user info and passwords and everything.  I want something that straight out remasters a custom Ubuntu distro, such as Mint, or any of the *ubuntu's.  Know how I can do this?

---

### Post by Nick_Jinn on 2010-07-31
> **TNAFan said:**
> I would love to do this exact thing, however the problem I have encountered when trying to use remastersys is that one can only use a default Ubuntu installation with the extra apps you have isntalled, or create something that installs your custom settings, but unfortunately also is necessary that it copies over your user info and passwords and everything.  I want something that straight out remasters a custom Ubuntu distro, such as Mint, or any of the *ubuntu's.  Know how I can do this?


I wonder if 'Morphing Morphix' could do that since its 'modular', whatever that means.

---

### Post by ankspo71 on 2010-07-31
> **TNAFan said:**
> I would love to do this exact thing, however the problem I have encountered when trying to use remastersys is that one can only use a default Ubuntu installation with the extra apps you have isntalled, or create something that installs your custom settings, but unfortunately also is necessary that it copies over your user info and passwords and everything.  I want something that straight out remasters a custom Ubuntu distro, such as Mint, or any of the *ubuntu's.  Know how I can do this?

Hi, 
The way to use your current customized settings is to basically copy some settings from your home folder and paste them into your /etc/skel/ folder, then change their permissions to root. Be sure not to include any passwords, or anything else you would consider private though.

See: "COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS" on this page for more details:
[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html) 
"DISTRO PREP" is also another section worth reading about customization.
Hope this helps. (Unless you were talking about rebranding, which is something totally different and I know little about.)

---

### Post by bodhi.zazen on 2010-07-31
> **TNAFan said:**
> I would love to do this exact thing, however the problem I have encountered when trying to use remastersys is that one can only use a default Ubuntu installation with the extra apps you have isntalled, or create something that installs your custom settings, but unfortunately also is necessary that it copies over your user info and passwords and everything.  I want something that straight out remasters a custom Ubuntu distro, such as Mint, or any of the *ubuntu's.  Know how I can do this?

First, read the remastersys documentation. Use the dist option :

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Second, once you make a base iso, extract it and modify it, then repackage it.

Or if you prefer, make one "from scratch"

[LiveCDCustomizationFromScratch - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch") 

You also need to understand how to use a chroot. Clear the logs and .bash_history before you package your custom iso.

[https://wiki.kubuntu.org/DebootstrapChroot](https://wiki.kubuntu.org/DebootstrapChroot)

You may do extensive customizations to a custom iso, BUT you will need to do extensive reading depending on what you want to change. You can, for example, make a custom boot screen (grub), customize the GDM screen, custom themes, customize the default window manager settings, add a set of default firefox settings, etc. Take a look at how to use /etc/skel ;)

Again, all these customizations will take a lot of reading and an understanding of the underlying system and system files.

If you have a specific question about a specific step, post here. But posting step - by -step instructions would look very much like the documentation linked in this post.

---

### Post by TNAFan on 2010-08-02
> **ankspo71 said:**
> Hi, 
The way to use your current customized settings is to basically copy some settings from your home folder and paste them into your /etc/skel/ folder, then change their permissions to root. Be sure not to include any passwords, or anything else you would consider private though.

See: "COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS" on this page for more details:
[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html) 
"DISTRO PREP" is also another section worth reading about customization.
Hope this helps. (Unless you were talking about rebranding, which is something totally different and I know little about.)

Thank you!  Will take a look when I can.

---

### Post by Nick_Jinn on 2010-08-07
So I have seen some options for naming the ISO and the user name, but what if I want to rebrand the name to something funny and appropriate to the theme. I dont see an option in Remasterys for rebranding.  I did see one in Morphing Morphix, a project which is discontinued. I dont even know where to find an ISO for that.

---

