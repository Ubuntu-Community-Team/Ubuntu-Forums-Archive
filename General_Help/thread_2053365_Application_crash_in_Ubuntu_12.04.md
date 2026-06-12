---
title: "Application crash in Ubuntu 12.04"
date: 2012-09-05
forum: General Help
---

### Post by sebin on 2012-09-05
After opening the applications like firefox it is crashing. 
 
I have attached the 'apport.log'. 
 
I have installed 12.04 a week back. And it is difficult to work with ubuntu. even the browser is crashing in seconds:(
 
Let me know what can be the problem.

---

### Post by sebin on 2012-09-05
What should i do now? Re-install the complete UBUNTU? Any suggestions? 

Lot of pop-up windows with 'report this problem'..

---

### Post by sebin on 2012-09-08
when i login i get this error(attached the screen shot). When i click the 'roport problem' i get another error. this keep on continue..:(

Any suggestions from any one?

---

### Post by sebin on 2012-09-08
i am not sure all my problems with ubuntu 12.04 is the same issue..

here i have another issue
```
seb@seb-desk:~$ mahjongg 
Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(mahjongg:4007): GLib-GIO-CRITICAL **: g_application_list_actions: assertion `application->priv->is_registered' failed
Segmentation fault

```

---

### Post by sebin on 2012-09-09
```

seb@seb-desk:~$ software-center
Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
2012-09-09 13:23:31,549 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-09-09 13:23:31,552 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:34:20: Not using units is deprecated. Assuming 'px'.

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:34:22: Not using units is deprecated. Assuming 'px'.

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:56:20: Not using units is deprecated. Assuming 'px'.

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:56:22: Not using units is deprecated. Assuming 'px'.

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:60:20: Not using units is deprecated. Assuming 'px'.

(software-center:2151): Gtk-WARNING **: Theme parsing error: softwarecenter.css:60:22: Not using units is deprecated. Assuming 'px'.
2012-09-09 13:23:31,847 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-09-09 13:23:31,973 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-09-09 13:23:31,980 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-09-09 13:23:32,025 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 8}']'
2012-09-09 13:23:32,025 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'ERROR:__main__:urclient_apps
Traceback (most recent call last):
  File "/usr/share/software-center/piston_generic_helper.py", line 214, in <module>
    piston_reply = f(**kwargs)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/validators.py", line 44, in wrapper
    return func(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/validators.py", line 44, in wrapper
    return func(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/validators.py", line 65, in wrapper
    return func(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 140, in wrapper
    data = json.loads(body)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 382, in raw_decode
    obj, end = self.scan_once(s, idx)
ValueError: Expecting : delimiter: line 22316 column 20 (char 581861)
'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 136, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 215, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 69, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 109, in __init__
    softwarecenter.paths.APP_INSTALL_PATH)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 250, in parse_applications_menu
    tree = ET.parse(f)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 1183, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 656, in parse
    parser.feed(data)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 1643, in feed
    self._raiseerror(v)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 1507, in _raiseerror
    raise err
xml.etree.ElementTree.ParseError: not well-formed (invalid token): line 68, column 33

```

---

### Post by sebin on 2012-09-10
```
seb@seb-desk:~$ transmission-gtk 
Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2971): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed
```

---

### Post by sebin on 2012-09-10
i don't know why no one had looked into my problem? 

Am i reporting something wrong? or in a wrong form? or in a wrong way?

But for me it become almost impossible to work in ubuntu. All the applications crashes this time or the other. :(

---

### Post by diogobaeder on 2012-10-05
> **sebin said:**
> i am not sure all my problems with ubuntu 12.04 is the same issue..

here i have another issue
```
seb@seb-desk:~$ mahjongg 
Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(mahjongg:4007): GLib-GIO-CRITICAL **: g_application_list_actions: assertion `application->priv->is_registered' failed
Segmentation fault

```

The same is happening to me today (that "application->priv->is_registered" error). I'm also not sure what's happening, but so far this is the only program that has this error that I saw so far.

---

### Post by sebin on 2012-10-05
i tried these things. 
1) remove the PAE kernal and install the normal one.
2) reinstall the  mahjongg

but the effect is the same. May be we have to get the source and recompile and see..

---

### Post by editheraven on 2012-10-05
What gnome session you are logging in? Unity or shell?

---

### Post by sebin on 2012-10-05
gnome classical

---

### Post by editheraven on 2012-10-05
Tryied unity? Just for trouble shoting?

---

### Post by sebin on 2012-10-05
i am on the middle of something. i will try that end of today.. and update you 
thanks.

---

### Post by sebin on 2012-10-05
I do had problem with the PAE kernels. I am not sure about, it is PAE problem or not. I am still investigating.

When i run the memtest from the Grub2 i was getting 50000+ error.
I have tried the memtest from ubuntu 10.4 live CD no error.

So i removed the PAE which is default in the ubuntu 12.04(even though i have 4GB ram). I am not sure my observations are correct or not.. but now things are not crashing as in the previous case

---

### Post by editheraven on 2012-10-05
Pae it's a patch for kernel. In fact, a custom option. Tryied recompiling your kenrel? Or, reinstalling it through synaptic?  Sounds like some packages did not get compiled in the kernel. More precisely, the kernel didn't got compiled with those packages.

---

### Post by sebin on 2012-10-05
I did not compiled the kernel. I installed Ubuntu 12.04. then from synaptic i removed the PAE versions and selected the non-pae version.

---

### Post by sebin on 2012-10-05
so the Grub memetest uses the kernel? any idea?

---

### Post by claracc on 2012-10-05
> **sebin said:**
> when i login i get this error(attached the screen shot). When i click the 'roport problem' i get another error. this keep on continue..:(

Any suggestions from any one?

As you can see in this link: [https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/959054](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/959054) it is a known bug, you can say it affects you too, in order to be solved as quick as possible.

I think you have not received any answer because you havent appots enough information about your hardware (run lspci in a xterm) and about the 12.04 release you are using ( 32 bits, 64 bits) and the desktop you are using.

Why were you using a PAE kernel?, have you do any other customization to the software?

---

### Post by sebin on 2012-10-05
```

seb@seb-desk:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4550]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
seb@seb-desk:~$ 

```I use 32bit 12.04 release

PAE kernel is the default in ubuntu 12.04 32bit. And i think to access 4gb memory i need PAE.

No i have not done any customization.

---

### Post by sebin on 2012-10-05
> **editheraven said:**
> Tryied unity? Just for trouble shoting?

i get the same error in unity too..

---

### Post by claracc on 2012-10-06
I think your problem can be in the drivers of your ATI graphics card.

Please, see this thread discussing the use of open source or privative driver for ATI card: [http://ubuntuforums.org/showthread.php?t=1609979](http://ubuntuforums.org/showthread.php?t=1609979)

---

