---
title: "question about ubuntu fork"
date: 2011-10-24
forum: General Help
---

### Post by khaled.battah on 2011-10-24
hello guys
I want to ask how can I make a small fork from ubuntu?? like Mint and these distros?? 
how can I do a fork?
I am asking because I want to make it as a graduation project from my collage can you help me?

---

### Post by techvish81 on 2011-10-24
actually developers can tell you the right way,  however there is a shortcut,  
download Ubuntu minimal,  use Ubuntu customization kit to install whatever desktop environment u like and default software u prefer.  u will get final live ISO.

---

### Post by khaled.battah on 2011-10-25
> **techvish81 said:**
> actually developers can tell you the right way,  however there is a shortcut,  
download Ubuntu minimal,  use Ubuntu customization kit to install whatever desktop environment u like and default software u prefer.  u will get final live ISO.
what is ubuntu minimal??
and what is ubuntu customization kit????
is that how I do a derivative from ubuntu????

---

### Post by oldtimer7777 on 2011-10-25
> **khaled.battah said:**
> what is ubuntu minimal??
and what is ubuntu customization kit????
is that how I do a derivative from ubuntu????

Can I just ask the point of this? I can help save you some time hopefully.  

You want to build an entire new fork disto Debian/Ubuntu? Why not just use Pure Debian? 

It really honestly depends on what you are trying to accomplish.

Is this a college project? I can think of a million ways to save you some time if you want.

Maybe even just use Relinux instead if you just want to mess around and create your own customized version of Ubuntu to share with other users?

---

### Post by haqking on 2011-10-25
> **khaled.battah said:**
> what is ubuntu minimal??
and what is ubuntu customization kit????
is that how I do a derivative from ubuntu????


Ubuntu minimal is a minimal version funnily enough ;-)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu customisation kit is so you can customise Ubuntu

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

yes

---

### Post by oldtimer7777 on 2011-10-25
I"m sorry to tell you this but UCK doesn't work in Ubuntu 11.10 defaults settings anymore. Try downloading and installing and customizing with it... It doesn't customize anymore. It did in 11.04. 11.10 is missing a way to change the configuration settings. They removed some of the packages that UCK needs to run properly in Ubuntu 11.10.  Reliux is what works now. It is the Remastersys replacement because Remastersys is no longer available. Frag took it down. I wish UCK still worked. That would be great.

> **haqking said:**
> Ubuntu minimal is a minimal version funnily enough ;-)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu customisation kit is so you can customise Ubuntu

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

yes

---

### Post by haqking on 2011-10-25
> **oldtimer7777 said:**
> I"m sorry to tell you this but UCK doesn't work in Ubuntu 11.10 defaults settings anymore. Try downloading and installing and customizing with it... It doesn't customize anymore. It did in 11.04. 11.10 is missing a way to change the configuration settings. They removed some of the packages that UCK needs to run properly in Ubuntu 11.10.  Reliux is what works now. It is the Remastersys replacement because Remastersys is no longer available. Frag took it down. I wish UCK still worked. That would be great.

true but no particular version was mentioned.

Yeah re-linux is the remastersys fork which you can find instructions for here [http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)

which has a link to the source.

You can also make a custom install CD [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by Dangertux on 2011-10-25
Not that I dislike Ubuntu or Debian...But do we really need another?

---

### Post by oldtimer7777 on 2011-10-25
> **Dangertux said:**
> Not that I dislike Ubuntu or Debian...But do we really need another?

I would really like to see a distro like Crunchbang was back in 9.04.  But after they changed the way GDM works, and now we are at LightDM, it would be a headache. Many people switched to Debian after that move. I haven't really tried Arch yet. It looks promising, yet a bit too complicated for novices, which may be a good thing depending on how you want to look at it.:D

---

### Post by khaled.battah on 2011-10-26
> **oldtimer7777 said:**
> Can I just ask the point of this? I can help save you some time hopefully.  

You want to build an entire new fork disto Debian/Ubuntu? Why not just use Pure Debian? 

It really honestly depends on what you are trying to accomplish.

Is this a college project? I can think of a million ways to save you some time if you want.

Maybe even just use Relinux instead if you just want to mess around and create your own customized version of Ubuntu to share with other users?
It is  a college project,
I want to make something new in this project,because it is the graduation project

---

### Post by oldtimer7777 on 2011-10-26
> **khaled.battah said:**
> It is  a college project,
I want to make something new in this project,because it is the graduation project

Use Relinux. That is how you would want to do it. If you were a small forigen country, creating your own distro with private repositories or whatever would make sense. But for a school project? No way..  Thousands already exist. Try something else we could use.. Like a replacement for Remastersys and creating your own Repository for that. Build something like that from source instead. We need another distro like we need a hole in our heads.

---

