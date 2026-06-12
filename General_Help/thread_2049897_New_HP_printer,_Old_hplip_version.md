---
title: "New HP printer, Old hplip version"
date: 2012-08-29
forum: General Help
---

### Post by AVH on 2012-08-29
The driver for my new HP Photosmart 6510 is only in hplip 3.11.10 and newer. I'm still using Lucid 10.4 LTS ( I like my eye candy), which uses hplip 3.10.2-2.

Is there a ppa for a newer version of hplip that will run in 10.4?

---

### Post by plucky on 2012-08-29
> **AVH said:**
> The driver for my new HP Photosmart 6510 is only in hplip 3.11.10 and newer. I'm still using Lucid 10.4 LTS ( I like my eye candy), which uses hplip 3.10.2-2.

Is there a ppa for a newer version of hplip that will run in 10.4?

Go to[HP Linux Imaging and Printing](http://hplipopensource.com/hplip-web/index.html) to download the latest version of HPlip.

Good Luck

---

### Post by AVH on 2012-08-29
I am hoping there is a repository available with a working backport . If there isn't I'll try the HP site.

Thanks though.

---

### Post by Ms. Daisy on 2012-08-29
In my experience with Hplip and 11.04 and 11.10, I found the version from the HP website to work better than the one in repository. YMMV.

---

### Post by AVH on 2012-08-30
I gave the version from HP a try. 

Something installed under the name the printer even though I couldn't find the printer in provided menu. But it missing most of the printer options.

As it is a wireless printer a print web server also installed. This has all the options but their selection is forbidden. When I try to change options after connecting to the web server I get ' Cups Server Error: There was an error during the CUPS operation: 'client-error-forbidden'. Below is the output of Sytem-Config-Printer-Debug...

```

alan@alan-NewBlueU:~$ system-config-printer --debug 2>&1 | tee log
Connected as user alan
refresh
Created subscription 78
<monitor.Monitor instance at 0x7f4ed4055b00>: printers and jobs lists provided
update_jobs
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
get_notifications
update_jobs
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
[]
update printer properties
no changes yet: full printer properties update
[]
Connected as user alan
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
[]
update printer properties
no changes yet: full printer properties update
[]
get_notifications
update_jobs
Authentication pass: 1
Authentication: password callback set
Authentication pass: 2
Forbidden: True
Authentication: Try as root
Connected as user root
Authentication pass: 3
Forbidden: True
Authentication: giving up
Authentication pass: 1
Authentication: password callback set
Authentication pass: 2
Forbidden: True
Authentication: giving up
get_notifications
update_jobs


```

---

### Post by jimmac49 on 2012-08-30
I use the HP Photosmart 6510, and have run it both in 10.04 and at this time 12.04, using  (hplip-3.12.6.run) available from HPLIP Website, just follow the instructions.

Hope this helps.

---

### Post by rickm1945 on 2012-08-30
HPLIP, both the toolbox and the printing and imaging software are in the Software manager in Ubuntu 12.04. HPLIP, both the toolbox and the printing and imaging sftware are in the Software manager in Ubuntu 12.04. Open Software manager an type hplip and they will come up, at least they did for me.

---

### Post by AVH on 2012-08-30
> **jimmac49 said:**
> I use the HP Photosmart 6510, and have run it both in 10.04 and at this time 12.04, using  (hplip-3.12.6.run) available from HPLIP Website, just follow the instructions.

Hope this helps.

Thats what I did to get what Ive got, but I cant edit any of the printer options

---

### Post by AVH on 2012-08-30
> **rickm1945 said:**
> HPLIP, both the toolbox and the printing and imaging software are in the Software manager in Ubuntu 12.04.

My problem is that I'm running Lucid Lynx 10.04 but need a newer version of HPLIP than the software store provides for that release of Ubuntu. 

The newer version of HPLIP that I got from HP doesn't see to work quite right with Lucid. I running into what looks somewhat like permission errors. See the output from a debug of 'system-config-printer'  above.

---

### Post by AVH on 2012-09-02
Figured it out! Finally.

I had to add the printer through CUPS, and not Ubuntu, by going to 'Localhost:631' in a browser and selecting the 'Adminsitration' tab and then 'Add Printer'.

---

