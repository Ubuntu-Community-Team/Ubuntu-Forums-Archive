---
title: "Synaptics Touch Pad in Lenovo"
date: 2011-05-20
forum: General Help
---

### Post by sindhughanti on 2011-05-20
I'm running Ubuntu 10.04 LTS on Lenovo
 The problem is that there is no way of configuring my touchpad under GUI.
First, there is no "Touchpad" tab in System -> Preferences -> Mouse.
I installed GSynaptics, but every time I try to run it, it gives the  "You have to set 'SHMConfig' 'true' in xorg.conf". 

The point is that  there is no default xorg.conf file in 10.04. I tried to make one with  Xorg -configure; it had no 'Synaptics Touchpad' entry; 

I created one,  and I did set the 'SHMConfig' option to 'true', but it didn't do  anything. Obviously, Xorg simply pays no attention to xorg.conf file any  longer.
 Then, I tried to use the new way of configuring Xorg with HAL  .fdi files. I created an **/etc/hal/****fdi/policy/preferences.****fdi file** and wrote
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>     
      <match key="input.x11_driver" string="synaptics"> 
        <merge key="input.x11_options.SHMConfig"     type="string">on</merge>     
      </match> 
    </device>
    </deviceinfo>
in it. 

This did nothing, GSynaptics still gives the error.
MY USB mouse works too. But if i touch the touchpad bymistake, the usb mouse+touchpad, both stop working.
 To summarize, there are two main bug issues:
1. No 'Touchpad' tab in System -> Preferences -> Mouse.
2. No way to enable SHMConfig to get other GUI touchpad preferences apps running.
 Please help
thanks

---

### Post by linuxinstalledfromhdd on 2011-05-20
I would check and see if a driver update has occured in the latest version of Ubuntu by creating a ubuntu live usb drive and booting from it. 

It could be a driver issue. 

Maybe someone else has more knowledge about Lenovo touchpad issues here and Ubuntu.

---

