---
title: "Mobile broadband working on one Lucid system, but not another"
date: 2011-02-08
forum: General Help
---

### Post by danemaslen on 2011-02-08
I'm not really expecting anyone to come up with an immediate solution to this problem.  Rather I'm hoping for suggestions as to what I should be doing to investigate it (e.g. which log file to look at).

I have two DELL systems (a desktop system and a netbook) that are both running Lucid.  I have a vodafone mobile broadband dongle (a K3520-Z).  It works successfully on the netbook but not on the desktop system.

A potted history of the netbook is that it was bought with Karmic installed and was upgraded to Lucid at the beginning of January courtesy of free wi-fi at a hotel I was staying in.  At some subsequent stage when I first plugged in the K3520-Z, the system recognised its presence and guided me through the procedure for setting up the mobile broadband connection.  That connection works (just so long as I have the dongle plugged in when I boot the system, but that's a gremlin I can live with).

A potted history of the desktop system is that it was bought with Hardy installed and for about 18 months I used Betavine's VMC software on it to have mobile broadband connectivity.  Yesterday I upgraded it to Lucid.  After the reboot the K3520-Z's presence was not recognised.  Instead I had to manually initiate the procedure for setting up a mobile broadband connection.  As far as I can see, I have it set up identically on both systems.  It does not, however, work on the desktop system.  Network manager's behaviour leads me to suspect that it is unaware of the existence of the device.

As and aside I'll mention that I have also installed the Betavine Connection Manager (BCM) software on both systems.  It also works on the netbook but not on the desktop system.  I believe, however, that this is (so far at least) down to a different problem as BCM isn't getting as far as starting up, let alone attempting to use the dongle.

As I said at the beginning, at this stage I'm mainly after suggestions about what I should be investigating.  For example are there any log files that could provide insight into why network manager is apparently finding the device on one system but not the other?  Thanks in advance for any suggestions.

---

### Post by aeiah on 2011-02-08
compare the loaded modules on each system:
```
lsmod
```

and kernels, i suppose
```
 uname -a
```

---

### Post by danemaslen on 2011-02-08
> **aeiah said:**
> compare the loaded modules on each system:
```
lsmod
```

and kernels, i suppose
```
 uname -a
```

Thanks.

The kernels are different, but with the failing system'having the more up-to-date kernel:
  notebook: Linux dell-desktop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
  desktop: Linux dell-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

There are differences in the loaded modules, but I need to get the listings from the two systems together onto this netbook to produce a definitive list and post it.  I'll do that a bit later today.

I am half wondering whether there might be a file protection problem somewhere.  I've already encountered one instance where the upgrade to Lucid on the desktop incorrectly left a file with no group or other read access.  I also suspect I know how that might have happened.  On the desktop I have 'umasl u=rwx,g=,o=' in my .profile.  Therefore if an installation script creates a file and sets the owner to root but doesn't explicitly set the protection, the file will finish up with no read access to group or other (given that the default umask has g=r,o=r such an installation script would 'work correctly' for most people).

---

### Post by danemaslen on 2011-02-08
Here's the result of comparing the lsmod output for the two systems.

On the desktop I did

lsmod | sort > desktop-lsmod.txt

and copied the file over to the netbook where I then did:

lsmod | sort > netbook-lsmod.txt
diff --side-by-side --minimal --suppress-common-lines netbook-lsmod.txt desktop-lsmod.txt

There are quite a lot of differences, though several are easily explained by hardware differences (e.g. the netbook has bluetooth but the desktop system doesn't).  I've no idea whether any of the other differences are significant.

```
agpgart                31724  2 drm,intel_agp		      |	agpgart                31724  2 fglrx,intel_agp
ahci                   32200  2 			      <
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb   |	dcdbas                  5422  0 
bnep                    9436  2 			      <
bridge                 45614  0 			      <
bsd_comp                4811  0 			      <
btusb                  10957  2 			      <
crc_ccitt               1339  1 ppp_async		      <
dcdbas                  5422  1 dell_laptop		      <
dell_laptop             6856  0 			      <
dm_crypt               11331  0 			      |	e1000e                119856  0 
drm                   162409  4 i915,drm_kms_helper	      <
drm_kms_helper         29329  1 i915			      <
							      >	fglrx                2092908  29 
							      >	floppy                 53016  0 
i2c_algo_bit            5028  1 i915			      |	hid                    67064  1 usbhid
i915                  287458  3 			      |	intel_agp              24375  0 
intel_agp              24375  2 i915			      <
joydev                  8740  0 			      <
l2cap                  30624  16 rfcomm,bnep		      <
lib80211                5046  2 lib80211_crypt_tkip,wl	      <
lib80211_crypt_tkip     7596  0 			      <
option                 20006  2 			      <
output                  1871  1 video			      <
ppp_async               6734  1 			      <
ppp_deflate             3682  0 			      <
rfcomm                 33421  4 			      <
rts_pstor             274072  0 			      <
sco                     7885  2 			      <
snd                    55750  18 snd_hda_codec_realtek,snd_hd |	snd                    54180  16 snd_hda_codec_realtek,snd_hd
snd_hda_codec          79741  2 snd_hda_codec_realtek,snd_hda |	snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda
snd_hda_codec_realtek   210814  1 			      |	snd_hda_codec_realtek   203408  1 
snd_hda_intel          20511  2 			      |	snd_hda_intel          22005  2 
snd_hwdep               5604  1 snd_hda_codec		      |	snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13897  1 snd_pcm_oss		      |	snd_mixer_oss          13746  1 snd_pcm_oss
snd_page_alloc          7108  2 snd_hda_intel,snd_pcm	      |	snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
snd_pcm                71433  3 snd_hda_intel,snd_hda_codec,s |	snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,s
snd_pcm_oss            34539  0 			      |	snd_pcm_oss            35308  0 
snd_rawmidi            19109  1 snd_seq_midi		      |	snd_rawmidi            19056  1 snd_seq_midi
snd_seq                47754  6 snd_seq_dummy,snd_seq_oss,snd |	snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd
snd_seq_device          6020  5 snd_seq_dummy,snd_seq_oss,snd |	snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd
snd_seq_dummy           1434  0 			      |	snd_seq_dummy           1338  0 
snd_seq_midi            4589  0 			      |	snd_seq_midi            4557  0 
snd_seq_oss            27370  0 			      |	snd_seq_oss            26722  0 
snd_timer              18688  2 snd_pcm,snd_seq		      |	snd_timer              19098  2 snd_pcm,snd_seq
stp                     1655  1 bridge			      <
tg3                   109324  0 			      <
usbserial              33019  6 option			      <
vga16fb                11385  0 			      |	usbhid                 36110  0 
							      >	usblp                  10481  0 
							      >	vga16fb                11385  1 
video                  17375  1 i915			      <
wl                   1959598  0 			      <
zlib_deflate           19568  1 ppp_deflate		      <
```

---

### Post by danemaslen on 2011-02-08
> **danemaslen said:**
> I am half wondering whether there might be a file protection problem somewhere.

I've been considering how I could test this hypothesis.  The only method I can see would be...

[INDENT]Enable root password
Login through the GUI as root
See if mobile broadband works for root
Logout as soon as possible!
Disable root password[/INDENT]

Any comments?

---

### Post by danemaslen on 2011-02-09
Based on some investigating I've been doing, I've come to the following conclusions (you'll note that they contradict earlier assumptions):

It's probably not a file protection issue.

BCM and Ubuntu's built-in mobile broadband support are almost certainly currently failing for the same reason.

That reason is that the modem-manager is not starting.

I've been looking at various log files.  In the first few reboots after the upgrade the modem-manager started successfully and Ubuntu was at least aware of the existence of the mobile broadband dongle.  In more recent reboots the modem-manager is apparently failing to start, so that's the first problem I have to solve.  Given, however, that just about the first thing I did after the first reboot after the upgrade was to attempt to use mobile broadband, it seems likely that even after dealing with the modem-manager problem I shall find that there is at least one more issue to be dealt with.

If I'm interpreting the contents of /var/log/dist-upgrade correctly, my upgrade to Lucid finished at about 2011-02-07 21:02.  That was followed by a reboot of course and subsequent to that I seem to have rebooted several times in fairly quick succession.  Alas I cannot remember what I did between each reboot, though in one instance it would have been to install BCM and the various packages that it required.

Below are extracts from daemon.log for the various reboots.  I've extracted those entries that I suspect might have some relevance to NetworkManager and mobile broadband.

You'll see that on the first, second and third reboots NetworkManager successfully starts modem-manager and there are various entries indicating that modem-manager is aware of the mobile broadband dongle.  Some of the differences between the reboots are likely to be down to me removing the dongle and putting it back in to see if that would make it work.

On the fourth reboot you'll see that the modem-manager caught a signal and shut itself down.  NetworkManager attempted to restart it, but evidently without success.  At the time that this was happening there are also 'dbus-daemon: Reloaded configuration' entries in the log file.  I'm assuming that this is not coincidental.

On all subsequent reboots there are entries like the following:

Feb  7 23:02:52 dell-desktop NetworkManager: <info>  Trying to start the modem-manager...

but there is never a subsequent entry to indicate that the modem-manager has become available.  It's therefore not surprising that my PC is blissfully unaware of the existence of the dongle.

My next step will be to rummage around on the internet to see if I can find out anything useful about problems with modem-manager.  In the meantime here are the daemon.log extracts for the various reboots.  In all cases I've omitted the lengthy series of entries that NetworkManager makes as it starts up.  Thereafter I've manually extracts those entries that seem to be relevant (so I might have missed some) and I've left a blank line wherever I have ignored entries as being seemingly irrelevant (i.e. made by other daemons).  


FIRST REBOOT

```
Feb  7 21:07:29 dell-desktop NetworkManager: <info>  modem-manager is now available
Feb  7 21:07:29 dell-desktop NetworkManager: <info>  Trying to start the supplicant...

Feb  7 21:07:37 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:07:37 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:07:37 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB1
Feb  7 21:07:37 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:07:37 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 as /org/freedesktop/ModemManager/Modems/0
Feb  7 21:07:37 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB3
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): now managed
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Feb  7 21:07:37 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
Feb  7 21:07:48 dell-desktop modem-manager: (ttyUSB0) closing serial device...

Feb  7 21:07:49 dell-desktop modem-manager: (ttyUSB2) closing serial device...

Feb  7 21:08:28 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:08:28 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Feb  7 21:08:29 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)

Feb  7 21:09:52 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:09:52 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> disabled)
Feb  7 21:09:52 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  (ttyUSB1): now unmanaged
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 1 (reason 36)
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  (ttyUSB1): cleaning up...
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  (ttyUSB1): taking down device.
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:09:52 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

SECOND REBOOT:

```
Feb  7 21:32:49 dell-desktop NetworkManager: <info>  modem-manager is now available
Feb  7 21:32:49 dell-desktop NetworkManager: <info>  Trying to start the supplicant...

Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:32:52 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'

Feb  7 21:32:57 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:32:57 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:32:57 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:32:57 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:32:58 dell-desktop usb_id[1335]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:32:58 dell-desktop usb_id[1334]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:32:58 dell-desktop usb_id[1336]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:32:58 dell-desktop usb_id[1337]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:32:58 dell-desktop usb_id[1339]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:32:58 dell-desktop usb_id[1340]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:32:58 dell-desktop usb_id[1338]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:32:58 dell-desktop usb_id[1341]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:32:58 dell-desktop usb_id[1364]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:32:58 dell-desktop usb_id[1365]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:32:58 dell-desktop usb_id[1366]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:32:58 dell-desktop usb_id[1368]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:32:58 dell-desktop usb_id[1367]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:32:58 dell-desktop usb_id[1369]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:32:58 dell-desktop usb_id[1370]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:32:58 dell-desktop usb_id[1372]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:32:58 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:32:58 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:32:58 dell-desktop modem-manager: (ttyUSB2) opening serial device...

Feb  7 21:32:58 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'

Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:32:59 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:00 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:01 dell-desktop modem-manager: Got failure code 100: Unknown error
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:01 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:02 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:03 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:05 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:06 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:06 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:06 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:07 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:33:08 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:33:11 dell-desktop modem-manager: Got failure code 100: Unknown error
Feb  7 21:33:14 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:33:15 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB0
Feb  7 21:33:15 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1

Feb  7 21:33:26 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:33:27 dell-desktop modem-manager: (ttyUSB3) closing serial device...

Feb  7 21:34:31 dell-desktop modem-manager: Removing modem claimed by removed device /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:34:31 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:34:31 dell-desktop modem-manager: failed to marshal parameter 1 for signal DeviceRemoved
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:34:33 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:34:39 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:34:39 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB1
Feb  7 21:34:39 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:34:39 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 as /org/freedesktop/ModemManager/Modems/0
Feb  7 21:34:39 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:34:39 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB3
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): now managed
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Feb  7 21:34:39 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
Feb  7 21:34:50 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:34:50 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:34:50 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  (ttyUSB1): now unmanaged
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 1 (reason 36)
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  (ttyUSB1): cleaning up...
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  (ttyUSB1): taking down device.
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:34:50 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

The second reboot also a whole host of entries similar to these:

```
Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules:11

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/51-hso-udev.rules:86

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/85-brltty.rules:8

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/99-huawei-e220.rules:2

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/99-novatel-ovation.rules:2

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/99-option-icon.rules:2

Feb  7 21:32:59 dell-desktop udevd[329]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules:11
```


THIRD REBOOT:

```
Feb  7 21:35:32 dell-desktop NetworkManager: <info>  modem-manager is now available

Feb  7 21:35:32 dell-desktop NetworkManager: <info>  Trying to start the supplicant...

Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:36:29 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:36:30 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:36:30 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:36:35 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:36:35 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB1
Feb  7 21:36:35 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:36:35 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 as /org/freedesktop/ModemManager/Modems/0
Feb  7 21:36:35 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:36:35 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1 claimed port ttyUSB3
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): now managed
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Feb  7 21:36:35 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
Feb  7 21:36:49 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:36:51 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:36:55 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:36:55 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Feb  7 21:36:55 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)

Feb  7 21:44:03 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> disabled)
Feb  7 21:44:03 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1
Feb  7 21:44:03 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  (ttyUSB1): now unmanaged
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 1 (reason 36)
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  (ttyUSB1): cleaning up...
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  (ttyUSB1): taking down device.
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:44:03 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

FOURTH REBOOT:

```
Feb  7 21:48:54 dell-desktop NetworkManager: <info>  modem-manager is now available
Feb  7 21:48:54 dell-desktop NetworkManager: <info>  Trying to start the supplicant...

Feb  7 21:48:57 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:48:57 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:48:57 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:48:57 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:48:58 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:48:58 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'

Feb  7 21:48:59 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:48:59 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'

Feb  7 21:49:02 dell-desktop modem-manager: (ttyUSB1) closing serial device...

Feb  7 21:49:04 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 claimed port ttyUSB1
Feb  7 21:49:04 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:49:04 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 as /org/freedesktop/ModemManager/Modems/0
Feb  7 21:49:04 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:04 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 claimed port ttyUSB3
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): now managed
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Feb  7 21:49:04 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)

