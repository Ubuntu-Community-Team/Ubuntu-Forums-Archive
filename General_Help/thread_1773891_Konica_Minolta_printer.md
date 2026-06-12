---
title: "Konica Minolta printer"
date: 2011-06-02
forum: General Help
---

### Post by Antrax_akb on 2011-06-02
hello and sorry for my bad English

I have a KONICA MINOLTA 7022 ip-422 and download the drivers and *. ppd and install correctly. to install the printer and select the. ppd tells me that we need a package called kmfilter.

 and look everywhere and can not find it, or if there is a generic driver or compatible with this printer.

 o. any way to fix it because i need the printer soon as posible and I have only linux


 thanks in advance
 Greetings

---

### Post by Toz on 2011-06-02
Try this: [http://ubuntuforums.org/showpost.php?p=9257352&postcount=3](http://ubuntuforums.org/showpost.php?p=9257352&postcount=3)

---

### Post by Antrax_akb on 2011-06-03
> **Toz said:**
> Try this: [http://ubuntuforums.org/showpost.php?p=9257352&postcount=3](http://ubuntuforums.org/showpost.php?p=9257352&postcount=3)


already tried but the printer says that is disabled and restart the CUPS but do not print anything. try a generic from xubuntu and if recognized him but for every  print, 11 copies out and i dont chosse that. there will be a way to not do that with the generic?

Escuse my bad english

bye.

---

### Post by Toz on 2011-06-03
Can you open a terminal window, type in the following and post back the results:```
ls -l /usr/lib/cups/filter/kmfilter
```

Also, can you post back the contents of: 
/var/log/cups/access_log
/var/log/cups/error_log
/var/log/cups/page_log

---

### Post by Antrax_akb on 2011-06-03
> **Toz said:**
> Can you open a terminal window, type in the following and post back the results:```
ls -l /usr/lib/cups/filter/kmfilter
```Also, can you post back the contents of: 
/var/log/cups/access_log
/var/log/cups/error_log
/var/log/cups/page_log


Thanks for your answer
 in the first line I get the following:
 "-r-xr-xr-x 2 test test 1785 25/4/2006 5:14 / usr / lib / cups / filter / kmfilter"

 in the following lines:

 "-rw-r - - - - - 1 root adm 5042 06/03/2011 15:26 / var / log / cups / acces_log"

 "-rw-r - - - - - 1 root adm 30925 03/06/2011 15:26 / var / log
 / cups / error_log "

 "ls: can not access / var / log / cups / page_log: No such file or directory"


 I hope you can help

---

### Post by Toz on 2011-06-03
Okay, lets try this again. Open a terminal window and type in:```
sudo bash
```and enter in your password when asked.

As we go through the following commands, please post back any error messages you might get.

1. Let's back up the existing kmfilter file. Type the following into the terminal window:```
cp /usr/lib/cups/filter/kmfilter /usr/lib/cups/filter/kmfilter.old
```

2. Let's link the proper filter file back in. Type into the terminal:```
ln -s /usr/lib/kmpu/printutility.filter.cups /usr/lib/cups/filter/kmfilter
```

3. Now post back the results of the following command:```
ls -l /usr/lib/cups/filter/kmfilter
```

4. Now let's restart cups:```
/etc/init.d/cups restart
```

5. Try to print something.

6. If it doesn't work, then post back the results of the following commands:```
cat /var/log/cups/access_log
``````
cat /var/log/cups/error_log
``````
cat /var/log/cups/page_log
```

---

### Post by Antrax_akb on 2011-06-03
> **Toz said:**
> Okay, lets try this again. Open a terminal window and type in:```
sudo bash
```and enter in your password when asked.

As we go through the following commands, please post back any error messages you might get.

1. Let's back up the existing kmfilter file. Type the following into the terminal window:```
cp /usr/lib/cups/filter/kmfilter /usr/lib/cups/filter/kmfilter.old
```2. Let's link the proper filter file back in. Type into the terminal:```
ln -s /usr/lib/kmpu/printutility.filter.cups /usr/lib/cups/filter/kmfilter
```3. Now post back the results of the following command:```
ls -l /usr/lib/cups/filter/kmfilter
```4. Now let's restart cups:```
/etc/init.d/cups restart
```5. Try to print something.

6. If it doesn't work, then post back the results of the following commands:```
cat /var/log/cups/access_log
``````
cat /var/log/cups/error_log
``````
cat /var/log/cups/page_log
```


thanks .. for your answer, still does not print. I put the results here

 one thing, change the "printutility.filter.cups"with "konicaminolta.filter.cups"as it was the only thing that was in that directory if it was wrong .. forgivesEscuchar
Leer fonéticamente




  	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  ```

 -r-xr-xr-x 2 test test 1785 2006-04-25 05:14 /usr/lib/cups/filter/kmfilter
 
```
 

 second
 ```

 root@sistemas-desktop:~# cat /var/log/cups/access_log 
 localhost - - [03/Jun/2011:15:01:52 -0500] "POST / HTTP/1.1" 200 256 Create-Printer-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:10:05 -0500] "POST / HTTP/1.1" 401 123 CUPS-Get-Devices successful-ok 
 localhost - sistemas [03/Jun/2011:15:10:05 -0500] "POST / HTTP/1.1" 200 1877 CUPS-Get-Devices - 
 localhost - sistemas [03/Jun/2011:15:10:10 -0500] "POST / HTTP/1.1" 200 486 CUPS-Get-Devices - 
 localhost - - [03/Jun/2011:15:10:20 -0500] "POST / HTTP/1.1" 200 2477701 CUPS-Get-PPDs - 
 localhost - - [03/Jun/2011:15:10:29 -0500] "POST / HTTP/1.1" 200 2477701 CUPS-Get-PPDs - 
 localhost - - [03/Jun/2011:15:11:50 -0500] "POST / HTTP/1.1" 401 75 CUPS-Get-Devices successful-ok 
 localhost - root [03/Jun/2011:15:11:50 -0500] "POST / HTTP/1.1" 200 2085 CUPS-Get-Devices - 
 localhost - - [03/Jun/2011:15:12:24 -0500] "POST / HTTP/1.1" 200 2477701 CUPS-Get-PPDs - 
 localhost - - [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 401 49435 CUPS-Add-Modify-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 49435 CUPS-Add-Modify-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 129 Resume-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 129 CUPS-Accept-Jobs successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 129 CUPS-Set-Default successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 162 CUPS-Add-Modify-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:13:38 -0500] "POST /admin/ HTTP/1.1" 200 160 CUPS-Add-Modify-Printer successful-ok 
 localhost - - [03/Jun/2011:15:15:27 -0500] "POST / HTTP/1.1" 200 156 Cancel-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:17:56 -0500] "POST / HTTP/1.1" 200 256 Create-Printer-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:18:08 -0500] "POST /printers/Konica-IP-422 HTTP/1.1" 200 205792 Print-Job successful-ok 
 localhost - - [03/Jun/2011:15:18:09 -0500] "POST / HTTP/1.1" 200 345 Create-Printer-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:19:35 -0500] "POST /admin/ HTTP/1.1" 401 129 CUPS-Delete-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:19:35 -0500] "POST /admin/ HTTP/1.1" 200 129 CUPS-Delete-Printer successful-ok 
 localhost - - [03/Jun/2011:15:19:43 -0500] "POST / HTTP/1.1" 401 123 CUPS-Get-Devices successful-ok 
 localhost - sistemas [03/Jun/2011:15:19:43 -0500] "POST / HTTP/1.1" 200 1877 CUPS-Get-Devices - 
 localhost - sistemas [03/Jun/2011:15:19:45 -0500] "POST / HTTP/1.1" 200 198 CUPS-Get-Devices - 
 localhost - - [03/Jun/2011:15:21:06 -0500] "POST / HTTP/1.1" 200 2477701 CUPS-Get-PPDs - 
 localhost - - [03/Jun/2011:15:22:03 -0500] "POST / HTTP/1.1" 401 75 CUPS-Get-Devices successful-ok 
 localhost - root [03/Jun/2011:15:22:03 -0500] "POST / HTTP/1.1" 200 2085 CUPS-Get-Devices - 
 localhost - - [03/Jun/2011:15:22:31 -0500] "POST / HTTP/1.1" 200 2477701 CUPS-Get-PPDs - 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 67495 CUPS-Add-Modify-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 137 Resume-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 137 CUPS-Accept-Jobs successful-ok 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 137 CUPS-Set-Default successful-ok 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 170 CUPS-Add-Modify-Printer successful-ok 
 localhost - sistemas [03/Jun/2011:15:23:53 -0500] "POST /admin/ HTTP/1.1" 200 176 CUPS-Add-Modify-Printer successful-ok 
 localhost - - [03/Jun/2011:15:23:58 -0500] "POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1" 200 205800 Print-Job successful-ok 
 localhost - - [03/Jun/2011:15:24:16 -0500] "POST / HTTP/1.1" 401 75 CUPS-Get-Devices successful-ok 
 localhost - sistemas [03/Jun/2011:15:24:16 -0500] "POST / HTTP/1.1" 200 2117 CUPS-Get-Devices - 
 localhost - sistemas [03/Jun/2011:15:24:41 -0500] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 2944 - - 
 localhost - - [03/Jun/2011:15:24:44 -0500] "POST / HTTP/1.1" 200 281 Create-Printer-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:24:47 -0500] "POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1" 200 497 Print-Job successful-ok 
 localhost - - [03/Jun/2011:15:25:01 -0500] "POST /jobs/ HTTP/1.1" 200 157 Cancel-Job successful-ok 
 localhost - - [03/Jun/2011:15:25:05 -0500] "POST /jobs/ HTTP/1.1" 200 157 Cancel-Job successful-ok 
 localhost - - [03/Jun/2011:15:25:10 -0500] "POST / HTTP/1.1" 200 156 Cancel-Subscription successful-ok 
 localhost - - [03/Jun/2011:15:25:11 -0500] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - - 
 localhost - sistemas [03/Jun/2011:15:25:11 -0500] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 2935 - - 
 localhost - - [03/Jun/2011:15:26:06 -0500] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - - 
 localhost - sistemas [03/Jun/2011:15:26:06 -0500] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 2894 - - 
 localhost - - [03/Jun/2011:15:39:18 -0500] "POST / HTTP/1.1" 200 156 Cancel-Subscription successful-ok 
 localhost - - [03/Jun/2011:17:36:34 -0500] "POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1" 200 262 Create-Job successful-ok 
 localhost - - [03/Jun/2011:17:36:35 -0500] "POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1" 200 18080 Send-Document successful-ok 
 
