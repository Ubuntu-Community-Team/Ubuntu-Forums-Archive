---
title: "Freezing after startup"
date: 2010-10-14
forum: General Help
---

### Post by Blimpsgo90 on 2010-10-14
my desktop running 10.4 will start up fine, but after 10-20 seconds of loading it freezes, and won't do anything else.

This started happening after installing some updates, which I am unsure of.

---

### Post by DarthScape on 2010-10-14
What type of computer are you using?

---

### Post by jacob.david on 2010-10-14
Post the contents of the /var/log/syslog.

---

### Post by Blimpsgo90 on 2010-10-15
> **jacob.david said:**
> Post the contents of the /var/log/syslog.

How would I get this if I can't open anything?

And the computer is a Older Core Duo with 6 gigs of ram and intel graphics.

---

### Post by ncohea on 2010-10-15
> **Blimpsgo90 said:**
> How would I get this if I can't open anything?

And the computer is a Older Core Duo with 6 gigs of ram and intel graphics.
I would try booting to the recovery mode (if that works) and copy the file to a flash stick or something, booting into something else like MacOS or Windows or whatever you have, and then posting here. I am not sure how to mount a flash stick or know what the mount point would be, but you can either do something like a 

```
cat /var/log/syslog > flashstick-whatever-it-is/log
```
or
```
cp /var/log/syslog flashstick-whatever-it-is/log
```