Feb  7 21:49:15 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:49:17 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:32 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:49:32 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Feb  7 21:49:32 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Feb  7 21:49:32 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:49:32 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> disabled)
Feb  7 21:49:32 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  (ttyUSB1): now unmanaged
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 1 (reason 36)
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  (ttyUSB1): cleaning up...
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  (ttyUSB1): taking down device.
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:49:32 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:49:33 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:33 dell-desktop usb_id[1525]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:49:33 dell-desktop usb_id[1523]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:49:33 dell-desktop usb_id[1526]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:49:33 dell-desktop usb_id[1528]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.4/ttyUSB0/tty/ttyUSB0'
Feb  7 21:49:33 dell-desktop usb_id[1538]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:49:33 dell-desktop usb_id[1539]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:49:33 dell-desktop usb_id[1542]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:49:33 dell-desktop usb_id[1543]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.3/ttyUSB1/tty/ttyUSB1'
Feb  7 21:49:34 dell-desktop usb_id[1560]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:49:34 dell-desktop usb_id[1561]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:49:34 dell-desktop usb_id[1562]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/ttyUSB3/tty/ttyUSB3'
Feb  7 21:49:34 dell-desktop usb_id[1564]: unable to access '/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/ttyUSB2/tty/ttyUSB2'
Feb  7 21:49:34 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:49:34 dell-desktop modem-manager: config_fd (ttyUSB1): TCGETA error: 5
Feb  7 21:49:34 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:49:34 dell-desktop modem-manager: supports_port: assertion `task == NULL' failed
Feb  7 21:49:35 dell-desktop modem-manager: last message repeated 2 times
Feb  7 21:49:34 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:35 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:35 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:35 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:36 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:38 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:39 dell-desktop modem-manager: Got failure code 3: No carrier
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:42 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:43 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:43 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:44 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:45 dell-desktop modem-manager: Got failure code 100: Unknown error
Feb  7 21:49:45 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:45 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:46 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:46 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:46 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:46 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:49:49 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:49:49 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 claimed port ttyUSB2
Feb  7 21:49:49 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:49:49 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 as /org/freedesktop/ModemManager/Modems/1
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): new GSM device (driver: 'option1')
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): now managed
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2 (reason 2)
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2).
Feb  7 21:49:49 dell-desktop NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3 (reason 0)
Feb  7 21:49:56 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:49:56 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  (ttyUSB2): now unmanaged
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 1 (reason 36)
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  (ttyUSB2): cleaning up...
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  (ttyUSB2): taking down device.
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:49:56 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB2) opening serial device...
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB0) opening serial device...
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB3) opening serial device...
Feb  7 21:49:59 dell-desktop modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Feb  7 21:50:06 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:50:06 dell-desktop modem-manager: (ttyUSB3) closing serial device...
Feb  7 21:50:07 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 claimed port ttyUSB1
Feb  7 21:50:07 dell-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:50:07 dell-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 as /org/freedesktop/ModemManager/Modems/2
Feb  7 21:50:07 dell-desktop modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2 claimed port ttyUSB3
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/3
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): now managed
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Feb  7 21:50:07 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)

Feb  7 21:50:18 dell-desktop modem-manager: (ttyUSB2) closing serial device...
Feb  7 21:50:19 dell-desktop modem-manager: (ttyUSB0) closing serial device...
Feb  7 21:50:21 dell-desktop modem-manager: (ttyUSB1) opening serial device...
Feb  7 21:50:21 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/2: state changed (disabled -> enabling)
Feb  7 21:50:21 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabling -> enabled)
Feb  7 21:51:02 dell-desktop modem-manager: (ttyUSB1) closing serial device...
Feb  7 21:51:02 dell-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabled -> disabled)
Feb  7 21:51:02 dell-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  (ttyUSB1): now unmanaged
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 1 (reason 36)
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  (ttyUSB1): cleaning up...
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  (ttyUSB1): taking down device.
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb  7 21:51:02 dell-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

Feb  7 21:59:12 dell-desktop modem-manager: Caught signal 15, shutting down...

Feb  7 21:59:12 dell-desktop dbus-daemon: Reloaded configuration
Feb  7 21:59:12 dell-desktop NetworkManager: <info>  modem manager disappeared
Feb  7 21:59:12 dell-desktop NetworkManager: <info>  Trying to start the modem-manager...
Feb  7 21:59:44 dell-desktop dbus-daemon: Reloaded configuration
Feb  7 21:59:44 dell-desktop dbus-daemon: Reloaded configuration

```
And there were also a host of the 'udevd[329]' entries, all timestamped Feb  7 21:59:12

