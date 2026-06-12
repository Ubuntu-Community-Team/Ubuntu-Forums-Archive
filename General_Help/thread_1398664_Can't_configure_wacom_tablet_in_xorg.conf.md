---
title: "Can't configure wacom tablet in xorg.conf"
date: 2010-02-04
forum: General Help
---

### Post by Hamiltonafjr on 2010-02-04
Hi! I have a wacom graphire3 tablet and two monitors. The tablet is workin properly with out of the box drivers. As well as the dual monitors configured as twinview through Nvidia X server. But the tablet is mapped for the two screens, then I searched the forums for a proper configuration and it it tells me to edit the xorg.conf file for twinview horizontal but, it don't make any difference. I've "sudo gedit" edited the xorg.conf and nothing happens. Nothing, the tablet is working properly, the system is stable and it's still mapped for two screens.
What can I do? The xorg.conf also isn't listing all my hardware, I can't see the confs for my mouse. I'm on karmic koala.

---

### Post by Favux on 2010-02-04
Hi Hamiltonafjr,

Welcome to Ubuntu forums!

The xorg.conf is deprecated in Karmic.  If you had Intel or ATI video you probably wouldn't even have one.  To configure things you are "suppose" to use a .fdi (device information file).

Using the xorg.conf means you don't have hot plugging for your Graphire3 (it's usb, correct?).

Is wacom-tools installed when you check in Synaptic Package Manager?

---

### Post by Hamiltonafjr on 2010-02-04
My graphire3 is USB. And wacom tools is installed.

I've found 10-linuxwacom.fdi file, but it seems too complicated, I won't mess with it. Is there a string I can add to enable twinview?

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
    <append key="wacom.types" type="strlist">cursor</append>
    <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
    <append key="info.capabilities" type="strlist">input</append>
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
    <merge key="input.device" type="copy_property">serial.device</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
      <!-- Serial tablets with touch capabilities -->
      <append key="wacom.types" type="strlist">touch</append>
    </match>
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <!-- Serial tablets that operate at higher baud rate -->
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
       </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
      <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
      <append key="wacom.types" type="strlist">eraser</append>
      <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>


```

---

### Post by Favux on 2010-02-05
Hi Hamiltonafjr,

It really isn't any more complicated than xorg.conf, just a different format.  The new-generic rc2 .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") has some labels that should help you see what's happening.  The commands are in this thread:  [http://ubuntuforums.org/showthread.php?t=1185904](http://ubuntuforums.org/showthread.php?t=1185904)

You can convert them into the xorg.conf version.  See these pages on the LWP's HOW TO:
[http://linuxwacom.sourceforge.net/index.php/howto/multimonitor](http://linuxwacom.sourceforge.net/index.php/howto/multimonitor)
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev) - for the xorg.conf commands
[http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

