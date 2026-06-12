---
title: "DVICO DVB-T Plus with 5.10 and MythTV - v4l problems!"
date: 2006-04-28
forum: General Help
---

### Post by hmogan on 2006-04-28
Hi guys,

Im trying to get my FusionHDTV DVB-T Plus ([this one]("http://www.fusionhdtv.co.kr/eng/Products/DVBTPlus.aspx")) to work with Breezy.

Ive read and read postings and it seems that the v4l-dvb build from linuxtv.org is the way to go ([following this HOWTO]("http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS")) but its spitting out a whole bunch of errors and im pretty much bashing my head against a brick wall now.

Im running Breezy on an amd64 (3200+) and an ASUS N6600LE gfx card.

Here is some outputs to mull over:

first, lspci (relevant bit):

[COLOR="Blue"][FONT="Courier New"]0000:01:07.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:01:07.2 Multimedia controller: Conexant: Unknown device 8802 (rev 05)[/FONT][/COLOR]

next, the output of the make install step (including the insmod steps):

[COLOR="Blue"][FONT="Courier New"]Inserting V4L/DVB modules into kernel
FATAL: Module crc32 not found.
insmod: error inserting './compat_ioctl32.ko': -1 Unknown symbol in module
insmod: can't read './v4l1-compat.ko': No such file or directory
insmod: can't read './tda9840.ko': No such file or directory
insmod: can't read './tea6415c.ko': No such file or directory
insmod: can't read './tea6420.ko': No such file or directory
insmod: can't read './mxb.ko': No such file or directory
insmod: can't read './stv0297_cs2.ko': No such file or directory
insmod: can't read './bt832.ko': No such file or directory
insmod: error inserting './bttv.ko': -1 Unknown symbol in module
insmod: error inserting './bt878.ko': -1 Unknown symbol in module
insmod: error inserting './dst.ko': -1 Unknown symbol in module
insmod: error inserting './dst_ca.ko': -1 Unknown symbol in module
insmod: error inserting './dvb-bt8xx.ko': -1 Unknown symbol in module
insmod: error inserting './cx8800.ko': -1 Unknown symbol in module
insmod: error inserting './cx88-blackbird.ko': -1 Unknown symbol in module
insmod: error inserting './saa7134.ko': -1 Unknown symbol in module
insmod: error inserting './saa7134-alsa.ko': -1 Unknown symbol in module
insmod: error inserting './saa7134-dvb.ko': -1 Unknown symbol in module
insmod: error inserting './saa7134-empress.ko': -1 Unknown symbol in module
insmod: error inserting './em28xx.ko': -1 Unknown symbol in module
insmod: error inserting './cpia2.ko': -1 Unknown symbol in module[/FONT]

next: output from dmesg:

[FONT="Courier New"][24569.214667] usbcore: deregistering driver b2c2_flexcop_usb
[24569.241405] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip unloaded successfully
[24569.246179] saa7146: unregister extension 'dvb'.
[24569.253331] saa7146: unregister extension 'budget dvb'.
[24569.257919] saa7146: unregister extension 'budget_av'.
[24569.263249] saa7146: unregister extension 'budget_ci dvb'.
[24569.268055] usbcore: deregistering driver ttusb-dec
[24569.269621] usbcore: deregistering driver ttusb
[24569.271974] usbcore: deregistering driver dvb_usb_nova_t_usb2
[24569.273491] usbcore: deregistering driver dvb_usb_a800
[24569.274972] usbcore: deregistering driver dvb_usb_umt_010
[24569.276378] usbcore: deregistering driver dvb_usb_dibusb_mc
[24569.277799] usbcore: deregistering driver dvb_usb_dibusb_mb
[24569.279950] usbcore: deregistering driver dvb_usb_vp7045
[24569.280847] usbcore: deregistering driver dvb_usb_dtt200u
[24569.282269] usbcore: deregistering driver dvb_usb_digitv
[24569.283685] usbcore: deregistering driver dvb_usb_cxusb
[24569.428048] ACPI: PCI interrupt for device 0000:01:07.2 disabled
[24569.547130] saa7146: unregister extension 'hexium gemini'.
[24569.548617] saa7146: unregister extension 'hexium HV-PCI6 Orion'.
[24569.550515] pvrusb2: pvr_exit
[24569.550519] usbcore: deregistering driver pvrusb2
[24569.605813] usbcore: deregistering driver cinergyT2
[24569.966998] compat_ioctl32: Unknown symbol v4l_printk_ioctl
[24570.005763] Linux video capture interface: v1.00
[24570.641833] saa7146: register extension 'dvb'.
[24570.653647] saa7146: register extension 'budget dvb'.
[24570.661353] saa7146: register extension 'budget_ci dvb'.
[24570.669726] saa7146: register extension 'budget_av'.
[24570.709380] saa7146: register extension 'hexium gemini'.
[24570.716687] saa7146: register extension 'hexium HV-PCI6 Orion'.
[24570.727839] usbcore: registered new driver ttusb
[24570.735568] usbcore: registered new driver ttusb-dec
[24570.772694] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[24570.779887] usbcore: registered new driver b2c2_flexcop_usb
[24570.794727] usbcore: registered new driver cinergyT2
[24570.806313] usbcore: registered new driver dvb_usb_vp7045
[24570.813372] usbcore: registered new driver dvb_usb_dtt200u
[24570.824997] usbcore: registered new driver dvb_usb_dibusb_mb
[24570.830757] usbcore: registered new driver dvb_usb_dibusb_mc
[24570.834025] usbcore: registered new driver dvb_usb_a800
[24570.836981] usbcore: registered new driver dvb_usb_nova_t_usb2
[24570.839918] usbcore: registered new driver dvb_usb_umt_010
[24570.842878] usbcore: registered new driver dvb_usb_digitv
[24570.846226] usbcore: registered new driver dvb_usb_cxusb
[24570.849970] bttv: Unknown symbol v4l_compat_ioctl32
[24570.885710] bt878: Unknown symbol bttv_read_gpio
[24570.885775] bt878: Unknown symbol bttv_write_gpio
[24570.885845] bt878: Unknown symbol bttv_gpio_enable
[24570.917984] dst: Unknown symbol bt878_device_control
[24570.919285] dst_ca: Unknown symbol write_dst
[24570.919333] dst_ca: Unknown symbol dst_pio_disable
[24570.919374] dst_ca: Unknown symbol dst_comm_init
[24570.919412] dst_ca: Unknown symbol read_dst
[24570.919455] dst_ca: Unknown symbol dst_check_sum
[24570.919494] dst_ca: Unknown symbol dst_error_bailout
[24570.919571] dst_ca: Unknown symbol dst_wait_dst_ready
[24570.919609] dst_ca: Unknown symbol rdc_reset_state
[24570.919657] dst_ca: Unknown symbol dst_error_recovery
[24570.951589] dvb_bt8xx: Unknown symbol bt878_num
[24570.951639] dvb_bt8xx: Unknown symbol bttv_sub_unregister
[24570.951706] dvb_bt8xx: Unknown symbol dst_attach
[24570.951773] dvb_bt8xx: Unknown symbol bttv_write_gpio
[24570.951842] dvb_bt8xx: Unknown symbol bttv_sub_register
[24570.951931] dvb_bt8xx: Unknown symbol bttv_get_pcidev
[24570.952048] dvb_bt8xx: Unknown symbol dst_ca_attach
[24570.952112] dvb_bt8xx: Unknown symbol bt878_start
[24570.952175] dvb_bt8xx: Unknown symbol bttv_gpio_enable
[24570.952342] dvb_bt8xx: Unknown symbol bt878_stop
[24570.952505] dvb_bt8xx: Unknown symbol bt878
[24570.983849] cx8800: Unknown symbol v4l_compat_ioctl32
[24571.067405] cx2388x dvb driver version 0.0.5 loaded
[24571.071714] CORE cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
[24571.071721] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[24571.287732] ACPI: PCI Interrupt 0000:01:07.2[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[24571.287745] cx88[0]/2: found at 0000:01:07.2, rev: 5, irq: 19, latency: 32, mmio: 0xf9000000
[24571.287757] cx88[0]/2: cx2388x based dvb card
[24571.289541] DVB: registering new adapter (cx88[0]).
[24571.289551] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[24571.344901] cx88_blackbird: Unknown symbol cx88_do_ioctl
[24571.398916] cx2388x alsa driver version 0.0.5 loaded
[24571.401967] saa7134: Unknown symbol v4l_compat_ioctl32
[24571.404936] saa7134_alsa: Unknown symbol saa_dsp_writel
[24571.405018] saa7134_alsa: Unknown symbol saa7134_devlist
[24571.405236] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[24571.405283] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[24571.405325] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[24571.405366] saa7134_alsa: Unknown symbol dmasound_exit
[24571.405508] saa7134_alsa: Unknown symbol dmasound_init
[24571.405814] saa7134_alsa: Unknown symbol saa7134_set_dmabits
[24571.412993] saa7134_dvb: Unknown symbol saa7134_ts_register
[24571.413109] saa7134_dvb: Unknown symbol saa7134_ts_qops
[24571.413156] saa7134_dvb: Unknown symbol saa7134_i2c_call_clients
[24571.413288] saa7134_dvb: Unknown symbol saa7134_ts_unregister
[24571.414734] saa7134_empress: Unknown symbol saa7134_devlist
[24571.414800] saa7134_empress: Unknown symbol saa7134_common_ioctl
[24571.415003] saa7134_empress: Unknown symbol saa7134_boards
[24571.415065] saa7134_empress: Unknown symbol saa7134_ts_register
[24571.415472] saa7134_empress: Unknown symbol saa7134_ts_qops
[24571.415610] saa7134_empress: Unknown symbol saa7134_i2c_call_clients
[24571.415736] saa7134_empress: Unknown symbol saa7134_ts_unregister
[24571.482290] em28xx: Unknown symbol v4l_compat_ioctl32
[24571.519541] pvrusb2: pvr_init
[24571.562684] usbcore: registered new driver pvrusb2
[24571.562690] /home/hcm/v4l-dvb/v4l/pvrusb2-main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[24571.562696] /home/hcm/v4l-dvb/v4l/pvrusb2-main.c: Debug mask is 16834943 (0x100e17f)
[24571.564127] cpia2: Unknown symbol v4l_compat_ioctl32
[24571.613936] videodev: "VTM Virtual Video Capture Board" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[24571.613945] Video Technology Magazine Virtual Video Capture Board (Load status: 0)[/FONT]
[/COLOR]

So I cant even get the module to load up, let alone be able to detect and/or tune it in MythTV (which I have working fine..)

Has anyone got any ideas? anywhere where I should start (again)?

Thanks for your help in advance.

---

### Post by bl0w on 2006-04-30
Hi, I've been struggling with the same problem and I'm not that experienced with linux so interpret my advice as you will:

It seems that there are 2 versions of the card Fusion Plus card and if you bought it recently then you have a newer version which may not be supported in the standard V4L drivers. I tried to compile them but hit the same problem as you. Drivers have been developed but I'm not sure if they're in the main branch, have a look at this site: [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)
The developer has added support to his development branch, so you could try downloading that and compiling the drivers from that - let me know if you're successfull in this.
Alternatively, and this is how I did it, you can compile kernel 2.6.17-rc-1 which has the driver support built in. This has the side effect of requiring me to build my nvidia graphics card drivers manually as the one in the ubuntu repository aren't compatible.... So if you can get support going in a standard kernel it would probably be better

Good luck!

---

### Post by koshari on 2006-07-08
you simply need to place the module name for the card in /etc/module file

for the older dvico cards its btxxdvb or something like that, 

the newer cards use module cxbtxxx or something beggining wiff c, 

check in /dev/dvb and see if you have 4 devices listed, if so the system has loaded up the card fine, 

then use one of the "scan" packages utilitys like tzap to test if the card can lock onto a stream, 

i had the best success with dvico dvb-t with kaffeins and mythtv.

i still havnt got it to work in VLC but havnt tried to much.

---