---

### Post by danemaslen on 2011-02-09
Just a quick update to say that I've discovered that modem-manager is replaced when installing bcm.  The failure of the modem-manager to start coincides to the second with the installation of wader_core, one of bcm's prerequisite packages, so it seems that the current problem is down to the Betavine software and I am pursuing the matter in their forum.  I believe there might well be other issues (after all I was unable to get Ubuntu to connect to the internet with my mobile broadband dongle even before I installed bcm), but they can only be investigated once the modem-manager problem has been resolved.

---

### Post by danemaslen on 2011-02-10
I've been investigating further and that has led me to the following:

[https://bugs.launchpad.net/ubuntu/+source/twisted/+bug/631486](https://bugs.launchpad.net/ubuntu/+source/twisted/+bug/631486)

which describes how the upgrade from hardy to lucid breaks getPlugins(IPlugin).  The resultant error that it describes, namely

OSError: [Errno 2] No such file or directory: '/usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py'

is indeed the error that wader_core is getting when it tries starting up.

This would explain why bcm is working on my netbook (which was upgraded from Karmic to Lucid) but not on my desktop system (which was upgraded from Hardy to Lucid).

So (for the moment at least) this has ceased being a problem for Betavine to fix.

For me the question has now become "What do I need to do to fix getPlugins(IPlugin)?

Investigation has revealed that /usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py is a broken link.  Interestingly the file doesn't exist at all on my netbook, so I'm going to try the effect of simply removing the broken link on the desktop system.

---

### Post by danemaslen on 2011-02-10
> **danemaslen said:**
> Investigation has revealed that /usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py is a broken link.  Interestingly the file doesn't exist at all on my netbook, so I'm going to try the effect of simply removing the broken link on the desktop system.

Success!  I removed the broken link, i.e.

rm -f /usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py

and rebooted, and mobile broadband is now working.

I believe I can also now retrospectively explain why mobile broadband wasn't working on the desktop system after the upgrade even before I installed bcm...

When I first contemplated upgrading from Hardy to Lucid the following articles led me to believe that Network Manager wouldn't support my mobile broadband dongle, a K3520-Z

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
[https://bugs.launchpad.net/bugs/598555](https://bugs.launchpad.net/bugs/598555)

I therefore expected to need bcm, but at that stage it was only on alpha release, so I sat back and continued to run Hardy.  In the meantime, having bought a netbook (which was running Karmic), I decided that the sensible approach would be to upgrade the latter to Lucid and confirm that I could use mobile broadband on it before upgrading my desktop PC.  The upgrade from Karmic to Lucid had to wait until I had wi-fi access in a hotel (in Gran Canaria) in January.  When I got the netbook home, I installed bcm on it and rebooted.  To my surprise the dongle worked directly from Network Manager.  I now know of course that bcm replaces Ubuntu's modem-manager, so on my netbook I never did discover whether the K3520-Z dongle would work with Lucid's modem-manager.  My experience on the desktop system, after upgrading to Lucid and before installing bcm, confirms my original belief (based on the articles above) that it doesn't.

Well, that's the easy bit done.  All I have to do know is work out how to mark this thread as solved!

---