```
 

 

 

 

 third
 ```

 root@sistemas-desktop:~# cat /var/log/cups/error_log 
 E [03/Jun/2011:15:10:21 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"! 
 E [03/Jun/2011:15:10:31 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"! 
 E [03/Jun/2011:15:12:25 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"! 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:13:38 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not available: No such file or directory 
 E [03/Jun/2011:15:16:46 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not owned by root 
 E [03/Jun/2011:15:16:46 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "Konica-IP-422" not owned by root 
 E [03/Jun/2011:15:16:46 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory 
 E [03/Jun/2011:15:18:08 -0500] Unable to execute /usr/lib/cups/filter/kmfilter: insecure file permissions (0100555) 
 E [03/Jun/2011:15:18:08 -0500] [Job 1] Unable to start filter "kmfilter" - Operation not permitted. 
 E [03/Jun/2011:15:18:08 -0500] [Job 1] Stopping job because the scheduler could not execute a filter. 
 E [03/Jun/2011:15:21:07 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"! 
 E [03/Jun/2011:15:22:32 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"! 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:53 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:23:58 -0500] Unable to execute /usr/lib/cups/filter/kmfilter: insecure file permissions (0100555) 
 E [03/Jun/2011:15:23:58 -0500] [Job 2] Unable to start filter "kmfilter" - Operation not permitted. 
 E [03/Jun/2011:15:23:58 -0500] [Job 2] Stopping job because the scheduler could not execute a filter. 
 I [03/Jun/2011:15:24:41 -0500] Listening to ::1:631 (IPv6) 
 I [03/Jun/2011:15:24:41 -0500] Listening to 127.0.0.1:631 (IPv4) 
 I [03/Jun/2011:15:24:41 -0500] Listening to /var/run/cups/cups.sock (Domain) 
 I [03/Jun/2011:15:24:41 -0500] Remote access is disabled. 
 D [03/Jun/2011:15:24:41 -0500] Added auto ServerAlias sistemas-desktop 
 I [03/Jun/2011:15:24:41 -0500] Loaded configuration file "/etc/cups/cupsd.conf" 
 I [03/Jun/2011:15:24:41 -0500] Using default TempDir of /var/spool/cups/tmp... 
 I [03/Jun/2011:15:24:41 -0500] Configured for up to 100 clients. 
 I [03/Jun/2011:15:24:41 -0500] Allowing up to 100 client connections per host. 
 I [03/Jun/2011:15:24:41 -0500] Using policy "default" as the default! 
 D [03/Jun/2011:15:24:41 -0500] cupsdMarkDirty(P-----) 
 D [03/Jun/2011:15:24:41 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:41 -0500] load_ppd: Loading /var/cache/cups/KONICA-MINOLTA-IP-424.ipp... 
 D [03/Jun/2011:15:24:41 -0500] cupsdMarkDirty(P-----) 
 E [03/Jun/2011:15:24:41 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:24:41 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 D [03/Jun/2011:15:24:41 -0500] cupsdRegisterPrinter(p=0x2223dec0(KONICA-MINOLTA-IP-424)) 
 D [03/Jun/2011:15:24:41 -0500] cupsdMarkDirty(---p--) 
 I [03/Jun/2011:15:24:41 -0500] Partial reload complete. 
 I [03/Jun/2011:15:24:41 -0500] Listening to ::1:631 on fd 5... 
 I [03/Jun/2011:15:24:41 -0500] Listening to 127.0.0.1:631 on fd 7... 
 I [03/Jun/2011:15:24:41 -0500] Listening to /var/run/cups/cups.sock on fd 8... 
 I [03/Jun/2011:15:24:41 -0500] Resuming new connection processing... 
 D [03/Jun/2011:15:24:41 -0500] Discarding unused server-restarted event... 
 D [03/Jun/2011:15:24:42 -0500] cupsdAcceptClient: 11 from localhost (Domain) 
 D [03/Jun/2011:15:24:42 -0500] Report: clients=1 
 D [03/Jun/2011:15:24:42 -0500] Report: jobs=2 
 D [03/Jun/2011:15:24:42 -0500] Report: jobs-active=1 
 D [03/Jun/2011:15:24:42 -0500] Report: printers=1 
 D [03/Jun/2011:15:24:42 -0500] Report: printers-implicit=0 
 D [03/Jun/2011:15:24:42 -0500] Report: stringpool-string-count=839 
 D [03/Jun/2011:15:24:42 -0500] Report: stringpool-alloc-bytes=8376 
 D [03/Jun/2011:15:24:42 -0500] Report: stringpool-total-bytes=19512 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1 
 D [03/Jun/2011:15:24:44 -0500] Get-Jobs ipp://localhost/printers/ 
 D [03/Jun/2011:15:24:44 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1 
 D [03/Jun/2011:15:24:44 -0500] Get-Jobs ipp://localhost/printers/ 
 D [03/Jun/2011:15:24:44 -0500] [Job 1] Loading attributes... 
 E [03/Jun/2011:15:24:44 -0500] [Job 1] Unable to queue job for destination "Konica-IP-422"! 
 D [03/Jun/2011:15:24:44 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:44 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:44 -0500] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1 
 D [03/Jun/2011:15:24:44 -0500] Create-Printer-Subscription / 
 D [03/Jun/2011:15:24:44 -0500] cupsdCreateSubscription(con=0x22281280(11), uri="/") 
 D [03/Jun/2011:15:24:44 -0500] pullmethod="ippget" 
 D [03/Jun/2011:15:24:44 -0500] notify-lease-duration=86400 
 D [03/Jun/2011:15:24:44 -0500] notify-time-interval=0 
 D [03/Jun/2011:15:24:44 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)") 
 D [03/Jun/2011:15:24:44 -0500] Added subscription 4 for server 
 D [03/Jun/2011:15:24:44 -0500] cupsdMarkDirty(-----S) 
 D [03/Jun/2011:15:24:44 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost 
 D [03/Jun/2011:15:24:44 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:45 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:45 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:45 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:45 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:24:45 -0500] Get-Notifications / 
 D [03/Jun/2011:15:24:45 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:24:45 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:24:45 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:47 -0500] cupsdAcceptClient: 13 from localhost (Domain) 
 D [03/Jun/2011:15:24:47 -0500] cupsdReadClient: 13 POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1 
 D [03/Jun/2011:15:24:47 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:47 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:47 -0500] cupsdReadClient: 13 1.1 Print-Job 1 
 D [03/Jun/2011:15:24:47 -0500] Print-Job ipp://localhost/printers/KONICA-MINOLTA-IP-424 
 D [03/Jun/2011:15:24:47 -0500] [Job ???] Auto-typing file... 
 I [03/Jun/2011:15:24:47 -0500] [Job ???] Request file type is application/vnd.cups-banner. 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(----J-) 
 D [03/Jun/2011:15:24:47 -0500] add_job: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:24:47 -0500] Adding default job-sheets values "none,none"... 
 I [03/Jun/2011:15:24:47 -0500] [Job 3] Adding start banner page "none". 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(-----S) 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(----J-) 
 I [03/Jun/2011:15:24:47 -0500] [Job 3] Adding end banner page "none". 
 I [03/Jun/2011:15:24:47 -0500] [Job 3] File of type application/vnd.cups-banner queued by "sistemas". 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] hold_until=0 
 I [03/Jun/2011:15:24:47 -0500] [Job 3] Queued on "KONICA-MINOLTA-IP-424" by "sistemas". 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(----J-) 
 D [03/Jun/2011:15:24:47 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(-----S) 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] job-sheets=none,none 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[0]="KONICA-MINOLTA-IP-424" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[1]="3" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[2]="sistemas" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[3]="Test Page" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[4]="1" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[5]="job-uuid=urn:uuid:72ed51d0-73c0-3d6b-641e-d049029d109b job-originating-host-name=localhost" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] argv[6]="/var/spool/cups/d00003-001" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[0]="CUPS_CACHEDIR=/var/cache/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[1]="CUPS_DATADIR=/usr/share/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[4]="CUPS_REQUESTROOT=/var/spool/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[5]="CUPS_SERVERBIN=/usr/lib/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[6]="CUPS_SERVERROOT=/etc/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[7]="CUPS_STATEDIR=/var/run/cups" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[8]="HOME=/var/spool/cups/tmp" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[10]="SERVER_ADMIN=root@sistemas-desktop" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[11]="SOFTWARE=CUPS/1.4.3" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[12]="TMPDIR=/var/spool/cups/tmp" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[13]="TZ=America/Mexico_City" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[14]="USER=root" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[16]="CUPS_ENCRYPTION=IfRequested" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[17]="IPP_PORT=631" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[18]="CHARSET=utf-8" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[19]="LANG=es_MX.UTF-8" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[20]="PPD=/etc/cups/ppd/KONICA-MINOLTA-IP-424.ppd" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[21]="RIP_MAX_CACHE=62424k" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[22]="CONTENT_TYPE=application/vnd.cups-banner" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[23]="DEVICE_URI=socket://172.16.1.59:9100" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[24]="PRINTER_INFO=KONICA MINOLTA IP-424" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[25]="PRINTER_LOCATION=172.16.1.59" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[26]="PRINTER=KONICA-MINOLTA-IP-424" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[27]="CUPS_FILETYPE=document" 
 D [03/Jun/2011:15:24:47 -0500] [Job 3] envp[28]="FINAL_CONTENT_TYPE=printer/KONICA-MINOLTA-IP-424" 
 I [03/Jun/2011:15:24:47 -0500] [Job 3] Started filter /usr/lib/cups/filter/bannertops (PID 1384) 
 E [03/Jun/2011:15:24:47 -0500] Unable to execute /usr/lib/cups/filter/kmfilter: insecure file permissions (0100555) 
 E [03/Jun/2011:15:24:47 -0500] [Job 3] Unable to start filter "kmfilter" - Operation not permitted. 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(-----S) 
 E [03/Jun/2011:15:24:47 -0500] [Job 3] Stopping job because the scheduler could not execute a filter. 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(----J-) 
 D [03/Jun/2011:15:24:47 -0500] cupsdMarkDirty(-----S) 
 D [03/Jun/2011:15:24:47 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost 
 D [03/Jun/2011:15:24:47 -0500] PID 1384 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15. 
 D [03/Jun/2011:15:24:47 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAcceptClient: 14 from localhost (Domain) 
 D [03/Jun/2011:15:24:48 -0500] [Job 3] Unloading... 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 14 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Notifications / 
 D [03/Jun/2011:15:24:48 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdAcceptClient: 16 from localhost (Domain) 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 1.1 Get-Jobs 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Jobs ipp://localhost/printers/ 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 WAITING Closing on EOF 
 D [03/Jun/2011:15:24:48 -0500] cupsdCloseClient: 16 
 D [03/Jun/2011:15:24:48 -0500] cupsdAcceptClient: 16 from localhost (Domain) 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Notifications / 
 D [03/Jun/2011:15:24:48 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdAcceptClient: 17 from localhost (Domain) 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 16 1.1 Get-Job-Attributes 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Job-Attributes ipp://localhost/jobs/3 
 D [03/Jun/2011:15:24:48 -0500] [Job 3] Loading attributes... 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/3) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdAcceptClient: 18 from localhost (Domain) 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 18 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Printer-Attributes ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 18 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 18 1.1 Get-Job-Attributes 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Job-Attributes ipp://localhost/jobs/3 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/3) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Notifications / 
 D [03/Jun/2011:15:24:48 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1 
 D [03/Jun/2011:15:24:48 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Printers 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Classes 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Default 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Default 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Printers 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Classes 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:48 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:24:48 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Default 1 
 D [03/Jun/2011:15:24:48 -0500] CUPS-Get-Default 
 D [03/Jun/2011:15:24:48 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost 
 D [03/Jun/2011:15:24:48 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:49 -0500] cupsdAcceptClient: 19 from localhost (Domain) 
 D [03/Jun/2011:15:24:49 -0500] cupsdReadClient: 18 WAITING Closing on EOF 
 D [03/Jun/2011:15:24:49 -0500] cupsdCloseClient: 18 
 D [03/Jun/2011:15:24:49 -0500] cupsdReadClient: 19 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:49 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:49 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:49 -0500] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1 
 D [03/Jun/2011:15:24:49 -0500] Get-Printer-Attributes ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424 
 D [03/Jun/2011:15:24:49 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424) from localhost 
 D [03/Jun/2011:15:24:49 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:24:49 -0500] cupsdReadClient: 19 POST / HTTP/1.1 
 D [03/Jun/2011:15:24:49 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:24:49 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:24:49 -0500] cupsdReadClient: 19 1.1 Get-Job-Attributes 1 
 D [03/Jun/2011:15:24:49 -0500] Get-Job-Attributes ipp://localhost/jobs/3 
 D [03/Jun/2011:15:24:49 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/3) from localhost 
 D [03/Jun/2011:15:24:49 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:01 -0500] cupsdAcceptClient: 18 from localhost (Domain) 
 D [03/Jun/2011:15:25:01 -0500] cupsdReadClient: 18 POST /jobs/ HTTP/1.1 
 D [03/Jun/2011:15:25:01 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:01 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:01 -0500] cupsdReadClient: 18 1.1 Cancel-Job 1 
 D [03/Jun/2011:15:25:01 -0500] Cancel-Job ipp://localhost/jobs/2 
 D [03/Jun/2011:15:25:01 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:25:01 -0500] cupsdMarkDirty(-----S) 
 I [03/Jun/2011:15:25:01 -0500] [Job 2] Job purged by "sistemas" 
 I [03/Jun/2011:15:25:01 -0500] [Job 2] Purged by "sistemas". 
 D [03/Jun/2011:15:25:01 -0500] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/2) from localhost 
 D [03/Jun/2011:15:25:01 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:02 -0500] cupsdAcceptClient: 20 from localhost (Domain) 
 D [03/Jun/2011:15:25:02 -0500] [Job 2] Unloading... 
 D [03/Jun/2011:15:25:02 -0500] cupsdReadClient: 20 POST / HTTP/1.1 
 D [03/Jun/2011:15:25:02 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:02 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:02 -0500] cupsdReadClient: 20 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:25:02 -0500] Get-Notifications / 
 D [03/Jun/2011:15:25:02 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:25:02 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:25:02 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:02 -0500] cupsdReadClient: 20 WAITING Closing on EOF 
 D [03/Jun/2011:15:25:02 -0500] cupsdCloseClient: 20 
 D [03/Jun/2011:15:25:05 -0500] cupsdAcceptClient: 20 from localhost (Domain) 
 D [03/Jun/2011:15:25:05 -0500] cupsdReadClient: 20 POST /jobs/ HTTP/1.1 
 D [03/Jun/2011:15:25:05 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:05 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:05 -0500] cupsdReadClient: 20 1.1 Cancel-Job 1 
 D [03/Jun/2011:15:25:05 -0500] Cancel-Job ipp://localhost/jobs/3 
 D [03/Jun/2011:15:25:05 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:25:05 -0500] cupsdMarkDirty(-----S) 
 I [03/Jun/2011:15:25:05 -0500] [Job 3] Job purged by "sistemas" 
 I [03/Jun/2011:15:25:05 -0500] [Job 3] Purged by "sistemas". 
 D [03/Jun/2011:15:25:05 -0500] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/3) from localhost 
 D [03/Jun/2011:15:25:05 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:05 -0500] cupsdAcceptClient: 21 from localhost (Domain) 
 D [03/Jun/2011:15:25:05 -0500] cupsdReadClient: 21 POST / HTTP/1.1 
 D [03/Jun/2011:15:25:05 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:05 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:05 -0500] cupsdReadClient: 21 1.1 Get-Notifications 1 
 D [03/Jun/2011:15:25:05 -0500] Get-Notifications / 
 D [03/Jun/2011:15:25:05 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:25:05 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost 
 D [03/Jun/2011:15:25:05 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:05 -0500] cupsdReadClient: 21 WAITING Closing on EOF 
 D [03/Jun/2011:15:25:05 -0500] cupsdCloseClient: 21 
 D [03/Jun/2011:15:25:10 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:10 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:10 -0500] cupsdReadClient: 11 1.1 Get-Job-Attributes 1 
 D [03/Jun/2011:15:25:10 -0500] Get-Job-Attributes ipp://localhost/jobs/3 
 D [03/Jun/2011:15:25:10 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/3) from localhost 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:10 -0500] cupsdReadClient: 11 POST / HTTP/1.1 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:10 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:10 -0500] cupsdReadClient: 11 1.1 Cancel-Subscription 1 
 D [03/Jun/2011:15:25:10 -0500] Cancel-Subscription / 
 D [03/Jun/2011:15:25:10 -0500] cupsdIsAuthorized: requesting-user-name="sistemas" 
 D [03/Jun/2011:15:25:10 -0500] cupsdMarkDirty(-----S) 
 D [03/Jun/2011:15:25:10 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:10 -0500] cupsdAcceptClient: 21 from localhost (Domain) 
 D [03/Jun/2011:15:25:10 -0500] cupsdReadClient: 21 GET /admin/log/error_log HTTP/1.1 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:10 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:10 -0500] cupsdSetBusyState: Dirty files 
 D [03/Jun/2011:15:25:11 -0500] cupsdReadClient: 21 PUT /admin/conf/cupsd.conf HTTP/1.1 
 D [03/Jun/2011:15:25:11 -0500] cupsdSetBusyState: Active clients and dirty files 
 D [03/Jun/2011:15:25:11 -0500] cupsdAuthorize: No authentication data provided. 
 D [03/Jun/2011:15:25:11 -0500] cupsdIsAuthorized: username="" 
 D [03/Jun/2011:15:25:11 -0500] cupsdSendHeader: 21 WWW-Authenticate: Basic realm="CUPS", trc="y" 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 21 
 D [03/Jun/2011:15:25:11 -0500] cupsdSetBusyState: Dirty files 
 I [03/Jun/2011:15:25:11 -0500] Saving printers.conf... 
 I [03/Jun/2011:15:25:11 -0500] Generating printcap /var/run/cups/printcap... 
 I [03/Jun/2011:15:25:11 -0500] Saving job cache file "/var/cache/cups/job.cache"... 
 I [03/Jun/2011:15:25:11 -0500] Saving subscriptions.conf... 
 D [03/Jun/2011:15:25:11 -0500] cupsdSetBusyState: Not busy 
 D [03/Jun/2011:15:25:11 -0500] cupsdAcceptClient: 21 from localhost (Domain) 
 D [03/Jun/2011:15:25:11 -0500] cupsdReadClient: 21 PUT /admin/conf/cupsd.conf HTTP/1.1 
 D [03/Jun/2011:15:25:11 -0500] cupsdSetBusyState: Active clients 
 D [03/Jun/2011:15:25:11 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred 
 D [03/Jun/2011:15:25:11 -0500] cupsdIsAuthorized: username="sistemas" 
 I [03/Jun/2011:15:25:11 -0500] Installing config file "/etc/cups/cupsd.conf"... 
 D [03/Jun/2011:15:25:11 -0500] cupsdSetBusyState: Not busy 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 11 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 13 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 14 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 16 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 17 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 19 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 18 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 20 
 D [03/Jun/2011:15:25:11 -0500] cupsdCloseClient: 21 
 I [03/Jun/2011:15:25:11 -0500] cupsdDefaultRIPCacheSize: 62424k 
 E [03/Jun/2011:15:25:11 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:25:11 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:26:06 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:15:26:06 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:17:35:22 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:17:35:22 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
 E [03/Jun/2011:17:35:22 -0500] [Job 1] Files have gone away! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 5! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 6! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 7! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 8! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 9! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 10! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 11! 
 E [03/Jun/2011:17:35:22 -0500] Missing <Job #> directive on line 12! 
 E [03/Jun/2011:17:35:22 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory 
 E [03/Jun/2011:17:36:36 -0500] Unable to execute /usr/lib/cups/filter/kmfilter: insecure file permissions (0100555) 
 E [03/Jun/2011:17:36:36 -0500] [Job 4] Unable to start filter "kmfilter" - Operation not permitted. 
 E [03/Jun/2011:17:36:36 -0500] [Job 4] Stopping job because the scheduler could not execute a filter. 
 
```
 

 Last
 ```

 root@sistemas-desktop:~# cat /var/log/cups/page_log 
 cat: /var/log/cups/page_log: no such file or directory
 
```

---

### Post by Toz on 2011-06-03
Ok - the logs are telling us something:
> E [03/Jun/2011:17:35:22 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root 
and
> E [03/Jun/2011:17:36:36 -0500] Unable to execute /usr/lib/cups/filter/kmfilter: insecure file permissions (0100555) 
 E [03/Jun/2011:17:36:36 -0500] [Job 4] Unable to start filter "kmfilter" - Operation not permitted. 
 E [03/Jun/2011:17:36:36 -0500] [Job 4] Stopping job because the scheduler could not execute a filter.

So lets try this:```

sudo chown root:root /usr/lib/cups/filter/kmfilter
sudo chmod 755 /usr/lib/cups/filter/kmfilter
sudo /etc/init.d/cups restart
```

And please try to print again. If it doesn't work, please post back /var/log/cups/error_log

---

### Post by Antrax_akb on 2011-06-04
Thanks for your answers.

 command to print something, and the pc tells me and send but not sent anything.

 This appears in the error_log

```

sistemas@sistemas-desktop:~$ sudo chown root:root /usr/lib/cups/filter/kmfilter
[sudo] password for sistemas: 
sistemas@sistemas-desktop:~$ sudo chmod 755 /usr/lib/cups/filter/kmfilter
sistemas@sistemas-desktop:~$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
sistemas@sistemas-desktop:~$ sudo cat /var/log/cups/error_log
E [04/Jun/2011:11:32:40 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root
E [04/Jun/2011:11:32:40 -0500] Filter "/usr/lib/cups/filter/kmfilter" for printer "KONICA-MINOLTA-IP-424" not owned by root
E [04/Jun/2011:12:15:32 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
sistemas@sistemas-desktop:~$

```


thanks for your great help are supporting me a lot and besides I am learning a lot

---

### Post by Toz on 2011-06-04
*scratches head*
What does ```
ls -l /usr/lib/cups/filter/kmfilter
```say?

---

### Post by Toz on 2011-06-04
An what does ```
ls -l /usr/lib/kmpu/printutility.filter.cups
```say?

---

### Post by Antrax_akb on 2011-06-06
Sorry takeme long to answer

> **Toz said:**
> *scratches head*
What does ```
ls -l /usr/lib/cups/filter/kmfilter
```say?


It say-


```

sistemas@sistemas-desktop:~$ ls -l /usr/lib/cups/filter/kmfilter
-rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/cups/filter/kmfilter
sistemas@sistemas-desktop:~$ 


```thnks



PS
I change the "printutility.filter.cups"with "konicaminolta.filter.cups

Say 
```

sistemas@sistemas-desktop:~$ ls -l /usr/lib/kmpu/printutility.filter.cups
ls: can not access /usr/lib/kmpu/printutility.filter.cups: No such file or directory
sistemas@sistemas-desktop:~$ ls -l /usr/lib/kmpu/konicaminolta.filter.cups
-rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/kmpu/konicaminolta.filter.cups
sistemas@sistemas-desktop:~$ 

```

---

### Post by Toz on 2011-06-06
Lets try one more time:

1. Post back results of ```
ls -l /usr/lib/kmpu/konicaminolta.filter.cups
```

2. ```
mv /usr/lib/cups/filter/kmfilter /usr/lib/cups/filter/kmfilter.old
```
Post back results of ```
ls -l /usr/lib/cups/filter/kmfilter*
```

3. ```
ln -s /usr/lib/kmpu/konicaminolta.filter.cups /usr/lib/cups/filter/kmfilter
```
Post back results of ```
ls -l /usr/lib/cups/filter/kmfilter*
```

4. Restart cups ```
/etc/init.d/cups restart
```

5. Post back results of ```
ls -l /usr/lib/cups/filter/kmfilter*
```

6. Print Something

7. Post back contents of > cat /var/log/cups/error_log

---

### Post by Antrax_akb on 2011-06-07
ok.. it says

```

sistemas@sistemas-desktop:~$ ls -l /usr/lib/kmpu/konicaminolta.filter.cups 
   -rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/kmpu/konicaminolta.filter.cups 
    sistemas@sistemas-desktop:~$ mv /usr/lib/cups/filter/kmfilter /usr/lib/cups/filter/kmfilter.old 
    mv intenta sobrescribr «/usr/lib/cups/filter/kmfilter.old». ¿ignorar modo 0555 (r-xr-xr-x)? s 
    mv: no se puede mover «/usr/lib/cups/filter/kmfilter» a «/usr/lib/cups/filter/kmfilter.old»: Permiso denegado 
    sistemas@sistemas-desktop:~$ sudo mv /usr/lib/cups/filter/kmfilter /usr/lib/cups/filter/kmfilter.old 
    [sudo] password for sistemas: 
    sistemas@sistemas-desktop:~$ ls -l /usr/lib/cups/filter/kmfilter 
    ls: no se puede acceder a /usr/lib/cups/filter/kmfilter: No existe el fichero o el directorio 
    sistemas@sistemas-desktop:~$ ls -l /usr/lib/cups/filter/kmfilter* 
    -rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/cups/filter/kmfilter.old 
    sistemas@sistemas-desktop:~$ sudo ln -s /usr/lib/kmpu/konicaminolta.filter.cups /usr/lib/cups/filter/kmfilter 
    sistemas@sistemas-desktop:~$ ls -l /usr/lib/cups/filter/kmfilter* 
    lrwxrwxrwx 1 root root   39 2011-06-07 12:02 /usr/lib/cups/filter/kmfilter -> /usr/lib/kmpu/konicaminolta.filter.cups 
    -rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/cups/filter/kmfilter.old 
    sistemas@sistemas-desktop:~$ /etc/init.d/cups restart 
     * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 792: Operation not permitted 
    cupsd: Child exited on signal 15! 
                                                                             [fail] 
    sistemas@sistemas-desktop:~$ /etc/init.d/cups restart 
     * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 792: Operation not permitted 
    cupsd: Child exited on signal 15! 
                                                                             [fail] 
    [LEFT]sistemas@sistemas-desktop:~$ sudo /etc/init.d/cups restart[/LEFT]
    [LEFT][sudo] password for sistemas: [/LEFT]
    [LEFT] * Restarting Common Unix Printing System: cupsd                         [ OK ] [/LEFT]
    [LEFT]sistemas@sistemas-desktop:~$ ls -l /usr/lib/cups/filter/kmfilter*[/LEFT]
    [LEFT]lrwxrwxrwx 1 root root   39 2011-06-07 12:02 /usr/lib/cups/filter/kmfilter -> /usr/lib/kmpu/konicaminolta.filter.cups[/LEFT]
    [LEFT]-rwxr-xr-x 2 root root 1785 2006-04-25 05:14 /usr/lib/cups/filter/kmfilter.old[/LEFT]
       
  

```ande the error_log

```

 sistemas@sistemas-desktop:~$ cat /var/log/cups/error_log
    [LEFT]E [07/Jun/2011:12:58:36 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory[/LEFT]
    [LEFT]E [07/Jun/2011:14:37:26 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory[/LEFT]
    [LEFT]E [07/Jun/2011:15:05:05 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory[/LEFT]
    [LEFT]E [07/Jun/2011:15:06:37 -0500] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]E [07/Jun/2011:15:07:36 -0500] [Job 11] Job stopped due to filter errors; please consult the error_log file for details.[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] The following messages were recorded from 15:07:30 to 15:07:36[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Adding start banner page "none".[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Adding end banner page "none".[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] File of type application/postscript queued by "sistemas".[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] hold_until=0[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Queued on "KONICA-MINOLTA-IP-424" by "sistemas".[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] job-sheets=none,none[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[0]="KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[1]="11"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[2]="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[3]="Test Page"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[4]="1"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[5]="PageSize=A4 job-uuid=urn:uuid:1c10675c-2f84-3307-6879-87968210c80f job-originating-host-name=localhost"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[6]="/var/spool/cups/d00011-001"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[0]="CUPS_CACHEDIR=/var/cache/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[1]="CUPS_DATADIR=/usr/share/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[6]="CUPS_SERVERROOT=/etc/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[7]="CUPS_STATEDIR=/var/run/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[8]="HOME=/var/spool/cups/tmp"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[10]="SERVER_ADMIN=root@sistemas-desktop"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[11]="SOFTWARE=CUPS/1.4.3"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[12]="TMPDIR=/var/spool/cups/tmp"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[13]="TZ=America/Mexico_City"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[14]="USER=root"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[16]="CUPS_ENCRYPTION=IfRequested"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[17]="IPP_PORT=631"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[18]="CHARSET=utf-8"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[19]="LANG=es_MX.UTF-8"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[20]="PPD=/etc/cups/ppd/KONICA-MINOLTA-IP-424.ppd"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[21]="RIP_MAX_CACHE=62424k"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[22]="CONTENT_TYPE=application/postscript"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[23]="DEVICE_URI=socket://172.16.1.58:9100"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[24]="PRINTER_INFO=KONICA MINOLTA IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[25]="PRINTER_LOCATION=172.16.1.58"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[26]="PRINTER=KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[27]="CUPS_FILETYPE=document"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] envp[28]="FINAL_CONTENT_TYPE=printer/KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Started filter /usr/lib/cups/filter/kmfilter (PID 1334)[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Started backend /usr/lib/cups/backend/socket (PID 1335)[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] /usr/lib/cups/filter/kmfilter: Permission denied[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: +connecting-to-device[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Looking up "172.16.1.58"...[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Connecting to 172.16.1.58:9100[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Conectando a la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -connecting-to-device[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Conectado a la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Connected to 172.16.1.58:9100 (IPv4)...[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] hrDeviceDesc="7235"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] ATTR: marker-colors=none[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] ATTR: marker-names="Toner"[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] ATTR: marker-types=toner[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] ATTR: marker-levels=-1[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: +media-low-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -media-empty-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -toner-low-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -toner-empty-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -door-open-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -media-jam-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -input-tray-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -output-tray-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -marker-supply-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -output-area-almost-full-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] STATE: -output-area-full-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0x20cec844, use_bc=1, side_cb=0xa20570)[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Archivo de impresión enviado; esperando a que finalice la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] prtMarkerSuppliesLevel.1.1 = -3[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] ATTR: marker-levels=-1[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] Lista para imprimir.[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] End of messages[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] printer-state=3(idle)[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] printer-state-message="Lista para imprimir."[/LEFT]
    [LEFT]D [07/Jun/2011:15:07:36 -0500] [Job 11] printer-state-reasons=media-low-report[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to ::1:631 (IPv6)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to 127.0.0.1:631 (IPv4)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to /var/run/cups/cups.sock (Domain)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Remote access is disabled.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] Added auto ServerAlias sistemas-desktop[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Loaded configuration file "/etc/cups/cupsd.conf"[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Using default TempDir of /var/spool/cups/tmp...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Configured for up to 100 clients.[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Allowing up to 100 client connections per host.[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Using policy "default" as the default![/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] load_ppd: Loading /var/cache/cups/KONICA-MINOLTA-IP-424.ipp...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] cupsdRegisterPrinter(p=0x21737690(KONICA-MINOLTA-IP-424))[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] cupsdMarkDirty(---p--)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Partial reload complete.[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to ::1:631 on fd 5...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to 127.0.0.1:631 on fd 7...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Listening to /var/run/cups/cups.sock on fd 8...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:22 -0500] Resuming new connection processing...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:22 -0500] Discarding unused server-restarted event...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] cupsdAcceptClient: 11 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: clients=1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: jobs=10[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: jobs-active=1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: printers=1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: printers-implicit=0[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: stringpool-string-count=1092[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: stringpool-alloc-bytes=8480[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:23 -0500] Report: stringpool-total-bytes=25248[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:24 -0500] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:24 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:24 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:24 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Get-Jobs ipp://localhost/printers/[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Get-Jobs ipp://localhost/printers/[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 2] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 3] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 4] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 5] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 6] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 7] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 8] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 9] Loading attributes...[/LEFT]
    [LEFT]E [07/Jun/2011:15:08:25 -0500] [Job 9] Unable to queue job for destination "KONICA-MINOLTA-IP-424-2"![/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] [Job 10] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Create-Printer-Subscription /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdCreateSubscription(con=0x217700a8(11), uri="/")[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] pullmethod="ippget"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] notify-lease-duration=86400[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] notify-time-interval=0[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Added subscription 13 for server[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:25 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:26 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAcceptClient: 13 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 13 POST /printers/KONICA-MINOLTA-IP-424 HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 13 1.1 Print-Job 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Print-Job ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job ???] Auto-typing file...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job ???] Request file type is application/vnd.cups-banner.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(----J-)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] add_job: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Adding default job-sheets values "none,none"...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Adding start banner page "none".[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(----J-)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Adding end banner page "none".[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] File of type application/vnd.cups-banner queued by "sistemas".[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] hold_until=0[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Queued on "KONICA-MINOLTA-IP-424" by "sistemas".[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(----J-)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] job-sheets=none,none[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[0]="KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[1]="12"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[2]="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[3]="Test Page"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[4]="1"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[5]="job-uuid=urn:uuid:62c18eca-d168-3898-5889-3ccb30238bea job-originating-host-name=localhost"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] argv[6]="/var/spool/cups/d00012-001"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[0]="CUPS_CACHEDIR=/var/cache/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[1]="CUPS_DATADIR=/usr/share/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[6]="CUPS_SERVERROOT=/etc/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[7]="CUPS_STATEDIR=/var/run/cups"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[8]="HOME=/var/spool/cups/tmp"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[10]="SERVER_ADMIN=root@sistemas-desktop"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[11]="SOFTWARE=CUPS/1.4.3"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[12]="TMPDIR=/var/spool/cups/tmp"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[13]="TZ=America/Mexico_City"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[14]="USER=root"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[16]="CUPS_ENCRYPTION=IfRequested"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[17]="IPP_PORT=631"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[18]="CHARSET=utf-8"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[19]="LANG=es_MX.UTF-8"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[20]="PPD=/etc/cups/ppd/KONICA-MINOLTA-IP-424.ppd"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[21]="RIP_MAX_CACHE=62424k"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[23]="DEVICE_URI=socket://172.16.1.58:9100"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[24]="PRINTER_INFO=KONICA MINOLTA IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[25]="PRINTER_LOCATION=172.16.1.58"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[26]="PRINTER=KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[27]="CUPS_FILETYPE=document"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] envp[28]="FINAL_CONTENT_TYPE=printer/KONICA-MINOLTA-IP-424"[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Started filter /usr/lib/cups/filter/bannertops (PID 1380)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Started filter /usr/lib/cups/filter/kmfilter (PID 1381)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Started backend /usr/lib/cups/backend/socket (PID 1382)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] PID 1381 (/usr/lib/cups/filter/kmfilter) stopped with status 22![/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] /usr/lib/cups/filter/kmfilter: Permission denied[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: +connecting-to-device[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] Looking up "172.16.1.58"...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] Connecting to 172.16.1.58:9100[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Conectando a la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -connecting-to-device[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:27 -0500] [Job 12] Conectado a la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] Connected to 172.16.1.58:9100 (IPv4)...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] load_banner(filename="/var/spool/cups/d00012-001")[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] ATTR: marker-colors=none[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(P-----)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] ATTR: marker-names="Toner"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(P-----)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] ATTR: marker-types=toner[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(P-----)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] ATTR: marker-levels=-1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(P-----)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: +media-low-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -media-empty-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -toner-low-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -toner-empty-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -door-open-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -media-jam-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -input-tray-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -output-tray-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -marker-supply-missing-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -output-area-almost-full-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] STATE: -output-area-full-warning[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0x21cd1844, use_bc=1, side_cb=0x9cb570)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] [Job 12] Page = 595x842; 12,12 to 583,830[/LEFT]
    [LEFT]E [07/Jun/2011:15:08:27 -0500] PID 1380 (/usr/lib/cups/filter/bannertops) crashed on signal 13![/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAcceptClient: 16 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 16 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAcceptClient: 17 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 1.1 Get-Jobs 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Jobs ipp://localhost/printers/[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 WAITING Closing on EOF[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdCloseClient: 17[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAcceptClient: 17 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAcceptClient: 18 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 17 1.1 Get-Job-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Job-Attributes ipp://localhost/jobs/12[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/12) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:27 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:28 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:29 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:30 -0500] cupsdSetBusyState: Printing jobs and dirty files[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:32 -0500] [Job 12] Archivo de impresión enviado; esperando a que finalice la impresora...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] ATTR: marker-levels=-1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(P-----)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:32 -0500] [Job 12] Lista para imprimir.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] PID 1382 (/usr/lib/cups/backend/socket) exited with no errors.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]E [07/Jun/2011:15:08:32 -0500] [Job 12] Job stopped due to filter errors; please consult the error_log file for details.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(----J-)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] The following messages were recorded from 15:08:27 to 15:08:32[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] hrDeviceDesc="7235"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] prtMarkerSuppliesLevel.1.1 = -3[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] End of messages[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] printer-state=3(idle)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] printer-state-message="Lista para imprimir."[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] [Job 12] printer-state-reasons=media-low-report[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAcceptClient: 14 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 14 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAcceptClient: 19 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 16 WAITING Closing on EOF[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdCloseClient: 16[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 19 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 19 1.1 Get-Jobs 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Get-Jobs ipp://localhost/printers/[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 19 WAITING Closing on EOF[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdCloseClient: 19[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAcceptClient: 16 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 16 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 17 WAITING Closing on EOF[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdCloseClient: 17[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Get-Notifications /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:32 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] [Job 12] Unloading...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAcceptClient: 17 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 17 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Get-Printer-Attributes ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://sistemas-desktop:0/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 17 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 17 1.1 Get-Job-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Get-Job-Attributes ipp://localhost/jobs/12[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] [Job 12] Loading attributes...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/12) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Get-Printer-Attributes ipp://localhost/printers/KONICA-MINOLTA-IP-424[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/KONICA-MINOLTA-IP-424) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:33 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Printers[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Classes[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdReadClient: 18 1.1 CUPS-Get-Default 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] CUPS-Get-Default[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:34 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] [Job 11] Unloading...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 11 1.1 Get-Job-Attributes 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] Get-Job-Attributes ipp://localhost/jobs/12[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/12) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 11 POST / HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 11 1.1 Cancel-Subscription 1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] Cancel-Subscription /[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdIsAuthorized: requesting-user-name="sistemas"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdMarkDirty(-----S)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAcceptClient: 19 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 19 GET /admin/log/error_log HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 19 PUT /admin/conf/cupsd.conf HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAuthorize: No authentication data provided.[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdIsAuthorized: username=""[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSendHeader: 19 WWW-Authenticate: Basic realm="CUPS", trc="y"[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 19[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAcceptClient: 19 from localhost (Domain)[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdReadClient: 19 PUT /admin/conf/cupsd.conf HTTP/1.1[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Active clients and dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdAuthorize: Authorized as sistemas using PeerCred[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdIsAuthorized: username="sistemas"[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] Installing config file "/etc/cups/cupsd.conf"...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Dirty files[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 11[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 13[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 18[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 14[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 16[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 17[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdCloseClient: 19[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] Saving printers.conf...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] Generating printcap /var/run/cups/printcap...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] Saving job cache file "/var/cache/cups/job.cache"...[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] Saving subscriptions.conf...[/LEFT]
    [LEFT]D [07/Jun/2011:15:08:39 -0500] cupsdSetBusyState: Not busy[/LEFT]
    [LEFT]I [07/Jun/2011:15:08:39 -0500] cupsdDefaultRIPCacheSize: 62424k[/LEFT]
   
  


```thnks for help me..

I call to konica central, and it say the only driver for linux it's in the page but, it's the same i downloaded.

and  said that is 100% functional and that the problem is caused by the OS.

I told them what happened and according will be looking for a solution

---

### Post by Toz on 2011-06-07
> E [07/Jun/2011:15:06:37 -0500] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/KONICA-MINOLTA-IP-424) from localhost> D [07/Jun/2011:15:07:36 -0500] [Job 11] argv[5]="PageSize=A4 job-uuid=urn:uuid:1c10675c-2f84-3307-6879-87968210c80f job-originating-host-name=localhost"
The page that you are sending seems to be formated for A4 but the printer can't accept this format. Can you go to your printer administration program and change the default printer type to "Letter" and try printing again?

Also, make sure you're print queue is empty before you try.

Post back results of error_log.

---

### Post by Antrax_akb on 2011-06-08
hello 
it say 

```

E [08/Jun/2011:10:54:43 -0500] [Job 17] Job stopped due to filter errors; please consult the error_log file for details.
D [08/Jun/2011:10:54:43 -0500] [Job 17] The following messages were recorded from 10:54:37 to 10:54:43
D [08/Jun/2011:10:54:43 -0500] [Job 17] Adding start banner page "none".
D [08/Jun/2011:10:54:43 -0500] [Job 17] Adding end banner page "none".
D [08/Jun/2011:10:54:43 -0500] [Job 17] File of type application/postscript queued by "sistemas".
D [08/Jun/2011:10:54:43 -0500] [Job 17] hold_until=0
D [08/Jun/2011:10:54:43 -0500] [Job 17] Queued on "KONICA-MINOLTA-IP-424" by "sistemas".
D [08/Jun/2011:10:54:43 -0500] [Job 17] job-sheets=none,none
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[0]="KONICA-MINOLTA-IP-424"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[1]="17"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[2]="sistemas"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[3]="Test Page"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[4]="1"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[5]="PageSize=Letter job-uuid=urn:uuid:54b50826-fe4e-385d-71e3-944f0cbeb4ff job-originating-host-name=localhost"
D [08/Jun/2011:10:54:43 -0500] [Job 17] argv[6]="/var/spool/cups/d00017-001"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[8]="HOME=/var/spool/cups/tmp"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[10]="SERVER_ADMIN=root@sistemas-desktop"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[11]="SOFTWARE=CUPS/1.4.3"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[13]="TZ=America/Mexico_City"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[14]="USER=root"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[17]="IPP_PORT=631"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[18]="CHARSET=utf-8"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[19]="LANG=es_MX.UTF-8"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[20]="PPD=/etc/cups/ppd/KONICA-MINOLTA-IP-424.ppd"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[21]="RIP_MAX_CACHE=62424k"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[22]="CONTENT_TYPE=application/postscript"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[23]="DEVICE_URI=socket://172.16.1.58:9100"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[24]="PRINTER_INFO=KONICA MINOLTA IP-424"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[25]="PRINTER_LOCATION=172.16.1.58"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[26]="PRINTER=KONICA-MINOLTA-IP-424"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[27]="CUPS_FILETYPE=document"
D [08/Jun/2011:10:54:43 -0500] [Job 17] envp[28]="FINAL_CONTENT_TYPE=printer/KONICA-MINOLTA-IP-424"
D [08/Jun/2011:10:54:43 -0500] [Job 17] Started filter /usr/lib/cups/filter/kmfilter (PID 1385)
D [08/Jun/2011:10:54:43 -0500] [Job 17] Started backend /usr/lib/cups/backend/socket (PID 1386)
D [08/Jun/2011:10:54:43 -0500] [Job 17] /usr/lib/cups/filter/kmfilter: Permission denied
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: +connecting-to-device
D [08/Jun/2011:10:54:43 -0500] [Job 17] Looking up "172.16.1.58"...
D [08/Jun/2011:10:54:43 -0500] [Job 17] Connecting to 172.16.1.58:9100
D [08/Jun/2011:10:54:43 -0500] [Job 17] Conectando a la impresora...
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -connecting-to-device
D [08/Jun/2011:10:54:43 -0500] [Job 17] Conectado a la impresora...
D [08/Jun/2011:10:54:43 -0500] [Job 17] Connected to 172.16.1.58:9100 (IPv4)...
D [08/Jun/2011:10:54:43 -0500] [Job 17] hrDeviceDesc="7235"
D [08/Jun/2011:10:54:43 -0500] [Job 17] ATTR: marker-colors=none
D [08/Jun/2011:10:54:43 -0500] [Job 17] ATTR: marker-names="Toner"
D [08/Jun/2011:10:54:43 -0500] [Job 17] ATTR: marker-types=toner
D [08/Jun/2011:10:54:43 -0500] [Job 17] ATTR: marker-levels=-1
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: +media-low-report
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -media-empty-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -toner-low-report
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -toner-empty-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -door-open-report
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -media-jam-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -input-tray-missing-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -output-tray-missing-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -marker-supply-missing-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -output-area-almost-full-report
D [08/Jun/2011:10:54:43 -0500] [Job 17] STATE: -output-area-full-warning
D [08/Jun/2011:10:54:43 -0500] [Job 17] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0x21873844, use_bc=1, side_cb=0x4a9570)
D [08/Jun/2011:10:54:43 -0500] [Job 17] Archivo de impresión enviado; esperando a que finalice la impresora...
D [08/Jun/2011:10:54:43 -0500] [Job 17] prtMarkerSuppliesLevel.1.1 = -3
D [08/Jun/2011:10:54:43 -0500] [Job 17] ATTR: marker-levels=-1
D [08/Jun/2011:10:54:43 -0500] [Job 17] Lista para imprimir.
D [08/Jun/2011:10:54:43 -0500] [Job 17] End of messages
D [08/Jun/2011:10:54:43 -0500] [Job 17] printer-state=3(idle)
D [08/Jun/2011:10:54:43 -0500] [Job 17] printer-state-message="Lista para imprimir."
D [08/Jun/2011:10:54:43 -0500] [Job 17] printer-state-reasons=media-low-report


```


and me getting tired .. mmm I can not use those who are already Linux.
There was one driver the printer and printed a sheet, but instead printed 11 sheet of 1, there is no way to use that to only print a sheet

Greetings

---

### Post by Toz on 2011-06-08
I'm sorry, I don't understand. Did it print? Did it print 17 copies instead of 1? 

Did you clear the queue? Maybe the queue was cleared and everything came out at once. Can you try again? Maybe this time from within a program like openoffice, libreoffice, abiword, gedit, etc....

---

### Post by Antrax_akb on 2011-06-08
> **Toz said:**
> I'm sorry, I don't understand. Did it print? Did it print 17 copies instead of 1? 

Did you clear the queue? Maybe the queue was cleared and everything came out at once. Can you try again? Maybe this time from within a program like openoffice, libreoffice, abiword, gedit, etc....


Excuse my english.. yes it did. but with the default driver in xubuntu, and the queue it's empty, it print the same page 11 times, and with openoffice, etc.

with the konica driver is with the error_log show you in last post and still not print

---

### Post by Toz on 2011-06-08
Check your printer options again - System->Printing. Right-click the printer, choose Properties and go to the Job Options section. Make sure Copies says 1 and not 11.

---

### Post by linuxinstalledfromhdd on 2011-06-08
Just out of curiosity did you try using a live 32-bit disc of Ubuntu 10.10 to check your system's printer driver to see if that could be the issue here? I had printer issues with 11.04 that sound very similar to this issue.

---

### Post by Antrax_akb on 2011-06-09
Hello:

I have not attempted to try a live cd 10.10, as the computer is old and this is the most stable version I have for my workstation

 mmm .. then I have no more than pressing konica to give me a compatible driver, as I see I will not be able to print right now ..


or print 11 times as he does now, XD

thnks

---

### Post by Toz on 2011-06-09
Did you check the print options as indicated in post #19?

---

