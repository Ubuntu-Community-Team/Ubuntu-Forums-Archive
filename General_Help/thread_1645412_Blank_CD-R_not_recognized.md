---
title: "Blank CD-R not recognized"
date: 2010-12-14
forum: General Help
---

### Post by J Bratton on 2010-12-14
I'm running Lucid. I've got a TST internal DVD/CD-RW drive. This drive reads music cds OK, reads DVDs OK, can burn data DVD-R, but CANNOT burn CD-R or CD-RW. What happens is this- in Brasero, I can start an audio cd project, but then when it prompts me to insert blank media if I don't want it to burn to an iso. I insert the blank media, the drive spins up, but nothing happens. There is nothing to choose but an iso. The blank media does not appear on the desktop. The blank media does not show up in when I go to "computer" and look at the DVD/CD drive.

Here's a little info from the command line: 

cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17


drive name:		sr1	sr0
drive speed:		51	40
drive # of slots:	1	1
Can close tray:		0	1
Can open tray:		1	1
Can lock tray:		1	1
Can change speed:	1	1
Can select disk:	0	0
Can read multisession:	1	1
Can read MCN:		1	1
Reports media changed:	1	1
Can play audio:		1	1
Can write CD-R:		0	1
Can write CD-RW:	0	1
Can read DVD:		0	1
Can write DVD-R:	0	1
Can write DVD-RAM:	0	1
Can read MRW:		1	1
Can write MRW:		1	1
Can write RAM:		1	1

<I'm not quite sure why a device sr1 showed up here... I think the drive in question here is the sr0>

sudo /lib/udev/cdrom_id /dev/sr0 
ID_CDROM=1
ID_CDROM_CD=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_R=1
ID_CDROM_DVD_RW=1
ID_CDROM_DVD_RAM=1
ID_CDROM_DVD_PLUS_R=1
ID_CDROM_DVD_PLUS_RW=1
ID_CDROM_DVD_PLUS_R_DL=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1

Based on a look at some of the bugs reports that seem similar but not exactly the same, I did this:

sudo add-apt-repository ppa:pitti/ppa

And then updated. Then:

sudo apt-get install udev

It didn't seem to change anything. Here are some diagnostics which I hope are helpful:

sudo /lib/udev/cdrom_id --debug /dev/sr0main: probing: '/dev/sr0'
cd_media_compat: CDROM_DRIVE_STATUS != CDS_DISC_OK
cd_inquiry: INQUIRY: [TSSTcorp][CD/DVDW TS-H652M][0414]
cd_profiles: GET CONFIGURATION: size of features buffer 0x0154
cd_profiles: GET CONFIGURATION: feature 'profiles', with 14 entries
feature_profiles: profile 0x15 <ignored>
feature_profiles: profile 0x16 <ignored>
feature_profiles: profile 0x2b dvd_plus_r_dl
feature_profiles: profile 0x1b dvd_plus_r
feature_profiles: profile 0x1a dvd_plus_rw
feature_profiles: profile 0x14 dvd_rw
feature_profiles: profile 0x13 dvd_rw
feature_profiles: profile 0x12 dvd_ram
feature_profiles: profile 0x11 <ignored>
feature_profiles: profile 0x10 dvd_rom
feature_profiles: profile 0x0a cd_rw
feature_profiles: profile 0x09 cd_r
feature_profiles: profile 0x08 cd_rom
feature_profiles: profile 0x02 <ignored>
cd_profiles: GET CONFIGURATION: feature 0x0001 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0002 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0003 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0004 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0010 <ignored>, with 0x08 bytes
cd_profiles: GET CONFIGURATION: feature 0x001d <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x001e <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x001f <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0020 <ignored>, with 0x0c bytes
cd_profiles: GET CONFIGURATION: feature 0x0021 <ignored>, with 0x08 bytes
cd_profiles: GET CONFIGURATION: feature 0x0023 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0024 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0026 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x002a <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002b <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002c <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002d <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002e <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002f <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0033 <ignored>, with 0x08 bytes
cd_profiles: GET CONFIGURATION: feature 0x003b <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0100 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0101 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0103 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0104 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0105 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0106 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0107 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0108 <ignored>, with 0x14 bytes
cd_profiles: GET CONFIGURATION: feature 0x010a <ignored>, with 0x0c bytes
cd_profiles: GET CONFIGURATION: feature 0x010b <ignored>, with 0x04 bytes
cd_profiles: no current profile, assuming no media
ID_CDROM=1
ID_CDROM_CD=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_R=1
ID_CDROM_DVD_RW=1
ID_CDROM_DVD_RAM=1
ID_CDROM_DVD_PLUS_R=1
ID_CDROM_DVD_PLUS_RW=1
ID_CDROM_DVD_PLUS_R_DL=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1

I've also tried GnomeBaker. That didn't work (I can remember the nature of the error). I also tried K3b. K3b got me farther in the process and allowed me to burn things, but it always burned coasters.

My apologies if I have not been able to provide a full breadcrumb-trail of what I have tried thus far to fix the problem... I've forgotten lots of what I've tried!

The drive worked previously to burn cds in windows XP, but since I haven't tried that in a good while, I can't 100% rule out a physical defect of the drive itself. It just seems unlikely, given that the drive can still read cds, and can burn DVDs. 

I'm interested in the cd-burning capability so can burn cds for my car. If there's any more info I can provide to help with a solution, please let me know.

---

### Post by Hippytaff on 2010-12-14
I have the same problem, but I haven't looked into a fix, I just reboot with the blank disc in and it is recognised. Not great advice but thought I'd share it anyway.

---

### Post by J Bratton on 2010-12-14
> **Hippytaff said:**
> I have the same problem, but I haven't looked into a fix, I just reboot with the blank disc in and it is recognised. Not great advice but thought I'd share it anyway.

Thanks. That'd be good enough for me, but it doesn't work in my case. Reboot with cd in still doesn't get the blank recognized...

---

### Post by Hippytaff on 2010-12-14
have you tried a different cd, a different brand, the cd in a different machine...best to rule all that out before you dig further

---

### Post by J Bratton on 2010-12-14
> **Hippytaff said:**
> have you tried a different cd, a different brand, the cd in a different machine...best to rule all that out before you dig further
Good point. Yes, I've tried about three different brands (Sony and a couple different types of Maxell) in both CD-R and CD-RW. All burned OK in the same computer and same drive previously under Windows XP.

---

### Post by Hippytaff on 2010-12-14
I'm afraid I haven't looked into this kind of issue as of yet, so I'm not best placed to help out, though others here have experience with this and will probably chip in shortly

---

### Post by skrap on 2012-04-26
Same problem for me.  Lucid Lynx on 64 bit with Nvidia graphics card.  Any help with this would be much appreciated.

---

