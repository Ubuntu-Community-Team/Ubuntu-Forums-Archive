---
title: "Disk Utility Problem"
date: 2012-04-06
forum: General Help
---

### Post by ZJE123 on 2012-04-06
For a while I have been having problems with my computer, specifically Windows.  If you would like to read about THAT problem you can here: [http://forum.notebookreview.com/thinkpad-edge-x1-x100e-x120e-sl-l/654611-e520-windows-boot-error-code-0x45d.html](http://forum.notebookreview.com/thinkpad-edge-x1-x100e-x120e-sl-l/654611-e520-windows-boot-error-code-0x45d.html)

However now I am having an Ubuntu related problem.  I used the smart utility through the terminal however, I am not sure if I was using it right and have no idea how to read the information.   I then decided to used the disk utility under Ubuntu however, I am am now having problems with that.  I opened the window that talks about my hard drive then I tried to run a self test, the extended one.  Then the progress bar went nowhere and after a few seconds it said "failed (read)" however it doesn't tell me anywhere why it won't start.  I thought it meant that the test failed, but it went too fast to even diagnose anything.  I now think it means that it failed to even start the test.  I doubt that the test is just that fast that it only takes a few seconds, especially on a 500 gb hard drive.  How do I get the self test to start?  Any help will be appreciated!  In the attachments there is a picture of what it looks like.

Basically, I got an error as to why Windows won't boot and it points to the hard drive.  I am trying to see whether the hard drive is actually bad or not or if it is just windows.  This will tell me whether I need to replace the hard drive or not.

---

### Post by rmil on 2012-04-06
First you have to have smart tools eneabled in bios. The best way to use smart tools is through smartmontools in terminal through smartctl command.

Anyway I suggest command in terminal 
```
sudo badblock /dev/sdx>toyourfile
``` to check disk surface. If this file is empty everything is ok

---

### Post by sudodus on 2012-04-06
I would try the same (with the disk utility) when you run the computer booted from your install CD or USB drive. Then the evaluation of the S.M.A.R.T. status is not depending on software on a drive that might be failing.

I think it is bad enough that there are 'a few bad sectors', and would try to save as much as possible to another drive of at least the same size with ***ddrescue***. It is in the repositories and can be installed to your live system or you can download the iso file to make a dedicated ***repair*** boot CD/USB system.

If the drive is failing, the amount of bad sectors might increase rapidly, so you should act now, or it may be too late.

---

### Post by ZJE123 on 2012-04-06
> **rmil said:**
> First you have to have smart tools eneabled in bios. The best way to use smart tools is through smartmontools in terminal through smartctl command.

Anyway I suggest command in terminal 
```
sudo badblock /dev/sdx>toyourfile
``` to check disk surface. If this file is empty everything is ok

> **sudodus said:**
> I would try the same (with the disk utility) when you run the computer booted from your install CD or USB drive. Then the evaluation of the S.M.A.R.T. status is not depending on software on a drive that might be failing.

I think it is bad enough that there are 'a few bad sectors', and would try to save as much as possible to another drive of at least the same size with ***ddrescue***. It is in the repositories and can be installed to your live system or you can download the iso file to make a dedicated ***repair*** boot CD/USB system.

If the drive is failing, the amount of bad sectors might increase rapidly, so you should act now, or it may be too late.

  Yes I am scanning the hard disk now through another laptop with Windows on it to double check the errors.  After that I am going to copy what I can to my WD external hard drive and tomorrow morning, I will be on the phone with Lenovo about getting a replacement.  Thank you guys for all of your help!

---

