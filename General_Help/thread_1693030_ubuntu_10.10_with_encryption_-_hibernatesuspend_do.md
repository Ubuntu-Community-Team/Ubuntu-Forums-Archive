---
title: "ubuntu 10.10 with encryption - hibernate/suspend doesn't wake up"
date: 2011-02-22
forum: General Help
---

### Post by ub4o777 on 2011-02-22
Hi all,

First, I apologize if I'm posting in the wrong place.

I installed Maverick on my new laptop (Dell Precision M6500) and hibernate/suspend don't work out of the box. I have 2 partitions: boot (not encrypted), root partition (encrypted). The root partition contains these mounts:  / (380 GB), /home (100 GB), swap (16 GB). I have 8 GB RAM.

Here's the issue I'm encountering. I can successfully hibernate or suspend my session. But when I try to wake up, this is what happens. The system boots up and I get the encryption passphrase screen, once I entered the passphrase, a small cursor is displayed in the upper left for about 5 seconds. Then the entire screen becomes dark and stays like that. I waited to see if it ever comes out and waited like 20 minutes and it stayed dark. I was expecting to see either the login screen or automatically loads my hibernated/suspended session, but neither happened.

I tried these suggested solutions after googling for answers and none work:  set bios primary password, disable network manager, blacklisted iwlagn. One solution suggested using one of the later linux kernels like 2.6.36 or later. I haven't tried that, yet. I'm running 2.6.35-25.

I really need hibernate or suspend to work. Please help.

I'm attaching the output of pm-suspend.log in case someone is interested. Please let me know if I need to provide some other info.

Thanks,

-ub


pm-suspend.log:


Initial commandline parameters: 
Tue Feb 22 07:42:30 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux homer 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7984  1 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
parport_pc             30086  0 
ppdev                   6804  0 
arc4                    1497  2 
joydev                 11395  0 
snd_hda_codec_idt      64699  1 
pcmcia                 40944  0 
snd_hda_intel          26115  2 
iwlagn                202721  0 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
iwlcore               146875  1 iwlagn
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
tifm_7xx1               4698  0 
yenta_socket           24279  0 
tifm_core               7686  1 tifm_7xx1
pcmcia_rsrc            10357  1 yenta_socket
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
mac80211              267163  2 iwlagn,iwlcore
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  12929  2 
soundcore               1240  1 snd
psmouse                62080  0 
cfg80211              170485  3 iwlagn,iwlcore,mac80211
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
serio_raw               4910  0 
lp                     10201  0 
dell_wmi_aio            2097  0 
dell_wmi                3372  0 
dell_laptop             6722  0 
parport                37032  3 parport_pc,ppdev,lp
dcdbas                  6910  1 dell_laptop
sha256_generic         10351  2 
cryptd                  8140  0 
aes_x86_64              7936  2 
aes_generic            27631  1 aes_x86_64
dm_crypt               13381  1 
usbhid                 42030  0 
hid                    84710  1 usbhid
nouveau               569200  2 
ahci                   22210  2 
ttm                    68212  1 nouveau
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
drm_kms_helper         32836  1 nouveau
firewire_ohci          24839  0 
drm                   206230  4 nouveau,ttm,drm_kms_helper
firewire_core          54327  1 firewire_ohci
tg3                   135768  0 
led_class               3393  1 sdhci
libahci                26148  1 ahci
crc_itu_t               1739  1 firewire_core
i2c_algo_bit            6208  1 nouveau
video                  22176  0 
output                  2527  1 video
             total       used       free     shared    buffers     cached
Mem:       8116480     931912    7184568          0     136180     297024
-/+ buffers/cache:     498708    7617772
Swap:     15622140          0   15622140

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:

/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Tue Feb 22 07:42:39 EST 2011: performing hibernate
Tue Feb 22 07:49:31 EST 2011: Awake.
Tue Feb 22 07:49:31 EST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/91wicd thaw hibernate:

/usr/lib/pm-utils/sleep.d/91wicd thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Tue Feb 22 07:49:52 EST 2011: Finished.

---

### Post by ub4o777 on 2011-02-23
I installed hibernate and uswsusp, I get "resuming from /dev/disk/XXX" after hibernate, then reboot, entered encryption password. Not much progress.

---

### Post by ub4o777 on 2011-02-26
OK, I'm finally back with good news. I resolved the hibernate/suspend wake up issue.

