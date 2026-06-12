---
title: "Bluetooth problem"
date: 2012-03-27
forum: General Help
---

### Post by Bleastboy on 2012-03-27
hello guys.
recently installed Ubuntu 11.10.had following problem. First tried to send files to phone via bluetooth, but was unable to do it, this was the error> pls see attached in image. i have also installed blueman and turned on file sharing but was not able to send or receive files either. Also paired the phone.

Then i tried to connect via data cable and run this command   "lsusb" and there was no phone there.
I'm new to Ubuntu so a little help would be appreciated.

---

### Post by gordintoronto on 2012-03-27
When connecting by USB cable, I find it sometimes helps to turn the device off, connect the cable, and turn the device on.

What brand and model of phone? Have you Googled the phone model along with "Ubuntu" or "Linux"?

Does Blueman run on the phone or the computer?

---

### Post by Bleastboy on 2012-03-27
i have nokia 5230. Followed your instruction turned off phone and attached data cable  but no phone at /media direc.
installed blueman in computer.
after blutooth error,run following command in terminal getting this
tail /var/log/syslog

```
Mar 25 13:19:17 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  144.187292] type=1400 audit(1332663557.854:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2994 comm="apparmor_parser"
Mar 25 13:19:18 bleast-HP-Compaq-nc6220-ED031UC-ABA anacron[3160]: Anacron 2.3 started on 2012-03-25
Mar 25 13:19:18 bleast-HP-Compaq-nc6220-ED031UC-ABA anacron[3160]: Normal exit (0 jobs run)
Mar 25 13:19:18 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  144.890948] init: apport pre-start process (3151) terminated with status 1
Mar 25 13:19:18 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  144.903881] init: apport post-stop process (3161) terminated with status 1
Mar 25 13:19:19 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  146.104374] init: plymouth-stop pre-start process (3295) terminated with status 1
Mar 25 13:20:01 bleast-HP-Compaq-nc6220-ED031UC-ABA CRON[3556]: (root) CMD (if [ -x /usr/bin/gsmsmsrequeue ]; then /usr/bin/gsmsmsrequeue; fi)
Mar 25 13:20:51 bleast-HP-Compaq-nc6220-ED031UC-ABA bluetoothd[1150]: Discovery session 0x20e838a0 with :1.69 activated
Mar 25 13:22:01 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  307.786457] hci_link_tx_to: hci0 link tx timeout
Mar 25 13:22:01 bleast-HP-Compaq-nc6220-ED031UC-ABA kernel: [  307.786474] hci_link_tx_to: hci0 killing stalled connection 5C:57:C8:DA:B9:FE
```

---

