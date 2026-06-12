---
title: "driver for Ralink 3070 not working"
date: 2011-02-28
forum: General Help
---

### Post by dag1 on 2011-02-28
I have EddieMax 771In
They provide the source code for driver.
[http://www.edimax.com/en/downloadBox...2_Linux_STA_v2]("http://www.edimax.com/en/downloadBox.php?pd_id=344&download_link=../images/Image/Driver_Utility/Wireless/NIC/EW-7711In/EW-7711IN_2010_07_16_RT3062_Linux_STA_v2")[1].4.0.0.tar.bz2.zip

I follow the instructions (in the pdf file of the above zip file)
this includes:
changing the file names to RT3070STA.dat
adding line blacklist rt2800usb to /etc/modprobe.d/blacklist.conf
make
make install

but lsmod does not list any rt

I try :   sudo modprbe rt3070sta
I get:

FATAL: Error inserting rt3070sta  (/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/rt3070sta.ko):  Unknown symbol in module, or unknown parameter (see dmesg)

I try:  dmesg
I get:

[ 1793.767388] rt3070sta: Unknown symbol usb_alloc_urb
[ 1793.767506] rt3070sta: Unknown symbol usb_free_urb
[ 1793.767850] rt3070sta: Unknown symbol usb_register_driver
[ 1793.768127] rt3070sta: Unknown symbol usb_put_dev
[ 1793.768222] rt3070sta: Unknown symbol usb_get_dev
[ 1793.768407] rt3070sta: Unknown symbol usb_submit_urb
[ 1793.768839] rt3070sta: Unknown symbol usb_control_msg
[ 1793.769153] rt3070sta: Unknown symbol usb_deregister
[ 1793.769590] rt3070sta: Unknown symbol usb_kill_urb
[ 1793.769681] rt3070sta: Unknown symbol usb_buffer_free
[ 1793.770092] rt3070sta: Unknown symbol usb_buffer_alloc

Please, any advise ?

thanks
Dag

---

