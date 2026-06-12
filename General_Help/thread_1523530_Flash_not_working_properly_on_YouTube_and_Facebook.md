---
title: "Flash not working properly on YouTube and Facebook"
date: 2010-07-03
forum: General Help
---

### Post by jonnierod on 2010-07-03
About a month or two ago Flash suddenly stopped working for me on YouTube and Facebook.  Everything else seems to work just find, but I can't watch video on YouTube and I can use a lot of things on Facebook.  These sites no longer work in Firefox or Chrome.

I've searched the forums, uninstalled and reinstalled Flash a hundred times, but nothing seems to work.  I'm running 10.04 on an Acer Aspire 5315.

Any ideas?
 Thanks,

Jonathan

---

### Post by lovinglinux on 2010-07-04
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by ansil on 2010-07-10
"Type **about:config** in Firefox address bar, then type **plugin.expose_full_path**  in the filter, then double-click the same item in the results to make  it **true**. "

ok did this and that part worked 




Then type **about:plugins** in the address  bar, find Shockwave Flash, copy the corresponding Path and Version and  paste here.


there was no about plugins when i typed it it was blank apparently its not reckognizing the plugins. but flash works great when its not full screen.  when its full screen it is like watching frame by frame slide show.

i have installed all the updates for ubuntu 10.04 everything says up to date. fire fox said i had the plugins i downloaded all of them. so what am i doing wrong here o captain my captain

---

### Post by lovinglinux on 2010-07-11
> **ansil said:**
> "Type **about:config** in Firefox address bar, then type **plugin.expose_full_path**  in the filter, then double-click the same item in the results to make  it **true**. "

ok did this and that part worked 




Then type **about:plugins** in the address  bar, find Shockwave Flash, copy the corresponding Path and Version and  paste here.


there was no about plugins when i typed it it was blank apparently its not reckognizing the plugins. but flash works great when its not full screen.  when its full screen it is like watching frame by frame slide show.

i have installed all the updates for ubuntu 10.04 everything says up to date. fire fox said i had the plugins i downloaded all of them. so what am i doing wrong here o captain my captain

Verify if you have the latest driver for your video card. "System >> Administration >> Hardware Drivers".

---

### Post by jonnierod on 2010-07-18
File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

---

### Post by lovinglinux on 2010-07-18
> **jonnierod said:**
> File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

That is an old version that has a critical vulnerability. 

Get version 1.0.7 of my [FLASH-AID](http://flash-aid-extension.blogspot.com/) extension. It will allow to easily install the latest flash version and remove conflicting plugins.

---

### Post by michael.the.bone on 2010-07-26
I'm still having the same problem.

I installed your package first a while ago and flash works when it wants to.

Just follwed your steps.

i have;

File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r53Also the admin-hardware drives, found nothing after i searched?


Cheers

---

### Post by lovinglinux on 2010-07-26
> **michael.the.bone said:**
> I'm still having the same problem.

I installed your package first a while ago and it worked when it wanted to, tried your steps.

Do i copied and paste the information for shockwave flash " file:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so" into the browser? then install it?

Also i did the admin-hardware drives, no results came up for me once it finished searching...

Please create your own thread and please be more descriptive about your problem. I don't understand half of it. From what I can understand, looks like you don' have a supported graphic driver.

---

### Post by michael.the.bone on 2010-07-27
Apologies, i edited it since my first post. I didn't think I would need a separate thread as its the same problem. My edited post stated:

"I'm still having the same problem.

I installed your package first a while ago and flash worked but when it wants to.

I follwed your steps.

i have;

File:   /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:    Shockwave Flash 10.1 r53

Also the admin-hardware drives, found nothing  after i searched?


Cheers"

I'll but sure to create a new thread next time a problem happens.

Thanks

---

### Post by PTOPedro on 2011-12-07
Hey there, i'm having the same problem. Facebook flash isn't working, but Youtube is. I don't quite understand.

---