If you can't get a recovery mode boot either (things are really bad), then you can get a LiveCD, boot from there, and then do one of the above.

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 07:57:34 andrew-desktop anacron[27387]: Job `cron.daily' terminated
Oct 14 07:57:34 andrew-desktop anacron[27387]: Normal exit (1 job run)
Oct 14 07:58:46 andrew-desktop kernel: [926591.031305] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:00:46 andrew-desktop kernel: [926711.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:02:46 andrew-desktop kernel: [926831.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:04:46 andrew-desktop kernel: [926951.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:06:46 andrew-desktop kernel: [927071.034249] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:08:46 andrew-desktop kernel: [927191.034189] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:10:46 andrew-desktop kernel: [927311.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:12:46 andrew-desktop kernel: [927431.034308] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:14:46 andrew-desktop kernel: [927551.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:16:46 andrew-desktop kernel: [927671.033641] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:17:01 andrew-desktop CRON[27848]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 08:18:46 andrew-desktop kernel: [927791.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:20:46 andrew-desktop kernel: [927911.031302] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:22:46 andrew-desktop kernel: [928031.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:24:46 andrew-desktop kernel: [928151.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:26:46 andrew-desktop kernel: [928271.034213] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:28:46 andrew-desktop kernel: [928391.034206] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:30:46 andrew-desktop kernel: [928511.030097] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:32:46 andrew-desktop kernel: [928631.033844] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:34:46 andrew-desktop kernel: [928751.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:36:46 andrew-desktop kernel: [928871.034195] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:38:46 andrew-desktop kernel: [928991.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:40:46 andrew-desktop kernel: [929111.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:42:46 andrew-desktop kernel: [929231.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:44:46 andrew-desktop kernel: [929351.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:46:46 andrew-desktop kernel: [929471.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:48:46 andrew-desktop kernel: [929591.030044] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:50:46 andrew-desktop kernel: [929711.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:52:46 andrew-desktop kernel: [929831.030076] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:54:46 andrew-desktop kernel: [929951.034383] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:56:46 andrew-desktop kernel: [930071.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 08:58:46 andrew-desktop kernel: [930191.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:00:46 andrew-desktop kernel: [930311.031307] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:02:46 andrew-desktop kernel: [930431.030040] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:04:46 andrew-desktop kernel: [930551.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:06:46 andrew-desktop kernel: [930671.034324] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:08:46 andrew-desktop kernel: [930791.034350] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:10:46 andrew-desktop kernel: [930911.034206] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:12:46 andrew-desktop kernel: [931031.034451] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:14:46 andrew-desktop kernel: [931151.034317] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:16:46 andrew-desktop kernel: [931271.034493] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:17:01 andrew-desktop CRON[28306]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 09:18:46 andrew-desktop kernel: [931391.036319] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:20:46 andrew-desktop kernel: [931511.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:22:46 andrew-desktop kernel: [931631.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:24:46 andrew-desktop kernel: [931751.035082] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:26:46 andrew-desktop kernel: [931871.030042] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:28:46 andrew-desktop kernel: [931991.034204] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:30:46 andrew-desktop kernel: [932111.030058] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:32:46 andrew-desktop kernel: [932231.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:34:46 andrew-desktop kernel: [932351.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:36:46 andrew-desktop kernel: [932471.034302] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:38:46 andrew-desktop kernel: [932591.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:40:46 andrew-desktop kernel: [932711.033448] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:42:46 andrew-desktop kernel: [932831.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:44:46 andrew-desktop kernel: [932951.034376] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:46:46 andrew-desktop kernel: [933071.030049] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:48:46 andrew-desktop kernel: [933191.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:50:46 andrew-desktop kernel: [933311.030061] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:52:46 andrew-desktop kernel: [933431.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:54:46 andrew-desktop kernel: [933551.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 09:56:46 andrew-desktop kernel: [933671.030043] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 09:58:46 andrew-desktop kernel: [933791.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:00:46 andrew-desktop kernel: [933911.031295] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 10:02:46 andrew-desktop kernel: [934031.034569] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 10:04:46 andrew-desktop kernel: [934151.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:06:46 andrew-desktop kernel: [934271.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:08:46 andrew-desktop kernel: [934391.034620] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:10:46 andrew-desktop kernel: [934511.030059] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 10:12:46 andrew-desktop kernel: [934631.030056] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:14:46 andrew-desktop kernel: [934751.031306] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:16:46 andrew-desktop kernel: [934871.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:17:01 andrew-desktop CRON[28773]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 10:18:46 andrew-desktop kernel: [934991.034315] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 10:20:46 andrew-desktop kernel: [935111.034189] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:22:46 andrew-desktop kernel: [935231.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:24:46 andrew-desktop kernel: [935351.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:26:46 andrew-desktop kernel: [935471.034236] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:28:46 andrew-desktop kernel: [935591.032063] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:30:46 andrew-desktop kernel: [935711.030073] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:32:46 andrew-desktop kernel: [935831.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:34:46 andrew-desktop kernel: [935951.030044] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:36:46 andrew-desktop kernel: [936071.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:38:46 andrew-desktop kernel: [936191.034248] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:40:46 andrew-desktop kernel: [936311.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:42:46 andrew-desktop kernel: [936431.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:44:46 andrew-desktop kernel: [936551.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:46:46 andrew-desktop kernel: [936671.031307] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:48:46 andrew-desktop kernel: [936791.034301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:50:46 andrew-desktop kernel: [936911.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:52:46 andrew-desktop kernel: [937031.031302] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:54:46 andrew-desktop kernel: [937151.030049] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 10:56:46 andrew-desktop kernel: [937271.031330] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 10:58:46 andrew-desktop kernel: [937391.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:00:46 andrew-desktop kernel: [937511.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:02:46 andrew-desktop kernel: [937631.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:04:46 andrew-desktop kernel: [937751.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:06:46 andrew-desktop kernel: [937871.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:08:46 andrew-desktop kernel: [937991.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:10:46 andrew-desktop kernel: [938111.034176] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:12:46 andrew-desktop kernel: [938231.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:14:46 andrew-desktop kernel: [938351.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:16:46 andrew-desktop kernel: [938471.030077] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 11:17:01 andrew-desktop CRON[29239]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 11:18:46 andrew-desktop kernel: [938591.034309] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 11:20:46 andrew-desktop kernel: [938711.030050] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:22:46 andrew-desktop kernel: [938831.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:24:46 andrew-desktop kernel: [938951.034501] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:26:46 andrew-desktop kernel: [939071.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:28:46 andrew-desktop kernel: [939191.031360] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:30:46 andrew-desktop kernel: [939311.034289] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:32:46 andrew-desktop kernel: [939431.030055] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 11:34:46 andrew-desktop kernel: [939551.031421] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:36:46 andrew-desktop kernel: [939671.030068] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:38:46 andrew-desktop kernel: [939791.031166] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:40:46 andrew-desktop kernel: [939911.030038] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:42:46 andrew-desktop kernel: [940031.030061] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:44:46 andrew-desktop kernel: [940151.030043] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:46:46 andrew-desktop kernel: [940271.030058] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:48:46 andrew-desktop kernel: [940391.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:50:46 andrew-desktop kernel: [940511.030312] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:52:46 andrew-desktop kernel: [940631.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:54:29 andrew-desktop dhclient: DHCPREQUEST of 10.0.0.2 on wlan0 to 10.0.0.1 port 67
Oct 14 11:54:29 andrew-desktop dhclient: DHCPACK of 10.0.0.2 from 10.0.0.1
Oct 14 11:54:29 andrew-desktop dhclient: bound to 10.0.0.2 -- renewal in 38268 seconds.
Oct 14 11:54:46 andrew-desktop kernel: [940751.032997] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:56:46 andrew-desktop kernel: [940871.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 11:58:46 andrew-desktop kernel: [940991.030049] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 12:00:46 andrew-desktop kernel: [941111.030057] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 12:02:46 andrew-desktop kernel: [941231.034299] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:04:46 andrew-desktop kernel: [941351.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:06:46 andrew-desktop kernel: [941471.030066] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:08:46 andrew-desktop kernel: [941591.033165] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:10:46 andrew-desktop kernel: [941711.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:12:46 andrew-desktop kernel: [941831.031296] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 12:14:46 andrew-desktop kernel: [941951.034391] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:16:46 andrew-desktop kernel: [942071.034831] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:17:01 andrew-desktop CRON[29698]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 12:18:46 andrew-desktop kernel: [942191.031410] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:20:46 andrew-desktop kernel: [942311.030043] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:22:46 andrew-desktop kernel: [942431.034197] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:24:46 andrew-desktop kernel: [942551.030099] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:26:46 andrew-desktop kernel: [942671.035666] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:28:46 andrew-desktop kernel: [942791.031306] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:30:46 andrew-desktop kernel: [942911.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:32:46 andrew-desktop kernel: [943031.031299] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 12:34:46 andrew-desktop kernel: [943151.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:36:46 andrew-desktop kernel: [943271.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:38:46 andrew-desktop kernel: [943391.031295] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 12:40:46 andrew-desktop kernel: [943511.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:42:46 andrew-desktop kernel: [943631.030079] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:44:46 andrew-desktop kernel: [943751.030057] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:46:46 andrew-desktop kernel: [943871.031322] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:48:46 andrew-desktop kernel: [943991.030576] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:50:46 andrew-desktop kernel: [944111.034175] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:52:46 andrew-desktop kernel: [944231.030040] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:54:46 andrew-desktop kernel: [944351.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:56:46 andrew-desktop kernel: [944471.034349] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 12:58:46 andrew-desktop kernel: [944591.030066] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:00:46 andrew-desktop kernel: [944711.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:02:46 andrew-desktop kernel: [944831.031301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:04:46 andrew-desktop kernel: [944951.030049] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:06:46 andrew-desktop kernel: [945071.030089] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:08:46 andrew-desktop kernel: [945191.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:10:46 andrew-desktop kernel: [945311.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:12:46 andrew-desktop kernel: [945431.030868] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:14:46 andrew-desktop kernel: [945551.034340] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 13:16:46 andrew-desktop kernel: [945671.030160] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:17:01 andrew-desktop CRON[30163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 13:18:46 andrew-desktop kernel: [945791.030039] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:20:46 andrew-desktop kernel: [945911.031300] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:22:46 andrew-desktop kernel: [946031.030059] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:24:46 andrew-desktop kernel: [946151.031303] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:26:46 andrew-desktop kernel: [946271.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:28:46 andrew-desktop kernel: [946391.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:30:46 andrew-desktop kernel: [946511.031298] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 13:32:46 andrew-desktop kernel: [946631.030055] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:34:46 andrew-desktop kernel: [946751.031875] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 13:36:46 andrew-desktop kernel: [946871.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:38:46 andrew-desktop kernel: [946991.030054] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:40:46 andrew-desktop kernel: [947111.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:42:46 andrew-desktop kernel: [947231.030054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 13:44:46 andrew-desktop kernel: [947351.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:46:46 andrew-desktop kernel: [947471.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:48:46 andrew-desktop kernel: [947591.034375] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:50:46 andrew-desktop kernel: [947711.031302] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:52:46 andrew-desktop kernel: [947831.032178] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:54:46 andrew-desktop kernel: [947951.030063] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 13:56:46 andrew-desktop kernel: [948071.031299] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 13:58:46 andrew-desktop kernel: [948191.034282] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:00:46 andrew-desktop kernel: [948311.031301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:02:46 andrew-desktop kernel: [948431.030043] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:04:46 andrew-desktop kernel: [948551.030056] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:06:46 andrew-desktop kernel: [948671.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:08:46 andrew-desktop kernel: [948791.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:10:46 andrew-desktop kernel: [948911.032097] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:12:46 andrew-desktop kernel: [949031.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:14:46 andrew-desktop kernel: [949151.031299] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:16:46 andrew-desktop kernel: [949271.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:17:01 andrew-desktop CRON[30632]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 14:18:46 andrew-desktop kernel: [949391.030067] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:20:46 andrew-desktop kernel: [949511.030752] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:22:46 andrew-desktop kernel: [949631.030056] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:24:46 andrew-desktop kernel: [949751.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:26:46 andrew-desktop kernel: [949871.034293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:28:46 andrew-desktop kernel: [949991.032398] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:30:46 andrew-desktop kernel: [950111.030044] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:32:46 andrew-desktop kernel: [950231.034175] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:34:46 andrew-desktop kernel: [950351.034336] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:36:46 andrew-desktop kernel: [950471.031301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:38:46 andrew-desktop kernel: [950591.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:40:46 andrew-desktop kernel: [950711.034227] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 14:42:46 andrew-desktop kernel: [950831.034333] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:44:46 andrew-desktop kernel: [950951.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:46:46 andrew-desktop kernel: [951071.030049] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:48:46 andrew-desktop kernel: [951191.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:50:46 andrew-desktop kernel: [951311.030056] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:52:46 andrew-desktop kernel: [951431.036361] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:54:46 andrew-desktop kernel: [951551.034190] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:56:46 andrew-desktop kernel: [951671.031344] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 14:58:46 andrew-desktop kernel: [951791.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:00:46 andrew-desktop kernel: [951911.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:02:46 andrew-desktop kernel: [952031.030075] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:04:46 andrew-desktop kernel: [952151.031349] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:06:46 andrew-desktop kernel: [952271.033089] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:08:46 andrew-desktop kernel: [952391.031291] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 15:10:46 andrew-desktop kernel: [952511.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:12:46 andrew-desktop kernel: [952631.031300] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:14:46 andrew-desktop kernel: [952751.030041] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:16:46 andrew-desktop kernel: [952871.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:17:01 andrew-desktop CRON[31101]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 15:18:46 andrew-desktop kernel: [952991.030077] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:20:46 andrew-desktop kernel: [953111.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:22:46 andrew-desktop kernel: [953231.031291] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 15:24:46 andrew-desktop kernel: [953351.030049] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:26:46 andrew-desktop kernel: [953471.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:28:46 andrew-desktop kernel: [953591.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:30:46 andrew-desktop kernel: [953711.031334] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:32:46 andrew-desktop kernel: [953831.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:34:46 andrew-desktop kernel: [953951.030048] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:36:46 andrew-desktop kernel: [954071.034180] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:38:46 andrew-desktop kernel: [954191.030298] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:40:46 andrew-desktop kernel: [954311.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:42:46 andrew-desktop kernel: [954431.030055] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:44:46 andrew-desktop kernel: [954551.034459] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:46:46 andrew-desktop kernel: [954671.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:48:46 andrew-desktop kernel: [954791.031304] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:50:46 andrew-desktop kernel: [954911.030075] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:52:46 andrew-desktop kernel: [955031.030059] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:54:46 andrew-desktop kernel: [955151.031310] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 15:56:46 andrew-desktop kernel: [955271.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 15:58:46 andrew-desktop kernel: [955391.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:00:46 andrew-desktop kernel: [955511.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:02:46 andrew-desktop kernel: [955631.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:04:46 andrew-desktop kernel: [955751.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:06:46 andrew-desktop kernel: [955871.035294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:08:46 andrew-desktop kernel: [955991.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:10:46 andrew-desktop kernel: [956111.030042] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:12:46 andrew-desktop kernel: [956231.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:14:46 andrew-desktop kernel: [956351.035666] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:16:46 andrew-desktop kernel: [956471.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:17:01 andrew-desktop CRON[31570]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 16:18:46 andrew-desktop kernel: [956591.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:20:46 andrew-desktop kernel: [956711.030050] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:22:46 andrew-desktop kernel: [956831.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:24:46 andrew-desktop kernel: [956951.031645] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:26:46 andrew-desktop kernel: [957071.031287] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:28:46 andrew-desktop kernel: [957191.031304] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:30:46 andrew-desktop kernel: [957311.034481] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:32:46 andrew-desktop kernel: [957431.032962] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:34:46 andrew-desktop kernel: [957551.031298] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 16:36:46 andrew-desktop kernel: [957671.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:38:46 andrew-desktop kernel: [957791.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:40:46 andrew-desktop kernel: [957911.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:42:46 andrew-desktop kernel: [958031.030074] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:44:46 andrew-desktop kernel: [958151.034202] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:46:46 andrew-desktop kernel: [958271.030046] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 16:48:46 andrew-desktop kernel: [958391.030044] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:50:46 andrew-desktop kernel: [958511.030073] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:52:46 andrew-desktop kernel: [958631.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 16:54:46 andrew-desktop kernel: [958751.030044] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 16:56:46 andrew-desktop kernel: [958871.030059] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 16:58:46 andrew-desktop kernel: [958991.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:00:46 andrew-desktop kernel: [959111.031303] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:02:46 andrew-desktop kernel: [959231.030043] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:04:46 andrew-desktop kernel: [959351.031290] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:06:46 andrew-desktop kernel: [959471.031319] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:08:46 andrew-desktop kernel: [959591.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:10:46 andrew-desktop kernel: [959711.034121] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:12:46 andrew-desktop kernel: [959831.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:14:46 andrew-desktop kernel: [959951.030044] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:16:46 andrew-desktop kernel: [960071.030044] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:17:01 andrew-desktop CRON[652]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 17:18:46 andrew-desktop kernel: [960191.030044] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:20:28 andrew-desktop kernel: [960293.078736] npviewer.bin[718]: segfault at f58d904c ip 00000000f624e757 sp 00000000ffc7e9c0 error 4 in libflashplayer.so[f5eaf000+b2c000]
Oct 14 17:20:46 andrew-desktop kernel: [960311.035093] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:22:46 andrew-desktop kernel: [960431.032541] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:24:46 andrew-desktop kernel: [960551.031311] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:26:46 andrew-desktop kernel: [960671.030054] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:28:46 andrew-desktop kernel: [960791.030102] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:30:46 andrew-desktop kernel: [960911.033393] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:32:46 andrew-desktop kernel: [961031.030057] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:34:46 andrew-desktop kernel: [961151.031298] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:36:46 andrew-desktop kernel: [961271.031299] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:38:46 andrew-desktop kernel: [961391.031297] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:40:46 andrew-desktop kernel: [961511.031297] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:42:46 andrew-desktop kernel: [961631.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:44:46 andrew-desktop kernel: [961751.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:46:46 andrew-desktop kernel: [961871.031300] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:48:46 andrew-desktop kernel: [961991.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:50:46 andrew-desktop kernel: [962111.036336] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:52:46 andrew-desktop kernel: [962231.031301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:54:46 andrew-desktop kernel: [962351.031296] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 17:56:46 andrew-desktop kernel: [962471.031298] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 17:58:46 andrew-desktop kernel: [962591.030113] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:00:46 andrew-desktop kernel: [962711.031296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:02:46 andrew-desktop kernel: [962831.036325] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:04:46 andrew-desktop kernel: [962951.031297] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:06:46 andrew-desktop kernel: [963071.030069] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:08:46 andrew-desktop kernel: [963191.031303] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:10:46 andrew-desktop kernel: [963311.031296] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:12:46 andrew-desktop kernel: [963431.030054] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:14:46 andrew-desktop kernel: [963551.030068] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:16:46 andrew-desktop kernel: [963671.030054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:17:01 andrew-desktop CRON[1390]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 18:18:46 andrew-desktop kernel: [963791.030054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:20:46 andrew-desktop kernel: [963911.036303] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:22:46 andrew-desktop kernel: [964031.030059] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:24:46 andrew-desktop kernel: [964151.030053] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:26:46 andrew-desktop kernel: [964271.030106] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:28:46 andrew-desktop kernel: [964391.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:30:46 andrew-desktop kernel: [964511.030054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:32:46 andrew-desktop kernel: [964631.030054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:34:46 andrew-desktop kernel: [964751.030086] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:36:46 andrew-desktop kernel: [964871.030056] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 148
Oct 14 18:38:46 andrew-desktop kernel: [964991.031307] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:40:46 andrew-desktop kernel: [965111.030058] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 579
Oct 14 18:42:46 andrew-desktop kernel: [965231.031542] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:44:46 andrew-desktop kernel: [965351.031298] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:46:46 andrew-desktop kernel: [965471.031303] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:48:46 andrew-desktop kernel: [965591.031299] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:50:46 andrew-desktop kernel: [965711.030124] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:52:46 andrew-desktop kernel: [965831.030057] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:54:46 andrew-desktop kernel: [965951.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 18:56:46 andrew-desktop kernel: [966071.031435] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 18:58:46 andrew-desktop kernel: [966191.031304] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:00:46 andrew-desktop kernel: [966311.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 435
Oct 14 19:02:46 andrew-desktop kernel: [966431.030076] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 19:04:46 andrew-desktop kernel: [966551.033181] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:06:46 andrew-desktop kernel: [966671.030053] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:08:46 andrew-desktop kernel: [966791.031314] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 19:10:46 andrew-desktop kernel: [966911.030053] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 19:12:46 andrew-desktop kernel: [967031.031321] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:14:46 andrew-desktop kernel: [967151.030054] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 19:16:46 andrew-desktop kernel: [967271.030050] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:17:01 andrew-desktop CRON[1842]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 19:18:46 andrew-desktop kernel: [967391.031288] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:20:46 andrew-desktop kernel: [967511.031339] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 580
Oct 14 19:22:46 andrew-desktop kernel: [967631.031140] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:24:46 andrew-desktop kernel: [967751.031348] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:26:46 andrew-desktop kernel: [967871.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:28:46 andrew-desktop kernel: [967991.030052] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:30:46 andrew-desktop kernel: [968111.030076] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:32:46 andrew-desktop kernel: [968231.030064] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:34:46 andrew-desktop kernel: [968351.030053] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 19:36:46 andrew-desktop kernel: [968471.031304] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:38:46 andrew-desktop kernel: [968591.037875] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 19:40:46 andrew-desktop kernel: [968711.030119] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:42:46 andrew-desktop kernel: [968831.031320] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:44:46 andrew-desktop kernel: [968951.034261] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:46:46 andrew-desktop kernel: [969071.031319] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:48:46 andrew-desktop kernel: [969191.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:50:46 andrew-desktop kernel: [969311.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:52:46 andrew-desktop kernel: [969431.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:54:46 andrew-desktop kernel: [969551.030391] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:56:46 andrew-desktop kernel: [969671.034026] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 19:58:46 andrew-desktop kernel: [969791.030849] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:00:46 andrew-desktop kernel: [969911.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:02:46 andrew-desktop kernel: [970031.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:04:46 andrew-desktop kernel: [970151.030057] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:06:46 andrew-desktop kernel: [970271.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:08:46 andrew-desktop kernel: [970391.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:10:46 andrew-desktop kernel: [970511.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:12:46 andrew-desktop kernel: [970631.031319] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:14:46 andrew-desktop kernel: [970751.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:16:46 andrew-desktop kernel: [970871.030061] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:17:01 andrew-desktop CRON[2597]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 20:18:46 andrew-desktop kernel: [970991.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:20:46 andrew-desktop kernel: [971111.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:22:46 andrew-desktop kernel: [971231.034215] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:24:46 andrew-desktop kernel: [971351.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:26:46 andrew-desktop kernel: [971471.030043] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:28:46 andrew-desktop kernel: [971591.034210] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:30:46 andrew-desktop kernel: [971711.034216] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:32:46 andrew-desktop kernel: [971831.034242] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:34:46 andrew-desktop kernel: [971951.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:36:46 andrew-desktop kernel: [972071.030072] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:38:46 andrew-desktop kernel: [972191.031906] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:40:46 andrew-desktop kernel: [972311.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:42:46 andrew-desktop kernel: [972431.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:44:46 andrew-desktop kernel: [972551.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:46:46 andrew-desktop kernel: [972671.032637] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:48:46 andrew-desktop kernel: [972791.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:50:46 andrew-desktop kernel: [972911.031320] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:52:46 andrew-desktop kernel: [973031.031310] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 20:54:46 andrew-desktop kernel: [973151.034267] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:56:46 andrew-desktop kernel: [973271.032343] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 20:58:46 andrew-desktop kernel: [973391.031316] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:00:46 andrew-desktop kernel: [973511.032892] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:02:46 andrew-desktop kernel: [973631.031309] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:04:46 andrew-desktop kernel: [973751.034264] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:06:46 andrew-desktop kernel: [973871.031827] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:08:46 andrew-desktop kernel: [973991.030068] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:10:46 andrew-desktop kernel: [974111.031291] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:12:46 andrew-desktop kernel: [974231.031458] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:14:46 andrew-desktop kernel: [974351.031521] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:16:46 andrew-desktop kernel: [974471.031293] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:17:01 andrew-desktop CRON[3482]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 21:18:46 andrew-desktop kernel: [974591.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:20:46 andrew-desktop kernel: [974711.031818] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:22:46 andrew-desktop kernel: [974831.030443] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:24:46 andrew-desktop kernel: [974951.031216] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:26:46 andrew-desktop kernel: [975071.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:28:46 andrew-desktop kernel: [975191.031291] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:30:46 andrew-desktop kernel: [975311.030047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:32:46 andrew-desktop kernel: [975431.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:34:46 andrew-desktop kernel: [975551.030049] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:36:46 andrew-desktop kernel: [975671.034379] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:38:46 andrew-desktop kernel: [975791.031332] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:38:59 andrew-desktop pulseaudio[1608]: ratelimit.c: 1054 events suppressed
Oct 14 21:40:46 andrew-desktop kernel: [975911.031333] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 148
Oct 14 21:42:46 andrew-desktop kernel: [976031.031290] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:44:46 andrew-desktop kernel: [976151.034247] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:46:46 andrew-desktop kernel: [976271.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:48:46 andrew-desktop kernel: [976391.030047] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:50:28 andrew-desktop pulseaudio[1608]: ratelimit.c: 979 events suppressed
Oct 14 21:50:46 andrew-desktop kernel: [976511.030874] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 21:52:46 andrew-desktop kernel: [976631.031292] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:54:46 andrew-desktop kernel: [976751.031303] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:56:46 andrew-desktop kernel: [976871.031299] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 21:58:46 andrew-desktop kernel: [976991.031424] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:00:46 andrew-desktop kernel: [977111.030070] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:02:46 andrew-desktop kernel: [977231.034572] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:04:46 andrew-desktop kernel: [977351.031310] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:06:46 andrew-desktop kernel: [977471.030045] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:08:46 andrew-desktop kernel: [977591.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:10:46 andrew-desktop kernel: [977711.031290] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:12:46 andrew-desktop kernel: [977831.030763] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:14:46 andrew-desktop kernel: [977951.030756] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:16:46 andrew-desktop kernel: [978071.030051] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:17:01 andrew-desktop CRON[4659]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 14 22:18:46 andrew-desktop kernel: [978191.031295] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:20:46 andrew-desktop kernel: [978311.034299] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:22:46 andrew-desktop kernel: [978431.031294] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:24:46 andrew-desktop kernel: [978551.031297] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:26:46 andrew-desktop kernel: [978671.031292] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:28:46 andrew-desktop kernel: [978791.031307] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:30:46 andrew-desktop kernel: [978911.031310] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 22:32:17 andrew-desktop dhclient: DHCPREQUEST of 10.0.0.2 on wlan0 to 10.0.0.1 port 67
Oct 14 22:32:17 andrew-desktop dhclient: DHCPACK of 10.0.0.2 from 10.0.0.1
Oct 14 22:32:17 andrew-desktop dhclient: bound to 10.0.0.2 -- renewal in 35343 seconds.
Oct 14 22:32:46 andrew-desktop kernel: [979031.030045] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:34:46 andrew-desktop kernel: [979151.034223] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:36:46 andrew-desktop kernel: [979271.030046] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:38:46 andrew-desktop kernel: [979391.031302] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:39:27 andrew-desktop kernel: [979432.934753] lo: Disabled Privacy Extensions
Oct 14 22:40:46 andrew-desktop kernel: [979511.034199] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:42:46 andrew-desktop kernel: [979631.030044] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:44:46 andrew-desktop kernel: [979751.032850] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:46:46 andrew-desktop kernel: [979871.030119] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:48:46 andrew-desktop kernel: [979991.034537] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:50:46 andrew-desktop kernel: [980111.030077] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:52:46 andrew-desktop kernel: [980231.030049] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:54:46 andrew-desktop kernel: [980351.031301] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 22:56:46 andrew-desktop kernel: [980471.031289] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 22:58:46 andrew-desktop kernel: [980591.031319] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 148
Oct 14 23:00:46 andrew-desktop kernel: [980711.031950] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 148
Oct 14 23:02:46 andrew-desktop kernel: [980831.031718] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 148
Oct 14 23:03:47 andrew-desktop kernel: [980892.900023] usb 1-1: new high speed USB device using ehci_hcd and address 7
Oct 14 23:03:48 andrew-desktop kernel: [980893.120280] hub 1-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:04:06 andrew-desktop kernel: [980911.230027] usb 1-1: new high speed USB device using ehci_hcd and address 8
Oct 14 23:04:06 andrew-desktop kernel: [980911.381488] usb 1-1: configuration #1 chosen from 2 choices
Oct 14 23:04:06 andrew-desktop kernel: [980911.387466] scsi9 : SCSI emulation for USB Mass Storage devices
Oct 14 23:04:06 andrew-desktop kernel: [980911.387617] usb-storage: device found at 8
Oct 14 23:04:06 andrew-desktop kernel: [980911.387620] usb-storage: waiting for device to settle before scanning
Oct 14 23:04:06 andrew-desktop kernel: [980911.780027] usb 4-1: new full speed USB device using uhci_hcd and address 22
Oct 14 23:04:06 andrew-desktop kernel: [980911.910025] usb 4-1: device descriptor read/64, error -71
Oct 14 23:04:07 andrew-desktop kernel: [980912.153682] usb 4-1: device descriptor read/64, error -71
Oct 14 23:04:07 andrew-desktop kernel: [980912.380026] usb 4-1: new full speed USB device using uhci_hcd and address 23
Oct 14 23:04:07 andrew-desktop kernel: [980912.510025] usb 4-1: device descriptor read/64, error -71
Oct 14 23:04:07 andrew-desktop kernel: [980912.750025] usb 4-1: device descriptor read/64, error -71
Oct 14 23:04:07 andrew-desktop kernel: [980912.980042] usb 4-1: new full speed USB device using uhci_hcd and address 24
Oct 14 23:04:08 andrew-desktop kernel: [980913.400018] usb 4-1: device not accepting address 24, error -71
Oct 14 23:04:08 andrew-desktop kernel: [980913.520025] usb 4-1: new full speed USB device using uhci_hcd and address 25
Oct 14 23:04:08 andrew-desktop kernel: [980913.940018] usb 4-1: device not accepting address 25, error -71
Oct 14 23:04:08 andrew-desktop kernel: [980913.940040] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:04:11 andrew-desktop kernel: [980916.380200] usb-storage: device scan complete
Oct 14 23:04:11 andrew-desktop kernel: [980916.387814] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Oct 14 23:04:11 andrew-desktop kernel: [980916.388508] sd 9:0:0:0: Attached scsi generic sg5 type 0
Oct 14 23:04:12 andrew-desktop kernel: [980917.070208] sd 9:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:04:12 andrew-desktop kernel: [980917.070697] sd 9:0:0:0: [sde] Write Protect is off
Oct 14 23:04:12 andrew-desktop kernel: [980917.070702] sd 9:0:0:0: [sde] Mode Sense: 68 00 00 08
Oct 14 23:04:12 andrew-desktop kernel: [980917.070706] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:04:12 andrew-desktop kernel: [980917.072331] sd 9:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:04:12 andrew-desktop kernel: [980917.072823] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:04:12 andrew-desktop kernel: [980917.072831]  sde: sde1
Oct 14 23:04:12 andrew-desktop kernel: [980917.075587] sd 9:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:04:12 andrew-desktop kernel: [980917.076075] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:04:12 andrew-desktop kernel: [980917.076082] sd 9:0:0:0: [sde] Attached SCSI removable disk
Oct 14 23:04:46 andrew-desktop kernel: [980951.032175] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:06:06 andrew-desktop init: tty4 main process (1018) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: tty5 main process (1040) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: tty2 main process (1059) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: tty3 main process (1060) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: tty6 main process (1063) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: cron main process (1108) killed by TERM signal
Oct 14 23:06:06 andrew-desktop init: tty1 main process (1218) killed by TERM signal
Oct 14 23:06:07 andrew-desktop avahi-daemon[903]: Got SIGTERM, quitting.
Oct 14 23:06:07 andrew-desktop kernel: Kernel logging (proc) stopped.
Oct 14 23:06:07 andrew-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="840" x-info="http://www.rsyslog.com"] exiting on signal 15.
Oct 14 23:07:11 andrew-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 14 23:07:11 andrew-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="912" x-info="http://www.rsyslog.com"] (re)start
Oct 14 23:07:11 andrew-desktop rsyslogd: rsyslogd's groupid changed to 103
Oct 14 23:07:14 andrew-desktop rsyslogd: rsyslogd's userid changed to 101
Oct 14 23:07:11 andrew-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] KERNEL supported cpus:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   Intel GenuineIntel
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   AMD AuthenticAMD
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   Centaur CentaurHauls
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] DMI present.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] MTRR default type: uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   00000-9FFFF write-back
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   D0000-DFFFF uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   E0000-EFFFF write-through
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   1 base 100000000 mask F80000000 write-back
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   2 base 180000000 mask FE0000000 write-back
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   4 base 0DDE00000 mask FFFE00000 uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   5 base 0DE000000 mask FFE000000 uncachable
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   6 disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   7 disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] e820 update range: 00000000dde00000 - 0000000100000000 (usable) ==> (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] last_pfn = 0xddd80 max_arch_pfn = 0x400000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] modified physical RAM map:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  modified: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ddd80000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  0000000000 - 00ddc00000 page 2M
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  00ddc00000 - 00ddd80000 page 4k
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to ddd80000 @ 10000-16000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  0100000000 - 01a0000000 page 2M
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to 1a0000000 @ 14000-1c000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] RAMDISK: 377fb000 - 37fef3a7
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: RSDP 00000000000fb6c0 00014 (v00 ACPIAM)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: RSDT 00000000ddd80000 00044 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: FACP 00000000ddd80200 00084 (v02 A_M_I_ OEMFACP  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: DSDT 00000000ddd80440 08DAC (v01  A1355 A1355000 00000000 INTL 20060113)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: FACS 00000000ddd8e000 00040
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: APIC 00000000ddd80390 0006C (v01 A_M_I_ OEMAPIC  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: MCFG 00000000ddd80400 0003C (v01 A_M_I_ OEMMCFG  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: OEMB 00000000ddd8e040 00089 (v01 A_M_I_ AMI_OEM  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: HPET 00000000ddd891f0 00038 (v01 A_M_I_ OEMHPET  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: GSCI 00000000ddd8e0d0 02024 (v01 A_M_I_ GMCHSCI  05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: SSDT 00000000ddd90510 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: SLIC 00000000ddd89230 00176 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] No NUMA configuration found
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Faking a node at 0000000000000000-00000001a0000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000001a0000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   NODE_DATA [0000000000017000 - 000000000001bfff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   bootmap [000000000001c000 -  000000000004ffff] pages 34
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 01a0000000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #3 [00377fb000 - 0037fef3a7]          RAMDISK ==> [00377fb000 - 0037fef3a7]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #5 [0001a2d000 - 0001a2d27c]              BRK ==> [0001a2d000 - 0001a2d27c]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   #7 [0000014000 - 0000017000]          PGTABLE ==> [0000014000 - 0000017000]
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0005bfffff] PMD -> [ffff880028600000-ffff88002dbfffff] on node 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x001a0000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000ddd80
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x001a0000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] On node 0 totalpages: 1563919
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA zone: 106 pages reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA zone: 3821 pages, LIFO batch:0
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   DMA32 zone: 890296 pages, LIFO batch:31
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   Normal zone: 8960 pages used for memmap
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000]   Normal zone: 646400 pages, LIFO batch:31
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] nr_irqs_gsi: 24
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd80000 - 00000000ddd8e000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd8e000 - 00000000dddd0000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dddd0000 - 00000000e0000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fee00000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ee00000)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1540517
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Policy zone: Normal
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Initializing CPU#0
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Checking aperture...
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] No AGP bridge found
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Memory: 6082276k/6815744k available (5419k kernel code, 560068k absent, 173400k reserved, 2974k data, 872k init)
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] console [tty0] enabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] allocated 62914560 bytes of page_cgroup
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] hpet clockevent registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Oct 14 23:07:14 andrew-desktop kernel: [    0.000000] Detected 2599.753 MHz processor.
Oct 14 23:07:14 andrew-desktop kernel: [    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5199.50 BogoMIPS (lpj=25997530)
Oct 14 23:07:14 andrew-desktop kernel: [    0.010032] Security Framework initialized
Oct 14 23:07:14 andrew-desktop kernel: [    0.010051] AppArmor: AppArmor initialized
Oct 14 23:07:14 andrew-desktop kernel: [    0.010645] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.015437] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.017742] Mount-cache hash table entries: 256
Oct 14 23:07:14 andrew-desktop kernel: [    0.017900] Initializing cgroup subsys ns
Oct 14 23:07:14 andrew-desktop kernel: [    0.017905] Initializing cgroup subsys cpuacct
Oct 14 23:07:14 andrew-desktop kernel: [    0.017908] Initializing cgroup subsys memory
Oct 14 23:07:14 andrew-desktop kernel: [    0.017916] Initializing cgroup subsys devices
Oct 14 23:07:14 andrew-desktop kernel: [    0.017919] Initializing cgroup subsys freezer
Oct 14 23:07:14 andrew-desktop kernel: [    0.017920] Initializing cgroup subsys net_cls
Oct 14 23:07:14 andrew-desktop kernel: [    0.017942] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:07:14 andrew-desktop kernel: [    0.017943] CPU: L2 cache: 2048K
Oct 14 23:07:14 andrew-desktop kernel: [    0.017946] CPU 0/0x0 -> Node 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.017948] CPU: Physical Processor ID: 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.017949] CPU: Processor Core ID: 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.017952] mce: CPU supports 6 MCE banks
Oct 14 23:07:14 andrew-desktop kernel: [    0.017959] CPU0: Thermal monitoring enabled (TM2)
Oct 14 23:07:14 andrew-desktop kernel: [    0.017963] using mwait in idle threads.
Oct 14 23:07:14 andrew-desktop kernel: [    0.017965] Performance Events: Core2 events, Intel PMU driver.
Oct 14 23:07:14 andrew-desktop kernel: [    0.017970] ... version:                2
Oct 14 23:07:14 andrew-desktop kernel: [    0.017971] ... bit width:              40
Oct 14 23:07:14 andrew-desktop kernel: [    0.017972] ... generic registers:      2
Oct 14 23:07:14 andrew-desktop kernel: [    0.017974] ... value mask:             000000ffffffffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.017975] ... max period:             000000007fffffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.017976] ... fixed-purpose events:   3
Oct 14 23:07:14 andrew-desktop kernel: [    0.017977] ... event mask:             0000000700000003
Oct 14 23:07:14 andrew-desktop kernel: [    0.020427] ACPI: Core revision 20090903
Oct 14 23:07:14 andrew-desktop kernel: [    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 14 23:07:14 andrew-desktop kernel: [    0.040011] ftrace: allocating 22538 entries in 89 pages
Oct 14 23:07:14 andrew-desktop kernel: [    0.050054] Setting APIC routing to flat
Oct 14 23:07:14 andrew-desktop kernel: [    0.050363] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 14 23:07:14 andrew-desktop kernel: [    0.164044] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
Oct 14 23:07:14 andrew-desktop kernel: [    0.170000] Booting processor 1 APIC 0x1 ip 0x6000
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] Initializing CPU#1
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU: L2 cache: 2048K
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Oct 14 23:07:14 andrew-desktop kernel: [    0.320080] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:07:14 andrew-desktop kernel: [    0.320087] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 14 23:07:14 andrew-desktop kernel: [    0.330016] Brought up 2 CPUs
Oct 14 23:07:14 andrew-desktop kernel: [    0.330018] Total of 2 processors activated (10399.50 BogoMIPS).
Oct 14 23:07:14 andrew-desktop kernel: [    0.330466] CPU0 attaching sched-domain:
Oct 14 23:07:14 andrew-desktop kernel: [    0.330469]  domain 0: span 0-1 level MC
Oct 14 23:07:14 andrew-desktop kernel: [    0.330471]   groups: 0 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.330476] CPU1 attaching sched-domain:
Oct 14 23:07:14 andrew-desktop kernel: [    0.330478]  domain 0: span 0-1 level MC
Oct 14 23:07:14 andrew-desktop kernel: [    0.330480]   groups: 1 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] devtmpfs: initialized
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] regulator: core version 0.5
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] Time:  3:07:02  Date: 10/15/10
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] NET: Registered protocol family 16
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] Trying to unpack rootfs image as initramfs...
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] ACPI: bus type pci registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] PCI: Not using MMCONFIG.
Oct 14 23:07:14 andrew-desktop kernel: [    0.330569] PCI: Using configuration type 1 for base access
Oct 14 23:07:14 andrew-desktop kernel: [    0.340154] bio: create slab <bio-0> at 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.340968] ACPI: EC: Look up EC in DSDT
Oct 14 23:07:14 andrew-desktop kernel: [    0.343685] ACPI: Executed 1 blocks of module-level executable AML code
Oct 14 23:07:14 andrew-desktop kernel: [    0.350062] ACPI: Interpreter enabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.350066] ACPI: (supports S0 S1 S3 S4 S5)
Oct 14 23:07:14 andrew-desktop kernel: [    0.350090] ACPI: Using IOAPIC for interrupt routing
Oct 14 23:07:14 andrew-desktop kernel: [    0.350146] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:07:14 andrew-desktop kernel: [    0.353146] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Oct 14 23:07:14 andrew-desktop kernel: [    0.354949] PCI: Using MMCONFIG at f0000000 - f3ffffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.362538] ACPI Warning: Incorrect checksum in table [OEMB] - 9A, should be 95 (20090903/tbutils-314)
Oct 14 23:07:14 andrew-desktop kernel: [    0.363436] ACPI: No dock devices found.
Oct 14 23:07:14 andrew-desktop kernel: [    0.363577] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 14 23:07:14 andrew-desktop kernel: [    0.363665] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe400000-0xfe7fffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363670] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363674] pci 0000:00:02.0: reg 20 io port: [0xdc00-0xdc07]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363708] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe900000-0xfe9fffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363789] pci 0000:00:1a.0: reg 20 io port: [0xd480-0xd49f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363857] pci 0000:00:1a.1: reg 20 io port: [0xd800-0xd81f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363920] pci 0000:00:1a.2: reg 20 io port: [0xd880-0xd89f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.363986] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe8fb000-0xfe8fb3ff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364043] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.364047] pci 0000:00:1a.7: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.364084] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364121] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.364124] pci 0000:00:1b.0: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.364181] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.364184] pci 0000:00:1c.0: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.364249] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.364252] pci 0000:00:1c.5: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.364301] pci 0000:00:1d.0: reg 20 io port: [0xd000-0xd01f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364367] pci 0000:00:1d.1: reg 20 io port: [0xd080-0xd09f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364431] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364497] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8fa000-0xfe8fa3ff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364549] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.364553] pci 0000:00:1d.7: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.364711] pci 0000:00:1f.2: reg 10 io port: [0xbc00-0xbc07]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364716] pci 0000:00:1f.2: reg 14 io port: [0xb880-0xb883]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364722] pci 0000:00:1f.2: reg 18 io port: [0xb800-0xb807]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364727] pci 0000:00:1f.2: reg 1c io port: [0xb480-0xb483]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364732] pci 0000:00:1f.2: reg 20 io port: [0xb400-0xb40f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364737] pci 0000:00:1f.2: reg 24 io port: [0xb080-0xb08f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364779] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe8f9000-0xfe8f90ff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364792] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364831] pci 0000:00:1f.5: reg 10 io port: [0xcc00-0xcc07]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364836] pci 0000:00:1f.5: reg 14 io port: [0xc880-0xc883]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364841] pci 0000:00:1f.5: reg 18 io port: [0xc800-0xc807]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364846] pci 0000:00:1f.5: reg 1c io port: [0xc480-0xc483]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364850] pci 0000:00:1f.5: reg 20 io port: [0xc400-0xc40f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364855] pci 0000:00:1f.5: reg 24 io port: [0xc080-0xc08f]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364927] pci 0000:02:00.0: reg 10 32bit mmio: [0xfebf0000-0xfebfffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.364991] pci 0000:02:00.0: PME# supported from D0 D3hot
Oct 14 23:07:14 andrew-desktop kernel: [    0.364995] pci 0000:02:00.0: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.365040] pci 0000:00:1c.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365102] pci 0000:01:00.0: reg 10 io port: [0xe800-0xe8ff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365123] pci 0000:01:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365144] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365188] pci 0000:01:00.0: supports D1 D2
Oct 14 23:07:14 andrew-desktop kernel: [    0.365189] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
Oct 14 23:07:14 andrew-desktop kernel: [    0.365194] pci 0000:01:00.0: PME# disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.365246] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365249] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365295] pci 0000:00:1e.0: transparent bridge
Oct 14 23:07:14 andrew-desktop kernel: [    0.365318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Oct 14 23:07:14 andrew-desktop kernel: [    0.365603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Oct 14 23:07:14 andrew-desktop kernel: [    0.380835] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.380936] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381040] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381140] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381240] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381337] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381436] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381536] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:07:14 andrew-desktop kernel: [    0.381632] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 14 23:07:14 andrew-desktop kernel: [    0.381643] vgaarb: loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.381746] SCSI subsystem initialized
Oct 14 23:07:14 andrew-desktop kernel: [    0.381833] libata version 3.00 loaded.
Oct 14 23:07:14 andrew-desktop kernel: [    0.381890] usbcore: registered new interface driver usbfs
Oct 14 23:07:14 andrew-desktop kernel: [    0.381899] usbcore: registered new interface driver hub
Oct 14 23:07:14 andrew-desktop kernel: [    0.381923] usbcore: registered new device driver usb
Oct 14 23:07:14 andrew-desktop kernel: [    0.382037] ACPI: WMI: Mapper loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.382039] PCI: Using ACPI for IRQ routing
Oct 14 23:07:14 andrew-desktop kernel: [    0.382183] NetLabel: Initializing
Oct 14 23:07:14 andrew-desktop kernel: [    0.382185] NetLabel:  domain hash size = 128
Oct 14 23:07:14 andrew-desktop kernel: [    0.382186] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 14 23:07:14 andrew-desktop kernel: [    0.382198] NetLabel:  unlabeled traffic allowed by default
Oct 14 23:07:14 andrew-desktop kernel: [    0.382226] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Oct 14 23:07:14 andrew-desktop kernel: [    0.382230] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Oct 14 23:07:14 andrew-desktop kernel: [    0.390126] Switching to clocksource tsc
Oct 14 23:07:14 andrew-desktop kernel: [    0.391588] AppArmor: AppArmor Filesystem Enabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.391605] pnp: PnP ACPI init
Oct 14 23:07:14 andrew-desktop kernel: [    0.391622] ACPI: bus type pnp registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.395187] pnp: PnP ACPI: found 16 devices
Oct 14 23:07:14 andrew-desktop kernel: [    0.395189] ACPI: ACPI bus type pnp unregistered
Oct 14 23:07:14 andrew-desktop kernel: [    0.395201] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395208] system 00:07: ioport range 0x290-0x297 has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395213] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395216] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395218] system 00:08: ioport range 0x500-0x57f has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395220] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395222] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395224] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395226] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395235] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395240] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395242] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395246] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395250] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395252] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395254] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395257] system 00:0f: iomem range 0x100000-0xdddfffff could not be reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.395259] system 00:0f: iomem range 0xf0000000-0xffffffff could not be reserved
Oct 14 23:07:14 andrew-desktop kernel: [    0.399984] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Oct 14 23:07:14 andrew-desktop kernel: [    0.399987] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Oct 14 23:07:14 andrew-desktop kernel: [    0.399991] pci 0000:00:1c.0:   MEM window: 0xfeb00000-0xfebfffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.399995] pci 0000:00:1c.0:   PREFETCH window: 0x000000f4000000-0x000000f41fffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.400000] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
Oct 14 23:07:14 andrew-desktop kernel: [    0.400003] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Oct 14 23:07:14 andrew-desktop kernel: [    0.400007] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.400011] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4200000-0x000000f43fffff
Oct 14 23:07:14 andrew-desktop kernel: [    0.400017] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Oct 14 23:07:14 andrew-desktop kernel: [    0.400018] pci 0000:00:1e.0:   IO window: disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.400022] pci 0000:00:1e.0:   MEM window: disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.400025] pci 0000:00:1e.0:   PREFETCH window: disabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.400036] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Oct 14 23:07:14 andrew-desktop kernel: [    0.400044]   alloc irq_desc for 17 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.400046]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.400052] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:07:14 andrew-desktop kernel: [    0.400056] pci 0000:00:1c.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.400063]   alloc irq_desc for 16 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.400065]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.400067] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:07:14 andrew-desktop kernel: [    0.400070] pci 0000:00:1c.5: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.400076] pci 0000:00:1e.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.400080] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400082] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400084] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400086] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400088] pci_bus 0000:02: resource 2 pref mem [0xf4000000-0xf41fffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400090] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400092] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400094] pci_bus 0000:01: resource 2 pref mem [0xf4200000-0xf43fffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400096] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400097] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:07:14 andrew-desktop kernel: [    0.400130] NET: Registered protocol family 2
Oct 14 23:07:14 andrew-desktop kernel: [    0.400348] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.401941] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.407034] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.407690] TCP: Hash tables configured (established 524288 bind 65536)
Oct 14 23:07:14 andrew-desktop kernel: [    0.407692] TCP reno registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.407817] NET: Registered protocol family 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.407839] pci 0000:00:02.0: Boot video device
Oct 14 23:07:14 andrew-desktop kernel: [    0.408164] Scanning for low memory corruption every 60 seconds
Oct 14 23:07:14 andrew-desktop kernel: [    0.408301] audit: initializing netlink socket (disabled)
Oct 14 23:07:14 andrew-desktop kernel: [    0.408311] type=2000 audit(1287112021.399:1): initialized
Oct 14 23:07:14 andrew-desktop kernel: [    0.416300] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 14 23:07:14 andrew-desktop kernel: [    0.417413] VFS: Disk quotas dquot_6.5.2
Oct 14 23:07:14 andrew-desktop kernel: [    0.417460] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 14 23:07:14 andrew-desktop kernel: [    0.417923] fuse init (API version 7.13)
Oct 14 23:07:14 andrew-desktop kernel: [    0.417986] msgmni has been set to 11879
Oct 14 23:07:14 andrew-desktop kernel: [    0.418161] alg: No test for stdrng (krng)
Oct 14 23:07:14 andrew-desktop kernel: [    0.418204] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 14 23:07:14 andrew-desktop kernel: [    0.418207] io scheduler noop registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.418208] io scheduler anticipatory registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.418210] io scheduler deadline registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.418236] io scheduler cfq registered (default)
Oct 14 23:07:14 andrew-desktop kernel: [    0.418364]   alloc irq_desc for 24 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.418365]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.418374] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Oct 14 23:07:14 andrew-desktop kernel: [    0.418382] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.418486]   alloc irq_desc for 25 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.418487]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.418493] pcieport 0000:00:1c.5: irq 25 for MSI/MSI-X
Oct 14 23:07:14 andrew-desktop kernel: [    0.418499] pcieport 0000:00:1c.5: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.418565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 14 23:07:14 andrew-desktop kernel: [    0.418634] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 14 23:07:14 andrew-desktop kernel: [    0.418747] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Oct 14 23:07:14 andrew-desktop kernel: [    0.418750] ACPI: Power Button [PWRB]
Oct 14 23:07:14 andrew-desktop kernel: [    0.418786] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 14 23:07:14 andrew-desktop kernel: [    0.418788] ACPI: Power Button [PWRF]
Oct 14 23:07:14 andrew-desktop kernel: [    0.419418] ACPI: SSDT 00000000ddd90100 00406 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Oct 14 23:07:14 andrew-desktop kernel: [    0.419761] processor LNXCPU:00: registered as cooling_device0
Oct 14 23:07:14 andrew-desktop kernel: [    0.419793] processor LNXCPU:01: registered as cooling_device1
Oct 14 23:07:14 andrew-desktop kernel: [    0.423508] Linux agpgart interface v0.103
Oct 14 23:07:14 andrew-desktop kernel: [    0.423538] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 14 23:07:14 andrew-desktop kernel: [    0.423638] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:07:14 andrew-desktop kernel: [    0.423944] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:07:14 andrew-desktop kernel: [    0.424779] brd: module loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.425160] loop: module loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.425237] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Oct 14 23:07:14 andrew-desktop kernel: [    0.425329] ata_piix 0000:00:1f.2: version 2.13
Oct 14 23:07:14 andrew-desktop kernel: [    0.425348]   alloc irq_desc for 19 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.425350]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.425356] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.425360] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 14 23:07:14 andrew-desktop kernel: [    0.425408] ata_piix 0000:00:1f.2: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.425489] scsi0 : ata_piix
Oct 14 23:07:14 andrew-desktop kernel: [    0.425552] scsi1 : ata_piix
Oct 14 23:07:14 andrew-desktop kernel: [    0.426853] ata1: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.426858] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.426877] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.426881] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 14 23:07:14 andrew-desktop kernel: [    0.426913] ata_piix 0000:00:1f.5: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.426957] scsi2 : ata_piix
Oct 14 23:07:14 andrew-desktop kernel: [    0.426997] scsi3 : ata_piix
Oct 14 23:07:14 andrew-desktop kernel: [    0.427972] ata3: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.427975] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.428221] Fixed MDIO Bus: probed
Oct 14 23:07:14 andrew-desktop kernel: [    0.428246] PPP generic driver version 2.4.2
Oct 14 23:07:14 andrew-desktop kernel: [    0.428291] tun: Universal TUN/TAP device driver, 1.6
Oct 14 23:07:14 andrew-desktop kernel: [    0.428293] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 14 23:07:14 andrew-desktop kernel: [    0.428372] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 14 23:07:14 andrew-desktop kernel: [    0.428389]   alloc irq_desc for 18 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.428391]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.428396] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:07:14 andrew-desktop kernel: [    0.428420] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.428423] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.428451] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.428476] ehci_hcd 0000:00:1a.7: debug port 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.432380] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Oct 14 23:07:14 andrew-desktop kernel: [    0.432401] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe8fb000
Oct 14 23:07:14 andrew-desktop kernel: [    0.449563] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Oct 14 23:07:14 andrew-desktop kernel: [    0.449684] usb usb1: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.449708] hub 1-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.449716] hub 1-0:1.0: 6 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.449788]   alloc irq_desc for 23 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.449790]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.449796] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:07:14 andrew-desktop kernel: [    0.449820] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.449823] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.449855] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 14 23:07:14 andrew-desktop kernel: [    0.449884] ehci_hcd 0000:00:1d.7: debug port 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.453771] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Oct 14 23:07:14 andrew-desktop kernel: [    0.453788] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8fa000
Oct 14 23:07:14 andrew-desktop kernel: [    0.469541] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 14 23:07:14 andrew-desktop kernel: [    0.469665] usb usb2: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.469688] hub 2-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.469697] hub 2-0:1.0: 6 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.469758] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 14 23:07:14 andrew-desktop kernel: [    0.469774] uhci_hcd: USB Universal Host Controller Interface driver
Oct 14 23:07:14 andrew-desktop kernel: [    0.469819]   alloc irq_desc for 20 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.469821]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.469826] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 14 23:07:14 andrew-desktop kernel: [    0.469836] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.469838] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.469868] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Oct 14 23:07:14 andrew-desktop kernel: [    0.469903] uhci_hcd 0000:00:1a.0: irq 20, io base 0x0000d480
Oct 14 23:07:14 andrew-desktop kernel: [    0.469976] usb usb3: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.469995] hub 3-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470000] hub 3-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.470035]   alloc irq_desc for 21 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.470036]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    0.470040] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Oct 14 23:07:14 andrew-desktop kernel: [    0.470044] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.470047] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.470070] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Oct 14 23:07:14 andrew-desktop kernel: [    0.470098] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d800
Oct 14 23:07:14 andrew-desktop kernel: [    0.470165] usb usb4: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.470184] hub 4-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470190] hub 4-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.470225] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:07:14 andrew-desktop kernel: [    0.470230] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.470233] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.470265] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Oct 14 23:07:14 andrew-desktop kernel: [    0.470287] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d880
Oct 14 23:07:14 andrew-desktop kernel: [    0.470352] usb usb5: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.470370] hub 5-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470375] hub 5-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.470408] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:07:14 andrew-desktop kernel: [    0.470413] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.470415] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.470449] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Oct 14 23:07:14 andrew-desktop kernel: [    0.470472] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d000
Oct 14 23:07:14 andrew-desktop kernel: [    0.470536] usb usb6: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.470557] hub 6-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470562] hub 6-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.470598] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:07:14 andrew-desktop kernel: [    0.470603] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.470605] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.470627] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Oct 14 23:07:14 andrew-desktop kernel: [    0.470648] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d080
Oct 14 23:07:14 andrew-desktop kernel: [    0.470725] usb usb7: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.470746] hub 7-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470753] hub 7-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.470784] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:07:14 andrew-desktop kernel: [    0.470789] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    0.470791] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 14 23:07:14 andrew-desktop kernel: [    0.470813] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Oct 14 23:07:14 andrew-desktop kernel: [    0.470833] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Oct 14 23:07:14 andrew-desktop kernel: [    0.470905] usb usb8: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    0.470923] hub 8-0:1.0: USB hub found
Oct 14 23:07:14 andrew-desktop kernel: [    0.470928] hub 8-0:1.0: 2 ports detected
Oct 14 23:07:14 andrew-desktop kernel: [    0.471004] PNP: No PS/2 controller found. Probing ports directly.
Oct 14 23:07:14 andrew-desktop kernel: [    0.473786] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.473791] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 14 23:07:14 andrew-desktop kernel: [    0.473898] mice: PS/2 mouse device common for all mice
Oct 14 23:07:14 andrew-desktop kernel: [    0.473998] rtc_cmos 00:03: RTC can wake from S4
Oct 14 23:07:14 andrew-desktop kernel: [    0.474032] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Oct 14 23:07:14 andrew-desktop kernel: [    0.474054] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 14 23:07:14 andrew-desktop kernel: [    0.474164] device-mapper: uevent: version 1.0.3
Oct 14 23:07:14 andrew-desktop kernel: [    0.474260] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Oct 14 23:07:14 andrew-desktop kernel: [    0.474309] device-mapper: multipath: version 1.1.0 loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.474311] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 14 23:07:14 andrew-desktop kernel: [    0.474426] cpuidle: using governor ladder
Oct 14 23:07:14 andrew-desktop kernel: [    0.474428] cpuidle: using governor menu
Oct 14 23:07:14 andrew-desktop kernel: [    0.474714] TCP cubic registered
Oct 14 23:07:14 andrew-desktop kernel: [    0.474828] NET: Registered protocol family 10
Oct 14 23:07:14 andrew-desktop kernel: [    0.475193] lo: Disabled Privacy Extensions
Oct 14 23:07:14 andrew-desktop kernel: [    0.475406] NET: Registered protocol family 17
Oct 14 23:07:14 andrew-desktop kernel: [    0.475954] PM: Resume from disk failed.
Oct 14 23:07:14 andrew-desktop kernel: [    0.475966] registered taskstats version 1
Oct 14 23:07:14 andrew-desktop kernel: [    0.476318]   Magic number: 14:530:108
Oct 14 23:07:14 andrew-desktop kernel: [    0.476327] usbmon usbmon4: hash matches
Oct 14 23:07:14 andrew-desktop kernel: [    0.476418] rtc_cmos 00:03: setting system clock to 2010-10-15 03:07:02 UTC (1287112022)
Oct 14 23:07:14 andrew-desktop kernel: [    0.476421] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 14 23:07:14 andrew-desktop kernel: [    0.476422] EDD information not available.
Oct 14 23:07:14 andrew-desktop kernel: [    0.483759] Freeing initrd memory: 8144k freed
Oct 14 23:07:14 andrew-desktop kernel: [    0.769427] usb 1-1: new high speed USB device using ehci_hcd and address 2
Oct 14 23:07:14 andrew-desktop kernel: [    0.790140] ata3: SATA link down (SStatus 0 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    0.800840] ata4: SATA link down (SStatus 0 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    1.041509] usb 1-1: configuration #1 chosen from 2 choices
Oct 14 23:07:14 andrew-desktop kernel: [    1.300064] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    1.300081] ata2.01: SATA link down (SStatus 0 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    1.300094] ata2.01: link offline, clearing class 3 to NONE
Oct 14 23:07:14 andrew-desktop kernel: [    1.310064] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    1.310080] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:07:14 andrew-desktop kernel: [    1.320427] ata2.00: ATAPI: ATAPI   DVD A  DH20A6S, 7P56, max UDMA/100
Oct 14 23:07:14 andrew-desktop kernel: [    1.340379] usb 2-4: new high speed USB device using ehci_hcd and address 3
Oct 14 23:07:14 andrew-desktop kernel: [    1.340431] ata1.00: ATA-8: Hitachi HDT721064SLA360, STDOA31B, max UDMA/133
Oct 14 23:07:14 andrew-desktop kernel: [    1.340437] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:07:14 andrew-desktop kernel: [    1.340599] ata1.01: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
Oct 14 23:07:14 andrew-desktop kernel: [    1.340605] ata1.01: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:07:14 andrew-desktop kernel: [    1.360240] ata2.00: configured for UDMA/100
Oct 14 23:07:14 andrew-desktop kernel: [    1.380432] ata1.00: configured for UDMA/133
Oct 14 23:07:14 andrew-desktop kernel: [    1.420330] ata1.01: configured for UDMA/133
Oct 14 23:07:14 andrew-desktop kernel: [    1.420494] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72106 STDO PQ: 0 ANSI: 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.420676] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    1.420681] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 14 23:07:14 andrew-desktop kernel: [    1.420712] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 23:07:14 andrew-desktop kernel: [    1.420714] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 14 23:07:14 andrew-desktop kernel: [    1.420732] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:07:14 andrew-desktop kernel: [    1.420765] scsi 0:0:1:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.420853] sd 0:0:1:0: Attached scsi generic sg1 type 0
Oct 14 23:07:14 andrew-desktop kernel: [    1.420867]  sda:
Oct 14 23:07:14 andrew-desktop kernel: [    1.421994] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A6S   7P56 PQ: 0 ANSI: 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.427828] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:07:14 andrew-desktop kernel: [    1.427833] Uniform CD-ROM driver Revision: 3.20
Oct 14 23:07:14 andrew-desktop kernel: [    1.427958] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 14 23:07:14 andrew-desktop kernel: [    1.428013] sr 1:0:0:0: Attached scsi generic sg2 type 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.432488]  sda1 sda2 <
Oct 14 23:07:14 andrew-desktop kernel: [    1.432498] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    1.464973]  sda5 >
Oct 14 23:07:14 andrew-desktop kernel: [    1.465042] sd 0:0:1:0: [sdb] Write Protect is off
Oct 14 23:07:14 andrew-desktop kernel: [    1.465046] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Oct 14 23:07:14 andrew-desktop kernel: [    1.465086] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:07:14 andrew-desktop kernel: [    1.465232]  sdb: sdb1 sdb2 <
Oct 14 23:07:14 andrew-desktop kernel: [    1.491153] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    1.492103]  sdb5 >
Oct 14 23:07:14 andrew-desktop kernel: [    1.492119] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 14 23:07:14 andrew-desktop kernel: [    1.492376] sd 0:0:1:0: [sdb] Attached SCSI disk
Oct 14 23:07:14 andrew-desktop kernel: [    1.492392] Freeing unused kernel memory: 872k freed
Oct 14 23:07:14 andrew-desktop kernel: [    1.492726] Write protecting the kernel read-only data: 7692k
Oct 14 23:07:14 andrew-desktop kernel: [    1.504038] udev: starting version 151
Oct 14 23:07:14 andrew-desktop kernel: [    1.570051] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 14 23:07:14 andrew-desktop kernel: [    1.570075] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:07:14 andrew-desktop kernel: [    1.570129] r8169 0000:01:00.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    1.570192]   alloc irq_desc for 26 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    1.570194]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    1.570208] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
Oct 14 23:07:14 andrew-desktop kernel: [    1.570678] eth0: RTL8168b/8111b at 0xffffc90000c76000, 00:24:8c:e6:75:c8, XID 18000000 IRQ 26
Oct 14 23:07:14 andrew-desktop kernel: [    1.573993] Initializing USB Mass Storage driver...
Oct 14 23:07:14 andrew-desktop kernel: [    1.575528] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 14 23:07:14 andrew-desktop kernel: [    1.575643] usb-storage: device found at 2
Oct 14 23:07:14 andrew-desktop kernel: [    1.575645] usb-storage: waiting for device to settle before scanning
Oct 14 23:07:14 andrew-desktop kernel: [    1.575666] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 14 23:07:14 andrew-desktop kernel: [    1.575769] usbcore: registered new interface driver usb-storage
Oct 14 23:07:14 andrew-desktop kernel: [    1.575770] USB Mass Storage support registered.
Oct 14 23:07:14 andrew-desktop kernel: [    1.578140] usb-storage: device found at 3
Oct 14 23:07:14 andrew-desktop kernel: [    1.578143] usb-storage: waiting for device to settle before scanning
Oct 14 23:07:14 andrew-desktop kernel: [    1.670023] usb 2-6: new high speed USB device using ehci_hcd and address 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.821233] usb 2-6: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    1.821455] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 14 23:07:14 andrew-desktop kernel: [    1.821596] usb-storage: device found at 5
Oct 14 23:07:14 andrew-desktop kernel: [    1.821597] usb-storage: waiting for device to settle before scanning
Oct 14 23:07:14 andrew-desktop kernel: [    2.028338] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 14 23:07:14 andrew-desktop kernel: [    2.100026] usb 4-1: new full speed USB device using uhci_hcd and address 2
Oct 14 23:07:14 andrew-desktop kernel: [    2.230020] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    2.470028] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    2.700024] usb 4-1: new full speed USB device using uhci_hcd and address 3
Oct 14 23:07:14 andrew-desktop kernel: [    2.830032] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    3.070021] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    3.300024] usb 4-1: new full speed USB device using uhci_hcd and address 4
Oct 14 23:07:14 andrew-desktop kernel: [    3.720016] usb 4-1: device not accepting address 4, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    3.840028] usb 4-1: new full speed USB device using uhci_hcd and address 5
Oct 14 23:07:14 andrew-desktop kernel: [    3.966112] Adding 17844216k swap on /dev/sda5.  Priority:-1 extents:1 across:17844216k 
Oct 14 23:07:14 andrew-desktop kernel: [    4.261261] usb 4-1: device not accepting address 5, error -71
Oct 14 23:07:14 andrew-desktop kernel: [    4.261279] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:07:14 andrew-desktop kernel: [    4.405392] udev: starting version 151
Oct 14 23:07:14 andrew-desktop kernel: [    4.540077] usb 7-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:07:14 andrew-desktop kernel: [    4.720233] usb 7-1: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    5.000028] usb 8-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:07:14 andrew-desktop kernel: [    5.035939] type=1505 audit(1287112027.053:2):  operation="profile_load" pid=582 name="/sbin/dhclient3"
Oct 14 23:07:14 andrew-desktop kernel: [    5.036564] type=1505 audit(1287112027.053:3):  operation="profile_load" pid=582 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:07:14 andrew-desktop kernel: [    5.036844] type=1505 audit(1287112027.053:4):  operation="profile_load" pid=582 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:07:14 andrew-desktop kernel: [    5.183455] usb 8-1: configuration #1 chosen from 1 choice
Oct 14 23:07:14 andrew-desktop kernel: [    5.245362] usbcore: registered new interface driver hiddev
Oct 14 23:07:14 andrew-desktop kernel: [    5.261483] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3
Oct 14 23:07:14 andrew-desktop kernel: [    5.261581] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
Oct 14 23:07:14 andrew-desktop kernel: [    5.276717] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
Oct 14 23:07:14 andrew-desktop kernel: [    5.276794] generic-usb 0003:046D:C312.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input0
Oct 14 23:07:14 andrew-desktop kernel: [    5.320461] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input5
Oct 14 23:07:14 andrew-desktop kernel: [    5.320660] generic-usb 0003:046D:C312.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input1
Oct 14 23:07:14 andrew-desktop kernel: [    5.320697] usbcore: registered new interface driver usbhid
Oct 14 23:07:14 andrew-desktop kernel: [    5.320699] usbhid: v2.6:USB HID core driver
Oct 14 23:07:14 andrew-desktop kernel: [    5.417733] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Oct 14 23:07:14 andrew-desktop kernel: [    5.427452] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Oct 14 23:07:14 andrew-desktop kernel: [    5.428003] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Oct 14 23:07:14 andrew-desktop kernel: [    5.436135] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:07:14 andrew-desktop kernel: [    5.436361] 
Oct 14 23:07:14 andrew-desktop kernel: [    5.436361] 
Oct 14 23:07:14 andrew-desktop kernel: [    5.436362] === pAd = ffffc90006382000, size = 627064 ===
Oct 14 23:07:14 andrew-desktop kernel: [    5.436362] 
Oct 14 23:07:14 andrew-desktop kernel: [    5.436364] <-- RTMPAllocAdapterBlock, Status=0
Oct 14 23:07:14 andrew-desktop kernel: [    5.436393] rt2860 0000:02:00.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    5.450342] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Oct 14 23:07:14 andrew-desktop kernel: [    5.561564] [drm] Initialized drm 1.1.0 20060810
Oct 14 23:07:14 andrew-desktop kernel: [    5.920208] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:07:14 andrew-desktop kernel: [    5.920212] i915 0000:00:02.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    5.933175] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Oct 14 23:07:14 andrew-desktop kernel: [    5.933178] [drm] MTRR allocation failed.  Graphics performance may suffer.
Oct 14 23:07:14 andrew-desktop kernel: [    5.933239]   alloc irq_desc for 27 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    5.933240]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    5.933248] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Oct 14 23:07:14 andrew-desktop kernel: [    5.933254] [drm] set up 31M of stolen space
Oct 14 23:07:14 andrew-desktop kernel: [    5.975029] parport_pc 00:06: reported by Plug and Play ACPI
Oct 14 23:07:14 andrew-desktop kernel: [    5.975137] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct 14 23:07:14 andrew-desktop kernel: [    6.037863] lp: driver loaded but no devices found
Oct 14 23:07:14 andrew-desktop kernel: [    6.041013] ppdev: user-space parallel port driver
Oct 14 23:07:14 andrew-desktop kernel: [    6.064385] lp0: using parport0 (interrupt-driven).
Oct 14 23:07:14 andrew-desktop kernel: [    6.268436] fb0: inteldrmfb frame buffer device
Oct 14 23:07:14 andrew-desktop kernel: [    6.268438] registered panic notifier
Oct 14 23:07:14 andrew-desktop kernel: [    6.268536] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 14 23:07:14 andrew-desktop kernel: [    6.570209] usb-storage: device scan complete
Oct 14 23:07:14 andrew-desktop kernel: [    6.570247] usb-storage: device scan complete
Oct 14 23:07:14 andrew-desktop kernel: [    6.570711] scsi 5:0:0:0: Direct-Access     WD       5000AAV External 1.75 PQ: 0 ANSI: 4
Oct 14 23:07:14 andrew-desktop kernel: [    6.577566] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Oct 14 23:07:14 andrew-desktop kernel: [    6.579080] sd 4:0:0:0: Attached scsi generic sg3 type 0
Oct 14 23:07:14 andrew-desktop kernel: [    6.580426] sd 4:0:0:0: [sdc] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    6.580441] sd 5:0:0:0: Attached scsi generic sg4 type 0
Oct 14 23:07:14 andrew-desktop kernel: [    6.580919] sd 4:0:0:0: [sdc] Write Protect is off
Oct 14 23:07:14 andrew-desktop kernel: [    6.580921] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
Oct 14 23:07:14 andrew-desktop kernel: [    6.580924] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.582439] sd 5:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    6.582940] sd 5:0:0:0: [sdd] Write Protect is off
Oct 14 23:07:14 andrew-desktop kernel: [    6.582943] sd 5:0:0:0: [sdd] Mode Sense: 23 00 00 00
Oct 14 23:07:14 andrew-desktop kernel: [    6.582945] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.584179] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.584216]  sdd:
Oct 14 23:07:14 andrew-desktop kernel: [    6.590062] sd 4:0:0:0: [sdc] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    6.590548] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.590595]  sdc: sdd1
Oct 14 23:07:14 andrew-desktop kernel: [    6.601191] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.601232] sd 5:0:0:0: [sdd] Attached SCSI disk
Oct 14 23:07:14 andrew-desktop kernel: [    6.821374] usb-storage: device scan complete
Oct 14 23:07:14 andrew-desktop kernel: [    6.821860] scsi 6:0:0:0: Direct-Access     WD       15EADS External  1.75 PQ: 0 ANSI: 4
Oct 14 23:07:14 andrew-desktop kernel: [    6.822671] sd 6:0:0:0: Attached scsi generic sg5 type 0
Oct 14 23:07:14 andrew-desktop kernel: [    6.823233] sd 6:0:0:0: [sde] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Oct 14 23:07:14 andrew-desktop kernel: [    6.823747] sd 6:0:0:0: [sde] Write Protect is off
Oct 14 23:07:14 andrew-desktop kernel: [    6.823750] sd 6:0:0:0: [sde] Mode Sense: 23 00 00 00
Oct 14 23:07:14 andrew-desktop kernel: [    6.823752] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.824963] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.825009]  sde: sde1
Oct 14 23:07:14 andrew-desktop kernel: [    6.827335] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    6.827375] sd 6:0:0:0: [sde] Attached SCSI disk
Oct 14 23:07:14 andrew-desktop kernel: [    7.551164]  sdc1
Oct 14 23:07:14 andrew-desktop kernel: [    7.552760] sd 4:0:0:0: [sdc] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:07:14 andrew-desktop kernel: [    7.553414] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:07:14 andrew-desktop kernel: [    7.553456] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Oct 14 23:07:14 andrew-desktop kernel: [    7.646654] vga16fb: initializing
Oct 14 23:07:14 andrew-desktop kernel: [    7.646657] vga16fb: mapped to 0xffff8800000a0000
Oct 14 23:07:14 andrew-desktop kernel: [    7.646660] vga16fb: not registering due to another framebuffer present
Oct 14 23:07:14 andrew-desktop kernel: [    8.414019] Console: switching to colour frame buffer device 210x65
Oct 14 23:07:14 andrew-desktop kernel: [    8.432658]   alloc irq_desc for 22 on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    8.432661]   alloc kstat_irqs on node -1
Oct 14 23:07:14 andrew-desktop kernel: [    8.432668] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 14 23:07:14 andrew-desktop kernel: [    8.432716] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 14 23:07:14 andrew-desktop kernel: [    8.849349] hda_codec: ALC887: BIOS auto-probing.
Oct 14 23:07:14 andrew-desktop kernel: [    8.850806] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Oct 14 23:07:15 andrew-desktop gdm-binary[942]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Successfully dropped root privileges.
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: avahi-daemon 0.6.25 starting up.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  starting...
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  Trying to start the modem-manager...
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Successfully called chroot().
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Successfully dropped remaining capabilities.
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: No service file found in /etc/avahi/services.
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Network interface enumeration completed.
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Registering HINFO record with values 'X86_64'/'LINUX'.
Oct 14 23:07:16 andrew-desktop avahi-daemon[952]: Server startup complete. Host name is andrew-desktop.local. Local service cookie is 674663101.
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0)
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Oct 14 23:07:16 andrew-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:07:16 andrew-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (32864544) ... get_connections.
Oct 14 23:07:16 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (32864544) ... get_connections (managed=false): return empty list.
Oct 14 23:07:16 andrew-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt2860')
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): now managed
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): bringing up device.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): preparing device.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Oct 14 23:07:16 andrew-desktop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): carrier is OFF
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): now managed
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): bringing up device.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): preparing device.
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Oct 14 23:07:16 andrew-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0
Oct 14 23:07:16 andrew-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  Trying to start the supplicant...
Oct 14 23:07:16 andrew-desktop kernel: [   14.691430] RX DESC ffff8800dd82e000  size = 2048
Oct 14 23:07:16 andrew-desktop kernel: [   14.691614] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 14 23:07:16 andrew-desktop kernel: [   14.694769] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Oct 14 23:07:16 andrew-desktop kernel: [   14.694771] 1. Phy Mode = 0
Oct 14 23:07:16 andrew-desktop kernel: [   14.694772] 2. Phy Mode = 0
Oct 14 23:07:16 andrew-desktop kernel: [   14.713208] 3. Phy Mode = 0
Oct 14 23:07:16 andrew-desktop kernel: [   14.715325] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 14 23:07:16 andrew-desktop kernel: [   14.715327] MCS Set = 00 00 00 00 00
Oct 14 23:07:16 andrew-desktop kernel: [   14.716896] <==== RTMPInitialize, Status=0
Oct 14 23:07:16 andrew-desktop kernel: [   14.716960] 0x1300 = 00073200
Oct 14 23:07:16 andrew-desktop kernel: [   14.719772] r8169: eth0: link down
Oct 14 23:07:16 andrew-desktop kernel: [   14.720892] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  modem-manager is now available
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Oct 14 23:07:16 andrew-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Oct 14 23:07:16 andrew-desktop modem-manager: Loaded plugin Novatel
Oct 14 23:07:16 andrew-desktop kernel: [   14.963232] type=1505 audit(1287112036.983:5):  operation="profile_load" pid=976 name="/usr/share/gdm/guest-session/Xsession"
Oct 14 23:07:16 andrew-desktop kernel: [   14.964781] type=1505 audit(1287112036.983:6):  operation="profile_replace" pid=977 name="/sbin/dhclient3"
Oct 14 23:07:16 andrew-desktop kernel: [   14.965301] type=1505 audit(1287112036.983:7):  operation="profile_replace" pid=977 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:07:16 andrew-desktop kernel: [   14.965586] type=1505 audit(1287112036.983:8):  operation="profile_replace" pid=977 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Nokia
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin ZTE
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin AnyData
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin MotoC
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Option
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Sierra
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Huawei
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Gobi
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Ericsson MBM
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Longcheer
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Generic
Oct 14 23:07:17 andrew-desktop modem-manager: Loaded plugin Option High-Speed
Oct 14 23:07:17 andrew-desktop kernel: [   15.135273] type=1505 audit(1287112037.154:9):  operation="profile_load" pid=978 name="/usr/bin/evince"
Oct 14 23:07:17 andrew-desktop kernel: [   15.142086] type=1505 audit(1287112037.164:10):  operation="profile_load" pid=978 name="/usr/bin/evince-previewer"
Oct 14 23:07:17 andrew-desktop kernel: [   15.146132] type=1505 audit(1287112037.164:11):  operation="profile_load" pid=978 name="/usr/bin/evince-thumbnailer"
Oct 14 23:07:17 andrew-desktop kernel: [   15.157419] type=1505 audit(1287112037.173:12):  operation="profile_load" pid=1043 name="/usr/lib/cups/backend/cups-pdf"
Oct 14 23:07:17 andrew-desktop kernel: [   15.158047] type=1505 audit(1287112037.173:13):  operation="profile_load" pid=1043 name="/usr/sbin/cupsd"
Oct 14 23:07:17 andrew-desktop gdm-binary[942]: WARNING: Unable to find users: no seat-id found
Oct 14 23:07:17 andrew-desktop kernel: [   15.270531] type=1505 audit(1287112037.293:14):  operation="profile_load" pid=1045 name="/usr/sbin/tcpdump"
Oct 14 23:07:17 andrew-desktop gdm-simple-slave[1046]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:07:17 andrew-desktop init: plymouth main process (360) killed by SEGV signal
Oct 14 23:07:18 andrew-desktop avahi-daemon[952]: Registering new address record for fe80::222:43ff:fe64:80ab on wlan0.*.
Oct 14 23:07:18 andrew-desktop cron[1093]: (CRON) INFO (pidfile fd = 3)
Oct 14 23:07:18 andrew-desktop acpid: starting up with proc fs
Oct 14 23:07:18 andrew-desktop init: apport pre-start process (1088) terminated with status 1
Oct 14 23:07:18 andrew-desktop init: apport post-stop process (1102) terminated with status 1
Oct 14 23:07:18 andrew-desktop cron[1107]: (CRON) STARTUP (fork ok)
Oct 14 23:07:18 andrew-desktop cron[1107]: (CRON) INFO (Running @reboot jobs)
Oct 14 23:07:18 andrew-desktop acpid: 36 rules loaded
Oct 14 23:07:18 andrew-desktop acpid: waiting for events: event logging is off
Oct 14 23:07:18 andrew-desktop anacron[1119]: Anacron 2.3 started on 2010-10-14
Oct 14 23:07:18 andrew-desktop anacron[1119]: Normal exit (0 jobs run)
Oct 14 23:07:21 andrew-desktop anacron[1255]: Anacron 2.3 started on 2010-10-14
Oct 14 23:07:21 andrew-desktop anacron[1255]: Normal exit (0 jobs run)
Oct 14 23:07:21 andrew-desktop kernel: [   19.350190] CPU0 attaching NULL sched-domain.
Oct 14 23:07:21 andrew-desktop kernel: [   19.350195] CPU1 attaching NULL sched-domain.
Oct 14 23:07:21 andrew-desktop kernel: [   19.501427] CPU0 attaching sched-domain:
Oct 14 23:07:21 andrew-desktop kernel: [   19.501429]  domain 0: span 0-1 level MC
Oct 14 23:07:21 andrew-desktop kernel: [   19.501431]   groups: 0 1
Oct 14 23:07:21 andrew-desktop kernel: [   19.501435] CPU1 attaching sched-domain:
Oct 14 23:07:21 andrew-desktop kernel: [   19.501437]  domain 0: span 0-1 level MC
Oct 14 23:07:21 andrew-desktop kernel: [   19.501438]   groups: 1 0
Oct 14 23:07:21 andrew-desktop kernel: [   19.941295] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 23:07:22 andrew-desktop init: plymouth-stop pre-start process (1285) terminated with status 1
Oct 14 23:07:22 andrew-desktop gdm-session-worker[1290]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Sucessfully called chroot.
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Sucessfully dropped privileges.
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Sucessfully limited resources.
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Running.
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Watchdog thread running.
Oct 14 23:07:22 andrew-desktop rtkit-daemon[1297]: Canary thread running.
Oct 14 23:07:23 andrew-desktop polkitd[1301]: started daemon version 0.96 using authority implementation `local' version `0.96'
Oct 14 23:07:23 andrew-desktop kernel: [   21.161263] usb 4-1: new full speed USB device using uhci_hcd and address 6
Oct 14 23:07:23 andrew-desktop kernel: [   21.290068] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:23 andrew-desktop rtkit-daemon[1297]: Sucessfully made thread 1295 of process 1295 (n/a) owned by '114' high priority at nice level -11.
Oct 14 23:07:23 andrew-desktop rtkit-daemon[1297]: Supervising 1 threads of 1 processes of 1 users.
Oct 14 23:07:23 andrew-desktop kernel: [   21.530030] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:23 andrew-desktop kernel: [   21.760021] usb 4-1: new full speed USB device using uhci_hcd and address 7
Oct 14 23:07:23 andrew-desktop kernel: [   21.890016] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:24 andrew-desktop kernel: [   22.130014] usb 4-1: device descriptor read/64, error -71
Oct 14 23:07:24 andrew-desktop kernel: [   22.360016] usb 4-1: new full speed USB device using uhci_hcd and address 8
Oct 14 23:07:24 andrew-desktop kernel: [   22.780021] usb 4-1: device not accepting address 8, error -71
Oct 14 23:07:24 andrew-desktop kernel: [   22.900021] usb 4-1: new full speed USB device using uhci_hcd and address 9
Oct 14 23:07:25 andrew-desktop kernel: [   23.320014] usb 4-1: device not accepting address 9, error -71
Oct 14 23:07:25 andrew-desktop kernel: [   23.320033] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:07:25 andrew-desktop rtkit-daemon[1297]: Sucessfully made thread 1302 of process 1295 (n/a) owned by '114' RT at priority 5.
Oct 14 23:07:25 andrew-desktop rtkit-daemon[1297]: Supervising 2 threads of 1 processes of 1 users.
Oct 14 23:07:25 andrew-desktop rtkit-daemon[1297]: Sucessfully made thread 1336 of process 1295 (n/a) owned by '114' RT at priority 5.
Oct 14 23:07:25 andrew-desktop rtkit-daemon[1297]: Supervising 3 threads of 1 processes of 1 users.
Oct 14 23:07:25 andrew-desktop anacron[1363]: Anacron 2.3 started on 2010-10-14
Oct 14 23:07:25 andrew-desktop anacron[1363]: Normal exit (0 jobs run)
Oct 14 23:07:25 andrew-desktop kernel: [   23.654579] CPU0 attaching NULL sched-domain.
Oct 14 23:07:25 andrew-desktop kernel: [   23.654584] CPU1 attaching NULL sched-domain.
Oct 14 23:07:25 andrew-desktop kernel: [   23.720113] CPU0 attaching sched-domain:
Oct 14 23:07:25 andrew-desktop kernel: [   23.720119]  domain 0: span 0-1 level MC
Oct 14 23:07:25 andrew-desktop kernel: [   23.720123]   groups: 0 1
Oct 14 23:07:25 andrew-desktop kernel: [   23.720132] CPU1 attaching sched-domain:
Oct 14 23:07:25 andrew-desktop kernel: [   23.720136]  domain 0: span 0-1 level MC
Oct 14 23:07:25 andrew-desktop kernel: [   23.720139]   groups: 1 0
Oct 14 23:07:25 andrew-desktop wpa_supplicant[962]: No network configuration found for the current AP
Oct 14 23:07:25 andrew-desktop wpa_supplicant[962]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:07:25 andrew-desktop wpa_supplicant[962]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:07:25 andrew-desktop kernel: [   23.741119] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct 14 23:07:25 andrew-desktop wpa_supplicant[962]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:07:25 andrew-desktop wpa_supplicant[962]: last message repeated 2 times
Oct 14 23:07:25 andrew-desktop kernel: [   23.742216] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct 14 23:07:26 andrew-desktop gdm-simple-greeter[1287]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Oct 14 23:07:27 andrew-desktop kernel: [   25.080009] wlan0: no IPv6 routers present
Oct 14 23:07:27 andrew-desktop acpid: client connected from 1415[108:114]
Oct 14 23:07:27 andrew-desktop acpid: 1 client rule loaded
Oct 14 23:07:28 andrew-desktop gdm-session-worker[1290]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct 14 23:07:32 andrew-desktop gnome-session[1192]: WARNING: Client '/org/gnome/SessionManager/Client2' failed to reply before timeout
Oct 14 23:07:42 andrew-desktop kernel: [   39.987242] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:07:50 andrew-desktop kernel: Kernel logging (proc) stopped.
Oct 14 23:08:43 andrew-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 14 23:08:43 andrew-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="767" x-info="http://www.rsyslog.com"] (re)start
Oct 14 23:08:43 andrew-desktop rsyslogd: rsyslogd's groupid changed to 103
Oct 14 23:08:44 andrew-desktop rsyslogd: rsyslogd's userid changed to 101
Oct 14 23:08:43 andrew-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] KERNEL supported cpus:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   Intel GenuineIntel
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   AMD AuthenticAMD
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   Centaur CentaurHauls
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] DMI present.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] MTRR default type: uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   00000-9FFFF write-back
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   D0000-DFFFF uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   E0000-EFFFF write-through
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   1 base 100000000 mask F80000000 write-back
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   2 base 180000000 mask FE0000000 write-back
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   4 base 0DDE00000 mask FFFE00000 uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   5 base 0DE000000 mask FFE000000 uncachable
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   6 disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   7 disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] e820 update range: 00000000dde00000 - 0000000100000000 (usable) ==> (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] last_pfn = 0xddd80 max_arch_pfn = 0x400000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] modified physical RAM map:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  modified: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ddd80000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  0000000000 - 00ddc00000 page 2M
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  00ddc00000 - 00ddd80000 page 4k
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to ddd80000 @ 10000-16000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  0100000000 - 01a0000000 page 2M
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to 1a0000000 @ 14000-1c000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] RAMDISK: 377fb000 - 37fef3a7
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: RSDP 00000000000fb6c0 00014 (v00 ACPIAM)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: RSDT 00000000ddd80000 00044 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: FACP 00000000ddd80200 00084 (v02 A_M_I_ OEMFACP  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: DSDT 00000000ddd80440 08DAC (v01  A1355 A1355000 00000000 INTL 20060113)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: FACS 00000000ddd8e000 00040
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: APIC 00000000ddd80390 0006C (v01 A_M_I_ OEMAPIC  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: MCFG 00000000ddd80400 0003C (v01 A_M_I_ OEMMCFG  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: OEMB 00000000ddd8e040 00089 (v01 A_M_I_ AMI_OEM  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: HPET 00000000ddd891f0 00038 (v01 A_M_I_ OEMHPET  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: GSCI 00000000ddd8e0d0 02024 (v01 A_M_I_ GMCHSCI  05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: SSDT 00000000ddd90510 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: SLIC 00000000ddd89230 00176 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] No NUMA configuration found
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Faking a node at 0000000000000000-00000001a0000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000001a0000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   NODE_DATA [0000000000017000 - 000000000001bfff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   bootmap [000000000001c000 -  000000000004ffff] pages 34
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 01a0000000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #3 [00377fb000 - 0037fef3a7]          RAMDISK ==> [00377fb000 - 0037fef3a7]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #5 [0001a2d000 - 0001a2d27c]              BRK ==> [0001a2d000 - 0001a2d27c]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   #7 [0000014000 - 0000017000]          PGTABLE ==> [0000014000 - 0000017000]
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0005bfffff] PMD -> [ffff880028600000-ffff88002dbfffff] on node 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x001a0000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000ddd80
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x001a0000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] On node 0 totalpages: 1563919
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA zone: 106 pages reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA zone: 3821 pages, LIFO batch:0
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   DMA32 zone: 890296 pages, LIFO batch:31
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   Normal zone: 8960 pages used for memmap
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000]   Normal zone: 646400 pages, LIFO batch:31
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] nr_irqs_gsi: 24
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd80000 - 00000000ddd8e000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd8e000 - 00000000dddd0000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dddd0000 - 00000000e0000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fee00000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ee00000)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1540517
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Policy zone: Normal
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Initializing CPU#0
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Checking aperture...
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] No AGP bridge found
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Memory: 6082276k/6815744k available (5419k kernel code, 560068k absent, 173400k reserved, 2974k data, 872k init)
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] console [tty0] enabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] allocated 62914560 bytes of page_cgroup
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] hpet clockevent registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Oct 14 23:08:44 andrew-desktop kernel: [    0.000000] Detected 2599.693 MHz processor.
Oct 14 23:08:44 andrew-desktop kernel: [    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5199.38 BogoMIPS (lpj=25996930)
Oct 14 23:08:44 andrew-desktop kernel: [    0.010032] Security Framework initialized
Oct 14 23:08:44 andrew-desktop kernel: [    0.010051] AppArmor: AppArmor initialized
Oct 14 23:08:44 andrew-desktop kernel: [    0.010644] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:08:44 andrew-desktop kernel: [    0.015376] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.017645] Mount-cache hash table entries: 256
Oct 14 23:08:44 andrew-desktop kernel: [    0.017799] Initializing cgroup subsys ns
Oct 14 23:08:44 andrew-desktop kernel: [    0.017804] Initializing cgroup subsys cpuacct
Oct 14 23:08:44 andrew-desktop kernel: [    0.017807] Initializing cgroup subsys memory
Oct 14 23:08:44 andrew-desktop kernel: [    0.017816] Initializing cgroup subsys devices
Oct 14 23:08:44 andrew-desktop kernel: [    0.017818] Initializing cgroup subsys freezer
Oct 14 23:08:44 andrew-desktop kernel: [    0.017820] Initializing cgroup subsys net_cls
Oct 14 23:08:44 andrew-desktop kernel: [    0.017840] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:08:44 andrew-desktop kernel: [    0.017842] CPU: L2 cache: 2048K
Oct 14 23:08:44 andrew-desktop kernel: [    0.017845] CPU 0/0x0 -> Node 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.017846] CPU: Physical Processor ID: 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.017847] CPU: Processor Core ID: 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.017851] mce: CPU supports 6 MCE banks
Oct 14 23:08:44 andrew-desktop kernel: [    0.017858] CPU0: Thermal monitoring enabled (TM2)
Oct 14 23:08:44 andrew-desktop kernel: [    0.017862] using mwait in idle threads.
Oct 14 23:08:44 andrew-desktop kernel: [    0.017863] Performance Events: Core2 events, Intel PMU driver.
Oct 14 23:08:44 andrew-desktop kernel: [    0.017869] ... version:                2
Oct 14 23:08:44 andrew-desktop kernel: [    0.017870] ... bit width:              40
Oct 14 23:08:44 andrew-desktop kernel: [    0.017871] ... generic registers:      2
Oct 14 23:08:44 andrew-desktop kernel: [    0.017872] ... value mask:             000000ffffffffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.017874] ... max period:             000000007fffffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.017875] ... fixed-purpose events:   3
Oct 14 23:08:44 andrew-desktop kernel: [    0.017876] ... event mask:             0000000700000003
Oct 14 23:08:44 andrew-desktop kernel: [    0.020297] ACPI: Core revision 20090903
Oct 14 23:08:44 andrew-desktop kernel: [    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 14 23:08:44 andrew-desktop kernel: [    0.040011] ftrace: allocating 22538 entries in 89 pages
Oct 14 23:08:44 andrew-desktop kernel: [    0.050054] Setting APIC routing to flat
Oct 14 23:08:44 andrew-desktop kernel: [    0.050362] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 14 23:08:44 andrew-desktop kernel: [    0.152930] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
Oct 14 23:08:44 andrew-desktop kernel: [    0.160000] APIC calibration not consistent with PM-Timer: 149ms instead of 100ms
Oct 14 23:08:44 andrew-desktop kernel: [    0.160000] APIC delta adjusted to PM-Timer: 1249998 (1874988)
Oct 14 23:08:44 andrew-desktop kernel: [    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] Initializing CPU#1
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU: L2 cache: 2048K
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Oct 14 23:08:44 andrew-desktop kernel: [    0.310119] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
Oct 14 23:08:44 andrew-desktop kernel: [    0.310125] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 14 23:08:44 andrew-desktop kernel: [    0.320016] Brought up 2 CPUs
Oct 14 23:08:44 andrew-desktop kernel: [    0.320018] Total of 2 processors activated (10399.38 BogoMIPS).
Oct 14 23:08:44 andrew-desktop kernel: [    0.320460] CPU0 attaching sched-domain:
Oct 14 23:08:44 andrew-desktop kernel: [    0.320464]  domain 0: span 0-1 level MC
Oct 14 23:08:44 andrew-desktop kernel: [    0.320466]   groups: 0 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.320471] CPU1 attaching sched-domain:
Oct 14 23:08:44 andrew-desktop kernel: [    0.320473]  domain 0: span 0-1 level MC
Oct 14 23:08:44 andrew-desktop kernel: [    0.320475]   groups: 1 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] devtmpfs: initialized
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] regulator: core version 0.5
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] Time:  3:08:37  Date: 10/15/10
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] NET: Registered protocol family 16
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] Trying to unpack rootfs image as initramfs...
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] ACPI: bus type pci registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] PCI: Not using MMCONFIG.
Oct 14 23:08:44 andrew-desktop kernel: [    0.320562] PCI: Using configuration type 1 for base access
Oct 14 23:08:44 andrew-desktop kernel: [    0.330151] bio: create slab <bio-0> at 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.330960] ACPI: EC: Look up EC in DSDT
Oct 14 23:08:44 andrew-desktop kernel: [    0.333670] ACPI: Executed 1 blocks of module-level executable AML code
Oct 14 23:08:44 andrew-desktop kernel: [    0.339962] ACPI: Interpreter enabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.339966] ACPI: (supports S0 S1 S3 S4 S5)
Oct 14 23:08:44 andrew-desktop kernel: [    0.340035] ACPI: Using IOAPIC for interrupt routing
Oct 14 23:08:44 andrew-desktop kernel: [    0.340092] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:08:44 andrew-desktop kernel: [    0.343102] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Oct 14 23:08:44 andrew-desktop kernel: [    0.344909] PCI: Using MMCONFIG at f0000000 - f3ffffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.352514] ACPI Warning: Incorrect checksum in table [OEMB] - 9A, should be 95 (20090903/tbutils-314)
Oct 14 23:08:44 andrew-desktop kernel: [    0.353403] ACPI: No dock devices found.
Oct 14 23:08:44 andrew-desktop kernel: [    0.353545] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 14 23:08:44 andrew-desktop kernel: [    0.353628] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe400000-0xfe7fffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353635] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353639] pci 0000:00:02.0: reg 20 io port: [0xdc00-0xdc07]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353673] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe900000-0xfe9fffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353753] pci 0000:00:1a.0: reg 20 io port: [0xd480-0xd49f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353820] pci 0000:00:1a.1: reg 20 io port: [0xd800-0xd81f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353883] pci 0000:00:1a.2: reg 20 io port: [0xd880-0xd89f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.353948] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe8fb000-0xfe8fb3ff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354003] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.354007] pci 0000:00:1a.7: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354044] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354081] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.354084] pci 0000:00:1b.0: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354140] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.354143] pci 0000:00:1c.0: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354209] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.354212] pci 0000:00:1c.5: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354261] pci 0000:00:1d.0: reg 20 io port: [0xd000-0xd01f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354325] pci 0000:00:1d.1: reg 20 io port: [0xd080-0xd09f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354389] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354456] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8fa000-0xfe8fa3ff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354507] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.354511] pci 0000:00:1d.7: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354668] pci 0000:00:1f.2: reg 10 io port: [0xbc00-0xbc07]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354673] pci 0000:00:1f.2: reg 14 io port: [0xb880-0xb883]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354678] pci 0000:00:1f.2: reg 18 io port: [0xb800-0xb807]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354683] pci 0000:00:1f.2: reg 1c io port: [0xb480-0xb483]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354689] pci 0000:00:1f.2: reg 20 io port: [0xb400-0xb40f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354695] pci 0000:00:1f.2: reg 24 io port: [0xb080-0xb08f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354737] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe8f9000-0xfe8f90ff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354749] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354788] pci 0000:00:1f.5: reg 10 io port: [0xcc00-0xcc07]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354793] pci 0000:00:1f.5: reg 14 io port: [0xc880-0xc883]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354798] pci 0000:00:1f.5: reg 18 io port: [0xc800-0xc807]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354803] pci 0000:00:1f.5: reg 1c io port: [0xc480-0xc483]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354807] pci 0000:00:1f.5: reg 20 io port: [0xc400-0xc40f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354812] pci 0000:00:1f.5: reg 24 io port: [0xc080-0xc08f]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354883] pci 0000:02:00.0: reg 10 32bit mmio: [0xfebf0000-0xfebfffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.354947] pci 0000:02:00.0: PME# supported from D0 D3hot
Oct 14 23:08:44 andrew-desktop kernel: [    0.354951] pci 0000:02:00.0: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.354995] pci 0000:00:1c.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355055] pci 0000:01:00.0: reg 10 io port: [0xe800-0xe8ff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355077] pci 0000:01:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355098] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355142] pci 0000:01:00.0: supports D1 D2
Oct 14 23:08:44 andrew-desktop kernel: [    0.355143] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
Oct 14 23:08:44 andrew-desktop kernel: [    0.355148] pci 0000:01:00.0: PME# disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.355198] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355201] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355249] pci 0000:00:1e.0: transparent bridge
Oct 14 23:08:44 andrew-desktop kernel: [    0.355271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Oct 14 23:08:44 andrew-desktop kernel: [    0.355554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Oct 14 23:08:44 andrew-desktop kernel: [    0.370779] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.370881] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.370985] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371084] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371183] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371281] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371378] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371476] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:08:44 andrew-desktop kernel: [    0.371571] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 14 23:08:44 andrew-desktop kernel: [    0.371583] vgaarb: loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.371683] SCSI subsystem initialized
Oct 14 23:08:44 andrew-desktop kernel: [    0.371768] libata version 3.00 loaded.
Oct 14 23:08:44 andrew-desktop kernel: [    0.371825] usbcore: registered new interface driver usbfs
Oct 14 23:08:44 andrew-desktop kernel: [    0.371834] usbcore: registered new interface driver hub
Oct 14 23:08:44 andrew-desktop kernel: [    0.371856] usbcore: registered new device driver usb
Oct 14 23:08:44 andrew-desktop kernel: [    0.371972] ACPI: WMI: Mapper loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.371973] PCI: Using ACPI for IRQ routing
Oct 14 23:08:44 andrew-desktop kernel: [    0.372117] NetLabel: Initializing
Oct 14 23:08:44 andrew-desktop kernel: [    0.372119] NetLabel:  domain hash size = 128
Oct 14 23:08:44 andrew-desktop kernel: [    0.372120] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 14 23:08:44 andrew-desktop kernel: [    0.372131] NetLabel:  unlabeled traffic allowed by default
Oct 14 23:08:44 andrew-desktop kernel: [    0.372158] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Oct 14 23:08:44 andrew-desktop kernel: [    0.372162] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Oct 14 23:08:44 andrew-desktop kernel: [    0.380042] Switching to clocksource tsc
Oct 14 23:08:44 andrew-desktop kernel: [    0.381581] AppArmor: AppArmor Filesystem Enabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.381598] pnp: PnP ACPI init
Oct 14 23:08:44 andrew-desktop kernel: [    0.381615] ACPI: bus type pnp registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.385174] pnp: PnP ACPI: found 16 devices
Oct 14 23:08:44 andrew-desktop kernel: [    0.385176] ACPI: ACPI bus type pnp unregistered
Oct 14 23:08:44 andrew-desktop kernel: [    0.385188] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385195] system 00:07: ioport range 0x290-0x297 has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385200] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385202] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385204] system 00:08: ioport range 0x500-0x57f has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385206] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385208] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385210] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385213] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385221] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385225] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385228] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385231] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385236] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385238] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385240] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385242] system 00:0f: iomem range 0x100000-0xdddfffff could not be reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.385244] system 00:0f: iomem range 0xf0000000-0xffffffff could not be reserved
Oct 14 23:08:44 andrew-desktop kernel: [    0.389962] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Oct 14 23:08:44 andrew-desktop kernel: [    0.389966] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389970] pci 0000:00:1c.0:   MEM window: 0xfeb00000-0xfebfffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389974] pci 0000:00:1c.0:   PREFETCH window: 0x000000f4000000-0x000000f41fffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389979] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
Oct 14 23:08:44 andrew-desktop kernel: [    0.389982] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389986] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389989] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4200000-0x000000f43fffff
Oct 14 23:08:44 andrew-desktop kernel: [    0.389994] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Oct 14 23:08:44 andrew-desktop kernel: [    0.389996] pci 0000:00:1e.0:   IO window: disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.390000] pci 0000:00:1e.0:   MEM window: disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.390003] pci 0000:00:1e.0:   PREFETCH window: disabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.390017] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Oct 14 23:08:44 andrew-desktop kernel: [    0.390024]   alloc irq_desc for 17 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.390026]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.390032] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:08:44 andrew-desktop kernel: [    0.390036] pci 0000:00:1c.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.390043]   alloc irq_desc for 16 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.390044]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.390047] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:08:44 andrew-desktop kernel: [    0.390051] pci 0000:00:1c.5: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.390056] pci 0000:00:1e.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.390060] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390062] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390064] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390066] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390068] pci_bus 0000:02: resource 2 pref mem [0xf4000000-0xf41fffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390070] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390072] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390074] pci_bus 0000:01: resource 2 pref mem [0xf4200000-0xf43fffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390076] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390077] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:08:44 andrew-desktop kernel: [    0.390109] NET: Registered protocol family 2
Oct 14 23:08:44 andrew-desktop kernel: [    0.390323] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.391908] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.397023] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.397662] TCP: Hash tables configured (established 524288 bind 65536)
Oct 14 23:08:44 andrew-desktop kernel: [    0.397664] TCP reno registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.397781] NET: Registered protocol family 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.397802] pci 0000:00:02.0: Boot video device
Oct 14 23:08:44 andrew-desktop kernel: [    0.398121] Scanning for low memory corruption every 60 seconds
Oct 14 23:08:44 andrew-desktop kernel: [    0.398252] audit: initializing netlink socket (disabled)
Oct 14 23:08:44 andrew-desktop kernel: [    0.398261] type=2000 audit(1287112116.389:1): initialized
Oct 14 23:08:44 andrew-desktop kernel: [    0.406242] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 14 23:08:44 andrew-desktop kernel: [    0.407354] VFS: Disk quotas dquot_6.5.2
Oct 14 23:08:44 andrew-desktop kernel: [    0.407398] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 14 23:08:44 andrew-desktop kernel: [    0.407862] fuse init (API version 7.13)
Oct 14 23:08:44 andrew-desktop kernel: [    0.407927] msgmni has been set to 11879
Oct 14 23:08:44 andrew-desktop kernel: [    0.408106] alg: No test for stdrng (krng)
Oct 14 23:08:44 andrew-desktop kernel: [    0.408148] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 14 23:08:44 andrew-desktop kernel: [    0.408151] io scheduler noop registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.408152] io scheduler anticipatory registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.408153] io scheduler deadline registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.408179] io scheduler cfq registered (default)
Oct 14 23:08:44 andrew-desktop kernel: [    0.408305]   alloc irq_desc for 24 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.408307]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.408316] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Oct 14 23:08:44 andrew-desktop kernel: [    0.408324] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.408424]   alloc irq_desc for 25 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.408425]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.408432] pcieport 0000:00:1c.5: irq 25 for MSI/MSI-X
Oct 14 23:08:44 andrew-desktop kernel: [    0.408440] pcieport 0000:00:1c.5: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.408506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 14 23:08:44 andrew-desktop kernel: [    0.408577] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 14 23:08:44 andrew-desktop kernel: [    0.408691] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Oct 14 23:08:44 andrew-desktop kernel: [    0.408694] ACPI: Power Button [PWRB]
Oct 14 23:08:44 andrew-desktop kernel: [    0.408731] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 14 23:08:44 andrew-desktop kernel: [    0.408733] ACPI: Power Button [PWRF]
Oct 14 23:08:44 andrew-desktop kernel: [    0.409364] ACPI: SSDT 00000000ddd90100 00406 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Oct 14 23:08:44 andrew-desktop kernel: [    0.409705] processor LNXCPU:00: registered as cooling_device0
Oct 14 23:08:44 andrew-desktop kernel: [    0.409737] processor LNXCPU:01: registered as cooling_device1
Oct 14 23:08:44 andrew-desktop kernel: [    0.413453] Linux agpgart interface v0.103
Oct 14 23:08:44 andrew-desktop kernel: [    0.413485] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 14 23:08:44 andrew-desktop kernel: [    0.413584] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:08:44 andrew-desktop kernel: [    0.413888] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:08:44 andrew-desktop kernel: [    0.414722] brd: module loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.415103] loop: module loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.415175] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Oct 14 23:08:44 andrew-desktop kernel: [    0.415266] ata_piix 0000:00:1f.2: version 2.13
Oct 14 23:08:44 andrew-desktop kernel: [    0.415284]   alloc irq_desc for 19 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.415286]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.415293] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.415297] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 14 23:08:44 andrew-desktop kernel: [    0.415343] ata_piix 0000:00:1f.2: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.415423] scsi0 : ata_piix
Oct 14 23:08:44 andrew-desktop kernel: [    0.415482] scsi1 : ata_piix
Oct 14 23:08:44 andrew-desktop kernel: [    0.416783] ata1: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.416788] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.416808] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.416812] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 14 23:08:44 andrew-desktop kernel: [    0.416844] ata_piix 0000:00:1f.5: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.416888] scsi2 : ata_piix
Oct 14 23:08:44 andrew-desktop kernel: [    0.416929] scsi3 : ata_piix
Oct 14 23:08:44 andrew-desktop kernel: [    0.417900] ata3: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.417903] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.418151] Fixed MDIO Bus: probed
Oct 14 23:08:44 andrew-desktop kernel: [    0.418177] PPP generic driver version 2.4.2
Oct 14 23:08:44 andrew-desktop kernel: [    0.418219] tun: Universal TUN/TAP device driver, 1.6
Oct 14 23:08:44 andrew-desktop kernel: [    0.418221] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 14 23:08:44 andrew-desktop kernel: [    0.418304] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 14 23:08:44 andrew-desktop kernel: [    0.418320]   alloc irq_desc for 18 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.418322]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.418328] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:08:44 andrew-desktop kernel: [    0.418352] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.418355] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.418380] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.418405] ehci_hcd 0000:00:1a.7: debug port 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.422298] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Oct 14 23:08:44 andrew-desktop kernel: [    0.422318] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe8fb000
Oct 14 23:08:44 andrew-desktop kernel: [    0.439609] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Oct 14 23:08:44 andrew-desktop kernel: [    0.439732] usb usb1: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.439755] hub 1-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.439764] hub 1-0:1.0: 6 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.439826]   alloc irq_desc for 23 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.439828]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.439833] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:08:44 andrew-desktop kernel: [    0.439857] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.439860] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.439894] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 14 23:08:44 andrew-desktop kernel: [    0.439926] ehci_hcd 0000:00:1d.7: debug port 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.443811] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Oct 14 23:08:44 andrew-desktop kernel: [    0.443830] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8fa000
Oct 14 23:08:44 andrew-desktop kernel: [    0.459589] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 14 23:08:44 andrew-desktop kernel: [    0.459723] usb usb2: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.459746] hub 2-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.459755] hub 2-0:1.0: 6 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.459813] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 14 23:08:44 andrew-desktop kernel: [    0.459828] uhci_hcd: USB Universal Host Controller Interface driver
Oct 14 23:08:44 andrew-desktop kernel: [    0.459882]   alloc irq_desc for 20 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.459884]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.459889] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 14 23:08:44 andrew-desktop kernel: [    0.459898] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.459901] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.459930] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Oct 14 23:08:44 andrew-desktop kernel: [    0.459965] uhci_hcd 0000:00:1a.0: irq 20, io base 0x0000d480
Oct 14 23:08:44 andrew-desktop kernel: [    0.460033] usb usb3: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460051] hub 3-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460056] hub 3-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.460093]   alloc irq_desc for 21 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.460095]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    0.460098] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Oct 14 23:08:44 andrew-desktop kernel: [    0.460104] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.460107] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.460130] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Oct 14 23:08:44 andrew-desktop kernel: [    0.460158] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d800
Oct 14 23:08:44 andrew-desktop kernel: [    0.460227] usb usb4: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460245] hub 4-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460250] hub 4-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.460285] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:08:44 andrew-desktop kernel: [    0.460290] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.460292] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.460325] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Oct 14 23:08:44 andrew-desktop kernel: [    0.460346] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d880
Oct 14 23:08:44 andrew-desktop kernel: [    0.460415] usb usb5: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460433] hub 5-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460438] hub 5-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.460471] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:08:44 andrew-desktop kernel: [    0.460476] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.460478] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.460511] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Oct 14 23:08:44 andrew-desktop kernel: [    0.460531] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d000
Oct 14 23:08:44 andrew-desktop kernel: [    0.460597] usb usb6: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460618] hub 6-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460623] hub 6-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.460660] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:08:44 andrew-desktop kernel: [    0.460664] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.460667] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.460688] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Oct 14 23:08:44 andrew-desktop kernel: [    0.460710] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d080
Oct 14 23:08:44 andrew-desktop kernel: [    0.460784] usb usb7: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460805] hub 7-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460812] hub 7-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.460847] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:08:44 andrew-desktop kernel: [    0.460851] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    0.460854] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 14 23:08:44 andrew-desktop kernel: [    0.460875] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Oct 14 23:08:44 andrew-desktop kernel: [    0.460896] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Oct 14 23:08:44 andrew-desktop kernel: [    0.460968] usb usb8: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    0.460986] hub 8-0:1.0: USB hub found
Oct 14 23:08:44 andrew-desktop kernel: [    0.460991] hub 8-0:1.0: 2 ports detected
Oct 14 23:08:44 andrew-desktop kernel: [    0.461068] PNP: No PS/2 controller found. Probing ports directly.
Oct 14 23:08:44 andrew-desktop kernel: [    0.463609] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.463614] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 14 23:08:44 andrew-desktop kernel: [    0.463720] mice: PS/2 mouse device common for all mice
Oct 14 23:08:44 andrew-desktop kernel: [    0.463814] rtc_cmos 00:03: RTC can wake from S4
Oct 14 23:08:44 andrew-desktop kernel: [    0.463848] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Oct 14 23:08:44 andrew-desktop kernel: [    0.463870] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 14 23:08:44 andrew-desktop kernel: [    0.463984] device-mapper: uevent: version 1.0.3
Oct 14 23:08:44 andrew-desktop kernel: [    0.464078] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Oct 14 23:08:44 andrew-desktop kernel: [    0.464127] device-mapper: multipath: version 1.1.0 loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.464129] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 14 23:08:44 andrew-desktop kernel: [    0.464254] cpuidle: using governor ladder
Oct 14 23:08:44 andrew-desktop kernel: [    0.464256] cpuidle: using governor menu
Oct 14 23:08:44 andrew-desktop kernel: [    0.464532] TCP cubic registered
Oct 14 23:08:44 andrew-desktop kernel: [    0.464647] NET: Registered protocol family 10
Oct 14 23:08:44 andrew-desktop kernel: [    0.465009] lo: Disabled Privacy Extensions
Oct 14 23:08:44 andrew-desktop kernel: [    0.465222] NET: Registered protocol family 17
Oct 14 23:08:44 andrew-desktop kernel: [    0.465757] PM: Resume from disk failed.
Oct 14 23:08:44 andrew-desktop kernel: [    0.465769] registered taskstats version 1
Oct 14 23:08:44 andrew-desktop kernel: [    0.466117]   Magic number: 14:530:108
Oct 14 23:08:44 andrew-desktop kernel: [    0.466127] usbmon usbmon4: hash matches
Oct 14 23:08:44 andrew-desktop kernel: [    0.466211] rtc_cmos 00:03: setting system clock to 2010-10-15 03:08:37 UTC (1287112117)
Oct 14 23:08:44 andrew-desktop kernel: [    0.466214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 14 23:08:44 andrew-desktop kernel: [    0.466215] EDD information not available.
Oct 14 23:08:44 andrew-desktop kernel: [    0.473668] Freeing initrd memory: 8144k freed
Oct 14 23:08:44 andrew-desktop kernel: [    0.759480] usb 1-1: new high speed USB device using ehci_hcd and address 2
Oct 14 23:08:44 andrew-desktop kernel: [    0.780155] ata3: SATA link down (SStatus 0 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    0.790884] ata4: SATA link down (SStatus 0 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    1.041440] usb 1-1: configuration #1 chosen from 2 choices
Oct 14 23:08:44 andrew-desktop kernel: [    1.290105] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    1.290122] ata2.01: SATA link down (SStatus 0 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    1.290135] ata2.01: link offline, clearing class 3 to NONE
Oct 14 23:08:44 andrew-desktop kernel: [    1.300064] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    1.300080] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:08:44 andrew-desktop kernel: [    1.310425] ata2.00: ATAPI: ATAPI   DVD A  DH20A6S, 7P56, max UDMA/100
Oct 14 23:08:44 andrew-desktop kernel: [    1.330427] ata1.00: ATA-8: Hitachi HDT721064SLA360, STDOA31B, max UDMA/133
Oct 14 23:08:44 andrew-desktop kernel: [    1.330433] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:08:44 andrew-desktop kernel: [    1.330623] ata1.01: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
Oct 14 23:08:44 andrew-desktop kernel: [    1.330629] ata1.01: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:08:44 andrew-desktop kernel: [    1.340015] usb 2-4: new high speed USB device using ehci_hcd and address 3

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:08:44 andrew-desktop kernel: [    1.350232] ata2.00: configured for UDMA/100
Oct 14 23:08:44 andrew-desktop kernel: [    1.370434] ata1.00: configured for UDMA/133
Oct 14 23:08:44 andrew-desktop kernel: [    1.410346] ata1.01: configured for UDMA/133
Oct 14 23:08:44 andrew-desktop kernel: [    1.410512] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72106 STDO PQ: 0 ANSI: 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.410687] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    1.410695] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 14 23:08:44 andrew-desktop kernel: [    1.410724] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 23:08:44 andrew-desktop kernel: [    1.410726] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 14 23:08:44 andrew-desktop kernel: [    1.410744] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:08:44 andrew-desktop kernel: [    1.410779] scsi 0:0:1:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.410867] sd 0:0:1:0: Attached scsi generic sg1 type 0
Oct 14 23:08:44 andrew-desktop kernel: [    1.410882]  sda:
Oct 14 23:08:44 andrew-desktop kernel: [    1.411989] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A6S   7P56 PQ: 0 ANSI: 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.417823] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 14 23:08:44 andrew-desktop kernel: [    1.417827] Uniform CD-ROM driver Revision: 3.20
Oct 14 23:08:44 andrew-desktop kernel: [    1.417953] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 14 23:08:44 andrew-desktop kernel: [    1.418009] sr 1:0:0:0: Attached scsi generic sg2 type 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.425039]  sda1 sda2 <
Oct 14 23:08:44 andrew-desktop kernel: [    1.425049] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    1.457527]  sda5 >
Oct 14 23:08:44 andrew-desktop kernel: [    1.457595] sd 0:0:1:0: [sdb] Write Protect is off
Oct 14 23:08:44 andrew-desktop kernel: [    1.457600] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Oct 14 23:08:44 andrew-desktop kernel: [    1.457640] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:08:44 andrew-desktop kernel: [    1.457786]  sdb: sdb1 sdb2 < sdb5 >
Oct 14 23:08:44 andrew-desktop kernel: [    1.484254] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 14 23:08:44 andrew-desktop kernel: [    1.484506] sd 0:0:1:0: [sdb] Attached SCSI disk
Oct 14 23:08:44 andrew-desktop kernel: [    1.484523] Freeing unused kernel memory: 872k freed
Oct 14 23:08:44 andrew-desktop kernel: [    1.484853] Write protecting the kernel read-only data: 7692k
Oct 14 23:08:44 andrew-desktop kernel: [    1.491089] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    1.496233] udev: starting version 151
Oct 14 23:08:44 andrew-desktop kernel: [    1.558857] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 14 23:08:44 andrew-desktop kernel: [    1.558882] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:08:44 andrew-desktop kernel: [    1.558940] r8169 0000:01:00.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    1.558998]   alloc irq_desc for 26 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    1.558999]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    1.559013] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
Oct 14 23:08:44 andrew-desktop kernel: [    1.559472] eth0: RTL8168b/8111b at 0xffffc90000c76000, 00:24:8c:e6:75:c8, XID 18000000 IRQ 26
Oct 14 23:08:44 andrew-desktop kernel: [    1.567724] Initializing USB Mass Storage driver...
Oct 14 23:08:44 andrew-desktop kernel: [    1.589121] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 14 23:08:44 andrew-desktop kernel: [    1.591927] usb-storage: device found at 2
Oct 14 23:08:44 andrew-desktop kernel: [    1.591930] usb-storage: waiting for device to settle before scanning
Oct 14 23:08:44 andrew-desktop kernel: [    1.596401] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 14 23:08:44 andrew-desktop kernel: [    1.596497] usbcore: registered new interface driver usb-storage
Oct 14 23:08:44 andrew-desktop kernel: [    1.596499] USB Mass Storage support registered.
Oct 14 23:08:44 andrew-desktop kernel: [    1.596583] usb-storage: device found at 3
Oct 14 23:08:44 andrew-desktop kernel: [    1.596585] usb-storage: waiting for device to settle before scanning
Oct 14 23:08:44 andrew-desktop kernel: [    1.670027] usb 2-6: new high speed USB device using ehci_hcd and address 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.821174] usb 2-6: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    1.821434] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 14 23:08:44 andrew-desktop kernel: [    1.821584] usb-storage: device found at 5
Oct 14 23:08:44 andrew-desktop kernel: [    1.821585] usb-storage: waiting for device to settle before scanning
Oct 14 23:08:44 andrew-desktop kernel: [    2.054472] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 14 23:08:44 andrew-desktop kernel: [    2.100021] usb 4-1: new full speed USB device using uhci_hcd and address 2
Oct 14 23:08:44 andrew-desktop kernel: [    2.230027] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    2.470021] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    2.700023] usb 4-1: new full speed USB device using uhci_hcd and address 3
Oct 14 23:08:44 andrew-desktop kernel: [    2.830027] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    3.070020] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    3.300021] usb 4-1: new full speed USB device using uhci_hcd and address 4
Oct 14 23:08:44 andrew-desktop kernel: [    3.720034] usb 4-1: device not accepting address 4, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    3.840026] usb 4-1: new full speed USB device using uhci_hcd and address 5
Oct 14 23:08:44 andrew-desktop kernel: [    3.958613] Adding 17844216k swap on /dev/sda5.  Priority:-1 extents:1 across:17844216k 
Oct 14 23:08:44 andrew-desktop kernel: [    4.260020] usb 4-1: device not accepting address 5, error -71
Oct 14 23:08:44 andrew-desktop kernel: [    4.260083] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:08:44 andrew-desktop kernel: [    4.457406] udev: starting version 151
Oct 14 23:08:44 andrew-desktop kernel: [    4.540088] usb 7-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:08:44 andrew-desktop kernel: [    4.720409] usb 7-1: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    5.010148] usb 8-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:08:44 andrew-desktop kernel: [    5.193654] usb 8-1: configuration #1 chosen from 1 choice
Oct 14 23:08:44 andrew-desktop kernel: [    5.277043] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Oct 14 23:08:44 andrew-desktop kernel: [    5.280739] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:08:44 andrew-desktop kernel: [    5.280881] 
Oct 14 23:08:44 andrew-desktop kernel: [    5.280881] 
Oct 14 23:08:44 andrew-desktop kernel: [    5.280882] === pAd = ffffc9000610d000, size = 627064 ===
Oct 14 23:08:44 andrew-desktop kernel: [    5.280882] 
Oct 14 23:08:44 andrew-desktop kernel: [    5.280884] <-- RTMPAllocAdapterBlock, Status=0
Oct 14 23:08:44 andrew-desktop kernel: [    5.280921] rt2860 0000:02:00.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    5.368356] type=1505 audit(1287112122.393:2):  operation="profile_load" pid=580 name="/sbin/dhclient3"
Oct 14 23:08:44 andrew-desktop kernel: [    5.368877] type=1505 audit(1287112122.393:3):  operation="profile_load" pid=580 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:08:44 andrew-desktop kernel: [    5.369153] type=1505 audit(1287112122.393:4):  operation="profile_load" pid=580 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:08:44 andrew-desktop kernel: [    5.830046] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Oct 14 23:08:44 andrew-desktop kernel: [    5.830723] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Oct 14 23:08:44 andrew-desktop kernel: [    5.852372] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Oct 14 23:08:44 andrew-desktop kernel: [    5.929866] usbcore: registered new interface driver hiddev
Oct 14 23:08:44 andrew-desktop kernel: [    5.945741] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3
Oct 14 23:08:44 andrew-desktop kernel: [    5.945835] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
Oct 14 23:08:44 andrew-desktop kernel: [    5.960940] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
Oct 14 23:08:44 andrew-desktop kernel: [    5.961027] generic-usb 0003:046D:C312.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input0
Oct 14 23:08:44 andrew-desktop kernel: [    6.005699] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input5
Oct 14 23:08:44 andrew-desktop kernel: [    6.005846] generic-usb 0003:046D:C312.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input1
Oct 14 23:08:44 andrew-desktop kernel: [    6.005871] usbcore: registered new interface driver usbhid
Oct 14 23:08:44 andrew-desktop kernel: [    6.005873] usbhid: v2.6:USB HID core driver
Oct 14 23:08:44 andrew-desktop kernel: [    6.011953] lp: driver loaded but no devices found
Oct 14 23:08:44 andrew-desktop kernel: [    6.092460] parport_pc 00:06: reported by Plug and Play ACPI
Oct 14 23:08:44 andrew-desktop kernel: [    6.092573] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct 14 23:08:44 andrew-desktop kernel: [    6.170361] lp0: using parport0 (interrupt-driven).
Oct 14 23:08:44 andrew-desktop kernel: [    6.307531] ppdev: user-space parallel port driver
Oct 14 23:08:44 andrew-desktop kernel: [    6.479343] [drm] Initialized drm 1.1.0 20060810
Oct 14 23:08:44 andrew-desktop kernel: [    6.590157] usb-storage: device scan complete
Oct 14 23:08:44 andrew-desktop kernel: [    6.590232] usb-storage: device scan complete
Oct 14 23:08:44 andrew-desktop kernel: [    6.590643] scsi 5:0:0:0: Direct-Access     WD       5000AAV External 1.75 PQ: 0 ANSI: 4
Oct 14 23:08:44 andrew-desktop kernel: [    6.591007] sd 5:0:0:0: Attached scsi generic sg3 type 0
Oct 14 23:08:44 andrew-desktop kernel: [    6.592284] sd 5:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    6.592751] sd 5:0:0:0: [sdc] Write Protect is off
Oct 14 23:08:44 andrew-desktop kernel: [    6.592756] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
Oct 14 23:08:44 andrew-desktop kernel: [    6.592760] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.593996] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.594045]  sdc:
Oct 14 23:08:44 andrew-desktop kernel: [    6.597511] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Oct 14 23:08:44 andrew-desktop kernel: [    6.598108] sd 4:0:0:0: Attached scsi generic sg4 type 0
Oct 14 23:08:44 andrew-desktop kernel: [    6.599864] sd 4:0:0:0: [sdd] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    6.600358] sd 4:0:0:0: [sdd] Write Protect is off
Oct 14 23:08:44 andrew-desktop kernel: [    6.600363] sd 4:0:0:0: [sdd] Mode Sense: 68 00 00 08
Oct 14 23:08:44 andrew-desktop kernel: [    6.600367] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.601860] sd 4:0:0:0: [sdd] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    6.602356] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.602402]  sdd: sdc1
Oct 14 23:08:44 andrew-desktop kernel: [    6.611034] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.611077] sd 5:0:0:0: [sdc] Attached SCSI disk
Oct 14 23:08:44 andrew-desktop kernel: [    6.822154] usb-storage: device scan complete
Oct 14 23:08:44 andrew-desktop kernel: [    6.822808] scsi 6:0:0:0: Direct-Access     WD       15EADS External  1.75 PQ: 0 ANSI: 4
Oct 14 23:08:44 andrew-desktop kernel: [    6.823281] sd 6:0:0:0: Attached scsi generic sg5 type 0
Oct 14 23:08:44 andrew-desktop kernel: [    6.824255] sd 6:0:0:0: [sde] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Oct 14 23:08:44 andrew-desktop kernel: [    6.824896] sd 6:0:0:0: [sde] Write Protect is off
Oct 14 23:08:44 andrew-desktop kernel: [    6.824899] sd 6:0:0:0: [sde] Mode Sense: 23 00 00 00
Oct 14 23:08:44 andrew-desktop kernel: [    6.824901] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.826148] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.826193]  sde: sde1
Oct 14 23:08:44 andrew-desktop kernel: [    6.828267] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    6.828310] sd 6:0:0:0: [sde] Attached SCSI disk
Oct 14 23:08:44 andrew-desktop kernel: [    7.558888]  sdd1
Oct 14 23:08:44 andrew-desktop kernel: [    7.560352] sd 4:0:0:0: [sdd] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:08:44 andrew-desktop kernel: [    7.560838] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:08:44 andrew-desktop kernel: [    7.560877] sd 4:0:0:0: [sdd] Attached SCSI removable disk
Oct 14 23:08:44 andrew-desktop kernel: [    7.603295] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:08:44 andrew-desktop kernel: [    7.603300] i915 0000:00:02.0: setting latency timer to 64
Oct 14 23:08:44 andrew-desktop kernel: [    7.616063] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Oct 14 23:08:44 andrew-desktop kernel: [    7.616066] [drm] MTRR allocation failed.  Graphics performance may suffer.
Oct 14 23:08:44 andrew-desktop kernel: [    7.616142]   alloc irq_desc for 27 on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    7.616144]   alloc kstat_irqs on node -1
Oct 14 23:08:44 andrew-desktop kernel: [    7.616151] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Oct 14 23:08:44 andrew-desktop kernel: [    7.616156] [drm] set up 31M of stolen space
Oct 14 23:08:44 andrew-desktop kernel: [    7.948324] fb0: inteldrmfb frame buffer device
Oct 14 23:08:44 andrew-desktop kernel: [    7.948326] registered panic notifier
Oct 14 23:08:44 andrew-desktop kernel: [    7.948422] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 14 23:08:45 andrew-desktop kernel: [    8.256920] vga16fb: initializing
Oct 14 23:08:45 andrew-desktop kernel: [    8.256924] vga16fb: mapped to 0xffff8800000a0000
Oct 14 23:08:45 andrew-desktop kernel: [    8.256927] vga16fb: not registering due to another framebuffer present
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Successfully dropped root privileges.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: avahi-daemon 0.6.25 starting up.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Successfully called chroot().
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Successfully dropped remaining capabilities.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: No service file found in /etc/avahi/services.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Network interface enumeration completed.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Registering HINFO record with values 'X86_64'/'LINUX'.
Oct 14 23:08:45 andrew-desktop avahi-daemon[900]: Server startup complete. Host name is andrew-desktop.local. Local service cookie is 1951797600.
Oct 14 23:08:45 andrew-desktop kernel: [    8.758715]   alloc irq_desc for 22 on node -1
Oct 14 23:08:45 andrew-desktop kernel: [    8.758723]   alloc kstat_irqs on node -1
Oct 14 23:08:45 andrew-desktop kernel: [    8.758725] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 14 23:08:45 andrew-desktop kernel: [    8.758784] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 14 23:08:45 andrew-desktop kernel: [    8.864185] Console: switching to colour frame buffer device 210x65
Oct 14 23:08:46 andrew-desktop kernel: [    9.108327] type=1505 audit(1287112126.133:5):  operation="profile_load" pid=921 name="/usr/share/gdm/guest-session/Xsession"
Oct 14 23:08:46 andrew-desktop kernel: [    9.109765] type=1505 audit(1287112126.133:6):  operation="profile_replace" pid=937 name="/sbin/dhclient3"
Oct 14 23:08:46 andrew-desktop kernel: [    9.110370] type=1505 audit(1287112126.143:7):  operation="profile_replace" pid=937 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:08:46 andrew-desktop kernel: [    9.110656] type=1505 audit(1287112126.143:8):  operation="profile_replace" pid=937 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:08:46 andrew-desktop NetworkManager: <info>  starting...
Oct 14 23:08:46 andrew-desktop kernel: [    9.150587] hda_codec: ALC887: BIOS auto-probing.
Oct 14 23:08:46 andrew-desktop kernel: [    9.152062] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Oct 14 23:08:46 andrew-desktop NetworkManager: <info>  Trying to start the modem-manager...
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Novatel
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Nokia
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin ZTE
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin AnyData
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin MotoC
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Option
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Sierra
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Huawei
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Gobi
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Ericsson MBM
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Longcheer
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Generic
Oct 14 23:08:46 andrew-desktop modem-manager: Loaded plugin Option High-Speed
Oct 14 23:08:46 andrew-desktop kernel: [    9.345162] type=1505 audit(1287112126.373:9):  operation="profile_load" pid=938 name="/usr/bin/evince"
Oct 14 23:08:46 andrew-desktop kernel: [    9.352050] type=1505 audit(1287112126.383:10):  operation="profile_load" pid=938 name="/usr/bin/evince-previewer"
Oct 14 23:08:46 andrew-desktop kernel: [    9.356227] type=1505 audit(1287112126.383:11):  operation="profile_load" pid=938 name="/usr/bin/evince-thumbnailer"
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0)
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Oct 14 23:08:46 andrew-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:08:46 andrew-desktop gdm-binary[896]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:08:46 andrew-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:08:46 andrew-desktop kernel: [    9.430241] type=1505 audit(1287112126.463:12):  operation="profile_load" pid=945 name="/usr/lib/cups/backend/cups-pdf"
Oct 14 23:08:46 andrew-desktop kernel: [    9.430875] type=1505 audit(1287112126.463:13):  operation="profile_load" pid=945 name="/usr/sbin/cupsd"
Oct 14 23:08:46 andrew-desktop kernel: [    9.438468] type=1505 audit(1287112126.463:14):  operation="profile_load" pid=950 name="/usr/sbin/tcpdump"
Oct 14 23:08:46 andrew-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Oct 14 23:08:46 andrew-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (11266336) ... get_connections.
Oct 14 23:08:46 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (11266336) ... get_connections (managed=false): return empty list.
Oct 14 23:08:47 andrew-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt2860')
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): now managed
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): bringing up device.
Oct 14 23:08:47 andrew-desktop kernel: [   10.509383] RX DESC ffff8800dd82f000  size = 2048
Oct 14 23:08:47 andrew-desktop kernel: [   10.509560] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 14 23:08:47 andrew-desktop kernel: [   10.512645] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Oct 14 23:08:47 andrew-desktop kernel: [   10.512646] 1. Phy Mode = 0
Oct 14 23:08:47 andrew-desktop kernel: [   10.512648] 2. Phy Mode = 0
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): preparing device.
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Oct 14 23:08:47 andrew-desktop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): carrier is OFF
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): now managed
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): bringing up device.
Oct 14 23:08:47 andrew-desktop kernel: [   10.530912] 3. Phy Mode = 0
Oct 14 23:08:47 andrew-desktop kernel: [   10.533030] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 14 23:08:47 andrew-desktop kernel: [   10.533032] MCS Set = 00 00 00 00 00
Oct 14 23:08:47 andrew-desktop kernel: [   10.534600] <==== RTMPInitialize, Status=0
Oct 14 23:08:47 andrew-desktop kernel: [   10.534663] 0x1300 = 00073200
Oct 14 23:08:47 andrew-desktop kernel: [   10.536955] r8169: eth0: link down
Oct 14 23:08:47 andrew-desktop kernel: [   10.537689] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): preparing device.
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Oct 14 23:08:47 andrew-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  modem-manager is now available
Oct 14 23:08:47 andrew-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  Trying to start the supplicant...
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Oct 14 23:08:47 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Oct 14 23:08:48 andrew-desktop gdm-binary[896]: WARNING: Unable to find users: no seat-id found
Oct 14 23:08:48 andrew-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Oct 14 23:08:48 andrew-desktop acpid: starting up with proc fs
Oct 14 23:08:48 andrew-desktop init: apport pre-start process (1071) terminated with status 1
Oct 14 23:08:48 andrew-desktop init: apport post-stop process (1084) terminated with status 1
Oct 14 23:08:48 andrew-desktop cron[1075]: (CRON) INFO (pidfile fd = 3)
Oct 14 23:08:48 andrew-desktop anacron[1089]: Anacron 2.3 started on 2010-10-14
Oct 14 23:08:48 andrew-desktop anacron[1089]: Normal exit (0 jobs run)
Oct 14 23:08:48 andrew-desktop cron[1090]: (CRON) STARTUP (fork ok)
Oct 14 23:08:48 andrew-desktop cron[1090]: (CRON) INFO (Running @reboot jobs)
Oct 14 23:08:49 andrew-desktop gdm-simple-slave[1065]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:08:49 andrew-desktop acpid: 36 rules loaded
Oct 14 23:08:49 andrew-desktop acpid: waiting for events: event logging is off
Oct 14 23:08:49 andrew-desktop avahi-daemon[900]: Registering new address record for fe80::222:43ff:fe64:80ab on wlan0.*.
Oct 14 23:08:50 andrew-desktop acpid: client connected from 1135[0:0]
Oct 14 23:08:50 andrew-desktop acpid: 1 client rule loaded
Oct 14 23:08:51 andrew-desktop anacron[1234]: Anacron 2.3 started on 2010-10-14
Oct 14 23:08:51 andrew-desktop anacron[1234]: Normal exit (0 jobs run)
Oct 14 23:08:51 andrew-desktop kernel: [   14.750063] CPU0 attaching NULL sched-domain.
Oct 14 23:08:51 andrew-desktop kernel: [   14.750069] CPU1 attaching NULL sched-domain.
Oct 14 23:08:51 andrew-desktop kernel: [   14.790116] CPU0 attaching sched-domain:
Oct 14 23:08:51 andrew-desktop kernel: [   14.790122]  domain 0: span 0-1 level MC
Oct 14 23:08:51 andrew-desktop kernel: [   14.790126]   groups: 0 1
Oct 14 23:08:51 andrew-desktop kernel: [   14.790135] CPU1 attaching sched-domain:
Oct 14 23:08:51 andrew-desktop kernel: [   14.790138]  domain 0: span 0-1 level MC
Oct 14 23:08:51 andrew-desktop kernel: [   14.790142]   groups: 1 0
Oct 14 23:08:52 andrew-desktop init: plymouth-stop pre-start process (1268) terminated with status 1
Oct 14 23:08:53 andrew-desktop kernel: [   16.422711] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 23:08:54 andrew-desktop gdm-session-worker[1279]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Sucessfully called chroot.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Sucessfully dropped privileges.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Sucessfully limited resources.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Running.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Watchdog thread running.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Canary thread running.
Oct 14 23:08:54 andrew-desktop kernel: [   17.570019] usb 4-1: new full speed USB device using uhci_hcd and address 6
Oct 14 23:08:54 andrew-desktop kernel: [   17.700026] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:54 andrew-desktop polkitd[1291]: started daemon version 0.96 using authority implementation `local' version `0.96'
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1285 of process 1285 (n/a) owned by '114' high priority at nice level -11.
Oct 14 23:08:54 andrew-desktop rtkit-daemon[1287]: Supervising 1 threads of 1 processes of 1 users.
Oct 14 23:08:54 andrew-desktop kernel: [   17.940024] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:55 andrew-desktop kernel: [   18.170039] usb 4-1: new full speed USB device using uhci_hcd and address 7
Oct 14 23:08:55 andrew-desktop kernel: [   18.301267] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:55 andrew-desktop kernel: [   18.540073] usb 4-1: device descriptor read/64, error -71
Oct 14 23:08:55 andrew-desktop kernel: [   18.770022] usb 4-1: new full speed USB device using uhci_hcd and address 8
Oct 14 23:08:56 andrew-desktop kernel: [   19.190015] usb 4-1: device not accepting address 8, error -71
Oct 14 23:08:56 andrew-desktop kernel: [   19.310018] usb 4-1: new full speed USB device using uhci_hcd and address 9
Oct 14 23:08:56 andrew-desktop wpa_supplicant[988]: No network configuration found for the current AP
Oct 14 23:08:56 andrew-desktop wpa_supplicant[988]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:08:56 andrew-desktop wpa_supplicant[988]: last message repeated 3 times
Oct 14 23:08:56 andrew-desktop kernel: [   19.604136] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct 14 23:08:56 andrew-desktop kernel: [   19.610014] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct 14 23:08:56 andrew-desktop wpa_supplicant[988]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:08:56 andrew-desktop kernel: [   19.730023] usb 4-1: device not accepting address 9, error -71
Oct 14 23:08:56 andrew-desktop kernel: [   19.730044] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:08:56 andrew-desktop kernel: [   19.730072] usb 1-1: USB disconnect, address 2
Oct 14 23:08:57 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1348 of process 1285 (n/a) owned by '114' RT at priority 5.
Oct 14 23:08:57 andrew-desktop rtkit-daemon[1287]: Supervising 2 threads of 1 processes of 1 users.
Oct 14 23:08:57 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1353 of process 1285 (n/a) owned by '114' RT at priority 5.
Oct 14 23:08:57 andrew-desktop rtkit-daemon[1287]: Supervising 3 threads of 1 processes of 1 users.
Oct 14 23:08:57 andrew-desktop anacron[1357]: Anacron 2.3 started on 2010-10-14
Oct 14 23:08:57 andrew-desktop anacron[1357]: Normal exit (0 jobs run)
Oct 14 23:08:57 andrew-desktop kernel: [   20.370203] CPU0 attaching NULL sched-domain.
Oct 14 23:08:57 andrew-desktop kernel: [   20.370209] CPU1 attaching NULL sched-domain.
Oct 14 23:08:57 andrew-desktop kernel: [   20.421347] CPU0 attaching sched-domain:
Oct 14 23:08:57 andrew-desktop kernel: [   20.421353]  domain 0: span 0-1 level MC
Oct 14 23:08:57 andrew-desktop kernel: [   20.421357]   groups: 0 1
Oct 14 23:08:57 andrew-desktop kernel: [   20.421366] CPU1 attaching sched-domain:
Oct 14 23:08:57 andrew-desktop kernel: [   20.421369]  domain 0: span 0-1 level MC
Oct 14 23:08:57 andrew-desktop kernel: [   20.421373]   groups: 1 0
Oct 14 23:08:57 andrew-desktop gdm-simple-greeter[1277]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Oct 14 23:08:58 andrew-desktop acpid: client connected from 1405[108:114]
Oct 14 23:08:58 andrew-desktop acpid: 1 client rule loaded
Oct 14 23:08:58 andrew-desktop kernel: [   21.470012] wlan0: no IPv6 routers present
Oct 14 23:09:11 andrew-desktop gdm-session-worker[1279]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct 14 23:09:14 andrew-desktop kernel: [   36.977560] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:09:14 andrew-desktop gnome-session[1433]: EggSMClient-WARNING: Desktop file '/home/andrew/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Oct 14 23:09:15 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1495 of process 1495 (n/a) owned by '1000' high priority at nice level -11.
Oct 14 23:09:15 andrew-desktop rtkit-daemon[1287]: Supervising 4 threads of 2 processes of 2 users.
Oct 14 23:09:17 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1520 of process 1495 (n/a) owned by '1000' RT at priority 5.
Oct 14 23:09:17 andrew-desktop rtkit-daemon[1287]: Supervising 5 threads of 2 processes of 2 users.
Oct 14 23:09:17 andrew-desktop rtkit-daemon[1287]: Sucessfully made thread 1521 of process 1495 (n/a) owned by '1000' RT at priority 5.
Oct 14 23:09:17 andrew-desktop rtkit-daemon[1287]: Supervising 6 threads of 2 processes of 2 users.
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto GAMEOFPRICKS'
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto GAMEOFPRICKS' requires no security.  No secrets needed.
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Config: added 'ssid' value 'GAMEOFPRICKS'
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 14 23:09:18 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Oct 14 23:09:19 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 14 23:09:23 andrew-desktop ntfs-3g[1607]: Version 2010.3.6 external FUSE 28
Oct 14 23:09:23 andrew-desktop ntfs-3g[1607]: Mounted /dev/sdc1 (Read-Write, label "THING 3", NTFS 3.1)
Oct 14 23:09:23 andrew-desktop ntfs-3g[1607]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 14 23:09:23 andrew-desktop ntfs-3g[1607]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096,default_permissions
Oct 14 23:09:23 andrew-desktop ntfs-3g[1607]: Global ownership and permissions enforced, configuration type 1
Oct 14 23:09:24 andrew-desktop wpa_supplicant[988]: Trying to associate with c0:3f:0e:4b:66:92 (SSID='GAMEOFPRICKS' freq=2437 MHz)
Oct 14 23:09:24 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 14 23:09:24 andrew-desktop kernel: [   46.987296] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:09:24 andrew-desktop kernel: [   46.987446] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Oct 14 23:09:24 andrew-desktop wpa_supplicant[988]: Association request to the driver failed
Oct 14 23:09:24 andrew-desktop wpa_supplicant[988]: Associated with c0:3f:0e:4b:66:92
Oct 14 23:09:24 andrew-desktop wpa_supplicant[988]: CTRL-EVENT-CONNECTED - Connection to c0:3f:0e:4b:66:92 completed (auth) [id=0 id_str=]
Oct 14 23:09:24 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Oct 14 23:09:24 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Oct 14 23:09:24 andrew-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'GAMEOFPRICKS'.
Oct 14 23:09:24 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
OctOct 14 23:18:29 andrew-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 14 23:18:29 andrew-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="803" x-info="http://www.rsyslog.com"] (re)start
Oct 14 23:18:29 andrew-desktop rsyslogd: rsyslogd's groupid changed to 103
Oct 14 23:18:29 andrew-desktop rsyslogd: rsyslogd's userid changed to 101
Oct 14 23:18:29 andrew-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] KERNEL supported cpus:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   Intel GenuineIntel
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   AMD AuthenticAMD
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   Centaur CentaurHauls
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] DMI present.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] MTRR default type: uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   00000-9FFFF write-back
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   D0000-DFFFF uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   E0000-EFFFF write-through
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   1 base 100000000 mask F80000000 write-back
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   2 base 180000000 mask FE0000000 write-back
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   4 base 0DDE00000 mask FFFE00000 uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   5 base 0DE000000 mask FFE000000 uncachable
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   6 disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   7 disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] e820 update range: 00000000dde00000 - 0000000100000000 (usable) ==> (reserved)

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] last_pfn = 0xddd80 max_arch_pfn = 0x400000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] modified physical RAM map:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000ddd80000 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd80000 - 00000000ddd8e000 (ACPI data)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000ddd8e000 - 00000000dddd0000 (ACPI NVS)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000dddd0000 - 00000000e0000000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  modified: 0000000100000000 - 00000001a0000000 (usable)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ddd80000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  0000000000 - 00ddc00000 page 2M
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  00ddc00000 - 00ddd80000 page 4k
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to ddd80000 @ 10000-16000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  0100000000 - 01a0000000 page 2M
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] kernel direct mapping tables up to 1a0000000 @ 14000-1c000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] RAMDISK: 377fb000 - 37fef3a7
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: RSDP 00000000000fb6c0 00014 (v00 ACPIAM)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: RSDT 00000000ddd80000 00044 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: FACP 00000000ddd80200 00084 (v02 A_M_I_ OEMFACP  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: DSDT 00000000ddd80440 08DAC (v01  A1355 A1355000 00000000 INTL 20060113)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: FACS 00000000ddd8e000 00040
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: APIC 00000000ddd80390 0006C (v01 A_M_I_ OEMAPIC  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: MCFG 00000000ddd80400 0003C (v01 A_M_I_ OEMMCFG  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: OEMB 00000000ddd8e040 00089 (v01 A_M_I_ AMI_OEM  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: HPET 00000000ddd891f0 00038 (v01 A_M_I_ OEMHPET  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: GSCI 00000000ddd8e0d0 02024 (v01 A_M_I_ GMCHSCI  05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: SSDT 00000000ddd90510 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: SLIC 00000000ddd89230 00176 (v01 _ASUS_ Notebook 05000913 MSFT 00000097)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] No NUMA configuration found
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Faking a node at 0000000000000000-00000001a0000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000001a0000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   NODE_DATA [0000000000017000 - 000000000001bfff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   bootmap [000000000001c000 -  000000000004ffff] pages 34
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 01a0000000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #3 [00377fb000 - 0037fef3a7]          RAMDISK ==> [00377fb000 - 0037fef3a7]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #5 [0001a2d000 - 0001a2d27c]              BRK ==> [0001a2d000 - 0001a2d27c]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   #7 [0000014000 - 0000017000]          PGTABLE ==> [0000014000 - 0000017000]
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0005bfffff] PMD -> [ffff880028600000-ffff88002dbfffff] on node 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x001a0000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000ddd80
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x001a0000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] On node 0 totalpages: 1563919
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA zone: 106 pages reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA zone: 3821 pages, LIFO batch:0
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   DMA32 zone: 890296 pages, LIFO batch:31
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   Normal zone: 8960 pages used for memmap
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000]   Normal zone: 646400 pages, LIFO batch:31
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] nr_irqs_gsi: 24
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd80000 - 00000000ddd8e000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ddd8e000 - 00000000dddd0000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dddd0000 - 00000000e0000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fee00000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ee00000)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1540517
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Policy zone: Normal
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=6da04b05-a4d6-4952-8112-2cb77027b607 ro quiet splash
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Initializing CPU#0
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Checking aperture...
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] No AGP bridge found
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Memory: 6082276k/6815744k available (5419k kernel code, 560068k absent, 173400k reserved, 2974k data, 872k init)
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] console [tty0] enabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] allocated 62914560 bytes of page_cgroup
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] hpet clockevent registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Oct 14 23:18:29 andrew-desktop kernel: [    0.000000] Detected 2599.491 MHz processor.
Oct 14 23:18:29 andrew-desktop kernel: [    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5198.98 BogoMIPS (lpj=25994910)
Oct 14 23:18:29 andrew-desktop kernel: [    0.010032] Security Framework initialized
Oct 14 23:18:29 andrew-desktop kernel: [    0.010051] AppArmor: AppArmor initialized
Oct 14 23:18:29 andrew-desktop kernel: [    0.010645] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.015374] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.017640] Mount-cache hash table entries: 256
Oct 14 23:18:29 andrew-desktop kernel: [    0.017793] Initializing cgroup subsys ns
Oct 14 23:18:29 andrew-desktop kernel: [    0.017798] Initializing cgroup subsys cpuacct
Oct 14 23:18:29 andrew-desktop kernel: [    0.017802] Initializing cgroup subsys memory
Oct 14 23:18:29 andrew-desktop kernel: [    0.017809] Initializing cgroup subsys devices
Oct 14 23:18:29 andrew-desktop kernel: [    0.017812] Initializing cgroup subsys freezer
Oct 14 23:18:29 andrew-desktop kernel: [    0.017813] Initializing cgroup subsys net_cls
Oct 14 23:18:29 andrew-desktop kernel: [    0.017834] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:18:29 andrew-desktop kernel: [    0.017836] CPU: L2 cache: 2048K
Oct 14 23:18:29 andrew-desktop kernel: [    0.017839] CPU 0/0x0 -> Node 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.017841] CPU: Physical Processor ID: 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.017842] CPU: Processor Core ID: 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.017845] mce: CPU supports 6 MCE banks
Oct 14 23:18:29 andrew-desktop kernel: [    0.017852] CPU0: Thermal monitoring enabled (TM2)
Oct 14 23:18:29 andrew-desktop kernel: [    0.017856] using mwait in idle threads.
Oct 14 23:18:29 andrew-desktop kernel: [    0.017858] Performance Events: Core2 events, Intel PMU driver.
Oct 14 23:18:29 andrew-desktop kernel: [    0.017863] ... version:                2
Oct 14 23:18:29 andrew-desktop kernel: [    0.017864] ... bit width:              40
Oct 14 23:18:29 andrew-desktop kernel: [    0.017865] ... generic registers:      2
Oct 14 23:18:29 andrew-desktop kernel: [    0.017867] ... value mask:             000000ffffffffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.017868] ... max period:             000000007fffffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.017869] ... fixed-purpose events:   3
Oct 14 23:18:29 andrew-desktop kernel: [    0.017870] ... event mask:             0000000700000003
Oct 14 23:18:29 andrew-desktop kernel: [    0.020293] ACPI: Core revision 20090903
Oct 14 23:18:29 andrew-desktop kernel: [    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 14 23:18:29 andrew-desktop kernel: [    0.040011] ftrace: allocating 22538 entries in 89 pages
Oct 14 23:18:29 andrew-desktop kernel: [    0.050054] Setting APIC routing to flat
Oct 14 23:18:29 andrew-desktop kernel: [    0.050359] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 14 23:18:29 andrew-desktop kernel: [    0.152468] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
Oct 14 23:18:29 andrew-desktop kernel: [    0.160000] APIC calibration not consistent with PM-Timer: 129ms instead of 100ms
Oct 14 23:18:29 andrew-desktop kernel: [    0.160000] APIC delta adjusted to PM-Timer: 1249997 (1624985)
Oct 14 23:18:29 andrew-desktop kernel: [    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] Initializing CPU#1
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU: L2 cache: 2048K
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Oct 14 23:18:29 andrew-desktop kernel: [    0.310061] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
Oct 14 23:18:29 andrew-desktop kernel: [    0.310067] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 14 23:18:29 andrew-desktop kernel: [    0.320017] Brought up 2 CPUs
Oct 14 23:18:29 andrew-desktop kernel: [    0.320019] Total of 2 processors activated (10398.96 BogoMIPS).
Oct 14 23:18:29 andrew-desktop kernel: [    0.320463] CPU0 attaching sched-domain:
Oct 14 23:18:29 andrew-desktop kernel: [    0.320467]  domain 0: span 0-1 level MC
Oct 14 23:18:29 andrew-desktop kernel: [    0.320469]   groups: 0 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.320475] CPU1 attaching sched-domain:
Oct 14 23:18:29 andrew-desktop kernel: [    0.320476]  domain 0: span 0-1 level MC
Oct 14 23:18:29 andrew-desktop kernel: [    0.320478]   groups: 1 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] devtmpfs: initialized
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] regulator: core version 0.5
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] Time:  3:18:18  Date: 10/15/10
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] NET: Registered protocol family 16
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] Trying to unpack rootfs image as initramfs...
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] ACPI: bus type pci registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] PCI: Not using MMCONFIG.
Oct 14 23:18:29 andrew-desktop kernel: [    0.320566] PCI: Using configuration type 1 for base access
Oct 14 23:18:29 andrew-desktop kernel: [    0.330159] bio: create slab <bio-0> at 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.330961] ACPI: EC: Look up EC in DSDT
Oct 14 23:18:29 andrew-desktop kernel: [    0.333669] ACPI: Executed 1 blocks of module-level executable AML code
Oct 14 23:18:29 andrew-desktop kernel: [    0.340040] ACPI: Interpreter enabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.340046] ACPI: (supports S0 S1 S3 S4 S5)
Oct 14 23:18:29 andrew-desktop kernel: [    0.340070] ACPI: Using IOAPIC for interrupt routing
Oct 14 23:18:29 andrew-desktop kernel: [    0.340124] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Oct 14 23:18:29 andrew-desktop kernel: [    0.343122] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Oct 14 23:18:29 andrew-desktop kernel: [    0.344926] PCI: Using MMCONFIG at f0000000 - f3ffffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.352512] ACPI Warning: Incorrect checksum in table [OEMB] - 9A, should be 95 (20090903/tbutils-314)
Oct 14 23:18:29 andrew-desktop kernel: [    0.353405] ACPI: No dock devices found.
Oct 14 23:18:29 andrew-desktop kernel: [    0.353545] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 14 23:18:29 andrew-desktop kernel: [    0.353633] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe400000-0xfe7fffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353639] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353643] pci 0000:00:02.0: reg 20 io port: [0xdc00-0xdc07]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353676] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe900000-0xfe9fffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353759] pci 0000:00:1a.0: reg 20 io port: [0xd480-0xd49f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353823] pci 0000:00:1a.1: reg 20 io port: [0xd800-0xd81f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353886] pci 0000:00:1a.2: reg 20 io port: [0xd880-0xd89f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.353956] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe8fb000-0xfe8fb3ff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354007] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.354011] pci 0000:00:1a.7: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.354047] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354084] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.354087] pci 0000:00:1b.0: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.354148] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.354151] pci 0000:00:1c.0: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.354213] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.354216] pci 0000:00:1c.5: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.354265] pci 0000:00:1d.0: reg 20 io port: [0xd000-0xd01f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354332] pci 0000:00:1d.1: reg 20 io port: [0xd080-0xd09f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354394] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354462] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8fa000-0xfe8fa3ff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354512] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.354516] pci 0000:00:1d.7: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.354675] pci 0000:00:1f.2: reg 10 io port: [0xbc00-0xbc07]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354680] pci 0000:00:1f.2: reg 14 io port: [0xb880-0xb883]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354685] pci 0000:00:1f.2: reg 18 io port: [0xb800-0xb807]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354689] pci 0000:00:1f.2: reg 1c io port: [0xb480-0xb483]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354694] pci 0000:00:1f.2: reg 20 io port: [0xb400-0xb40f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354699] pci 0000:00:1f.2: reg 24 io port: [0xb080-0xb08f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354742] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe8f9000-0xfe8f90ff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354754] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354793] pci 0000:00:1f.5: reg 10 io port: [0xcc00-0xcc07]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354798] pci 0000:00:1f.5: reg 14 io port: [0xc880-0xc883]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354803] pci 0000:00:1f.5: reg 18 io port: [0xc800-0xc807]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354808] pci 0000:00:1f.5: reg 1c io port: [0xc480-0xc483]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354812] pci 0000:00:1f.5: reg 20 io port: [0xc400-0xc40f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354817] pci 0000:00:1f.5: reg 24 io port: [0xc080-0xc08f]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354890] pci 0000:02:00.0: reg 10 32bit mmio: [0xfebf0000-0xfebfffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.354954] pci 0000:02:00.0: PME# supported from D0 D3hot
Oct 14 23:18:29 andrew-desktop kernel: [    0.354958] pci 0000:02:00.0: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.355005] pci 0000:00:1c.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355066] pci 0000:01:00.0: reg 10 io port: [0xe800-0xe8ff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355087] pci 0000:01:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355107] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355153] pci 0000:01:00.0: supports D1 D2
Oct 14 23:18:29 andrew-desktop kernel: [    0.355154] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
Oct 14 23:18:29 andrew-desktop kernel: [    0.355159] pci 0000:01:00.0: PME# disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.355208] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355211] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355257] pci 0000:00:1e.0: transparent bridge
Oct 14 23:18:29 andrew-desktop kernel: [    0.355279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Oct 14 23:18:29 andrew-desktop kernel: [    0.355565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Oct 14 23:18:29 andrew-desktop kernel: [    0.370793] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.370895] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371002] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371100] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371200] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371298] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371398] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371495] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 23:18:29 andrew-desktop kernel: [    0.371595] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 14 23:18:29 andrew-desktop kernel: [    0.371608] vgaarb: loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.371704] SCSI subsystem initialized
Oct 14 23:18:29 andrew-desktop kernel: [    0.371789] libata version 3.00 loaded.
Oct 14 23:18:29 andrew-desktop kernel: [    0.371849] usbcore: registered new interface driver usbfs
Oct 14 23:18:29 andrew-desktop kernel: [    0.371858] usbcore: registered new interface driver hub
Oct 14 23:18:29 andrew-desktop kernel: [    0.371883] usbcore: registered new device driver usb
Oct 14 23:18:29 andrew-desktop kernel: [    0.371992] ACPI: WMI: Mapper loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.371994] PCI: Using ACPI for IRQ routing
Oct 14 23:18:29 andrew-desktop kernel: [    0.372138] NetLabel: Initializing
Oct 14 23:18:29 andrew-desktop kernel: [    0.372139] NetLabel:  domain hash size = 128
Oct 14 23:18:29 andrew-desktop kernel: [    0.372140] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 14 23:18:29 andrew-desktop kernel: [    0.372152] NetLabel:  unlabeled traffic allowed by default
Oct 14 23:18:29 andrew-desktop kernel: [    0.372181] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Oct 14 23:18:29 andrew-desktop kernel: [    0.372186] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Oct 14 23:18:29 andrew-desktop kernel: [    0.380049] Switching to clocksource tsc
Oct 14 23:18:29 andrew-desktop kernel: [    0.381584] AppArmor: AppArmor Filesystem Enabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.381600] pnp: PnP ACPI init
Oct 14 23:18:29 andrew-desktop kernel: [    0.381617] ACPI: bus type pnp registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.385181] pnp: PnP ACPI: found 16 devices
Oct 14 23:18:29 andrew-desktop kernel: [    0.385183] ACPI: ACPI bus type pnp unregistered
Oct 14 23:18:29 andrew-desktop kernel: [    0.385196] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385202] system 00:07: ioport range 0x290-0x297 has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385208] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385210] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385212] system 00:08: ioport range 0x500-0x57f has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385214] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385216] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385218] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385220] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385229] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385233] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385236] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385240] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385244] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385246] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385248] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385250] system 00:0f: iomem range 0x100000-0xdddfffff could not be reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.385253] system 00:0f: iomem range 0xf0000000-0xffffffff could not be reserved
Oct 14 23:18:29 andrew-desktop kernel: [    0.389974] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Oct 14 23:18:29 andrew-desktop kernel: [    0.389978] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Oct 14 23:18:29 andrew-desktop kernel: [    0.389982] pci 0000:00:1c.0:   MEM window: 0xfeb00000-0xfebfffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.389985] pci 0000:00:1c.0:   PREFETCH window: 0x000000f4000000-0x000000f41fffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.389991] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
Oct 14 23:18:29 andrew-desktop kernel: [    0.389993] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Oct 14 23:18:29 andrew-desktop kernel: [    0.389997] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.390001] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4200000-0x000000f43fffff
Oct 14 23:18:29 andrew-desktop kernel: [    0.390007] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Oct 14 23:18:29 andrew-desktop kernel: [    0.390008] pci 0000:00:1e.0:   IO window: disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.390012] pci 0000:00:1e.0:   MEM window: disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.390016] pci 0000:00:1e.0:   PREFETCH window: disabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.390027] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Oct 14 23:18:29 andrew-desktop kernel: [    0.390035]   alloc irq_desc for 17 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.390037]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.390043] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:18:29 andrew-desktop kernel: [    0.390047] pci 0000:00:1c.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.390054]   alloc irq_desc for 16 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.390055]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.390058] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:18:29 andrew-desktop kernel: [    0.390061] pci 0000:00:1c.5: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.390067] pci 0000:00:1e.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.390071] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390073] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390075] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390077] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390079] pci_bus 0000:02: resource 2 pref mem [0xf4000000-0xf41fffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390081] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390083] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390085] pci_bus 0000:01: resource 2 pref mem [0xf4200000-0xf43fffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390087] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390089] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Oct 14 23:18:29 andrew-desktop kernel: [    0.390121] NET: Registered protocol family 2
Oct 14 23:18:29 andrew-desktop kernel: [    0.390336] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.391903] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.396995] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.397634] TCP: Hash tables configured (established 524288 bind 65536)
Oct 14 23:18:29 andrew-desktop kernel: [    0.397636] TCP reno registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.397753] NET: Registered protocol family 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.397779] pci 0000:00:02.0: Boot video device
Oct 14 23:18:29 andrew-desktop kernel: [    0.398100] Scanning for low memory corruption every 60 seconds
Oct 14 23:18:29 andrew-desktop kernel: [    0.398235] audit: initializing netlink socket (disabled)
Oct 14 23:18:29 andrew-desktop kernel: [    0.398244] type=2000 audit(1287112698.389:1): initialized
Oct 14 23:18:29 andrew-desktop kernel: [    0.406223] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 14 23:18:29 andrew-desktop kernel: [    0.407332] VFS: Disk quotas dquot_6.5.2
Oct 14 23:18:29 andrew-desktop kernel: [    0.407378] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 14 23:18:29 andrew-desktop kernel: [    0.407840] fuse init (API version 7.13)
Oct 14 23:18:29 andrew-desktop kernel: [    0.407903] msgmni has been set to 11879
Oct 14 23:18:29 andrew-desktop kernel: [    0.408083] alg: No test for stdrng (krng)
Oct 14 23:18:29 andrew-desktop kernel: [    0.408126] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:18:29 andrew-desktop kernel: [    0.408129] io scheduler noop registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.408130] io scheduler anticipatory registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.408132] io scheduler deadline registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.408158] io scheduler cfq registered (default)
Oct 14 23:18:29 andrew-desktop kernel: [    0.408285]   alloc irq_desc for 24 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.408287]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.408296] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Oct 14 23:18:29 andrew-desktop kernel: [    0.408303] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.408405]   alloc irq_desc for 25 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.408406]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.408413] pcieport 0000:00:1c.5: irq 25 for MSI/MSI-X
Oct 14 23:18:29 andrew-desktop kernel: [    0.408420] pcieport 0000:00:1c.5: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.408486] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 14 23:18:29 andrew-desktop kernel: [    0.408557] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 14 23:18:29 andrew-desktop kernel: [    0.408668] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Oct 14 23:18:29 andrew-desktop kernel: [    0.408671] ACPI: Power Button [PWRB]
Oct 14 23:18:29 andrew-desktop kernel: [    0.408708] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 14 23:18:29 andrew-desktop kernel: [    0.408710] ACPI: Power Button [PWRF]
Oct 14 23:18:29 andrew-desktop kernel: [    0.409341] ACPI: SSDT 00000000ddd90100 00406 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Oct 14 23:18:29 andrew-desktop kernel: [    0.409682] processor LNXCPU:00: registered as cooling_device0
Oct 14 23:18:29 andrew-desktop kernel: [    0.409713] processor LNXCPU:01: registered as cooling_device1
Oct 14 23:18:29 andrew-desktop kernel: [    0.413424] Linux agpgart interface v0.103
Oct 14 23:18:29 andrew-desktop kernel: [    0.413455] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 14 23:18:29 andrew-desktop kernel: [    0.413554] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:18:29 andrew-desktop kernel: [    0.413859] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 23:18:29 andrew-desktop kernel: [    0.414693] brd: module loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.415079] loop: module loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.415152] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Oct 14 23:18:29 andrew-desktop kernel: [    0.415241] ata_piix 0000:00:1f.2: version 2.13
Oct 14 23:18:29 andrew-desktop kernel: [    0.415258]   alloc irq_desc for 19 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.415260]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.415267] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.415272] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 14 23:18:29 andrew-desktop kernel: [    0.415316] ata_piix 0000:00:1f.2: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.415395] scsi0 : ata_piix
Oct 14 23:18:29 andrew-desktop kernel: [    0.415455] scsi1 : ata_piix
Oct 14 23:18:29 andrew-desktop kernel: [    0.416758] ata1: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.416762] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.416782] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.416786] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 14 23:18:29 andrew-desktop kernel: [    0.416817] ata_piix 0000:00:1f.5: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.416851] scsi2 : ata_piix
Oct 14 23:18:29 andrew-desktop kernel: [    0.416897] scsi3 : ata_piix
Oct 14 23:18:29 andrew-desktop kernel: [    0.417871] ata3: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.417874] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.418122] Fixed MDIO Bus: probed
Oct 14 23:18:29 andrew-desktop kernel: [    0.418147] PPP generic driver version 2.4.2
Oct 14 23:18:29 andrew-desktop kernel: [    0.418188] tun: Universal TUN/TAP device driver, 1.6
Oct 14 23:18:29 andrew-desktop kernel: [    0.418189] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 14 23:18:29 andrew-desktop kernel: [    0.418274] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 14 23:18:29 andrew-desktop kernel: [    0.418290]   alloc irq_desc for 18 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.418292]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.418297] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:18:29 andrew-desktop kernel: [    0.418322] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.418325] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.418349] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.418375] ehci_hcd 0000:00:1a.7: debug port 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.422266] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Oct 14 23:18:29 andrew-desktop kernel: [    0.422286] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe8fb000
Oct 14 23:18:29 andrew-desktop kernel: [    0.439667] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Oct 14 23:18:29 andrew-desktop kernel: [    0.439782] usb usb1: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.439806] hub 1-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.439814] hub 1-0:1.0: 6 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.439885]   alloc irq_desc for 23 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.439887]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.439893] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:18:29 andrew-desktop kernel: [    0.439917] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.439920] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.439950] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 14 23:18:29 andrew-desktop kernel: [    0.439977] ehci_hcd 0000:00:1d.7: debug port 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.443841] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Oct 14 23:18:29 andrew-desktop kernel: [    0.443859] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8fa000
Oct 14 23:18:29 andrew-desktop kernel: [    0.459647] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 14 23:18:29 andrew-desktop kernel: [    0.459772] usb usb2: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.459795] hub 2-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.459804] hub 2-0:1.0: 6 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.459864] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 14 23:18:29 andrew-desktop kernel: [    0.459880] uhci_hcd: USB Universal Host Controller Interface driver
Oct 14 23:18:29 andrew-desktop kernel: [    0.459923]   alloc irq_desc for 20 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.459925]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.459930] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 14 23:18:29 andrew-desktop kernel: [    0.459939] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.459942] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.459971] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Oct 14 23:18:29 andrew-desktop kernel: [    0.460005] uhci_hcd 0000:00:1a.0: irq 20, io base 0x0000d480
Oct 14 23:18:29 andrew-desktop kernel: [    0.460076] usb usb3: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.460094] hub 3-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.460099] hub 3-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.460135]   alloc irq_desc for 21 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.460136]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    0.460140] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Oct 14 23:18:29 andrew-desktop kernel: [    0.460144] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.460147] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.460169] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Oct 14 23:18:29 andrew-desktop kernel: [    0.460197] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d800
Oct 14 23:18:29 andrew-desktop kernel: [    0.460265] usb usb4: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.460284] hub 4-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.460289] hub 4-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.460326] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:18:29 andrew-desktop kernel: [    0.460331] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.460334] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.460367] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Oct 14 23:18:29 andrew-desktop kernel: [    0.460389] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d880
Oct 14 23:18:29 andrew-desktop kernel: [    0.460454] usb usb5: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.460472] hub 5-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.460477] hub 5-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.460511] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 23:18:29 andrew-desktop kernel: [    0.460515] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.460518] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.460553] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Oct 14 23:18:29 andrew-desktop kernel: [    0.460574] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d000
Oct 14 23:18:29 andrew-desktop kernel: [    0.460639] usb usb6: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.460660] hub 6-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.460665] hub 6-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.460702] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 23:18:29 andrew-desktop kernel: [    0.460706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.460709] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.460730] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Oct 14 23:18:29 andrew-desktop kernel: [    0.460752] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d080
Oct 14 23:18:29 andrew-desktop kernel: [    0.460829] usb usb7: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.460850] hub 7-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.460857] hub 7-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.460889] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 23:18:29 andrew-desktop kernel: [    0.460893] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    0.460896] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 14 23:18:29 andrew-desktop kernel: [    0.460917] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Oct 14 23:18:29 andrew-desktop kernel: [    0.460938] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Oct 14 23:18:29 andrew-desktop kernel: [    0.461010] usb usb8: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    0.461028] hub 8-0:1.0: USB hub found
Oct 14 23:18:29 andrew-desktop kernel: [    0.461034] hub 8-0:1.0: 2 ports detected
Oct 14 23:18:29 andrew-desktop kernel: [    0.461111] PNP: No PS/2 controller found. Probing ports directly.
Oct 14 23:18:29 andrew-desktop kernel: [    0.463646] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.463652] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 14 23:18:29 andrew-desktop kernel: [    0.463756] mice: PS/2 mouse device common for all mice
Oct 14 23:18:29 andrew-desktop kernel: [    0.463853] rtc_cmos 00:03: RTC can wake from S4
Oct 14 23:18:29 andrew-desktop kernel: [    0.463888] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Oct 14 23:18:29 andrew-desktop kernel: [    0.463910] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 14 23:18:29 andrew-desktop kernel: [    0.464019] device-mapper: uevent: version 1.0.3
Oct 14 23:18:29 andrew-desktop kernel: [    0.464117] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Oct 14 23:18:29 andrew-desktop kernel: [    0.464167] device-mapper: multipath: version 1.1.0 loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.464169] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 14 23:18:29 andrew-desktop kernel: [    0.464286] cpuidle: using governor ladder
Oct 14 23:18:29 andrew-desktop kernel: [    0.464287] cpuidle: using governor menu
Oct 14 23:18:29 andrew-desktop kernel: [    0.464569] TCP cubic registered
Oct 14 23:18:29 andrew-desktop kernel: [    0.464685] NET: Registered protocol family 10
Oct 14 23:18:29 andrew-desktop kernel: [    0.465049] lo: Disabled Privacy Extensions
Oct 14 23:18:29 andrew-desktop kernel: [    0.465262] NET: Registered protocol family 17
Oct 14 23:18:29 andrew-desktop kernel: [    0.465804] PM: Resume from disk failed.
Oct 14 23:18:29 andrew-desktop kernel: [    0.465815] registered taskstats version 1
Oct 14 23:18:29 andrew-desktop kernel: [    0.466166]   Magic number: 14:736:310
Oct 14 23:18:29 andrew-desktop kernel: [    0.466198] tty tty39: hash matches
Oct 14 23:18:29 andrew-desktop kernel: [    0.466263] rtc_cmos 00:03: setting system clock to 2010-10-15 03:18:18 UTC (1287112698)
Oct 14 23:18:29 andrew-desktop kernel: [    0.466265] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 14 23:18:29 andrew-desktop kernel: [    0.466267] EDD information not available.
Oct 14 23:18:29 andrew-desktop kernel: [    0.473622] Freeing initrd memory: 8144k freed
Oct 14 23:18:29 andrew-desktop kernel: [    0.780222] ata3: SATA link down (SStatus 0 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    0.790941] ata4: SATA link down (SStatus 0 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    0.939516] usb 2-4: new high speed USB device using ehci_hcd and address 3
Oct 14 23:18:29 andrew-desktop kernel: [    1.091165] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    1.270025] usb 2-6: new high speed USB device using ehci_hcd and address 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.300068] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    1.300084] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    1.300262] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    1.300273] ata2.01: SATA link down (SStatus 0 SControl 300)
Oct 14 23:18:29 andrew-desktop kernel: [    1.300282] ata2.01: link offline, clearing class 3 to NONE
Oct 14 23:18:29 andrew-desktop kernel: [    1.320378] ata2.00: ATAPI: ATAPI   DVD A  DH20A6S, 7P56, max UDMA/100
Oct 14 23:18:29 andrew-desktop kernel: [    1.340488] ata1.00: ATA-8: Hitachi HDT721064SLA360, STDOA31B, max UDMA/133
Oct 14 23:18:29 andrew-desktop kernel: [    1.340494] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:18:29 andrew-desktop kernel: [    1.340727] ata1.01: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
Oct 14 23:18:29 andrew-desktop kernel: [    1.340732] ata1.01: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 14 23:18:29 andrew-desktop kernel: [    1.360236] ata2.00: configured for UDMA/100
Oct 14 23:18:29 andrew-desktop kernel: [    1.380430] ata1.00: configured for UDMA/133
Oct 14 23:18:29 andrew-desktop kernel: [    1.421313] usb 2-6: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    1.422192] ata1.01: configured for UDMA/133
Oct 14 23:18:29 andrew-desktop kernel: [    1.422358] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72106 STDO PQ: 0 ANSI: 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.422456] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Oct 14 23:18:29 andrew-desktop kernel: [    1.422459] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 14 23:18:29 andrew-desktop kernel: [    1.422493] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 23:18:29 andrew-desktop kernel: [    1.422495] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 14 23:18:29 andrew-desktop kernel: [    1.422514] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:18:29 andrew-desktop kernel: [    1.422544] scsi 0:0:1:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.422633] sd 0:0:1:0: Attached scsi generic sg1 type 0
Oct 14 23:18:29 andrew-desktop kernel: [    1.422643]  sda:
Oct 14 23:18:29 andrew-desktop kernel: [    1.423839] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A6S   7P56 PQ: 0 ANSI: 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.429702] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 14 23:18:29 andrew-desktop kernel: [    1.429706] Uniform CD-ROM driver Revision: 3.20
Oct 14 23:18:29 andrew-desktop kernel: [    1.429837] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 14 23:18:29 andrew-desktop kernel: [    1.429889] sr 1:0:0:0: Attached scsi generic sg2 type 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.441279]  sda1 sda2 <
Oct 14 23:18:29 andrew-desktop kernel: [    1.441291] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Oct 14 23:18:29 andrew-desktop kernel: [    1.473761]  sda5 >
Oct 14 23:18:29 andrew-desktop kernel: [    1.473810] sd 0:0:1:0: [sdb] Write Protect is off
Oct 14 23:18:29 andrew-desktop kernel: [    1.473815] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Oct 14 23:18:29 andrew-desktop kernel: [    1.473854] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 23:18:29 andrew-desktop kernel: [    1.474009]  sdb: sdb1 sdb2 < sdb5 >
Oct 14 23:18:29 andrew-desktop kernel: [    1.665499] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 14 23:18:29 andrew-desktop kernel: [    1.665716] sd 0:0:1:0: [sdb] Attached SCSI disk
Oct 14 23:18:29 andrew-desktop kernel: [    1.665734] Freeing unused kernel memory: 872k freed
Oct 14 23:18:29 andrew-desktop kernel: [    1.666066] Write protecting the kernel read-only data: 7692k
Oct 14 23:18:29 andrew-desktop kernel: [    1.677344] udev: starting version 151
Oct 14 23:18:29 andrew-desktop kernel: [    1.700032] usb 4-1: new full speed USB device using uhci_hcd and address 2
Oct 14 23:18:29 andrew-desktop kernel: [    1.733499] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 14 23:18:29 andrew-desktop kernel: [    1.733523] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 23:18:29 andrew-desktop kernel: [    1.733576] r8169 0000:01:00.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [    1.733633]   alloc irq_desc for 26 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    1.733635]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [    1.733649] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
Oct 14 23:18:29 andrew-desktop kernel: [    1.734106] eth0: RTL8168b/8111b at 0xffffc90000c76000, 00:24:8c:e6:75:c8, XID 18000000 IRQ 26
Oct 14 23:18:29 andrew-desktop kernel: [    1.745434] Initializing USB Mass Storage driver...
Oct 14 23:18:29 andrew-desktop kernel: [    1.773251] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 14 23:18:29 andrew-desktop kernel: [    1.775389] usb-storage: device found at 3
Oct 14 23:18:29 andrew-desktop kernel: [    1.775391] usb-storage: waiting for device to settle before scanning
Oct 14 23:18:29 andrew-desktop kernel: [    1.776249] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 14 23:18:29 andrew-desktop kernel: [    1.776337] usbcore: registered new interface driver usb-storage
Oct 14 23:18:29 andrew-desktop kernel: [    1.776340] USB Mass Storage support registered.
Oct 14 23:18:29 andrew-desktop kernel: [    1.776427] usb-storage: device found at 5
Oct 14 23:18:29 andrew-desktop kernel: [    1.776428] usb-storage: waiting for device to settle before scanning
Oct 14 23:18:29 andrew-desktop kernel: [    1.830026] usb 4-1: device descriptor read/64, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    2.070020] usb 4-1: device descriptor read/64, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    2.185573] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Oct 14 23:18:29 andrew-desktop kernel: [    2.185577] EXT4-fs (sda1): write access will be enabled during recovery
Oct 14 23:18:29 andrew-desktop kernel: [    2.300026] usb 4-1: new full speed USB device using uhci_hcd and address 3
Oct 14 23:18:29 andrew-desktop kernel: [    2.430014] usb 4-1: device descriptor read/64, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    2.517316] EXT4-fs (sda1): recovery complete
Oct 14 23:18:29 andrew-desktop kernel: [    2.517708] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 14 23:18:29 andrew-desktop kernel: [    2.670029] usb 4-1: device descriptor read/64, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    2.900041] usb 4-1: new full speed USB device using uhci_hcd and address 4
Oct 14 23:18:29 andrew-desktop kernel: [    3.320019] usb 4-1: device not accepting address 4, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    3.440020] usb 4-1: new full speed USB device using uhci_hcd and address 5
Oct 14 23:18:29 andrew-desktop kernel: [    3.860018] usb 4-1: device not accepting address 5, error -71
Oct 14 23:18:29 andrew-desktop kernel: [    3.860040] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:18:29 andrew-desktop kernel: [    4.140030] usb 7-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:18:29 andrew-desktop kernel: [    4.319682] usb 7-1: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    4.600023] usb 8-1: new low speed USB device using uhci_hcd and address 2
Oct 14 23:18:29 andrew-desktop kernel: [    4.783959] usb 8-1: configuration #1 chosen from 1 choice
Oct 14 23:18:29 andrew-desktop kernel: [    6.770231] usb-storage: device scan complete
Oct 14 23:18:29 andrew-desktop kernel: [    6.770281] usb-storage: device scan complete
Oct 14 23:18:29 andrew-desktop kernel: [    6.770820] scsi 5:0:0:0: Direct-Access     WD       15EADS External  1.75 PQ: 0 ANSI: 4
Oct 14 23:18:29 andrew-desktop kernel: [    6.770884] scsi 4:0:0:0: Direct-Access     WD       5000AAV External 1.75 PQ: 0 ANSI: 4
Oct 14 23:18:29 andrew-desktop kernel: [    6.771240] sd 5:0:0:0: Attached scsi generic sg3 type 0
Oct 14 23:18:29 andrew-desktop kernel: [    6.771509] sd 4:0:0:0: Attached scsi generic sg4 type 0
Oct 14 23:18:29 andrew-desktop kernel: [    6.771800] sd 5:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Oct 14 23:18:29 andrew-desktop kernel: [    6.772051] sd 4:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 14 23:18:29 andrew-desktop kernel: [    6.772292] sd 5:0:0:0: [sdc] Write Protect is off
Oct 14 23:18:29 andrew-desktop kernel: [    6.772297] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
Oct 14 23:18:29 andrew-desktop kernel: [    6.772300] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.772566] sd 4:0:0:0: [sdd] Write Protect is off
Oct 14 23:18:29 andrew-desktop kernel: [    6.772570] sd 4:0:0:0: [sdd] Mode Sense: 23 00 00 00
Oct 14 23:18:29 andrew-desktop kernel: [    6.772574] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.773412] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.773416]  sdc:
Oct 14 23:18:29 andrew-desktop kernel: [    6.773676] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.773680]  sdd: sdc1
Oct 14 23:18:29 andrew-desktop kernel: [    6.775042] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.775047] sd 5:0:0:0: [sdc] Attached SCSI disk
Oct 14 23:18:29 andrew-desktop kernel: [    6.793060]  sdd1
Oct 14 23:18:29 andrew-desktop kernel: [    6.794295] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct 14 23:18:29 andrew-desktop kernel: [    6.794300] sd 4:0:0:0: [sdd] Attached SCSI disk
Oct 14 23:18:29 andrew-desktop kernel: [   10.600142] udev: starting version 151
Oct 14 23:18:29 andrew-desktop kernel: [   10.629175] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Oct 14 23:18:29 andrew-desktop kernel: [   10.629755] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Oct 14 23:18:29 andrew-desktop kernel: [   10.832349] Adding 17844216k swap on /dev/sda5.  Priority:-1 extents:1 across:17844216k 
Oct 14 23:18:29 andrew-desktop kernel: [   10.837998] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Oct 14 23:18:29 andrew-desktop kernel: [   10.844654] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Oct 14 23:18:29 andrew-desktop kernel: [   10.848057] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:18:29 andrew-desktop kernel: [   10.848189] 
Oct 14 23:18:29 andrew-desktop kernel: [   10.848189] 
Oct 14 23:18:29 andrew-desktop kernel: [   10.848190] === pAd = ffffc90006451000, size = 627064 ===
Oct 14 23:18:29 andrew-desktop kernel: [   10.848190] 
Oct 14 23:18:29 andrew-desktop kernel: [   10.848192] <-- RTMPAllocAdapterBlock, Status=0
Oct 14 23:18:29 andrew-desktop kernel: [   10.848231] rt2860 0000:02:00.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [   10.852380] [drm] Initialized drm 1.1.0 20060810
Oct 14 23:18:29 andrew-desktop kernel: [   10.858226] parport_pc 00:06: reported by Plug and Play ACPI
Oct 14 23:18:29 andrew-desktop kernel: [   10.858338] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct 14 23:18:29 andrew-desktop kernel: [   10.863063] usbcore: registered new interface driver hiddev
Oct 14 23:18:29 andrew-desktop kernel: [   10.879100] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3
Oct 14 23:18:29 andrew-desktop kernel: [   10.879194] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
Oct 14 23:18:29 andrew-desktop kernel: [   10.879543] lp: driver loaded but no devices found
Oct 14 23:18:29 andrew-desktop kernel: [   10.894367] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
Oct 14 23:18:29 andrew-desktop kernel: [   10.894445] generic-usb 0003:046D:C312.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input0
Oct 14 23:18:29 andrew-desktop kernel: [   10.903544] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 23:18:29 andrew-desktop kernel: [   10.903549] i915 0000:00:02.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [   10.908912] ppdev: user-space parallel port driver
Oct 14 23:18:29 andrew-desktop kernel: [   10.919169] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Oct 14 23:18:29 andrew-desktop kernel: [   10.919173] [drm] MTRR allocation failed.  Graphics performance may suffer.
Oct 14 23:18:29 andrew-desktop kernel: [   10.919283]   alloc irq_desc for 27 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [   10.919285]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [   10.919295] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Oct 14 23:18:29 andrew-desktop kernel: [   10.919301] [drm] set up 31M of stolen space
Oct 14 23:18:29 andrew-desktop kernel: [   10.937155] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input5
Oct 14 23:18:29 andrew-desktop kernel: [   10.937268] generic-usb 0003:046D:C312.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input1
Oct 14 23:18:29 andrew-desktop kernel: [   10.937292] usbcore: registered new interface driver usbhid
Oct 14 23:18:29 andrew-desktop kernel: [   10.937294] usbhid: v2.6:USB HID core driver
Oct 14 23:18:29 andrew-desktop kernel: [   10.950226] lp0: using parport0 (interrupt-driven).
Oct 14 23:18:29 andrew-desktop kernel: [   10.994306] type=1505 audit(1287112709.024:2):  operation="profile_load" pid=655 name="/sbin/dhclient3"
Oct 14 23:18:29 andrew-desktop kernel: [   10.994826] type=1505 audit(1287112709.024:3):  operation="profile_load" pid=655 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:18:29 andrew-desktop kernel: [   10.995105] type=1505 audit(1287112709.024:4):  operation="profile_load" pid=655 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  starting...
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  Trying to start the modem-manager...
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0)
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Oct 14 23:18:29 andrew-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:18:29 andrew-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 14 23:18:29 andrew-desktop kernel: [   11.272683] fb0: inteldrmfb frame buffer device
Oct 14 23:18:29 andrew-desktop kernel: [   11.272685] registered panic notifier
Oct 14 23:18:29 andrew-desktop kernel: [   11.272944] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 14 23:18:29 andrew-desktop kernel: [   11.273028]   alloc irq_desc for 22 on node -1
Oct 14 23:18:29 andrew-desktop kernel: [   11.273031]   alloc kstat_irqs on node -1
Oct 14 23:18:29 andrew-desktop kernel: [   11.273038] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 14 23:18:29 andrew-desktop kernel: [   11.273071] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 14 23:18:29 andrew-desktop kernel: [   11.275440] vga16fb: initializing
Oct 14 23:18:29 andrew-desktop kernel: [   11.275444] vga16fb: mapped to 0xffff8800000a0000
Oct 14 23:18:29 andrew-desktop kernel: [   11.275448] vga16fb: not registering due to another framebuffer present
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (11069728) ... get_connections.
Oct 14 23:18:29 andrew-desktop NetworkManager:    SCPlugin-Ifupdown: (11069728) ... get_connections (managed=false): return empty list.
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Novatel
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Nokia
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin ZTE
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin AnyData
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin MotoC
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Option
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Sierra
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Huawei
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Gobi
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Ericsson MBM
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Longcheer
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Generic
Oct 14 23:18:29 andrew-desktop modem-manager: Loaded plugin Option High-Speed
Oct 14 23:18:29 andrew-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt2860')
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): now managed
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): bringing up device.
Oct 14 23:18:29 andrew-desktop avahi-daemon[848]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Oct 14 23:18:29 andrew-desktop avahi-daemon[848]: Successfully dropped root privileges.
Oct 14 23:18:29 andrew-desktop avahi-daemon[848]: avahi-daemon 0.6.25 starting up.
Oct 14 23:18:29 andrew-desktop avahi-daemon[848]: Successfully called chroot().
Oct 14 23:18:29 andrew-desktop avahi-daemon[848]: Successfully dropped remaining capabilities.
Oct 14 23:18:29 andrew-desktop gdm-binary[849]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): preparing device.
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Oct 14 23:18:29 andrew-desktop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): carrier is OFF
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): now managed
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): bringing up device.
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): preparing device.
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Oct 14 23:18:29 andrew-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:01:00.0/net/eth0
Oct 14 23:18:29 andrew-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  modem-manager is now available
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  Trying to start the supplicant...
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Oct 14 23:18:29 andrew-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Oct 14 23:18:29 andrew-desktop kernel: [   11.306249] RX DESC ffff8800dd82e000  size = 2048
Oct 14 23:18:29 andrew-desktop kernel: [   11.306456] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 14 23:18:29 andrew-desktop kernel: [   11.309639] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Oct 14 23:18:29 andrew-desktop kernel: [   11.309642] 1. Phy Mode = 0
Oct 14 23:18:29 andrew-desktop kernel: [   11.309643] 2. Phy Mode = 0
Oct 14 23:18:29 andrew-desktop kernel: [   11.329217] 3. Phy Mode = 0
Oct 14 23:18:29 andrew-desktop kernel: [   11.338187] type=1505 audit(1287112709.364:5):  operation="profile_load" pid=876 name="/usr/share/gdm/guest-session/Xsession"
Oct 14 23:18:29 andrew-desktop kernel: [   11.339549] type=1505 audit(1287112709.364:6):  operation="profile_replace" pid=877 name="/sbin/dhclient3"
Oct 14 23:18:29 andrew-desktop kernel: [   11.340092] type=1505 audit(1287112709.364:7):  operation="profile_replace" pid=877 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 14 23:18:29 andrew-desktop kernel: [   11.340440] type=1505 audit(1287112709.364:8):  operation="profile_replace" pid=877 name="/usr/lib/connman/scripts/dhclient-script"
Oct 14 23:18:29 andrew-desktop kernel: [   11.342988] type=1505 audit(1287112709.374:9):  operation="profile_load" pid=878 name="/usr/bin/evince"
Oct 14 23:18:29 andrew-desktop kernel: [   11.349781] type=1505 audit(1287112709.374:10):  operation="profile_load" pid=878 name="/usr/bin/evince-previewer"
Oct 14 23:18:29 andrew-desktop kernel: [   11.351860] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 14 23:18:29 andrew-desktop kernel: [   11.351863] MCS Set = 00 00 00 00 00
Oct 14 23:18:29 andrew-desktop kernel: [   11.353447] <==== RTMPInitialize, Status=0
Oct 14 23:18:29 andrew-desktop kernel: [   11.353510] 0x1300 = 00073200
Oct 14 23:18:29 andrew-desktop kernel: [   11.357066] type=1505 audit(1287112709.384:11):  operation="profile_load" pid=878 name="/usr/bin/evince-thumbnailer"
Oct 14 23:18:29 andrew-desktop kernel: [   11.359614] r8169: eth0: link down
Oct 14 23:18:29 andrew-desktop kernel: [   11.360435] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 23:18:29 andrew-desktop kernel: [   11.454040] Console: switching to colour frame buffer device 210x65
Oct 14 23:18:29 andrew-desktop kernel: [   11.517212] hda_codec: ALC887: BIOS auto-probing.
Oct 14 23:18:29 andrew-desktop kernel: [   11.518669] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Oct 14 23:18:34 andrew-desktop kernel: [   16.430033] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:18:37 andrew-desktop wpa_supplicant[911]: No network configuration found for the current AP
Oct 14 23:18:37 andrew-desktop wpa_supplicant[911]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 14 23:18:37 andrew-desktop wpa_supplicant[911]: last message repeated 2 times
Oct 14 23:18:37 andrew-desktop kernel: [   19.430014] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct 14 23:18:39 andrew-desktop kernel: [   21.610006] wlan0: no IPv6 routers present
Oct 14 23:18:54 andrew-desktop gdm-binary[849]: WARNING: Unable to find users: no seat-id found
Oct 14 23:18:54 andrew-desktop gdm-simple-slave[1013]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:18:55 andrew-desktop kernel: [   36.977033] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: No service file found in /etc/avahi/services.
Oct 14 23:18:57 andrew-desktop console-kit-daemon[1016]: WARNING: Failed to acquire org.freedesktop.ConsoleKit
Oct 14 23:18:57 andrew-desktop console-kit-daemon[1016]: WARNING: Could not acquire name; bailing out
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: Network interface enumeration completed.
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: Registering new address record for fe80::222:43ff:fe64:80ab on wlan0.*.
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: Server startup complete. Host name is andrew-desktop.local. Local service cookie is 2104631956.
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: Registering HINFO record with values 'X86_64'/'LINUX'.
Oct 14 23:18:57 andrew-desktop avahi-daemon[848]: write() failed while writing return value to pipe: Broken pipe

