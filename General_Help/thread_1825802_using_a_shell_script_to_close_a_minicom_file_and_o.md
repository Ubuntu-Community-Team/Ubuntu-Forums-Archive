---
title: "using a shell script to close a minicom file and open a new one."
date: 2011-08-15
forum: General Help
---

### Post by sd_read on 2011-08-15
Hi,

I have built a microprocessor board which will allow me to log my hydro usage. It involves a photo diode on my hydro meter which counts flashes.

Every 10 minutes I send the kWh out the serial port. Obviously I am power conscious and so I am connecting this to one of my servers which is on anyway.

I am then using minicom to collect the data but it is very hard to look at as one big fat file. What I want to do is have a cron job call a shell script to close the previous days log file and then start up another one for the present day. 

So, at say 12:05 am, close off the present minicom log file and start a new file using the new date as the file name.

So, I will have one file per day.

I did figure out how to start minicom and start logging with a file name made from the present date.

Here is my script so far:

[FONT="Times New Roman"]
     #!/bin/bash
     # By -sdr- 14/08/2011
     # Revision 1.0 14/08/2011

     # Make script crontab friendly:
     cd $(dirname $0)

     # datadir is the directory you want podcasts saved to:
     datadir=$(date +%Y-%m-%d_%H:%M:%S)

     # start minicom with file name of todays date
     minicom -C $datadir.txt
[/FONT]

What I don't know how to do is cleanly close the log file and shut down minicom.

Any help is greatly appreciated.

Thank you - Steve

---

### Post by Argus on 2012-12-20
Did you ever get anywhere with this? I'm trying to do something along the same line.

TKS

---

