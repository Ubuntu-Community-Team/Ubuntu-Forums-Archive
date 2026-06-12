---
title: "Virtual Box - How can i change display of 16bit to 32bit?"
date: 2010-05-11
forum: General Help
---

### Post by chinmaya_n on 2010-05-11
This is the error it is displaying in the window!(In brown color, below)

[COLOR="DarkRed"]The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS.[/COLOR]

And It stops showing anything after clicking oK!
I didnt get it!
How can i change display of 16bit to 32bit? ( I could not open display properties of
With out changing it I could not load many OSs which I was trying!
 *Ubuntu 10.04
 *Mandriva
 *Ubuntu Studio 10.04
All these gave me the same error...
I googled, I saw some threads but none for 9.10 and they doesnt mean any thing... They could not solve me..
Any help will be greatly appreciated ....
Thanx

---

### Post by cap10Ibraim on 2010-05-11
How much memory did you set for the Video Display ?

---

### Post by bodhi.zazen on 2010-05-11
> **chinmaya_n said:**
> This is the error it is displaying in the window!(In brown color, below)

[COLOR="DarkRed"]The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS.[/COLOR]

And It stops showing anything after clicking oK!
I didnt get it!
How can i change display of 16bit to 32bit? ( I could not open display properties of
With out changing it I could not load many OSs which I was trying!
 *Ubuntu 10.04
 *Mandriva
 *Ubuntu Studio 10.04
All these gave me the same error...
I googled, I saw some threads but none for 9.10 and they doesnt mean any thing... They could not solve me..
Any help will be greatly appreciated ....
Thanx

For the most part, with Linux guests, you can ignore that message.

You set the graphics in the Guest. With Linux that would mean writing a xorg.conf

If you like, there is an xorg.conf in this post:

[http://forums.virtualbox.org/viewtopic.php?f=6&t=26309](http://forums.virtualbox.org/viewtopic.php?f=6&t=26309)

---

### Post by chinmaya_n on 2010-05-11
> **cap10Ibraim said:**
> How much memory did you set for the Video Display ?
I tried with 50MB.... but it didnt work :(

---

### Post by chinmaya_n on 2010-05-11
> **bodhi.zazen said:**
> For the most part, with Linux guests, you can ignore that message.

You set the graphics in the Guest. With Linux that would mean writing a xorg.conf

I read that in 9.10 we dont 've xorg.conf ! So how could I do that !?

---

### Post by cap10Ibraim on 2010-05-11
> **chinmaya_n said:**
> I tried with 50MB.... but it didnt work :(

I have it 128 mb can you try to set it to more than 64

---

### Post by chinmaya_n on 2010-05-11
> **cap10Ibraim said:**
> I have it 128 mb can you try to set it to more than 64

you can see in the attachment I 've kept it 128MB Its max in my system!
And Enabled 3D  acceleration too...
But It showed same error!! (See the attachment)

---

### Post by bodhi.zazen on 2010-05-11
> **chinmaya_n said:**
> I read that in 9.10 we dont 've xorg.conf ! So how could I do that !?

you have to write (copy  paste) the xorg.conf manually, in the guest

```
gksu gedit /etc/X11/xorg.conf
```

Be sure to install the guest additions first.

---

### Post by chinmaya_n on 2010-05-12
> **bodhi.zazen said:**
> 
Be sure to install the guest additions first.

I read this too, in some post that I searched in Google.!
I'm so sorry, I'm too confused...:confused:

How could I install Guest Additions with out installing a OS !?

I 've created a new harddisk in virtual box and I'm trying to install the distros.. or atleast trying to boot lively from an image that i've downloaded! ==> I don't 've OS to install Guest Additions!
And I was asked to write xorg.conf in guest ?
What do u mean by guest OS...? I'm running ubuntu 9.10 and trying to install or boot lively an image in virtual box. So, where do u want me to write that xorg.conf?

Edit: I created xorg.conf in /etc/X11 and it took me to low graphics mode after a restart so... I deleted it!

---

### Post by bodhi.zazen on 2010-05-12
If you are new to linux and virtualbox, seriously, I would ignore that "error message" and come back to it when you are more comfortable with both Virtualbox and Linux.

You are starting to ask very broad questions and unless you have a specific question about a specific issue unique to Ubuntu you will need to do some reading.

The best source of information on Virtualbox is the User manual which is listed on the VirtualBox downloads page:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

[http://download.virtualbox.org/virtualbox/3.1.8/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.1.8/UserManual.pdf)

Second best is the Virtualbox Forums.

[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

To install the Additions see either the Virtualbox user guide or use google (there are several on line guides).

[http://www.google.com/search?num=50&hl=en&client=firefox-a&hs=84s&rls=org.mozilla%3Aen-US%3Aofficial&q=ubuntu+install+virtualbox+guest+additions&aq=f&aqi=g1&aql=&oq=&gs_rfai=](http://www.google.com/search?num=50&hl=en&client=firefox-a&hs=84s&rls=org.mozilla%3Aen-US%3Aofficial&q=ubuntu+install+virtualbox+guest+additions&aq=f&aqi=g1&aql=&oq=&gs_rfai=)

The reason X failed is, as I indicated, you need to install the guest additions first.

Again, if you get stuck on a specific step or have a specific question please ask, but you are asking us to re-type the user guide and/or existing on line guides.

---

### Post by cboteros on 2010-06-10
I'm having this same problem, but I think with the opposite configuration.

I'm running VirtualBox from an Ubuntu Host (installed in a Macbook 2.1) and I'm running Windows XP guest with Guest Additions installed (and I installed it from "Safe mode" as suggested in other forums).

I also have 3D acceleration enabled according to the Settings, but I'm still getting this error message about my system not having 32 bit color depth but only 16...

I'm not sure how I can verify which color dept I'm using, specially now that Unbuntu Lucid Lynx doesn't make use of the xorg.conf file

Any idea anyone?

---

### Post by hippiehacker on 2012-01-02
It looks like much of the problem is related to people not wanting to see the message. It interferes with automation and makes people think there is an underlying problem to be solved.

I suggest just running a command to automatically never show such messages because it doesn't seem to affect performance for me at all.

From this post ->[https://forums.virtualbox.org/viewtopic.php?f=2&t=24273](https://forums.virtualbox.org/viewtopic.php?f=2&t=24273) it looks like you can make the warnings go away by settings some extra data params on the command line.

VBoxManage setextradata global GUI/SuppressMessages remindAboutAutoCapture,\
confirmInputCapture,remindAboutMouseIntegrationOn, remindAboutWrongColorDepth,\
confirmGoingFullscreen,remindAboutMouseIntegration Off

---

### Post by oldos2er on 2012-01-02
Closed, necromancy.

---

