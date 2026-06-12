---
title: "How to enable compiz under Virtualbox on Dell Inspiron 1525"
date: 2010-08-02
forum: General Help
---

### Post by aaronkatrini on 2010-08-02
I have a dell inspiron 1525 and installed Virtualbox 3.2.6 and installed Ubuntu 10.04 on a VM. The installers went fine. After updating and installing the guest additions and also installing compiz-setting-manager i'm still not able to get the compiz effects. please any suggestions . :)

---

### Post by Joe of loath on 2010-08-02
Compiz needs a fast (ish) video card, something virtualbox can't give you I'm afraid.

What's the host OS?

---

### Post by aaronkatrini on 2010-08-02
> **Joe of loath said:**
> Compiz needs a fast (ish) video card, something virtualbox can't give you I'm afraid.

What's the host OS?

yes it is possible! many others did but i can't :(

this guy did       [http://www.youtube.com/watch?v=USmiMF-OunM](http://www.youtube.com/watch?v=USmiMF-OunM)

---

### Post by aaronkatrini on 2010-08-02
> **123456raju said:**
> I have a dell inspiron 1525 and installed Virtualbox 3.2.6 and installed Ubuntu 10.04 on a VM.
regards,

phe9oxis,


[http://www.dynamicdrive.com](http://www.dynamicdrive.com)
 
and you can run compiz?? 
if so how you did it ?

---

### Post by Joe of loath on 2010-08-02
> **aaronkatrini said:**
> and you can run compiz?? 
if so how you did it ?

They're a spammer. They just repeated your first sentence.

---

### Post by aaronkatrini on 2010-08-02
> **Joe of loath said:**
> They're a spammer. They just repeated your first sentence.
  
I just realized that.

What about the compiz running on Virtualbox. 

(BTW the host is Vista Basic SP1.)

---

### Post by fabrixx on 2010-11-04
Same problem with Virtualbox 3.2.10 (running on Debian/Ubuntu 11.04 Guest), compiz appear installed in ubuntu 11.04,  Vbox addons is installed, 3d is enable (128mb).

When i try to enable effects from Administration menu to medium i receive impossible to enable effcts (with flashing windows).
Not find any proprietary driver.

When i run compiz from terminal nautilus windows crashes and receive multiple gk error messages.

I'm not able tu install

I've see the video linked up.

My compiz-check: 
> 
Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
 Driver in use:         vboxvideo
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in useI run Vbox on hp dv51179/nvidia 9600m gt.

Any suggestion to fix?

Thanks..excuse me for my bad english..


edit: I not have any /etc/X11/xorg.conf and i edited a new one but with no results..

---

### Post by dcstar on 2010-11-04
> **fabrixx said:**
> 
.........
Any suggestion to fix?

Thanks..excuse me for my bad english..


edit: I not have any /etc/X11/xorg.conf and i edited a new one but with no results..

VM issues belong in the Virtualization forum, if there is a solution it is probably already there.

---

### Post by fabrixx on 2010-11-06
Thks i will try in that session.

---

