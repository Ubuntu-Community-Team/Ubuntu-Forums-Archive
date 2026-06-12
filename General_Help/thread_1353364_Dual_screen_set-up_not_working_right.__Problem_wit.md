---
title: "Dual screen set-up not working right.  Problem with virtual resolution."
date: 2009-12-12
forum: General Help
---

### Post by srikesh on 2009-12-12
Hello all,

I am trying to get my dual-screen set up to work in Ubuntu 9.10.

I am working with:

a) Toshiba Satellite Laptop
b) HP 2035 External Monitor

I have partially succeeded in getting the dual-screen set-up to work to the point where I get maximum resolution on the external monitor (1600x1200) but the laptop display resolution is low (800x600).

In the 'Display Preferences' dialog box I have the option to increase the resolution of the laptop display to '1024x768' or '1280x800'. But when I try one of those two options, I get the following error message:

"Monitor Resolution Settings has detected that the virtual resolution must be set in your configuration file in order to apply your settings.  Would you like Screen Resolution to set the virtual resolution for you? (Recommended)".

If I select the recommended option, I am not able to log back into the regular gnome interface and get an error. Looking around in the error message I realized that Ubuntu writes a new 'xorg.conf' file that only lists the external monitor with the maximum virtual resolution of 1600x1200.  The only way for me to get back to the usual ubuntu desktop screen is to replace the new 'xorg.conf' file with the backed-up file.

Can someone please help me figure out what is going on.  Why can I get 800x600 with out a problem but with anything higher, Ubuntu complaints about virtual resolution?  I would like to have the maximum resolution in both the screens.

According to my 'lspci', my graphics card is VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Thanks.
Srikesh

---

### Post by edster on 2010-01-21
I too am having the same problem with adding an external monitor to an IBM Thinkpad R51.  The 'virtual resolution' setting in the 'Screen' section that is added by that process

```
 	SubSection "Display"
 		Virtual	2304 1024
 	EndSubSection
```

Causes an error:

```
failed to add fb

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```

under the latest kernel 2.6.28-17...  2.6.28-15 and 2.6.28-16 will not crash but I cannot increase the resolution of my secondary display -- nothing is updated in the xorg.conf, simply a message requesting I logout to restart X.

Please advise!

---

