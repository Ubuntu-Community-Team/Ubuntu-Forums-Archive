---
title: "Unable to print first time! Please help!"
date: 2009-11-25
forum: General Help
---

### Post by Pipps on 2009-11-25
I have a fresh installation of Ubuntu Netbook Remix. I have connected my Samsung SCX-4300 laser print, and it is recognised immediately and prints an initial test-page.

The problem arises whenever I try to print subsequently. Whenever I send a job, I can see the small printer icon appear on the panel menu. It always tells me that the job is 'pending'.

However, the job never prints. No matter how long I wait. Twelve hours, in some cases.

I then discovered that restarting my laptop caused the job to begin printing on reboot.

I then also discovered that simple removing the USB printer cable from my laptop, and then reconnecting it, also caused the job to print immediately upon reconnection.

What could be causing this problem?
Why do I have to disconnected my laptop from the printer in order to make it print?
What should I do to solve this problem and return things to their normal expected mode of operation?

---

### Post by Pipps on 2009-11-28
To summarise:

1. I click 'print' --> nothing happens.

2. I remove and reconnect my printer's USB cable --> it prints!

I cannot print any other way!

Why could this be?

---

### Post by wilee-nilee on 2009-11-28
I'm not sure if this will help but you can download the manual and there is probably firmware for it.
[http://www.samsung.com/ph/consumer/monitor-peripherals-printer/printer-multifunction/mono-multifunction/SCX-4300/XSS/index.idx?pagetype=prd_detail](http://www.samsung.com/ph/consumer/monitor-peripherals-printer/printer-multifunction/mono-multifunction/SCX-4300/XSS/index.idx?pagetype=prd_detail)

I have a old HP printer that has a specific number and then mplus the exact driver doesn't work but the one that matches the number does so you might try the messing with the drivers for Linux. It does sound strange though mine either prints or doesn't not any thing like you describe.

---

### Post by Pipps on 2009-12-10
I have today found a solution.

The driver package at the following location provided the requisite driver and its necessary installation package.

[UnifiedLinuxDriver.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UK&CttFileID=2161671&CDCttType=DR&ModelType=N&ModelName=SCX-4300&VPath=DR/200911/20091118145843093/)

To use it, simply unpack the tar file with the 'right click' > 'Extract here', and then navigate to the directory which contains the file 'install.sh', and then open a terminal in that directory and type 'sh install.sh'. Wait a few seconds, and the installation prompt should appear.

The driver which it installs is specific to the SCX-4300 printer, and the installation tool appears to have a multitude of additional drivers available, and the SCX-4300 driver which worked for me was superior to that of the default generic driver which Ubuntu found and installed previously.

Now, my documents print first time.

---

