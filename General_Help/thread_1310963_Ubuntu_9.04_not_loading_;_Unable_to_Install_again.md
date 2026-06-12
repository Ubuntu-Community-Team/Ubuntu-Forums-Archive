---
title: "Ubuntu 9.04 not loading ; Unable to Install again"
date: 2009-11-02
forum: General Help
---

### Post by deepla on 2009-11-02
Hi i had dual booted ubuntu 9.04 with windows xp on my Acer 1641NWLMi laptop and everything was working fine. Then suddenly windows refused to load but that was fixed when i tried again. But soon Ubuntu was not loading. The ubuntu screen with sliding bar appears and slides to and fro for a long time then the screen goes blank and error messages appear. (Please see the attached Boot1 and Boot 2. ). When i tried to install ubuntu again, i am not able to as i get error message after the ubuntu screen appears . (Please see the attached Reinstall 1 and Reinstall 2 files. These are two photos i took while the error messages were running)


	The windows loads and works without any problem . CD drive also works well.My laptop's battery or power management system has some problem so i am able to run windows only with the acpi option switched off (accessed from the control panel). This way i am not able to see how much battery power is left when i am using the comp. When i tried in the past to install the previous version of ubuntu(Ubuntu 7) , i was able to do so only when i removed the battery and was running on a/c power. I could use ubuntu only this way. But Ubuntu 9.04 installed and worked without any issues . Ubuntu this time was even able to show how much battery is left. 
	


     I tried booting Ubuntu with the option acipi off and noacpi but still no improvement. Same with recvery mode. The update manager had indicated about some security updates which had to be installed but i had postponed it. Can it be due to that ? but then why am i not able to install Ubuntu afresh ?. I use a cd which i got when i ordered one online. 


	My system has Intel premium M725 processor, 512 MB ddr2 memmory and Intel graphics media accelerator 900. Please help.

---

### Post by oldos2er on 2009-11-02
Have you tried running fsck from the Live CD? Make sure your partitions are unmounted first.

---

### Post by Jayferd on 2009-11-02
The "{ DRDY ERR }" thing you're getting is usually associated with a bad hard drive or corrupted data.  See [http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872).

Good luck!

Peace,
--Jay

---

### Post by deepla on 2009-11-08
Hi friends, Thanks for your reply. sorry i could not get back earlier. It is sad to think the hard drive is faulty. I reformated the ubuntu partion with windows and ran fixmbr from recovery mode using windows cd. This removed the Grub.Windows seems not to have any problem with the hard drive. However when i tried to reinstall Ubuntu 9.04 again the same problem appears. I could not run fsck as oldos2er suggested. Dont know what to do now. Should i try the new version of ubuntu ? Will installing from a pen drive help ? Thank you so much for the help again

---

### Post by deepla on 2009-11-21
Hi after many attempts at installing Ubuntu 9.1 , i was finally successful when i installed from my flash drive. As Jayfred suggested there are 5 bad sectors in the hard drive. Initially the boot time was 5 minutes with all the error reporting. But now it is fast . 

Only problem is now the software centre or synaptic package manager does not connect to internet. Firefox was not connecting initially but after searching a bit i was able to find that i need to disable ipv6 in firefox. After this the wireless and the wired connections are working well for firefox but other applications does not connect to net. So unable to install anyother program. When i installed from the flash drive a warning came saying ' failed to load additional packages of apt config ' ( or something like that ). The error i get now when i try to reload in synaptic package manager is 
W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://je.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to je.archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Can you please help ?

---