---

### Post by Blimpsgo90 on 2010-10-15
Oct 14 23:18:57 andrew-desktop init: apport pre-start process (1135) terminated with status 1
Oct 14 23:18:57 andrew-desktop cron[1148]: (CRON) INFO (pidfile fd = 3)
Oct 14 23:18:57 andrew-desktop acpid: starting up with proc fs
Oct 14 23:18:57 andrew-desktop init: apport post-stop process (1158) terminated with status 1
Oct 14 23:18:57 andrew-desktop acpid: 36 rules loaded
Oct 14 23:18:57 andrew-desktop acpid: waiting for events: event logging is off
Oct 14 23:18:57 andrew-desktop anacron[1176]: Anacron 2.3 started on 2010-10-14
Oct 14 23:18:57 andrew-desktop cron[1190]: (CRON) STARTUP (fork ok)
Oct 14 23:18:57 andrew-desktop cron[1190]: (CRON) INFO (Running @reboot jobs)
Oct 14 23:18:58 andrew-desktop anacron[1176]: Normal exit (0 jobs run)
Oct 14 23:18:58 andrew-desktop anacron[1268]: Anacron 2.3 started on 2010-10-14
Oct 14 23:18:58 andrew-desktop anacron[1268]: Normal exit (0 jobs run)
Oct 14 23:18:58 andrew-desktop kernel: [   40.492895] CPU0 attaching NULL sched-domain.
Oct 14 23:18:58 andrew-desktop kernel: [   40.492901] CPU1 attaching NULL sched-domain.
Oct 14 23:18:58 andrew-desktop kernel: [   40.561313] CPU0 attaching sched-domain:
Oct 14 23:18:58 andrew-desktop kernel: [   40.561316]  domain 0: span 0-1 level MC
Oct 14 23:18:58 andrew-desktop kernel: [   40.561318]   groups: 0 1
Oct 14 23:18:58 andrew-desktop kernel: [   40.561323] CPU1 attaching sched-domain:
Oct 14 23:18:58 andrew-desktop kernel: [   40.561324]  domain 0: span 0-1 level MC
Oct 14 23:18:58 andrew-desktop kernel: [   40.561326]   groups: 1 0
Oct 14 23:18:58 andrew-desktop init: plymouth-stop pre-start process (1293) terminated with status 1
Oct 14 23:18:59 andrew-desktop gdm-session-worker[1327]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Sucessfully called chroot.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Sucessfully dropped privileges.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Sucessfully limited resources.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Running.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Canary thread running.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Watchdog thread running.
Oct 14 23:18:59 andrew-desktop polkitd[1339]: started daemon version 0.96 using authority implementation `local' version `0.96'
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 1333 of process 1333 (n/a) owned by '114' high priority at nice level -11.
Oct 14 23:18:59 andrew-desktop rtkit-daemon[1335]: Supervising 1 threads of 1 processes of 1 users.
Oct 14 23:19:00 andrew-desktop kernel: [   42.101266] usb 4-1: new full speed USB device using uhci_hcd and address 6
Oct 14 23:19:00 andrew-desktop kernel: [   42.230017] usb 4-1: device descriptor read/64, error -71
Oct 14 23:19:00 andrew-desktop kernel: [   42.470020] usb 4-1: device descriptor read/64, error -71
Oct 14 23:19:00 andrew-desktop kernel: [   42.700022] usb 4-1: new full speed USB device using uhci_hcd and address 7
Oct 14 23:19:00 andrew-desktop kernel: [   42.830019] usb 4-1: device descriptor read/64, error -71
Oct 14 23:19:01 andrew-desktop kernel: [   43.070029] usb 4-1: device descriptor read/64, error -71
Oct 14 23:19:01 andrew-desktop kernel: [   43.300028] usb 4-1: new full speed USB device using uhci_hcd and address 8
Oct 14 23:19:01 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 1340 of process 1333 (n/a) owned by '114' RT at priority 5.
Oct 14 23:19:01 andrew-desktop rtkit-daemon[1335]: Supervising 2 threads of 1 processes of 1 users.
Oct 14 23:19:01 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 1341 of process 1333 (n/a) owned by '114' RT at priority 5.
Oct 14 23:19:01 andrew-desktop rtkit-daemon[1335]: Supervising 3 threads of 1 processes of 1 users.
Oct 14 23:19:01 andrew-desktop kernel: [   43.720045] usb 4-1: device not accepting address 8, error -71
Oct 14 23:19:01 andrew-desktop kernel: [   43.840014] usb 4-1: new full speed USB device using uhci_hcd and address 9
Oct 14 23:19:02 andrew-desktop kernel: [   44.260012] usb 4-1: device not accepting address 9, error -71
Oct 14 23:19:02 andrew-desktop kernel: [   44.260026] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:19:02 andrew-desktop gdm-simple-greeter[1325]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Oct 14 23:19:02 andrew-desktop anacron[1402]: Anacron 2.3 started on 2010-10-14
Oct 14 23:19:02 andrew-desktop anacron[1402]: Normal exit (0 jobs run)
Oct 14 23:19:02 andrew-desktop kernel: [   44.343524] CPU0 attaching NULL sched-domain.
Oct 14 23:19:02 andrew-desktop kernel: [   44.343529] CPU1 attaching NULL sched-domain.
Oct 14 23:19:02 andrew-desktop kernel: [   44.400078] CPU0 attaching sched-domain:
Oct 14 23:19:02 andrew-desktop kernel: [   44.400082]  domain 0: span 0-1 level MC
Oct 14 23:19:02 andrew-desktop kernel: [   44.400084]   groups: 0 1
Oct 14 23:19:02 andrew-desktop kernel: [   44.400089] CPU1 attaching sched-domain:
Oct 14 23:19:02 andrew-desktop kernel: [   44.400090]  domain 0: span 0-1 level MC
Oct 14 23:19:02 andrew-desktop kernel: [   44.400092]   groups: 1 0
Oct 14 23:19:02 andrew-desktop acpid: client connected from 1450[108:114]
Oct 14 23:19:02 andrew-desktop acpid: 1 client rule loaded
Oct 14 23:19:25 andrew-desktop kernel: [   66.978277] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 23:20:05 andrew-desktop kernel: [  106.979314] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:20:55 andrew-desktop kernel: [  156.978154] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:21:55 andrew-desktop kernel: [  216.978177] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:22:55 andrew-desktop kernel: [  276.977547] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:23:55 andrew-desktop kernel: [  336.978180] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:24:55 andrew-desktop kernel: [  396.978191] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:25:55 andrew-desktop kernel: [  456.978156] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:26:55 andrew-desktop kernel: [  516.978168] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:27:55 andrew-desktop kernel: [  576.978176] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:28:55 andrew-desktop kernel: [  636.978180] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 292
Oct 14 23:29:55 andrew-desktop kernel: [  696.977931] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:30:55 andrew-desktop kernel: [  756.977896] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:31:14 andrew-desktop gdm-session-worker[1327]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct 14 23:31:20 andrew-desktop kernel: [  782.050027] usb 1-1: new high speed USB device using ehci_hcd and address 3
Oct 14 23:31:20 andrew-desktop kernel: [  782.201348] usb 1-1: configuration #1 chosen from 2 choices
Oct 14 23:31:20 andrew-desktop kernel: [  782.208643] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 14 23:31:20 andrew-desktop kernel: [  782.208811] usb-storage: device found at 3
Oct 14 23:31:20 andrew-desktop kernel: [  782.208814] usb-storage: waiting for device to settle before scanning
Oct 14 23:31:20 andrew-desktop kernel: [  782.530025] usb 4-1: new full speed USB device using uhci_hcd and address 10
Oct 14 23:31:20 andrew-desktop kernel: [  782.660028] usb 4-1: device descriptor read/64, error -71
Oct 14 23:31:20 andrew-desktop kernel: [  782.900032] usb 4-1: device descriptor read/64, error -71
Oct 14 23:31:21 andrew-desktop kernel: [  783.130023] usb 4-1: new full speed USB device using uhci_hcd and address 11
Oct 14 23:31:21 andrew-desktop kernel: [  783.260028] usb 4-1: device descriptor read/64, error -71
Oct 14 23:31:21 andrew-desktop kernel: [  783.500032] usb 4-1: device descriptor read/64, error -71
Oct 14 23:31:21 andrew-desktop kernel: [  783.730022] usb 4-1: new full speed USB device using uhci_hcd and address 12
Oct 14 23:31:22 andrew-desktop kernel: [  784.150025] usb 4-1: device not accepting address 12, error -71
Oct 14 23:31:22 andrew-desktop kernel: [  784.270029] usb 4-1: new full speed USB device using uhci_hcd and address 13
Oct 14 23:31:22 andrew-desktop kernel: [  784.690031] usb 4-1: device not accepting address 13, error -71
Oct 14 23:31:22 andrew-desktop kernel: [  784.690043] hub 4-0:1.0: unable to enumerate USB device on port 1
Oct 14 23:31:25 andrew-desktop kernel: [  787.200229] usb-storage: device scan complete
Oct 14 23:31:25 andrew-desktop kernel: [  787.207595] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Oct 14 23:31:25 andrew-desktop kernel: [  787.208249] sd 6:0:0:0: Attached scsi generic sg5 type 0
Oct 14 23:31:25 andrew-desktop kernel: [  787.210837] sd 6:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:31:25 andrew-desktop kernel: [  787.211370] sd 6:0:0:0: [sde] Write Protect is off
Oct 14 23:31:25 andrew-desktop kernel: [  787.211375] sd 6:0:0:0: [sde] Mode Sense: 68 00 00 08
Oct 14 23:31:25 andrew-desktop kernel: [  787.211380] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:31:25 andrew-desktop kernel: [  787.214628] sd 6:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:31:25 andrew-desktop kernel: [  787.215215] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:31:25 andrew-desktop kernel: [  787.215224]  sde: sde1
Oct 14 23:31:25 andrew-desktop kernel: [  787.895844] sd 6:0:0:0: [sde] 29255991 4096-byte logical blocks: (119 GB/111 GiB)
Oct 14 23:31:25 andrew-desktop kernel: [  787.896332] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 14 23:31:25 andrew-desktop kernel: [  787.896339] sd 6:0:0:0: [sde] Attached SCSI removable disk
Oct 14 23:31:27 andrew-desktop gdm-session-worker[3495]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 14 23:31:36 andrew-desktop gdm-session-worker[3495]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct 14 23:31:41 andrew-desktop gnome-session[3533]: EggSMClient-WARNING: Desktop file '/home/andrew/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Oct 14 23:31:42 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 3599 of process 3599 (n/a) owned by '1000' high priority at nice level -11.
Oct 14 23:31:42 andrew-desktop rtkit-daemon[1335]: Supervising 4 threads of 2 processes of 2 users.
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto GAMEOFPRICKS'
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto GAMEOFPRICKS' requires no security.  No secrets needed.
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Config: added 'ssid' value 'GAMEOFPRICKS'
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 14 23:31:42 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 3700 of process 3599 (n/a) owned by '1000' RT at priority 5.
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Supervising 5 threads of 2 processes of 2 users.
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 3701 of process 3599 (n/a) owned by '1000' RT at priority 5.
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Supervising 6 threads of 2 processes of 2 users.
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Sucessfully made thread 3703 of process 3703 (n/a) owned by '1000' high priority at nice level -11.
Oct 14 23:31:44 andrew-desktop rtkit-daemon[1335]: Supervising 7 threads of 3 processes of 2 users.
Oct 14 23:31:44 andrew-desktop pulseaudio[3703]: pid.c: Daemon already running.
Oct 14 23:31:45 andrew-desktop ntfs-3g[3709]: Version 2010.3.6 external FUSE 28
Oct 14 23:31:45 andrew-desktop ntfs-3g[3709]: Mounted /dev/sdd1 (Read-Write, label "THING 3", NTFS 3.1)
Oct 14 23:31:45 andrew-desktop ntfs-3g[3709]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 14 23:31:45 andrew-desktop ntfs-3g[3709]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdd1,blkdev,blksize=4096,default_permissions
Oct 14 23:31:45 andrew-desktop ntfs-3g[3709]: Global ownership and permissions enforced, configuration type 1
Oct 14 23:31:47 andrew-desktop wpa_supplicant[911]: Trying to associate with c0:3f:0e:4b:66:92 (SSID='GAMEOFPRICKS' freq=2437 MHz)
Oct 14 23:31:47 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 14 23:31:47 andrew-desktop kernel: [  809.927011] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:31:47 andrew-desktop kernel: [  809.927207] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Oct 14 23:31:47 andrew-desktop wpa_supplicant[911]: Association request to the driver failed
Oct 14 23:31:48 andrew-desktop wpa_supplicant[911]: Associated with c0:3f:0e:4b:66:92
Oct 14 23:31:48 andrew-desktop wpa_supplicant[911]: CTRL-EVENT-CONNECTED - Connection to c0:3f:0e:4b:66:92 completed (auth) [id=0 id_str=]
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'GAMEOFPRICKS'.
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  dhclient started with pid 3713
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 14 23:31:48 andrew-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 14 23:31:48 andrew-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 14 23:31:48 andrew-desktop dhclient: All rights reserved.
Oct 14 23:31:48 andrew-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct 14 23:31:48 andrew-desktop dhclient: 
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Oct 14 23:31:48 andrew-desktop dhclient: Listening on LPF/wlan0/00:22:43:64:80:ab
Oct 14 23:31:48 andrew-desktop dhclient: Sending on   LPF/wlan0/00:22:43:64:80:ab
Oct 14 23:31:48 andrew-desktop dhclient: Sending on   Socket/fallback
Oct 14 23:31:48 andrew-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 14 23:31:48 andrew-desktop dhclient: DHCPOFFER of 10.0.0.2 from 10.0.0.1
Oct 14 23:31:48 andrew-desktop dhclient: DHCPREQUEST of 10.0.0.2 on wlan0 to 255.255.255.255 port 67
Oct 14 23:31:48 andrew-desktop dhclient: DHCPACK of 10.0.0.2 from 10.0.0.1
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>    address 10.0.0.2
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>    gateway 10.0.0.1
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>    nameserver '10.0.0.1'
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 14 23:31:48 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 14 23:31:48 andrew-desktop avahi-daemon[848]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.2.
Oct 14 23:31:48 andrew-desktop avahi-daemon[848]: New relevant interface wlan0.IPv4 for mDNS.
Oct 14 23:31:48 andrew-desktop avahi-daemon[848]: Registering new address record for 10.0.0.2 on wlan0.IPv4.
Oct 14 23:31:48 andrew-desktop dhclient: bound to 10.0.0.2 -- renewal in 39787 seconds.
Oct 14 23:31:49 andrew-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Oct 14 23:31:49 andrew-desktop NetworkManager: <info>  Policy set 'Auto GAMEOFPRICKS' (wlan0) as default for routing and DNS.
Oct 14 23:31:49 andrew-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct 14 23:31:49 andrew-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 14 23:31:08 andrew-desktop ntpdate[3758]: step time server 91.189.94.4 offset -44.122336 sec
Oct 14 23:31:08 andrew-desktop ntfs-3g[3771]: Version 2010.3.6 external FUSE 28
Oct 14 23:31:08 andrew-desktop ntfs-3g[3771]: Mounted /dev/sdc1 (Read-Write, label "Thing 2", NTFS 3.1)
Oct 14 23:31:08 andrew-desktop ntfs-3g[3771]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Oct 14 23:31:08 andrew-desktop ntfs-3g[3771]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096,default_permissions
Oct 14 23:31:08 andrew-desktop ntfs-3g[3771]: Global ownership and permissions enforced, configuration type 1
Oct 14 23:31:29 andrew-desktop kernel: [  835.148816] lo: Disabled Privacy Extensions
Oct 14 23:31:45 andrew-desktop kernel: [  851.336662] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:31:45 andrew-desktop kernel: [  851.336669] ata1.00: BMDMA stat 0x65
Oct 14 23:31:45 andrew-desktop kernel: [  851.336674] ata1.00: failed command: READ DMA EXT
Oct 14 23:31:45 andrew-desktop kernel: [  851.336683] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:31:45 andrew-desktop kernel: [  851.336685]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:31:45 andrew-desktop kernel: [  851.336689] ata1.00: status: { DRDY ERR }
Oct 14 23:31:45 andrew-desktop kernel: [  851.336693] ata1.00: error: { UNC }
Oct 14 23:31:45 andrew-desktop kernel: [  851.390416] ata1.00: configured for UDMA/133
Oct 14 23:31:45 andrew-desktop kernel: [  851.430349] ata1.01: configured for UDMA/133
Oct 14 23:31:45 andrew-desktop kernel: [  851.430383] ata1: EH complete
Oct 14 23:31:55 andrew-desktop kernel: [  861.100047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:31:59 andrew-desktop kernel: [  865.529194] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:31:59 andrew-desktop kernel: [  865.529200] ata1.00: BMDMA stat 0x65
Oct 14 23:31:59 andrew-desktop kernel: [  865.529206] ata1.00: failed command: READ DMA EXT
Oct 14 23:31:59 andrew-desktop kernel: [  865.529215] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:31:59 andrew-desktop kernel: [  865.529217]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:31:59 andrew-desktop kernel: [  865.529221] ata1.00: status: { DRDY ERR }
Oct 14 23:31:59 andrew-desktop kernel: [  865.529225] ata1.00: error: { UNC }
Oct 14 23:31:59 andrew-desktop kernel: [  865.580422] ata1.00: configured for UDMA/133
Oct 14 23:31:59 andrew-desktop kernel: [  865.620358] ata1.01: configured for UDMA/133
Oct 14 23:31:59 andrew-desktop kernel: [  865.620398] ata1: EH complete
Oct 14 23:32:13 andrew-desktop kernel: [  879.838392] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:32:13 andrew-desktop kernel: [  879.838399] ata1.00: BMDMA stat 0x65
Oct 14 23:32:13 andrew-desktop kernel: [  879.838404] ata1.00: failed command: READ DMA EXT
Oct 14 23:32:13 andrew-desktop kernel: [  879.838413] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:32:13 andrew-desktop kernel: [  879.838415]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:32:13 andrew-desktop kernel: [  879.838419] ata1.00: status: { DRDY ERR }
Oct 14 23:32:13 andrew-desktop kernel: [  879.838423] ata1.00: error: { UNC }
Oct 14 23:32:13 andrew-desktop kernel: [  879.890414] ata1.00: configured for UDMA/133
Oct 14 23:32:13 andrew-desktop kernel: [  879.930335] ata1.01: configured for UDMA/133
Oct 14 23:32:13 andrew-desktop kernel: [  879.930375] ata1: EH complete
Oct 14 23:32:28 andrew-desktop kernel: [  894.164262] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:32:28 andrew-desktop kernel: [  894.164269] ata1.00: BMDMA stat 0x65
Oct 14 23:32:28 andrew-desktop kernel: [  894.164275] ata1.00: failed command: READ DMA EXT
Oct 14 23:32:28 andrew-desktop kernel: [  894.164284] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:32:28 andrew-desktop kernel: [  894.164286]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:32:28 andrew-desktop kernel: [  894.164290] ata1.00: status: { DRDY ERR }
Oct 14 23:32:28 andrew-desktop kernel: [  894.164293] ata1.00: error: { UNC }
Oct 14 23:32:28 andrew-desktop kernel: [  894.220412] ata1.00: configured for UDMA/133
Oct 14 23:32:28 andrew-desktop kernel: [  894.260335] ata1.01: configured for UDMA/133
Oct 14 23:32:28 andrew-desktop kernel: [  894.260370] ata1: EH complete
Oct 14 23:32:42 andrew-desktop kernel: [  908.948492] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:32:42 andrew-desktop kernel: [  908.948499] ata1.00: BMDMA stat 0x65
Oct 14 23:32:42 andrew-desktop kernel: [  908.948504] ata1.00: failed command: READ DMA EXT
Oct 14 23:32:42 andrew-desktop kernel: [  908.948513] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:32:42 andrew-desktop kernel: [  908.948515]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:32:42 andrew-desktop kernel: [  908.948520] ata1.00: status: { DRDY ERR }
Oct 14 23:32:42 andrew-desktop kernel: [  908.948524] ata1.00: error: { UNC }
Oct 14 23:32:42 andrew-desktop kernel: [  909.000412] ata1.00: configured for UDMA/133
Oct 14 23:32:42 andrew-desktop kernel: [  909.040371] ata1.01: configured for UDMA/133
Oct 14 23:32:42 andrew-desktop kernel: [  909.040409] ata1: EH complete
Oct 14 23:32:55 andrew-desktop kernel: [  921.105195] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 436
Oct 14 23:32:57 andrew-desktop kernel: [  923.299358] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:32:57 andrew-desktop kernel: [  923.299365] ata1.00: BMDMA stat 0x65
Oct 14 23:32:57 andrew-desktop kernel: [  923.299370] ata1.00: failed command: READ DMA EXT
Oct 14 23:32:57 andrew-desktop kernel: [  923.299380] ata1.00: cmd 25/00:50:00:09:00/00:00:42:00:00/e0 tag 0 dma 40960 in
Oct 14 23:32:57 andrew-desktop kernel: [  923.299382]          res 51/40:35:1b:09:00/40:00:42:00:00/e2 Emask 0x9 (media error)
Oct 14 23:32:57 andrew-desktop kernel: [  923.299386] ata1.00: status: { DRDY ERR }
Oct 14 23:32:57 andrew-desktop kernel: [  923.299389] ata1.00: error: { UNC }
Oct 14 23:32:57 andrew-desktop kernel: [  923.350408] ata1.00: configured for UDMA/133
Oct 14 23:32:57 andrew-desktop kernel: [  923.390351] ata1.01: configured for UDMA/133
Oct 14 23:32:57 andrew-desktop kernel: [  923.390395] sd 0:0:0:0: [sda] Unhandled sense code
Oct 14 23:32:57 andrew-desktop kernel: [  923.390398] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 23:32:57 andrew-desktop kernel: [  923.390404] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Oct 14 23:32:57 andrew-desktop kernel: [  923.390412] Descriptor sense data with sense descriptors (in hex):
Oct 14 23:32:57 andrew-desktop kernel: [  923.390415]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct 14 23:32:57 andrew-desktop kernel: [  923.390430]         42 00 09 1b 
Oct 14 23:32:57 andrew-desktop kernel: [  923.390436] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Oct 14 23:32:57 andrew-desktop kernel: [  923.390443] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 42 00 09 00 00 00 50 00
Oct 14 23:32:57 andrew-desktop kernel: [  923.390456] end_request: I/O error, dev sda, sector 1107298587
Oct 14 23:32:57 andrew-desktop kernel: [  923.390477] ata1: EH complete
Oct 14 23:33:03 andrew-desktop kernel: [  929.849765] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 14 23:33:03 andrew-desktop kernel: [  929.849772] ata1.00: BMDMA stat 0x65

---

### Post by VMC on 2010-10-15
Blimpsgo90, In the future please put those extra long outputs within CODE tags. Its the hash marks '#'

---

### Post by Blimpsgo90 on 2010-10-15
> **VMC said:**
> Blimpsgo90, In the future please put those extra long outputs within CODE tags. Its the hash marks '#'



ok had no idea how to do that, sorry.

---

### Post by Blimpsgo90 on 2010-10-16
I hate to bump this

but I can figure it out

---