As a final resort, I tried to upgrade to the latest stable Linux kernel (2.6.37.1) and that fixed it. So for those who have the same problem that I did, if you exhausted all your options, perhaps, try to upgrade to the latest kernel to see if that fixes it.

After rebuilding and installing the latest kernel, it would not work with "hibernate" and "uswsusp" packages installed. I had to remove them in order for hibernate/suspend to wake up.

If everything works correctly, when you hibernate, here are the expected sequences of events:
1) hibernate closes the GUI and goes to the terminal with s2disk running then computer shuts down
2) to wake up, after the computer starts up, you're prompted with the disk encryption password
3) once the password is entered, it switches into the terminal screen and a cursor blinks at the upper left for about 45 seconds
4) then the screen goes dark for about 3 seconds, then you're prompted with your account password
5) once the password is entered, the GUI is restored to its previous state

When you suspend, here are the expected sequence of events:
1) suspend automatically closes the GUI and suspends the machine (with minimal power running)
2) to wake up, after the computer starts up, you're prompted with your account password
3) once the password is entered, the GUI is restored to its previous state

These were the things that I tried before I upgraded the kernel (it may work for some of you):
a)sudo apt-get remove hibernate uswsusp  :  [http://ubuntuforums.org/showthread.php?t=1578902](http://ubuntuforums.org/showthread.php?t=1578902)
b) install hibernate and uswsusp work  :  [http://ubuntuforums.org/showthread.php?p=10364339](http://ubuntuforums.org/showthread.php?p=10364339)
c) change grub  :  [http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html](http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html)

For those you want to build the latest kernel:
a) download kernel source codes:  [http://www.kernel.org/](http://www.kernel.org/)
b) compile instructions:  [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)
    i) I ran these commands after downloading the sources (you may need to install packages [using Synaptic Package Manager] if they're not there, i.e. fakeroot, make-kpkg):
      #  tar xjf <sources>.tar.bz2
      #  make menuconfig
      #  make-kpkg clean
      #  fakeroot make-kpkg --initrd --revision=custom.1.0 kernel_image
      #  dpkg -i ../linux-image-2.6.37.1_custom.1.0_amd64.deb
   ii) restart the computer

That's it. Hope it helps you.

---

### Post by bedge on 2011-03-20
I have the same laptop, an m6500, but it won't suspend or sleep.

It acts like it's going to, all external displays (I'm running with a dock with lid closed) go dark, but the primary display (dual external monitors) never loses sync and comes back on after about 15 sec of darkness, then the aux monitor comes back on too.
Same thing for hibernate.

I am running the 2.6.38 kernel from here:
[http://www.megatek.net.br/customkernels/](http://www.megatek.net.br/customkernels/)

I've attached the pm-{suspend,powersave}.log files

I'm using the hard disk passwd for encryption and Mint-10-kde (10.10 based) on sda5.

---

### Post by bedge on 2011-03-20
> **bedge said:**
> I have the same laptop, an m6500, but it won't suspend or sleep.

It acts like it's going to, all external displays (I'm running with a dock with lid closed) go dark, but the primary display (dual external monitors) never loses sync and comes back on after about 15 sec of darkness, then the aux monitor comes back on too.
Same thing for hibernate.

I am running the 2.6.38 kernel from here:
[http://www.megatek.net.br/customkernels/](http://www.megatek.net.br/customkernels/)

I've attached the pm-{suspend,powersave}.log files

I'm using the hard disk passwd for encryption and Mint-10-kde (10.10 based) on sda5.

Oops, logs fell off, here they are.

---

### Post by kemelli on 2011-08-02
I have the same problem here, after the encryption. The link on how to compile the kernel is broken. Any other suggestions (even though I am definitely not an expert, and I'd love to fix this problem - it bothers me a lot!)

Thanks!

---

### Post by kemelli on 2011-09-26
I had some professional help (thanks Sam!!!) and here is how we fixed the problem: updating the kernel to version 3.0.

Simply type:
sudo apt-get install linux-headers-3.0.0-8-generic linux-headers-3.0.0-8
sudo apt-get install linux-image-3.0.0-8-generic

[SIZE=3]The new kernel will be available in your boot menu[/SIZE]. 
(To get the boot menu: [SIZE=3]reboot, while the machine is starting, hold down the left shift key.[/SIZE][SIZE=3])[/SIZE]
[SIZE=3]Select the linux 3.0 kernel.[/SIZE]
After you've done that once, the 3.0 kernel should start up by default; no need to select it from the menu anymore.

I hope this helps other people. It worked for me.
;)

---

