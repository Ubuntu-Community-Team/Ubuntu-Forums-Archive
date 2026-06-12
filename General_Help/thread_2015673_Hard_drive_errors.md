---
title: "Hard drive errors?"
date: 2012-07-03
forum: General Help
---

### Post by Ranko Kohime on 2012-07-03
So, the attached screenshot is interesting.  For the Read Error Rate value.  Seek errors are over 250 million.  Hardware ECC Recovered value is almost 100 million.

I'm guessing the drive is failing, but I'm not having any trouble with it, otherwise.  It's a headless server, and the drive only contains Ubuntu, so I'm not worried about losing data...  I'm just too lazy to fix what ain't broke.

Should I clone it now to a spare disk, just in case?

---

### Post by bodhi.zazen on 2012-07-03
I advise you have a backup. Your choice of best backup strategy.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by dcstar on 2012-07-04
> **Ranko Kohime said:**
> So, the attached screenshot is interesting.  .........

Best to wait for the test to actually finish.

---

### Post by lolpenguin on 2012-07-04
If your HDD supports SMART then have a look at the SMART report. Most disk utilities will let you do this.

---

### Post by rubylaser on 2012-07-04
> **lolpenguin said:**
> If your HDD supports SMART then have a look at the SMART report. Most disk utilities will let you do this.

That is SMART data that it's showing.  To the OP, the Read Error Rate can be an indicator of a imminent hard drive failure, but the RAW value is vendor specific and doesn't really mean much by itself.  [Wikipedia]("http://en.wikipedia.org/wiki/S.M.A.R.T.") has a good description of each of the values.  Personally, I really focus on the Reallocated Sector Count and Offline Uncorrectable Errors as indicators of a potential drive failure.  These seem to be the first values that start to rise before some of the other bad SMART values.

Can you run smartctl from the command line and paste the whole output back here?  This will allow you to easily paste all your values back here so we can see them.

I see your drive is an IDE drive, so this is likely the command you'd need to run (unless your drive isn't available at /dev/hda).
```
smartctl -a /dev/hda
```

For an example, here is one of the hard drives in my 9 disk RAID array.  You can see it has a very high raw value for Read Error Rate, but the two values I mentioned earlier are zeroes.  This is a very healthy disk.

```
  **[COLOR="SeaGreen"]1 Raw_Read_Error_Rate[/COLOR]**     0x000f   105   099   006    Pre-fail  Always       -       **[COLOR="SeaGreen"]9238512[/COLOR]**
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1949
  **[COLOR="Red"]5 Reallocated_Sector_Ct[/COLOR]**   0x0033   100   100   036    Pre-fail  Always       -       **[COLOR="Red"]0[/COLOR]**
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       17223964099
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7640
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       61
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   093   000    Old_age   Always       -       24
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   065   045    Old_age   Always       -       32 (Lifetime Min/Max 30/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       57
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       2030
194 Temperature_Celsius     0x0022   032   040   000    Old_age   Always       -       32 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   015   011   000    Old_age   Always       -       9238512
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
**[COLOR="red"]198 Offline_Uncorrectable[/COLOR]**   0x0010   100   100   000    Old_age   Offline      -       **[COLOR="red"]0[/COLOR]**
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       167632573565486
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       625301185
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       315834349
```

---

### Post by Ranko Kohime on 2012-07-06
> **rubylaser said:**
> That is SMART data that it's showing.  To the OP, the Read Error Rate can be an indicator of a imminent hard drive failure, but the RAW value is vendor specific and doesn't really mean much by itself.  [Wikipedia]("http://en.wikipedia.org/wiki/S.M.A.R.T.") has a good description of each of the values.  Personally, I really focus on the Reallocated Sector Count and Offline Uncorrectable Errors as indicators of a potential drive failure.  These seem to be the first values that start to rise before some of the other bad SMART values.

Can you run smartctl from the command line and paste the whole output back here?  This will allow you to easily paste all your values back here so we can see them.
The RSC value was the one I would usually be concerned about as well, but fortunately, it's zero.  As for OUE, I don't recall whether the drive had that parameter listed or not.  I'll post again with the smartctl output when I'm back on that network Friday afternoon.

---

### Post by Ranko Kohime on 2012-07-06
Update: No "Offline Uncorrectable Errors" tag exists, but "Current Pending Sector Count", "Uncorrectable Sector Count" and "Reallocated Sector Count" are all zero.

---

