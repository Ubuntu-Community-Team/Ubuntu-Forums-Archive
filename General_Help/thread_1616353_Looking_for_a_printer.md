---
title: "Looking for a printer"
date: 2010-11-08
forum: General Help
---

### Post by richlyn9 on 2010-11-08
After using Ubuntu for three years i have come to a stage where i dont feel the need of Windows(though i work on 7 in office) and now when the thought of buying a printer for home use (mostly documents / projects and sometimes photos) i am now looking for one that will  smoothly work in ubuntu 32 and 64 bit. 

I hear that HP is best recommended but 
i have been going through a few posts an came across this
"[B]Scanners are different.
There are some scanners (as do some printers) that work only in Windows via the GDI interface - they are designed this way. So dont buy GDI printers and stuff.
For a scanner to work in Linux, it has to be SANE compatible.

And most vendors dont bother to check their devices compatibility with Linux so missing a "Linux compatible" label doesnt say anything. Just try using xsane see if it works.[/B]
"
on [http://ubuntuforums.org/showthread.php?t=1536343&highlight=supported+printers]("http://ubuntuforums.org/showthread.php?t=1536343&highlight=supported+printers")

and now want to be doubly sure of things

so can someone recommend me a all-in-one printer (personally i feel HP is best for where i am in mumbai keeping in mind the after sales services)  that will work flawlessly with min hazards

---

### Post by richlyn9 on 2010-11-08
i was looking up the [HLIP]("http://hplipopensource.com/hplip-web/about.html") and found that the Deskjet 1050 is supported but also found that SCAn and GUI features are not there :(:( in the 10.4 distro

Installer	GUI14	Scan3	Fax5	Status	PhotoCard4	USB
Yes	         No	  No   	No	  Yes	   No          Yes

though i am not sure what it means
is anyone using these printers??
and am wondering if scan is supported??

---

### Post by TBABill on 2010-11-08
My HP Photosmart all in one printer works with printer, scanner, etc. in Ubuntu. It's a C309A model. I do not know if it is currently available where you live, but I bought it within the last 8 months. I use different scanner programs and they all work ok and the printer installs and configures easily with Ubuntu. It is also wireless so I use 5 different computers to print to it.

---

### Post by YuiDaoren on 2010-11-08
I just bought an HP Officejet 4500 (The wireless model, but the driver will work for the Ethernet model, too. I use the USB port in Linux, my wife uses the wireless from her Windows XP netbook.)

You will need the latest [HPLIP]("http://hplipopensource.com/hplip-web/index.html"), but scanning with xsane, printing and faxing all work.

Getting the latest HPLIP might make the Deskjet 1050 a winner, too. Worth a look.

---

### Post by richlyn9 on 2010-11-09
I have zeroed on hp deskjet 1050 as its not too much on the purse and i am not one who would be printing everyday and will rarely print high quality pics.

any things that i should know or any suggestions are valued.

Thanks!!

---

### Post by richlyn9 on 2010-11-27
finally i bought the HP deskjet 1050 AIO printer.
Works fine in windows  but it does not detect in 10.4 Lucid.
I installed the hp gui but it dosent detect either.

---

### Post by richlyn9 on 2010-11-27
the Hplip site to lookup [printer models]("http://hplipopensource.com/hplip-web/supported_devices/index.html") lists my printer as
** Support Information:**
Item	                Description
Minimum HPLIP version	3.10.6
Support level	        Partial (See note11.)
Recommended?	        No (See note15.)
Unsupported feature(s)	Scan

---

### Post by Spyderkid on 2010-11-27
Almost ever HP printer/Scanner comes with driver software on it for Linux. So I would suggest a HP All-In-One. Also you might want to get a Kodak all in one and go to source-forge and download and install a Kodak 5 driver from there it works for me.

---

### Post by Aryamaan on 2010-11-27
If you want a deskjet you should definitely give HP's 4400 Series a try. The best one in that is F4488. And if you want just a printer then i would recommend a HP Laserjet. And yes all HP Printers are extremely easy to use on linux or ubuntu

---

### Post by ImprisonedPride on 2010-11-27
If you want a laser printer, Newegg currently has the Samsung ML-1665 17ppm Laser Printer on a Black-Friday special for $39.99 with free 3-day shipping to continental US residents [HERE]("http://www.newegg.com/Product/Product.aspx?Item=N82E16828112195"). I bought one yesterday but it's not here yet so I can't give you a formal recommendation, although it was recommended to me from several friends. Hope it helps.

---

### Post by dougalkerr on 2010-11-27
Sorry richlyn9 the last few posters have obviously got in after you saying you have bought the HP 1050. I would back-up the HP printer you bought and say that it may well work fine with the Linux driver from another printer on the CUPS list.

I have the C4480 All-in-one and it works well with Linux too.

HP are bad for Windows 7 though. We have had to replace our HP printer at work after upgrading to Windows 7 and finding that the HP support for the printer is just not there. Even opting for Windows 7 to download the latest driver and install it automatically gave us no error messages but, the printer would just not function, full stop. It works just fine in Linux though and will still be used with it.

Persevere.

---

### Post by ImprisonedPride on 2010-11-27
I only suggested the deal because he said it doesn't work with 10.04 Lucid, and being that he purchased the printer so recently he could return it and possibly get the great deal offered on the one I listed for $40. I know the Samsung ML-1665 works with 9.04, 10.04 and 10.10 from friends' testimonies but I can't yet personally confirm this until mine arrives. When I thought about it I did my homework before I bought the printer. I found one very help thread that said there are actually Linux-driver instructions right in the manual for the printer. If you don't get a manual for some strange reason, it's available from their site [HERE]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=IT&CttFileID=3134655&CDCttType=UM&ModelType=N&ModelName=ML-1665&VPath=UM/201008/20100804163340687/EN/UPD_Guide_EN.pdf") and the driver itself [HERE]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=dk&CttFileID=2745812&CDCttType=DR&ModelType=N&ModelName=ML-1665&VPath=DR/201001/20100121132724343/UnifiedLinuxDriver_0.86.tar.gz"). The system requirements for the ML-1665 are:

> "Ubuntu 6.06, 6.10, 7.04, 7.10, 8.04, 8.10, 9.04, 9.10, 10.04 (32/64 bit)"

"CPU Pentium IV 2,4 GHz (Intel Core&#8482;2)"

"RAM 512 MB (1.024 MB)"


Hope this helps (more than my last post) and clears the air a bit. (To actually address the OP, I've never had good luck with HP-anything with Ubuntu or Windows-7.)

Good luck.

---

### Post by richlyn9 on 2010-11-28
Well Thanks !!! **dougalkerr** and **ImprisonedPride** 
i will look it up though i am not sure if i can return the printer that i have bought (not that i can't return it, but just that it involves too much trouble, not so simple as an exchange here where i am)

---

### Post by richlyn9 on 2010-11-28
downloaded the latest version of hplip in .tar.gz format on to the desktop and tried installing

hplip-3.10.9/data/images/16x16/ok.png
hplip-3.10.9/data/images/16x16/thumbnail.png
hplip-3.10.9/data/images/16x16/battery.png
hplip-3.10.9/data/images/16x16/active.png
hplip-3.10.9/data/images/16x16/remove_user.png
hplip-3.10.9/data/images/16x16/minus.png
hplip-3.10.9/data/images/16x16/plus.png
hplip-3.10.9/data/images/16x16/folder_remove.png
hplip-3.10.9/data/images/16x16/paper.png
hplip-3.10.9/data/images/16x16/mimetypes.png
hplip-3.10.9/data/images/16x16/up.png
hplip-3.10.9/data/images/16x16/refresh1.png
hplip-3.10.9/data/images/16x16/down_user.png
hplip-3.10.9/data/images/32x32/
hplip-3.10.9/data/images/32x32/fab.png
hplip-3.10.9/data/images/32x32/hp_logo.png
hplip-3.10.9/data/images/32x32/plugin.png
hplip-3.10.9/data/images/32x32/makecopies.png
hplip-3.10.9/data/images/32x32/ews.png
hplip-3.10.9/data/images/32x32/toner.png
hplip-3.10.9/data/images/32x32/fax_machine.png
hplip-3.10.9/data/images/32x32/pcard.png
hplip-3.10.9/data/images/32x32/clean.png
hplip-3.10.9/data/images/32x32/idle.png
hplip-3.10.9/data/images/32x32/firmware.png
hplip-3.10.9/data/images/32x32/linefeed_cal.png
hplip-3.10.9/data/images/32x32/print.png
hplip-3.10.9/data/images/32x32/info.png
hplip-3.10.9/data/images/32x32/wireless.png
hplip-3.10.9/data/images/32x32/error.png
hplip-3.10.9/data/images/32x32/lock.png
hplip-3.10.9/data/images/32x32/download.png
hplip-3.10.9/data/images/32x32/help.png
hplip-3.10.9/data/images/32x32/makecopies-disabled.png
hplip-3.10.9/data/images/32x32/scan-disabled.png
hplip-3.10.9/data/images/32x32/warning.png
hplip-3.10.9/data/images/32x32/toner_cartridge.png
hplip-3.10.9/data/images/32x32/busy.png
hplip-3.10.9/data/images/32x32/colorcal.png
hplip-3.10.9/data/images/32x32/pq_diag.png
hplip-3.10.9/data/images/32x32/inkdrop.png
hplip-3.10.9/data/images/32x32/pcard-disabled.png
hplip-3.10.9/data/images/32x32/scan.png
hplip-3.10.9/data/images/32x32/cups.png
hplip-3.10.9/data/images/32x32/align.png
hplip-3.10.9/data/images/32x32/testpage.png
hplip-3.10.9/data/images/32x32/settings.png
hplip-3.10.9/data/images/32x32/keys.png
hplip-3.10.9/data/images/32x32/print-disabled.png
hplip-3.10.9/data/images/32x32/fax.png
hplip-3.10.9/data/images/32x32/ok.png
hplip-3.10.9/data/images/32x32/battery.png
hplip-3.10.9/data/images/32x32/lporg.png
hplip-3.10.9/data/images/32x32/fax-disabled.png
hplip-3.10.9/data/images/32x32/fax_setup.png
hplip-3.10.9/data/images/32x32/paper.png
hplip-3.10.9/data/images/256x256/
hplip-3.10.9/data/images/256x256/hp_logo.png
hplip-3.10.9/data/images/256x256/logo.png
hplip-3.10.9/data/images/128x128/
hplip-3.10.9/data/images/128x128/gif.png
hplip-3.10.9/data/images/128x128/hp_logo.png
hplip-3.10.9/data/images/128x128/jpg.png
hplip-3.10.9/data/images/128x128/png.png
hplip-3.10.9/data/images/128x128/tif.png
hplip-3.10.9/data/images/128x128/mpg.png
hplip-3.10.9/data/images/128x128/audio.png
hplip-3.10.9/data/images/128x128/unknown.png
hplip-3.10.9/data/images/128x128/movie.png
hplip-3.10.9/data/images/128x128/bmp.png
hplip-3.10.9/data/rules/
hplip-3.10.9/data/rules/56-hpmud_support.rules
hplip-3.10.9/data/rules/40-hplip.rules
hplip-3.10.9/data/rules/20-hplip-devices.fdi
hplip-3.10.9/data/rules/55-hpmud.rules
hplip-3.10.9/data/models/
hplip-3.10.9/data/models/models.dat
hplip-3.10.9/data/ldl/
hplip-3.10.9/data/ldl/cbccal.ldl.gz
hplip-3.10.9/data/ldl/cb2pcal_done.ldl.gz
hplip-3.10.9/data/ldl/cbcpcal.ldl.gz
hplip-3.10.9/data/ldl/cb2pcal.ldl.gz
hplip-3.10.9/data/ldl/cbbcal.ldl.gz
hplip-3.10.9/data/ldl/cbpcal.ldl.gz
hplip-3.10.9/data/ldl/cbccal_done.ldl.gz
hplip-3.10.9/data/policykit/
hplip-3.10.9/data/policykit/com.hp.hplip.service
hplip-3.10.9/data/policykit/com.hp.hplip.policy
hplip-3.10.9/data/policykit/com.hp.hplip.service.in
hplip-3.10.9/data/policykit/com.hp.hplip.conf
hplip-3.10.9/print.py
hplip-3.10.9/dat2drv.py
hplip-3.10.9/linefeedcal.py
hplip-3.10.9/installer/
hplip-3.10.9/installer/distros.dat
hplip-3.10.9/installer/core_install.py
hplip-3.10.9/installer/__init__.py
hplip-3.10.9/installer/text_install.py
hplip-3.10.9/installer/dcheck.py
hplip-3.10.9/Makefile.am
hplip-3.10.9/hpdio.py
hplip-3.10.9/plugin.py
hplip-3.10.9/configure
hplip-3.10.9/probe.py
hplip-3.10.9/devicesettings.py
hplip-3.10.9/__init__.py
hplip-3.10.9/pqdiag.py
hplip-3.10.9/ltmain.sh
hplip-3.10.9/base/
hplip-3.10.9/base/status.py
hplip-3.10.9/base/pexpect.py
hplip-3.10.9/base/pml.py
hplip-3.10.9/base/logger.py
hplip-3.10.9/base/pkit.py
hplip-3.10.9/base/g.py
hplip-3.10.9/base/utils.py
hplip-3.10.9/base/mdns.py
hplip-3.10.9/base/magic.py
hplip-3.10.9/base/slp.py
hplip-3.10.9/base/strings.py
hplip-3.10.9/base/exif.py
hplip-3.10.9/base/codes.py
hplip-3.10.9/base/models.py
hplip-3.10.9/base/tui.py
hplip-3.10.9/base/dime.py
hplip-3.10.9/base/ldif.py
hplip-3.10.9/base/__init__.py
hplip-3.10.9/base/wifi.py
hplip-3.10.9/base/mfpdtf.py
hplip-3.10.9/base/maint.py
hplip-3.10.9/base/module.py
hplip-3.10.9/base/imagesize.py
hplip-3.10.9/base/vcard.py
hplip-3.10.9/base/device.py
hplip-3.10.9/hplip-install
hplip-3.10.9/hplip.state
hplip-3.10.9/install.py
hplip-3.10.9/foomatic_drv.inc
hplip-3.10.9/fax/
hplip-3.10.9/fax/filters/
hplip-3.10.9/fax/filters/pstotiff
hplip-3.10.9/fax/filters/pstotiff.convs
hplip-3.10.9/fax/filters/pstotiff.types
hplip-3.10.9/fax/ppd/
hplip-3.10.9/fax/ppd/HP-Fax-hpcups.ppd.gz
hplip-3.10.9/fax/ppd/HP-Fax2-hpcups.ppd.gz
hplip-3.10.9/fax/ppd/HP-Fax3-hpcups.ppd.gz
hplip-3.10.9/fax/ppd/HP-Fax2-hpijs.ppd.gz
hplip-3.10.9/fax/ppd/HP-Fax3-hpijs.ppd.gz
hplip-3.10.9/fax/ppd/HP-Fax-hpijs.ppd.gz
hplip-3.10.9/fax/marvellfax.py
hplip-3.10.9/fax/faxdevice.py
hplip-3.10.9/fax/coverpages.py
hplip-3.10.9/fax/fax.py
hplip-3.10.9/fax/pmlfax.py
hplip-3.10.9/fax/__init__.py
hplip-3.10.9/fax/backend/
hplip-3.10.9/fax/backend/hpfax.py
hplip-3.10.9/fax/soapfax.py
hplip-3.10.9/setup.py
hplip-3.10.9/Makefile.in
hplip-3.10.9/doc/
hplip-3.10.9/doc/commandline.html
hplip-3.10.9/doc/systray.html
hplip-3.10.9/doc/plugins.html
hplip-3.10.9/doc/sendfax.html
hplip-3.10.9/doc/setup.html
hplip-3.10.9/doc/mainttask.html
hplip-3.10.9/doc/devicemanager.html
hplip-3.10.9/doc/scanning.html
hplip-3.10.9/doc/faxtrouble.html
hplip-3.10.9/doc/printing.html
hplip-3.10.9/doc/copying.html
hplip-3.10.9/doc/gettinghelp.html
hplip-3.10.9/doc/uninstalling.html
hplip-3.10.9/doc/upgrading.html
hplip-3.10.9/doc/print.html
hplip-3.10.9/doc/troubleshooting.html
hplip-3.10.9/doc/scantrouble.html
hplip-3.10.9/doc/printtroubleshooting.html
hplip-3.10.9/doc/hpscan.html
hplip-3.10.9/doc/images/
hplip-3.10.9/doc/images/toolbox_actions.png
hplip-3.10.9/doc/images/xsane.png
hplip-3.10.9/doc/images/toolbox_print_control.png
hplip-3.10.9/doc/images/favicon.ico
hplip-3.10.9/doc/images/print.png
hplip-3.10.9/doc/images/toolbox_status.png
hplip-3.10.9/doc/images/toolbox_fax.png
hplip-3.10.9/doc/images/toolbox_print_settings.png
hplip-3.10.9/doc/images/toolbox_supplies.png
hplip-3.10.9/doc/styles/
hplip-3.10.9/doc/styles/css.css
hplip-3.10.9/doc/index.html
hplip-3.10.9/doc/printoptions.html
hplip-3.10.9/init-suse-firewall
hplip-3.10.9/hpssd.py
hplip-3.10.9/align.py
hplip-3.10.9/hplip.conf.in
hplip-3.10.9/ui4/
hplip-3.10.9/ui4/aligndialog_base.py
hplip-3.10.9/ui4/loadpapergroupbox.py
hplip-3.10.9/ui4/makecopiesdialog_base.py
hplip-3.10.9/ui4/linefeedcaldialog.py
hplip-3.10.9/ui4/printtestpagedialog.py
hplip-3.10.9/ui4/deviceuricombobox.py
hplip-3.10.9/ui4/colorcaldialog.py
hplip-3.10.9/ui4/nodevicesdialog_base.py
hplip-3.10.9/ui4/cleandialog_base.ui
hplip-3.10.9/ui4/pluginlicensedialog_base.ui
hplip-3.10.9/ui4/firmwaredialog_base.py
hplip-3.10.9/ui4/aboutdialog_base.ui
hplip-3.10.9/ui4/printdialog_base.ui
hplip-3.10.9/ui4/plugindialog_base.py
hplip-3.10.9/ui4/fabgrouptable.py
hplip-3.10.9/ui4/infodialog_base.py
hplip-3.10.9/ui4/mimetypesdialog_base.ui
hplip-3.10.9/ui4/faxsetupdialog_base.py
hplip-3.10.9/ui4/aboutdialog.py
hplip-3.10.9/ui4/systrayframe.py
hplip-3.10.9/ui4/cleandialog_base.py
hplip-3.10.9/ui4/wifisetupdialog_base.py
hplip-3.10.9/ui4/colorcaldialog_base.py
hplip-3.10.9/ui4/pqdiagdialog_base.ui
hplip-3.10.9/ui4/sendfaxdialog_base.ui
hplip-3.10.9/ui4/infodialog_base.ui
hplip-3.10.9/ui4/ui_utils.py
hplip-3.10.9/ui4/firmwaredialog_base.ui
hplip-3.10.9/ui4/readonlyradiobutton.py
hplip-3.10.9/ui4/printernamecombobox.py
hplip-3.10.9/ui4/setupdialog_base.ui
hplip-3.10.9/ui4/makecopiesdialog_base.ui
hplip-3.10.9/ui4/devicesetupdialog.py
hplip-3.10.9/ui4/devmgr5_base.ui
hplip-3.10.9/ui4/nodevicesdialog_base.ui
hplip-3.10.9/ui4/fabwindow_base.py
hplip-3.10.9/ui4/settingsdialog_base.py
hplip-3.10.9/ui4/linefeedcaldialog_base.py
hplip-3.10.9/ui4/pluginlicensedialog_base.py
hplip-3.10.9/ui4/setupdialog.py
hplip-3.10.9/ui4/fabwindow.py
hplip-3.10.9/ui4/sendfaxdialog_base.py
hplip-3.10.9/ui4/linefeedcaldialog_base.ui
hplip-3.10.9/ui4/setupdialog_base.py
hplip-3.10.9/ui4/devmgr5_base.py
hplip-3.10.9/ui4/aligndialog_base.ui
hplip-3.10.9/ui4/infodialog.py
hplip-3.10.9/ui4/printsettingsdialog_base.py
hplip-3.10.9/ui4/makecopiesdialog.py
hplip-3.10.9/ui4/wifisetupdialog_base.ui
hplip-3.10.9/ui4/faxsetupdialog.py
hplip-3.10.9/ui4/settingsdialog_base.ui
hplip-3.10.9/ui4/__init__.py
hplip-3.10.9/ui4/mimetypesdialog_base.py
hplip-3.10.9/ui4/aboutdialog_base.py
hplip-3.10.9/ui4/nodevicesdialog.py
hplip-3.10.9/ui4/printtestpagedialog_base.py
hplip-3.10.9/ui4/colorcaldialog_base.ui
hplip-3.10.9/ui4/mimetypesdialog.py
hplip-3.10.9/ui4/pluginlicensedialog.py
hplip-3.10.9/ui4/printsettingsdialog.py
hplip-3.10.9/ui4/wifisetupdialog.py
hplip-3.10.9/ui4/filetable.py
hplip-3.10.9/ui4/aligndialog.py
hplip-3.10.9/ui4/pqdiagdialog.py
hplip-3.10.9/ui4/devmgr5.py
hplip-3.10.9/ui4/firmwaredialog.py
hplip-3.10.9/ui4/cleandialog.py
hplip-3.10.9/ui4/plugindialog_base.ui
hplip-3.10.9/ui4/printsettingstoolbox.py
hplip-3.10.9/ui4/printdialog.py
hplip-3.10.9/ui4/fabnametable.py
hplip-3.10.9/ui4/printdialog_base.py
hplip-3.10.9/ui4/printsettingsdialog_base.ui
hplip-3.10.9/ui4/pqdiagdialog_base.py
hplip-3.10.9/ui4/systemtray.py
hplip-3.10.9/ui4/plugindialog.py
hplip-3.10.9/ui4/sendfaxdialog.py
hplip-3.10.9/ui4/settingsdialog.py
hplip-3.10.9/ui4/systrayframe_base.ui
hplip-3.10.9/ui4/devicesetupdialog_base.ui
hplip-3.10.9/ui4/faxsetupdialog_base.ui
hplip-3.10.9/ui4/devicesetupdialog_base.py
hplip-3.10.9/ui4/fabwindow_base.ui
hplip-3.10.9/ui4/printtestpagedialog_base.ui
hplip-3.10.9/ui4/systrayframe_base.py
hplip-3.10.9/clean.py
hplip-3.10.9/install-sh
hplip-3.10.9/firmware.py
hplip-3.10.9/config.sub
hplip-3.10.9/printsettings.py
hplip-3.10.9/toolbox.py
hplip-3.10.9/systray.py
hplip-3.10.9/pkservice.py
hplip-3.10.9/ui/
hplip-3.10.9/ui/loadpaperform_base.py
hplip-3.10.9/ui/setupsettings_base.ui
hplip-3.10.9/ui/coloradjform_base.py
hplip-3.10.9/ui/aligntype6form2_base.ui
hplip-3.10.9/ui/faxaddrbookgroupsform_base.ui
hplip-3.10.9/ui/pluginlicenseform_base.ui
hplip-3.10.9/ui/setupsettings_base.py
hplip-3.10.9/ui/align10form_base.py
hplip-3.10.9/ui/aboutdlg_base.ui
hplip-3.10.9/ui/coverpageform.py
hplip-3.10.9/ui/setupform_base.py
hplip-3.10.9/ui/coloradjform.py
hplip-3.10.9/ui/faxaddrbookform.py
hplip-3.10.9/ui/loadpaperform_base.ui
hplip-3.10.9/ui/allowabletypesdlg_base.ui
hplip-3.10.9/ui/waitform_base.py
hplip-3.10.9/ui/cleaningform_base.ui
hplip-3.10.9/ui/align10form.py
hplip-3.10.9/ui/allowabletypesdlg.py
hplip-3.10.9/ui/aligntype6form1_base.ui
hplip-3.10.9/ui/faxaddrbookform_base.py
hplip-3.10.9/ui/waitform.py
hplip-3.10.9/ui/imagepropertiesdlg.py
hplip-3.10.9/ui/paperedgealignform_base.ui
hplip-3.10.9/ui/devmgr4.py
hplip-3.10.9/ui/aligntype6form2.py
hplip-3.10.9/ui/makecopiesform.py
hplip-3.10.9/ui/pluginlicenseform.py
hplip-3.10.9/ui/paperedgealignform_base.py
hplip-3.10.9/ui/faxsettingsform_base.py
hplip-3.10.9/ui/setupform_base.ui
hplip-3.10.9/ui/faxaddrbookeditform_base.py
hplip-3.10.9/ui/colorcal4form_base.ui
hplip-3.10.9/ui/ui_utils.py
hplip-3.10.9/ui/faxaddrbookgroupsform_base.py
hplip-3.10.9/ui/colorcalform_base.py
hplip-3.10.9/ui/unloadform.py
hplip-3.10.9/ui/scrollprintsettings.py
hplip-3.10.9/ui/cleaningform2_base.ui
hplip-3.10.9/ui/cleaningform.py
hplip-3.10.9/ui/colorcalform2_base.ui
hplip-3.10.9/ui/faxsendjobform.py
hplip-3.10.9/ui/settingsdialog_base.py
hplip-3.10.9/ui/coverpageform_base.ui
hplip-3.10.9/ui/pluginlicenseform_base.py
hplip-3.10.9/ui/allowabletypesdlg_base.py
hplip-3.10.9/ui/waitform_base.ui
hplip-3.10.9/ui/aligntype6form1_base.py
hplip-3.10.9/ui/pluginform2_base.py
hplip-3.10.9/ui/devmgr4_base.py
hplip-3.10.9/ui/loadpaperform.py
hplip-3.10.9/ui/jobstoragemixin.py
hplip-3.10.9/ui/cleaningform2.py
hplip-3.10.9/ui/setupform.py
hplip-3.10.9/ui/faxsettingsform_base.ui
hplip-3.10.9/ui/aligntype6form2_base.py
hplip-3.10.9/ui/setupmanualfind.py
hplip-3.10.9/ui/align13form.py
hplip-3.10.9/ui/colorcalform_base.ui
hplip-3.10.9/ui/align13form_base.py
hplip-3.10.9/ui/chooseprinterdlg.py
hplip-3.10.9/ui/scrollunload.py
hplip-3.10.9/ui/settingsdialog_base.ui
hplip-3.10.9/ui/__init__.py
hplip-3.10.9/ui/setupsettings.py
hplip-3.10.9/ui/coloradjform_base.ui
hplip-3.10.9/ui/faxaddrbookgroupeditform_base.py
hplip-3.10.9/ui/nodevicesform_base.py
hplip-3.10.9/ui/cleaningform2_base.py
hplip-3.10.9/ui/colorcal4form_base.py
hplip-3.10.9/ui/align10form_base.ui
hplip-3.10.9/ui/scrollprint.py
hplip-3.10.9/ui/pluginform2.py
hplip-3.10.9/ui/colorcal4form.py
hplip-3.10.9/ui/colorcalform.py
hplip-3.10.9/ui/setupmanualfind_base.py
hplip-3.10.9/ui/pluginform2_base.ui
hplip-3.10.9/ui/nodevicesform.py
hplip-3.10.9/ui/imagepropertiesdlg_base.ui
hplip-3.10.9/ui/cleaningform_base.py
hplip-3.10.9/ui/printerform.py
hplip-3.10.9/ui/colorcalform2_base.py
hplip-3.10.9/ui/aboutdlg.py
hplip-3.10.9/ui/nodevicesform_base.ui
hplip-3.10.9/ui/aligntype6form1.py
hplip-3.10.9/ui/alignform.py
hplip-3.10.9/ui/devmgr4_base.ui
hplip-3.10.9/ui/paperedgealignform.py
hplip-3.10.9/ui/scrollview.py
hplip-3.10.9/ui/choosedevicedlg.py
hplip-3.10.9/ui/align13form_base.ui
hplip-3.10.9/ui/faxsettingsform.py
hplip-3.10.9/ui/scrollcopy.py
hplip-3.10.9/ui/colorcalform2.py
hplip-3.10.9/ui/imagepropertiesdlg_base.py
hplip-3.10.9/ui/scrollfax.py
hplip-3.10.9/ui/systemtray.py
hplip-3.10.9/ui/settingsdialog.py
hplip-3.10.9/ui/coverpageform_base.py
hplip-3.10.9/ui/faxaddrbookgroupeditform_base.ui
hplip-3.10.9/ui/setupmanualfind_base.ui
hplip-3.10.9/ui/faxaddrbookform_base.ui
hplip-3.10.9/ui/aboutdlg_base.py
hplip-3.10.9/ui/faxaddrbookeditform_base.ui
hplip-3.10.9/io/
hplip-3.10.9/io/hpmud/
hplip-3.10.9/io/hpmud/jd.h
hplip-3.10.9/io/hpmud/mlc.h
hplip-3.10.9/io/hpmud/pml.h
hplip-3.10.9/io/hpmud/jd.c
hplip-3.10.9/io/hpmud/pp.h
hplip-3.10.9/io/hpmud/hpmud.h
hplip-3.10.9/io/hpmud/musb.h
hplip-3.10.9/io/hpmud/pml.c
hplip-3.10.9/io/hpmud/musb.c
hplip-3.10.9/io/hpmud/hpmud.c
hplip-3.10.9/io/hpmud/hpmudi.h
hplip-3.10.9/io/hpmud/list.h
hplip-3.10.9/io/hpmud/model.c
hplip-3.10.9/io/hpmud/dot4.c
hplip-3.10.9/io/hpmud/hp-mkuri.c
hplip-3.10.9/io/hpmud/pp.c
hplip-3.10.9/io/hpmud/dot4.h
hplip-3.10.9/io/hpmud/mlc.c
hplip-3.10.9/io/mudext/
hplip-3.10.9/io/mudext/hpmudext.c
hplip-3.10.9/COPYING
hplip-3.10.9/copier/
hplip-3.10.9/copier/copier.py
hplip-3.10.9/copier/__init__.py
hplip-3.10.9/scan/
hplip-3.10.9/scan/scanext/
hplip-3.10.9/scan/scanext/scanext.c
hplip-3.10.9/scan/sane.py
hplip-3.10.9/scan/__init__.py
hplip-3.10.9/scan/sane/
hplip-3.10.9/scan/sane/saneopts.h
hplip-3.10.9/scan/sane/soapi.h
hplip-3.10.9/scan/sane/soap.h
hplip-3.10.9/scan/sane/marvell.c
hplip-3.10.9/scan/sane/io.h
hplip-3.10.9/scan/sane/sanei.h
hplip-3.10.9/scan/sane/pml.h
hplip-3.10.9/scan/sane/marvelli.h
hplip-3.10.9/scan/sane/io.c
hplip-3.10.9/scan/sane/ledm.h
hplip-3.10.9/scan/sane/ledmi.h
hplip-3.10.9/scan/sane/http.c
hplip-3.10.9/scan/sane/bb_ledm.c
hplip-3.10.9/scan/sane/soapht.c
hplip-3.10.9/scan/sane/common.h
hplip-3.10.9/scan/sane/soapht.h
hplip-3.10.9/scan/sane/tables.h
hplip-3.10.9/scan/sane/scl.h
hplip-3.10.9/scan/sane/pml.c
hplip-3.10.9/scan/sane/mfpdtf.c
hplip-3.10.9/scan/sane/marvell.h
hplip-3.10.9/scan/sane/soap.c
hplip-3.10.9/scan/sane/sanei_debug.h
hplip-3.10.9/scan/sane/hpaio.c
hplip-3.10.9/scan/sane/http.h
hplip-3.10.9/scan/sane/sane.h
hplip-3.10.9/scan/sane/hpaio.desc
hplip-3.10.9/scan/sane/soaphti.h
hplip-3.10.9/scan/sane/xml.h
hplip-3.10.9/scan/sane/ledm.c
hplip-3.10.9/scan/sane/hpaio.h
hplip-3.10.9/scan/sane/scl.c
hplip-3.10.9/scan/sane/xml.c
hplip-3.10.9/scan/sane/mfpdtf.h
hplip-3.10.9/scan/sane/common.c
hplip-3.10.9/scan/sane/sanei_init_debug.c
hplip-3.10.9/aclocal.m4
hplip-3.10.9/info.py
richlyn@richlyn-lucid:~/Desktop$ cd hplip-3.10.9
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$ ./configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib64 --prefix=/usr --enable-udev-acl-rules --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: in `/home/richlyn/Desktop/hplip-3.10.9':
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$ make
make: *** No targets specified and no makefile found.  Stop.
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$ sudo make
[sudo] password for richlyn: 
make: *** No targets specified and no makefile found.  Stop.
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$ sudo make install
make: *** No rule to make target `install'.  Stop.
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$ 


**not sure why i cant get the make to work**

---

### Post by richlyn9 on 2010-11-29
> **richlyn9 said:**
> downloaded the latest version of hplip in .tar.gz format on to the desktop and tried installing

checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: in `/home/richlyn/Desktop/hplip-3.10.9':
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

**not sure why i cant get the make to work**

I think some deps are not installed....right??

Okay i will install them by doing this and try again.

sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

---

### Post by Brian1215 on 2010-11-29
Getting that all in one device to work is highly unlikely.
[http://www.hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_1050_j410_series.html](http://www.hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_1050_j410_series.html)
full details of all HP all in one devices here
[http://hplipopensource.com/hplip-web/supported_devices/deskjet_aio.html](http://hplipopensource.com/hplip-web/supported_devices/deskjet_aio.html)
The easy way to install hplip is to use Synaptic. 
Brian

---

### Post by richlyn9 on 2010-11-29
> **Brian1215 said:**
> 
The easy way to install hplip is to use Synaptic. 
Brian

how may i know to get it through synaptic as i need the latest version of hplip. I tried the hp gui available in synaptic but it didn't work

---

### Post by Brian1215 on 2010-11-29
As usual I didn't look closely enough. You could use the automatic installer [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)
 or otherwise continue to track down the missing dependencies. The last time I did that the update had been released in Synaptic before I resolved them all!
I will now return to my place under the stone.
Brian

---

### Post by richlyn9 on 2010-11-30
did this now 

data/images/64x64"
 /usr/bin/install -c -m 644 data/images/64x64/hp_logo.png '/usr/share/hplip/data/images/64x64'
test -z "/usr/share/hplip/data/images/devices" || /bin/mkdir -p "/usr/share/hplip/data/images/devices"
 /usr/bin/install -c -m 644 data/images/devices/120.png data/images/devices/COLOR_INKJET_PRINTER_CP1700.png data/images/devices/cp1160.png data/images/devices/CP_1700.png data/images/devices/default_business_inkjet.png data/images/devices/default_designjet.png data/images/devices/default_deskjet.png data/images/devices/default_laserjet.png data/images/devices/default_officejet.png data/images/devices/default_photosmart.png data/images/devices/default_printer.png data/images/devices/default_psc.png data/images/devices/desket_5650.png data/images/devices/DESKJET_1120C.png data/images/devices/DESKJET_1220C.png data/images/devices/deskjet_1280.png data/images/devices/DESKJET_2500C.png data/images/devices/deskjet_3200.png data/images/devices/deskjet_3320.png data/images/devices/deskjet_3325.png data/images/devices/deskjet_3420.png data/images/devices/deskjet_3425.png data/images/devices/deskjet_3500.png data/images/devices/deskjet_3600.png data/images/devices/Deskjet_3740.png data/images/devices/DESKJET_3820.png data/images/devices/deskjet_3840.png data/images/devices/deskjet_5100.png data/images/devices/Deskjet_5400_series.png data/images/devices/deskjet_5550.png data/images/devices/deskjet_5552.png data/images/devices/deskjet_5600.png data/images/devices/Deskjet_5700.png data/images/devices/DESKJET_5740.png data/images/devices/Deskjet_5900_series.png data/images/devices/DESKJET_610.png data/images/devices/deskjet_6120.png data/images/devices/DESKJET_630C.png data/images/devices/Deskjet_6500.png data/images/devices/DESKJET_650C.png '/usr/share/hplip/data/images/devices'
 /usr/bin/install -c -m 644 data/images/devices/Deskjet_6800.png data/images/devices/deskjet_6980.png data/images/devices/DESKJET_840C.png data/images/devices/DESKJET_916C.png data/images/devices/DESKJET_9600.png data/images/devices/DESKJET_960C.png data/images/devices/DESKJET_970C.png data/images/devices/DESKJET_990C.png data/images/devices/DESKJET_995C.png data/images/devices/deskjet_D2360.png data/images/devices/dj350.png data/images/devices/dj450.png data/images/devices/HP_2000C.png data/images/devices/HP_2500C.png data/images/devices/HP_BI_3000.png data/images/devices/hp_business_inkjet_1100.png data/images/devices/HP_Business_Inkjet_1200.png data/images/devices/hp_business_inkjet_2200.png data/images/devices/hp_business_inkjet_2600.png data/images/devices/hp_business_inkjet_3000.png data/images/devices/HP_Color_LaserJet_1500.png data/images/devices/hp_color_LaserJet_2550.png data/images/devices/HP_Color_LaserJet_2840.png data/images/devices/hp_color_LaserJet_3700.png data/images/devices/HP_Color_LaserJet_4500.png data/images/devices/hp_color_LaserJet_4600.png data/images/devices/HP_Color_LaserJet_4730mfp.png data/images/devices/HP_Color_LaserJet_8550.png data/images/devices/hp_color_LaserJet_9500.png data/images/devices/hp_color_laserjet_cm1015_mfp.png data/images/devices/hp_color_laserjet_cm1312_mfp.png data/images/devices/hp_color_laserjet_cp2025.png data/images/devices/hp_color_laserjet_cp3505.png data/images/devices/hp_color_laserjet_cp3525.png data/images/devices/hp_color_laserjet_cp4005.png data/images/devices/hp_color_laserjet_cp6015.png data/images/devices/hp_deskjet_9300.png data/images/devices/hp_deskjet_f4200.png data/images/devices/HP_LaserJet_1012.png data/images/devices/hp_LaserJet_1200.png '/usr/share/hplip/data/images/devices'
 /usr/bin/install -c -m 644 data/images/devices/HP_LaserJet_1220.png data/images/devices/hp_LaserJet_2100.png data/images/devices/hp_LaserJet_3015.png data/images/devices/hp_LaserJet_3020.png data/images/devices/hp_laserjet_3050.png data/images/devices/HP_LaserJet_3200M.png data/images/devices/HP_LaserJet_3300_3310_3320.png data/images/devices/HP_LaserJet_4000.png data/images/devices/HP_LaserJet_4100_MFP.png data/images/devices/hp_LaserJet_4345_mfp.png data/images/devices/HP_LaserJet_4M.png data/images/devices/hp_LaserJet_5000.png data/images/devices/HP_LaserJet_5Si.png data/images/devices/HP_LaserJet_6MP.png data/images/devices/hp_LaserJet_8000.png data/images/devices/HP_LaserJet_8100_Series.png data/images/devices/HP_LaserJet_9000_MFP.png data/images/devices/HP_LaserJet_9040_MFP.png data/images/devices/HP_LaserJet_9500dn.png data/images/devices/HP_LaserJet_m1005.png data/images/devices/HP_LaserJet_m1522.png data/images/devices/hp_laserjet_m2727_mfp.png data/images/devices/hp_laserjet_p2015.png data/images/devices/HP_LJ1xxx.png data/images/devices/HP_Officejet_Pro_L7700.png data/images/devices/hp_photosmart_b8500_series.png data/images/devices/laserjet_2410.png data/images/devices/LASERJET_3500.png data/images/devices/LASERJET_4650dtn.png data/images/devices/LASERJET_4650.png data/images/devices/LASERJET_5500dtn.png data/images/devices/LASERJET_5500.png data/images/devices/LASERJET_5550DTN.png data/images/devices/LASERJET_5550.png data/images/devices/officejet_4200_series.png data/images/devices/officejet_500.png data/images/devices/OfficeJet_5105.png data/images/devices/officejet_5500_series.png data/images/devices/officejet_5600.png data/images/devices/OfficeJet_6100_Series.png '/usr/share/hplip/data/images/devices'
 /usr/bin/install -c -m 644 data/images/devices/Officejet_6150_Series.png data/images/devices/Officejet_6200_series.png data/images/devices/Officejet_7200_series.png data/images/devices/Officejet_9100_series.png data/images/devices/OfficeJet_G85.png data/images/devices/officejet_j3600_series.png data/images/devices/officejet_j5500_series.png data/images/devices/officejet_k550.png data/images/devices/officejet_k80.png data/images/devices/OFFICEJET_PRO_1150C.png data/images/devices/OfficeJet_Series_300.png data/images/devices/PHOTOSMART_100.png data/images/devices/PHOTOSMART_1218.png data/images/devices/PHOTOSMART_1315.png data/images/devices/Photosmart_2600_series.png data/images/devices/Photosmart_2700_series.png data/images/devices/Photosmart_3300_series.png data/images/devices/Photosmart_370_series.png data/images/devices/photosmart_7150.png data/images/devices/Photosmart_7400_series.png data/images/devices/photosmart_7900_series.png data/images/devices/Photosmart_8050.png data/images/devices/Photosmart_8100_series.png data/images/devices/Photosmart_8250.png data/images/devices/Photosmart_8400_series.png data/images/devices/Photosmart_8750_series.png data/images/devices/Photosmart_a310.png data/images/devices/Photosmart_a510.png data/images/devices/photosmart_a610.png data/images/devices/Photosmart_a710.png data/images/devices/photosmart_a820_series.png data/images/devices/Photosmart_C3100.png data/images/devices/Photosmart_C4100.png data/images/devices/Photosmart_C5100.png data/images/devices/Photosmart_C6100.png data/images/devices/Photosmart_D5060.png data/images/devices/Photosmart_D5100.png data/images/devices/Photosmart_D6160.png data/images/devices/Photosmart_D7100.png data/images/devices/Photosmart_D7300.png '/usr/share/hplip/data/images/devices'
 /usr/bin/install -c -m 644 data/images/devices/PHOTOSMART_P1100.png data/images/devices/Photosmart_Pro_B8300.png data/images/devices/Photosmart_Pro_B9180.png data/images/devices/psc_1100_series.png data/images/devices/psc_1610.png data/images/devices/psc_2300_series.png data/images/devices/PSC_900_Series.png '/usr/share/hplip/data/images/devices'
test -z "/usr/share/hplip/data/images/other" || /bin/mkdir -p "/usr/share/hplip/data/images/other"
 /usr/bin/install -c -m 644 data/images/other/aio_align.png data/images/other/align10.png data/images/other/clean.png data/images/other/color_adj.png data/images/other/confidential_coverpage.png data/images/other/confidential_title.png data/images/other/fax2.png data/images/other/fax.png data/images/other/generic_coverpage.png data/images/other/generic_title.png data/images/other/h-kc-2.png data/images/other/h-kc-3.png data/images/other/hp-tux-printer.png data/images/other/load_paper.png data/images/other/opensource-75x65.png data/images/other/panel_lcd.png data/images/other/pens.png data/images/other/powered_by_python.png data/images/other/signal0.png data/images/other/signal1.png data/images/other/signal2.png data/images/other/signal3.png data/images/other/signal4.png data/images/other/signal5.png data/images/other/standard_coverpage.png data/images/other/type4_color_patch.png data/images/other/type4_gray_patch.png data/images/other/urgent_coverpage.png data/images/other/urgent_title.png data/images/other/usb_connection.png data/images/other/v-c-2.png data/images/other/v-c-3.png data/images/other/v-k-2.png data/images/other/v-k-3.png data/images/other/v-kc-2.png data/images/other/v-kc-3.png data/images/other/zca.png '/usr/share/hplip/data/images/other'
test -z "/usr/share/hplip/installer" || /bin/mkdir -p "/usr/share/hplip/installer"
 /usr/bin/install -c -m 644 installer/__init__.py installer/dcheck.py installer/distros.dat installer/core_install.py '/usr/share/hplip/installer'
test -z "/usr/share/hplip/data/ldl" || /bin/mkdir -p "/usr/share/hplip/data/ldl"
 /usr/bin/install -c -m 644 data/ldl/cb2pcal.ldl.gz data/ldl/cb2pcal_done.ldl.gz data/ldl/cbbcal.ldl.gz data/ldl/cbccal.ldl.gz data/ldl/cbccal_done.ldl.gz data/ldl/cbcpcal.ldl.gz data/ldl/cbpcal.ldl.gz '/usr/share/hplip/data/ldl'
test -z "/usr/share/hplip/data/localization" || /bin/mkdir -p "/usr/share/hplip/data/localization"
 /usr/bin/install -c -m 644 data/localization/hplip_de.qm data/localization/hplip_es.qm data/localization/hplip_fr.qm data/localization/hplip_it.qm data/localization/hplip_pt.qm data/localization/hplip_ru.qm data/localization/hplip_zh.qm '/usr/share/hplip/data/localization'
test -z "/usr/share/hplip/data/models" || /bin/mkdir -p "/usr/share/hplip/data/models"
 /usr/bin/install -c -m 644 data/models/models.dat '/usr/share/hplip/data/models'
test -z "/usr/share/hplip/pcard" || /bin/mkdir -p "/usr/share/hplip/pcard"
 /usr/bin/install -c -m 644 pcard/__init__.py pcard/photocard.py '/usr/share/hplip/pcard'
test -z "/usr/share/hplip/data/pcl" || /bin/mkdir -p "/usr/share/hplip/data/pcl"
 /usr/bin/install -c -m 644 data/pcl/align1_8xx.pcl.gz data/pcl/align1_9xx.pcl.gz data/pcl/align2_8xx.pcl.gz data/pcl/align3_8xx.pcl.gz data/pcl/align4_8xx.pcl.gz data/pcl/align5_8xx.pcl.gz data/pcl/align2_9xx.pcl.gz data/pcl/align3_9xx.pcl.gz data/pcl/align4_450.pcl.gz data/pcl/align6_450.pcl.gz data/pcl/colorcal1_450.pcl.gz data/pcl/colorcal2_450.pcl.gz data/pcl/crbcal.pcl.gz data/pcl/crcaldone.pcl.gz data/pcl/crcbcal.pcl.gz data/pcl/crccal.pcl.gz data/pcl/crcpcal.pcl.gz data/pcl/crpcal.pcl.gz '/usr/share/hplip/data/pcl'
test -z "/usr/share/hplip/ui4/plugins" || /bin/mkdir -p "/usr/share/hplip/ui4/plugins"
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "/usr/share/hplip/data/ps" || /bin/mkdir -p "/usr/share/hplip/data/ps"
 /usr/bin/install -c -m 644 data/ps/testpage.ps.gz data/ps/clean_page.pdf.gz '/usr/share/hplip/data/ps'
test -z "/usr/share/ppd/HP" || /bin/mkdir -p "/usr/share/ppd/HP"
 /usr/bin/install -c -m 644 prnt/ps/hp-laserjet_4250-ps.ppd.gz prnt/ps/hp-laserjet_p3005-ps.ppd.gz prnt/ps/hp-laserjet_p4515-ps.ppd.gz prnt/ps/hp-color_laserjet_3700n-ps.ppd.gz prnt/ps/hp-color_laserjet_4610-ps.ppd.gz prnt/ps/hp-designjet_4020ps-ps.ppd.gz prnt/ps/hp-color_laserjet_4550-ps.ppd.gz prnt/ps/hp-color_laserjet_cp5225-ps.ppd.gz prnt/ps/hp-laserjet_3015-ps.ppd.gz prnt/ps/hp-designjet_t1100ps_24in-ps.ppd.gz prnt/ps/hp-color_laserjet_cm2320n_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp3525-ps.ppd.gz prnt/ps/hp-laserjet_9055mfp-ps.ppd.gz prnt/ps/hp-business_inkjet_2250-ps.ppd.gz prnt/ps/hp-laserjet_m3035_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cm6040_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_2605dn-ps.ppd.gz prnt/ps/hp-laserjet_m3027_mfp-ps.ppd.gz prnt/ps/hp-laserjet_5000_series-ps.ppd.gz prnt/ps/hp-laserjet_p4515xm-ps.ppd.gz prnt/ps/hp-laserjet_8000-ps.ppd.gz prnt/ps/hp-color_laserjet_cm6030_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp2025n-ps.ppd.gz prnt/ps/hp-color_laserjet_2605-ps.ppd.gz prnt/ps/hp-color_laserjet_4650-ps.ppd.gz prnt/ps/hp-color_laserjet_cp5225n-ps.ppd.gz prnt/ps/hp-laserjet_1320_series-ps.ppd.gz prnt/ps/hp-laserjet_4300-ps.ppd.gz prnt/ps/hp-laserjet_9065mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp4020_series-ps.ppd.gz prnt/ps/hp-color_laserjet_4700-ps.ppd.gz prnt/ps/hp-laserjet_5200lx-ps.ppd.gz prnt/ps/hp-color_laserjet_2800-ps.ppd.gz prnt/ps/hp-laserjet_2200-ps.ppd.gz prnt/ps/hp-color_laserjet_cp2025x-ps.ppd.gz prnt/ps/hp-designjet_t770_postscript-ps.ppd.gz prnt/ps/hp-laserjet_2430-ps.ppd.gz prnt/ps/hp-laserjet_9040-ps.ppd.gz prnt/ps/hp-laserjet_p4015tn-ps.ppd.gz prnt/ps/hp-laserjet_1300-ps.ppd.gz '/usr/share/ppd/HP'
 /usr/bin/install -c -m 644 prnt/ps/hp-laserjet_5200-ps.ppd.gz prnt/ps/hp-color_laserjet_cm2320nf_mfp-ps.ppd.gz prnt/ps/hp-laserjet_m1522n_mfp-ps.ppd.gz prnt/ps/hp-designjet_4520ps-ps.ppd.gz prnt/ps/hp-color_laserjet_cp1514n-ps.ppd.gz prnt/ps/hp-color_laserjet_2500-ps.ppd.gz prnt/ps/hp-designjet_t1120ps_24in-ps.ppd.gz prnt/ps/hp-color_laserjet_cm2320fxi_mfp-ps.ppd.gz prnt/ps/hp-laserjet_m9050_mfp-ps.ppd.gz prnt/ps/hp-laserjet_4200-ps.ppd.gz prnt/ps/hp-laserjet_9040_mfp-ps.ppd.gz prnt/ps/hp-designjet_t1100ps_44in-ps.ppd.gz prnt/ps/hp-laserjet_4100_mfp-ps.ppd.gz prnt/ps/hp-laserjet_4_plus-ps.ppd.gz prnt/ps/hp-color_laserjet_cp4005-ps.ppd.gz prnt/ps/hp-laserjet_9000_series-ps.ppd.gz prnt/ps/hp-mopier_320-ps.ppd.gz prnt/ps/hp-business_inkjet_2280-ps.ppd.gz prnt/ps/hp-laserjet_4-ps.ppd.gz prnt/ps/hp-laserjet_p2015n_series-ps.ppd.gz prnt/ps/hp-laserjet_4240-ps.ppd.gz prnt/ps/hp-laserjet_3300_3310_3320-ps.ppd.gz prnt/ps/hp-business_inkjet_3000-ps.ppd.gz prnt/ps/hp-laserjet_1220se-ps.ppd.gz prnt/ps/hp-designjet_4500ps.ppd.gz prnt/ps/hp-laserjet_p4015-ps.ppd.gz prnt/ps/hp-laserjet_1200n-ps.ppd.gz prnt/ps/hp-laserjet_5100_series-ps.ppd.gz prnt/ps/hp-laserjet_p4515n-ps.ppd.gz prnt/ps/hp-color_laserjet_5m-ps.ppd.gz prnt/ps/hp-laserjet_4100_series-ps.ppd.gz prnt/ps/hp-cm8050_mfp_with_edgeline-ps.ppd.gz prnt/ps/hp-color_laserjet_3800-ps.ppd.gz prnt/ps/hp-laserjet_p4014dn-ps.ppd.gz prnt/ps/hp-laserjet_1320tn-ps.ppd.gz prnt/ps/hp-color_laserjet_cp1515n-ps.ppd.gz prnt/ps/hp-color_laserjet_2840-ps.ppd.gz prnt/ps/hp-laserjet_4345_mfp-ps.ppd.gz prnt/ps/hp-laserjet_4si-ps.ppd.gz prnt/ps/hp-color_laserjet_cp6015-ps.ppd.gz '/usr/share/ppd/HP'
 /usr/bin/install -c -m 644 prnt/ps/hp-laserjet_4mp-ps.ppd.gz prnt/ps/hp-laserjet_p2055x-ps.ppd.gz prnt/ps/hp-laserjet_2300_series-ps.ppd.gz prnt/ps/hp-color_laserjet_8500-ps.ppd.gz prnt/ps/hp-laserjet_p4014-ps.ppd.gz prnt/ps/hp-laserjet_8100_series-ps.ppd.gz prnt/ps/hp-laserjet_1320-ps.ppd.gz prnt/ps/hp-laserjet_p4515tn-ps.ppd.gz prnt/ps/hp-laserjet_m2727nfs_mfp-ps.ppd.gz prnt/ps/hp-designjet_4500mfp.ppd.gz prnt/ps/hp-laserjet_6mp-ps.ppd.gz prnt/ps/hp-cm8060_mfp_with_edgeline-ps.ppd.gz prnt/ps/hp-laserjet_5200l-ps.ppd.gz prnt/ps/hp-laserjet_3052-ps.ppd.gz prnt/ps/hp-laserjet_m1522nf_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cm1015-ps.ppd.gz prnt/ps/hp-color_laserjet_8550-ps.ppd.gz prnt/ps/hp-laserjet_1220-ps.ppd.gz prnt/ps/hp-color_laserjet_2700n-ps.ppd.gz prnt/ps/hp-laserjet_1300xi-ps.ppd.gz prnt/ps/hp-color_laserjet_2605dtn-ps.ppd.gz prnt/ps/hp-laserjet_m2727_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_3000-ps.ppd.gz prnt/ps/hp-color_laserjet_cm1312_mfp-ps.ppd.gz prnt/ps/hp-laserjet_2420-ps.ppd.gz prnt/ps/hp-laserjet_5mp-ps.ppd.gz prnt/ps/hp-color_laserjet_2550_series-ps.ppd.gz prnt/ps/hp-color_laserjet_9500-ps.ppd.gz prnt/ps/hp-laserjet_8150_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp5225dn-ps.ppd.gz prnt/ps/hp-laserjet_m5035_mfp-ps.ppd.gz prnt/ps/hp-laserjet_2200_series-ps.ppd.gz prnt/ps/hp-laserjet_m1522_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp3505-ps.ppd.gz prnt/ps/hp-business_inkjet_2800-ps.ppd.gz prnt/ps/hp-laserjet_4350-ps.ppd.gz prnt/ps/hp-laserjet_p2055dn-ps.ppd.gz prnt/ps/hp-color_laserjet-ps.ppd.gz prnt/ps/hp-laserjet_m5025_mfp-ps.ppd.gz prnt/ps/hp-laserjet_2100-ps.ppd.gz '/usr/share/ppd/HP'
 /usr/bin/install -c -m 644 prnt/ps/hp-laserjet_p3010_series-ps.ppd.gz prnt/ps/hp-color_laserjet_4500-ps.ppd.gz prnt/ps/hp-laserjet_3050-ps.ppd.gz prnt/ps/hp-laserjet_p2015x_series-ps.ppd.gz prnt/ps/hp-laserjet_3200m-ps.ppd.gz prnt/ps/hp-laserjet_p4015dn-ps.ppd.gz prnt/ps/hp-laserjet_p2015dn_series-ps.ppd.gz prnt/ps/hp-laserjet_1300n-ps.ppd.gz prnt/ps/hp-laserjet_3380-ps.ppd.gz prnt/ps/hp-color_laserjet_2830-ps.ppd.gz prnt/ps/hp-laserjet_9050-ps.ppd.gz prnt/ps/hp-laserjet_5si_mopier-ps.ppd.gz prnt/ps/hp-color_laserjet_4600_series-ps.ppd.gz prnt/ps/hp-designjet_t770ps_24in-ps.ppd.gz prnt/ps/hp-color_laserjet_cm4730_mfp-ps.ppd.gz prnt/ps/hp-laserjet_3030-ps.ppd.gz prnt/ps/hp-color_laserjet_9500_mfp-ps.ppd.gz prnt/ps/hp-laserjet_m4345_mfp-ps.ppd.gz prnt/ps/hp-laserjet_p3004-ps.ppd.gz prnt/ps/hp-color_laserjet_4730mfp-ps.ppd.gz prnt/ps/hp-laserjet_m4349_mfp-ps.ppd.gz prnt/ps/hp-laserjet_p2055-ps.ppd.gz prnt/ps/hp-laserjet_5p-ps.ppd.gz prnt/ps/hp-laserjet_m9059_mfp-ps.ppd.gz prnt/ps/hp-laserjet_m2727nf_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_3700-ps.ppd.gz prnt/ps/hp-color_laserjet_cp2025dn-ps.ppd.gz prnt/ps/hp-laserjet_5000-ps.ppd.gz prnt/ps/hp-laserjet_1320n-ps.ppd.gz prnt/ps/hp-color_laserjet_cm6049_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_2700-ps.ppd.gz prnt/ps/hp-laserjet_p4515x-ps.ppd.gz prnt/ps/hp-color_laserjet_cp4520_series-ps.ppd.gz prnt/ps/hp-laserjet_p2055d-ps.ppd.gz prnt/ps/hp-color_laserjet_5500-ps.ppd.gz prnt/ps/hp-laserjet_2300-ps.ppd.gz prnt/ps/hp-laserjet_3390-ps.ppd.gz prnt/ps/hp-business_inkjet_2600-ps.ppd.gz prnt/ps/hp-color_laserjet_cm1312nfi_mfp-ps.ppd.gz prnt/ps/hp-laserjet_3020-ps.ppd.gz '/usr/share/ppd/HP'
 /usr/bin/install -c -m 644 prnt/ps/hp-laserjet_1320nw-ps.ppd.gz prnt/ps/hp-laserjet_4050_series-ps.ppd.gz prnt/ps/hp-color_laserjet_5550-ps.ppd.gz prnt/ps/hp-laserjet_p2015_series-ps.ppd.gz prnt/ps/hp-laserjet_p4014n-ps.ppd.gz prnt/ps/hp-color_laserjet_cm1017-ps.ppd.gz prnt/ps/hp-color_laserjet_2820-ps.ppd.gz prnt/ps/hp-laserjet_4v-ps.ppd.gz prnt/ps/hp-laserjet_2100_series-ps.ppd.gz prnt/ps/hp-laserjet_9050_mfp-ps.ppd.gz prnt/ps/hp-business_inkjet_2300-ps.ppd.gz prnt/ps/hp-laserjet_5si-ps.ppd.gz prnt/ps/hp-designjet_4520mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_cp1518ni-ps.ppd.gz prnt/ps/hp-laserjet_2410-ps.ppd.gz prnt/ps/hp-designjet_t1120ps_44in-ps.ppd.gz prnt/ps/hp-mopier_240-ps.ppd.gz prnt/ps/hp-laserjet_6p-ps.ppd.gz prnt/ps/hp-laserjet_1200-ps.ppd.gz prnt/ps/hp-designjet_t1200_postscript-ps.ppd.gz prnt/ps/hp-laserjet_4ml-ps.ppd.gz prnt/ps/hp-laserjet_m9040_mfp-ps.ppd.gz prnt/ps/hp-color_laserjet_4600-ps.ppd.gz prnt/ps/hp-color_laserjet_cp2025-ps.ppd.gz prnt/ps/hp-color_laserjet_cm3530_mfp-ps.ppd.gz prnt/ps/hp-laserjet_p4015n-ps.ppd.gz prnt/ps/hp-laserjet_8100_mfp-ps.ppd.gz prnt/ps/hp-laserjet_p4015x-ps.ppd.gz prnt/ps/hp-laserjet_8000_series-ps.ppd.gz prnt/ps/hp-laserjet_4000_series-ps.ppd.gz prnt/ps/hp-color_laserjet_2500_series-ps.ppd.gz prnt/ps/hp-color_laserjet_cm2320_mfp-ps.ppd.gz prnt/ps/hp-laserjet_9000_mfp-ps.ppd.gz '/usr/share/ppd/HP'
test -z "/usr/share/hplip/prnt" || /bin/mkdir -p "/usr/share/hplip/prnt"
 /usr/bin/install -c -m 644 prnt/cups.py prnt/__init__.py prnt/ldl.py prnt/pcl.py prnt/colorcal.py '/usr/share/hplip/prnt'
test -z "" || /bin/mkdir -p ""
test -z "/etc/udev/rules.d" || /bin/mkdir -p "/etc/udev/rules.d"
 /usr/bin/install -c -m 644 data/rules/56-hpmud_support.rules data/rules/40-hplip.rules '/etc/udev/rules.d'
test -z "/usr/share/hplip/scan" || /bin/mkdir -p "/usr/share/hplip/scan"
 /usr/bin/install -c -m 644 scan/__init__.py scan/sane.py '/usr/share/hplip/scan'
test -z "/usr/share/hplip/ui4" || /bin/mkdir -p "/usr/share/hplip/ui4"
 /usr/bin/install -c -m 644 ui4/aboutdialog_base.py ui4/aboutdialog.py ui4/aligndialog_base.py ui4/aligndialog.py ui4/cleandialog_base.py ui4/cleandialog.py ui4/colorcaldialog_base.py ui4/colorcaldialog.py ui4/devicesetupdialog_base.py ui4/devicesetupdialog.py ui4/deviceuricombobox.py ui4/devmgr5_base.py ui4/devmgr5.py ui4/fabgrouptable.py ui4/fabnametable.py ui4/fabwindow_base.py ui4/fabwindow.py ui4/faxsetupdialog_base.py ui4/faxsetupdialog.py ui4/filetable.py ui4/firmwaredialog_base.py ui4/firmwaredialog.py ui4/infodialog_base.py ui4/infodialog.py ui4/__init__.py ui4/linefeedcaldialog_base.py ui4/linefeedcaldialog.py ui4/loadpapergroupbox.py ui4/makecopiesdialog_base.py ui4/makecopiesdialog.py ui4/mimetypesdialog_base.py ui4/mimetypesdialog.py ui4/nodevicesdialog_base.py ui4/nodevicesdialog.py ui4/plugindialog_base.py ui4/plugindialog.py ui4/pluginlicensedialog_base.py ui4/pluginlicensedialog.py ui4/pqdiagdialog_base.py ui4/pqdiagdialog.py '/usr/share/hplip/ui4'
 /usr/bin/install -c -m 644 ui4/printdialog_base.py ui4/printdialog.py ui4/printernamecombobox.py ui4/printsettingsdialog_base.py ui4/printsettingsdialog.py ui4/printsettingstoolbox.py ui4/printtestpagedialog_base.py ui4/printtestpagedialog.py ui4/readonlyradiobutton.py ui4/sendfaxdialog_base.py ui4/sendfaxdialog.py ui4/settingsdialog_base.py ui4/settingsdialog.py ui4/setupdialog_base.py ui4/setupdialog.py ui4/systemtray.py ui4/systrayframe_base.py ui4/systrayframe.py ui4/ui_utils.py ui4/wifisetupdialog_base.py ui4/wifisetupdialog.py '/usr/share/hplip/ui4'
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "/usr/share/doc/hplip-3.10.9" || /bin/mkdir -p "/usr/share/doc/hplip-3.10.9"
 /usr/bin/install -c -m 644 doc/index.html doc/commandline.html doc/copying.html doc/devicemanager.html doc/faxtrouble.html doc/gettinghelp.html doc/hpscan.html doc/mainttask.html doc/plugins.html doc/print.html doc/printing.html doc/printoptions.html doc/printtroubleshooting.html doc/scanning.html doc/scantrouble.html doc/sendfax.html doc/setup.html doc/systray.html doc/troubleshooting.html doc/uninstalling.html doc/upgrading.html '/usr/share/doc/hplip-3.10.9'
test -z "/usr/share/doc/hplip-3.10.9/styles" || /bin/mkdir -p "/usr/share/doc/hplip-3.10.9/styles"
 /usr/bin/install -c -m 644 doc/styles/css.css '/usr/share/doc/hplip-3.10.9/styles'
test -z "/usr/share/doc/hplip-3.10.9/images" || /bin/mkdir -p "/usr/share/doc/hplip-3.10.9/images"
 /usr/bin/install -c -m 644 doc/images/favicon.ico doc/images/print.png doc/images/toolbox_actions.png doc/images/toolbox_fax.png doc/images/toolbox_print_control.png doc/images/toolbox_print_settings.png doc/images/toolbox_status.png doc/images/toolbox_supplies.png doc/images/xsane.png '/usr/share/doc/hplip-3.10.9/images'
test -z "/usr/share/doc/hplip-3.10.9" || /bin/mkdir -p "/usr/share/doc/hplip-3.10.9"
 /usr/bin/install -c -m 644 COPYING copyright prnt/hpijs/README_LIBJPG '/usr/share/doc/hplip-3.10.9'
test -z "/usr/lib/cups/backend" || /bin/mkdir -p "/usr/lib/cups/backend"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c hp '/usr/lib/cups/backend'
/usr/bin/install -c .libs/hp /usr/lib/cups/backend/hp
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c hp-mkuri '/usr/bin'
/usr/bin/install -c .libs/hp-mkuri /usr/bin/hp-mkuri
test -z "/usr/lib/cups/filter" || /bin/mkdir -p "/usr/lib/cups/filter"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c hpcups '/usr/lib/cups/filter'
/usr/bin/install -c hpcups /usr/lib/cups/filter/hpcups
test -z "/usr/lib/cups/filter" || /bin/mkdir -p "/usr/lib/cups/filter"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c hpcupsfax '/usr/lib/cups/filter'
/usr/bin/install -c .libs/hpcupsfax /usr/lib/cups/filter/hpcupsfax
test -z "/etc/hp" || /bin/mkdir -p "/etc/hp"
 /usr/bin/install -c -m 644 hplip.conf '/etc/hp'
test -z "/usr/share/applications" || /bin/mkdir -p "/usr/share/applications"
 /usr/bin/install -c -m 644 hplip.desktop '/usr/share/applications'
test -z "/etc/xdg/autostart" || /bin/mkdir -p "/etc/xdg/autostart"
 /usr/bin/install -c -m 644 hplip-systray.desktop '/etc/xdg/autostart'
test -z "/usr/lib/cups/filter" || /bin/mkdir -p "/usr/lib/cups/filter"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c hplipjs '/usr/lib/cups/filter'
/usr/bin/install -c hplipjs /usr/lib/cups/filter/hplipjs
test -z "/usr/lib/python2.6/dist-packages" || /bin/mkdir -p "/usr/lib/python2.6/dist-packages"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   hpmudext.la '/usr/lib/python2.6/dist-packages'
libtool: install: warning: relinking `hpmudext.la'
(cd /home/richlyn/Desktop/hplip-3.10.9; /bin/bash ./libtool  --tag=CC --mode=relink gcc -I/usr/include/python2.6 -g -O2 -module -avoid-version -o hpmudext.la -rpath /usr/lib/python2.6/dist-packages hpmudext_la-hpmudext.lo libhpmud.la -lcrypto )  
libtool: link: warning: `/usr/lib64/libusb.la' seems to be moved
libtool: link: warning: `/usr/lib64/libnetsnmp.la' seems to be moved
gcc -shared  .libs/hpmudext_la-hpmudext.o  -L/usr/lib64 -lhpmud -lcrypto  -Wl,-soname -Wl,hpmudext.so -o .libs/hpmudext.so
/usr/bin/install -c .libs/hpmudext.soT /usr/lib/python2.6/dist-packages/hpmudext.so
/usr/bin/install -c .libs/hpmudext.lai /usr/lib/python2.6/dist-packages/hpmudext.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/python2.6/dist-packages
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/python2.6/dist-packages

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/lib64/sane" || /bin/mkdir -p "/usr/lib64/sane"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libsane-hpaio.la '/usr/lib64/sane'
libtool: install: warning: relinking `libsane-hpaio.la'
(cd /home/richlyn/Desktop/hplip-3.10.9; /bin/bash ./libtool  --tag=CC --mode=relink gcc -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -version-info 1:0:0 -o libsane-hpaio.la -rpath /usr/lib64/sane libsane_hpaio_la-hpaio.lo libsane_hpaio_la-mfpdtf.lo libsane_hpaio_la-pml.lo libsane_hpaio_la-scl.lo libsane_hpaio_la-io.lo libsane_hpaio_la-common.lo libsane_hpaio_la-sanei_init_debug.lo libsane_hpaio_la-marvell.lo libsane_hpaio_la-soapht.lo libsane_hpaio_la-soap.lo libsane_hpaio_la-xml.lo libsane_hpaio_la-ledm.lo libsane_hpaio_la-bb_ledm.lo libsane_hpaio_la-http.lo libhpip.la libhpmud.la -L/lib -ldbus-1 -lpthread -lrt -lcups -ldl -lcrypto )  
libtool: link: warning: `/usr/lib64/libusb.la' seems to be moved
libtool: link: warning: `/usr/lib64/libnetsnmp.la' seems to be moved
gcc -shared  .libs/libsane_hpaio_la-hpaio.o .libs/libsane_hpaio_la-mfpdtf.o .libs/libsane_hpaio_la-pml.o .libs/libsane_hpaio_la-scl.o .libs/libsane_hpaio_la-io.o .libs/libsane_hpaio_la-common.o .libs/libsane_hpaio_la-sanei_init_debug.o .libs/libsane_hpaio_la-marvell.o .libs/libsane_hpaio_la-soapht.o .libs/libsane_hpaio_la-soap.o .libs/libsane_hpaio_la-xml.o .libs/libsane_hpaio_la-ledm.o .libs/libsane_hpaio_la-bb_ledm.o .libs/libsane_hpaio_la-http.o  -L/usr/lib64 -lhpip -lhpmud -L/lib -ldbus-1 -lpthread -lrt -lcups -ldl -lcrypto  -Wl,-soname -Wl,libsane-hpaio.so.1 -o .libs/libsane-hpaio.so.1.0.0
/usr/bin/install -c .libs/libsane-hpaio.so.1.0.0T /usr/lib64/sane/libsane-hpaio.so.1.0.0
(cd /usr/lib64/sane && { ln -s -f libsane-hpaio.so.1.0.0 libsane-hpaio.so.1 || { rm -f libsane-hpaio.so.1 && ln -s libsane-hpaio.so.1.0.0 libsane-hpaio.so.1; }; })
(cd /usr/lib64/sane && { ln -s -f libsane-hpaio.so.1.0.0 libsane-hpaio.so || { rm -f libsane-hpaio.so && ln -s libsane-hpaio.so.1.0.0 libsane-hpaio.so; }; })
/usr/bin/install -c .libs/libsane-hpaio.lai /usr/lib64/sane/libsane-hpaio.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib64/sane
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib64/sane

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/lib/python2.6/dist-packages" || /bin/mkdir -p "/usr/lib/python2.6/dist-packages"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   pcardext.la '/usr/lib/python2.6/dist-packages'
/usr/bin/install -c .libs/pcardext.so /usr/lib/python2.6/dist-packages/pcardext.so
/usr/bin/install -c .libs/pcardext.lai /usr/lib/python2.6/dist-packages/pcardext.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/python2.6/dist-packages
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/python2.6/dist-packages

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/lib/cups/filter" || /bin/mkdir -p "/usr/lib/cups/filter"
 /usr/bin/install -c fax/filters/pstotiff '/usr/lib/cups/filter'
test -z "/usr/lib/python2.6/dist-packages" || /bin/mkdir -p "/usr/lib/python2.6/dist-packages"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   scanext.la '/usr/lib/python2.6/dist-packages'
/usr/bin/install -c .libs/scanext.so /usr/lib/python2.6/dist-packages/scanext.so
/usr/bin/install -c .libs/scanext.lai /usr/lib/python2.6/dist-packages/scanext.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/python2.6/dist-packages
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/python2.6/dist-packages

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-data-hook
make[2]: Entering directory `/home/richlyn/Desktop/hplip-3.10.9'
if [ "yes" = "yes" ]; then \
	   /bin/bash /home/richlyn/Desktop/hplip-3.10.9/install-sh -d /etc/sane.d; \
	   if [ ! -f /etc/sane.d/dll.conf ]; then \
		  touch /etc/sane.d/dll.conf; \
	   fi; \
	   if ! grep ^hpaio /etc/sane.d/dll.conf >/dev/null 2>/dev/null ; then \
		  echo "Adding hpaio entry to /etc/sane.d/dll.conf." ; \
		  echo hpaio >>/etc/sane.d/dll.conf ; \
	   fi \
	fi
Adding hpaio entry to /etc/sane.d/dll.conf.
/bin/bash /home/richlyn/Desktop/hplip-3.10.9/install-sh -d /usr/bin
for i in align.py info.py print.py toolbox.py clean.py colorcal.py unload.py testpage.py makeuri.py check.py fab.py levels.py sendfax.py setup.py makecopies.py probe.py timedate.py firmware.py scan.py systray.py plugin.py linefeedcal.py pqdiag.py faxsetup.py devicesettings.py printsettings.py query.py pkservice.py wificonfig.py; do \
	   cmd=`basename $i .py`; \
	   if [ ! \( "$cmd" = "toolbox" -a "yes" = "no" \) ]; then \
		  ln -sf ../share/hplip/$i /usr/bin/hp-$cmd; \
	   fi \
	done
if [ "yes" = "yes" ]; then \
	   mv /usr/lib/cups/backend/hpfax.py /usr/lib/cups/backend/hpfax; \
	   chmod 700 /usr/lib/cups/backend/hpfax; \
	fi
make[2]: Leaving directory `/home/richlyn/Desktop/hplip-3.10.9'
make[1]: Leaving directory `/home/richlyn/Desktop/hplip-3.10.9'
richlyn@richlyn-lucid:~/Desktop/hplip-3.10.9$

---

### Post by richlyn9 on 2010-11-30
i rebooted and then ran this

richlyn@richlyn-lucid:~$ sudo hp-setup
[sudo] password for richlyn: 

HP Linux Imaging and Printing System (ver. 3.10.9)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/warning: No PPD found for model deskjet_1050_j410_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_1050_j410 using old algorithm.
error: No appropriate print PPD file found for model deskjet_1050_j410_series
error:  Printer queue setup failed.  Please add user to "lpadmin" group(s)
lpr: Connection refused
error: Print command failed with exit code 256!

Done.
richlyn@richlyn-lucid:~$ sudo usermod -a -G lp $ richlyn
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -Z, --selinux-user            new SELinux user mapping for the user account

richlyn@richlyn-lucid:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.10.9)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/warning: No PPD found for model deskjet_1050_j410_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_1050_j410 using old algorithm.
error: No appropriate print PPD file found for model deskjet_1050_j410_series
error:  Printer queue setup failed.  Please add user to "lpadmin" group(s)
lpr: Connection refused
error: Print command failed with exit code 256!

Done.
richlyn@richlyn-lucid:~$ 



**i cant see to find the cups for the deskjet 1050....**

---

### Post by Yellow Pasque on 2010-11-30
I hooked up a cheap deskjet 1600 to kubuntu 10.10 and it worked with no fuss. YMMV.

---

### Post by richlyn9 on 2010-11-30
I have installed the 3.10.9 hplip but it dosent have a pdd file for the deskjet  1050 .
any one having the same printer and working in ubuntu 10.04

---

### Post by richlyn9 on 2010-12-02
can some one tell me which other printers PDD are closest to deskjet 1050?

---

### Post by richlyn9 on 2010-12-03
I tried this again...

richlyn@richlyn-lucid:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.10.9)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux richlyn-lucid 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is not running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.10.9 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.9

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.10.9
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.9.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = 

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.9.11
date_time = Friday 03 December 2010 12:40:33

[settings]
systray_messages = 0
systray_visible = 0

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = true
type = 1

[polling]
enable = false
device_list = 
interval = 5



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                      
  --------------------------------  ---------------------------
  hp:/usb/Deskjet_1050_J410_series  HP Deskjet 1050 J410 series
  ?serial=CN09N2N1YT05HW                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
lpstat
------
Type: Unknown
Device URI: Connection refused


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Deskjet_1050_J410_series?serial=CN09N2N1YT05HW' is a Hewlett-Packard Deskjet_1050_J410_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x8911 at 001:004: 
    Device URI: hp:/usb/Deskjet_1050_J410_series?serial=CN09N2N1YT05HW

HP Linux Imaging and Printing System (ver. 3.10.9)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
    Device node: /dev/bus/usb/001/004
    Mode: 0664

---------------
| USER GROUPS |
---------------

richlyn adm dialout fax cdrom tape audio dip video plugdev lpadmin netdev admin sambashare vboxusers


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
richlyn@richlyn-lucid:~$ sudo hp-setup
[sudo] password for richlyn: 

HP Linux Imaging and Printing System (ver. 3.10.9)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/warning: No PPD found for model deskjet_1050_j410_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_1050_j410 using old algorithm.
error: No appropriate print PPD file found for model deskjet_1050_j410_series
error:  Printer queue setup failed.  Please add user to "lpadmin" group(s)
lpr: Connection refused
error: Print command failed with exit code 256!

Done.
richlyn@richlyn-lucid:~$ sudo usermod -a -G lp $richlyn
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -Z, --selinux-user            new SELinux user mapping for the user account

richlyn@richlyn-lucid:~$ sudo usermod -a -G lp richlyn
richlyn@richlyn-lucid:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.10.9)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/warning: No PPD found for model deskjet_1050_j410_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_1050_j410 using old algorithm.
error: No appropriate print PPD file found for model deskjet_1050_j410_series
error:  Printer queue setup failed.  Please add user to "lpadmin" group(s)
lpr: Connection refused
error: Print command failed with exit code 256!

Done.
richlyn@richlyn-lucid:~$ 



will logout and try again,,,

---

### Post by richlyn9 on 2010-12-03
Added my profile as ipadmin 
and ran set up and it detected the printer and configured with the ppd
richlyn@richlyn-lucid:~$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
richlyn@richlyn-lucid:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.10.9)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/
Done.
richlyn@richlyn-lucid:~$ 



however i am still unable to print

---

### Post by Orographic on 2010-12-05
I understand this HP 1050 printer works in 10.10 but without the scanner working until the bug is fixed. Is this correct? I have a F2280 which works great but my wife's printer has died and I can get the HP 1050 from a local store here in the Blue Mountains for a very good price.

---

### Post by richlyn9 on 2010-12-06
yes i have read the hplip official list of supported printers and the 1050 does seem to work well without the scan function

---

### Post by Orographic on 2010-12-06
Thanks for that, yes I have read the same list. I was also hoping to hear from anyone using the HP 1050 in Lucid?

---

### Post by richlyn9 on 2010-12-09
I finally installed The Ubuntu Maverick 10.10 and fixed my issue.Though i was unable to solve it.

---

### Post by fzn on 2012-06-03
> **richlyn9 said:**
> I finally installed The Ubuntu Maverick 10.10 and fixed my issue.Though i was unable to solve it.

i ve same problem with you , i ve looking out the way to solveit but no one success , but i found one solution at the end you just reinstall the cups
like: apt-get remove --purge cups
and: apt-get install cups
and hp-setup :D

---

