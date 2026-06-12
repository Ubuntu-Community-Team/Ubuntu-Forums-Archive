---
title: "How to watch TV on Ubuntu?"
date: 2009-11-12
forum: General Help
---

### Post by goatgonads on 2009-11-12
Hello, just switched from windows to Ubuntu 9.1 today. So, I am a complete noob. I need some pointers on how to set up a tuner card. I have a Hauppauge HVR-1600 and previously used it to watch TV with Windows Media Center with Comcast's QAM signal. I have spent a few nights looking for a solid "How To" but I am not finding anything that is on my level. The easier the better. I don't care if it records even.

Any tips would be appreciated. Again, my experience level with linux is less than one week. Location USA.

---

### Post by PrivateSNAFU on 2009-11-12
Have a look for tutorial on installing mythtv or   try 
sudo apt-get install dvb-utils
and install mplayer or vlc (this might be better)

The hardware should be supported in version 9.10 of ubuntu.

---

### Post by fazzuk on 2009-11-12
You might want to check out Me-TV [https://launchpad.net/me-tv](https://launchpad.net/me-tv)

It works well for me as a lightweight TV player using my Hauppauge WinTV Nova-HD-S2 card.

As of Karmic its in the universe repository.

---

### Post by goatgonads on 2009-11-12
I tinkered with MythTV for an afternoon, I couldn't get it set up correctly. I just tried Me-TV and got the following: MythTV seems to take a PHD to set up.

Me-TV produced the following error:  Failed to scan: scanning is only supported for DVB-T, DVB-S and DVB-C devices

I am not very knowledgable on the subject, but isn't USA ATSC? I tried all of the available lists included with the package, and got the same errors.

---

### Post by yazmonium on 2009-11-14
maybe this will help

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

---

### Post by goatgonads on 2009-11-15
I got MythTV to play channels, it doesn't seem to be quite what I wanted. Kaffeine seems to be what I am looking for. It shows my tuner, but does not come up with any channels when it scans.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
I've had the same problem with that tuner. I can get channels in mythtv but hate it. I just want to use vlc but so far none of the scan scripts work with this set up. Hope someone out there can help us.

---

### Post by autonomy on 2009-11-15
I think my problem is I haven't subscribed to that service to get the channels, and me-tv doesn't work for me because I don't have a dvb tuner card.

---

### Post by goatgonads on 2009-11-16
I am using w_scan and am getting the following results:

w_scan -A2 -c US >> channels.conf
w_scan version 20090808 (compiled for DVB API 5.0)
main:2741: FATAL: VDR doesn't support ATSC. Waiting for VDR channels.conf support.. :-( 

I dont know if w_scan is what I should be using, just trying everything I can. If anyone knows a better way, please advise.

---

### Post by goatgonads on 2009-11-18
Assuming you are trying to set up an ATSC tuner with me-tv try the following and let me know what you get. I have gotten it to scan, and am working on the next step.

"
As I'm sure you've deduced, Me TV does not support scanning on ATSC devices.
 To get past this, simply use the command line applications w_scan or scan to generate a channels.conf file that you can import into Me TV. The "scan" application should be already available on your system so you're almost there. Typically I think that you would run scan like this,
 

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > channels.conf
 

You might need a different tuning file though."


Here is a link to the help being given at Me-TV regarding my problem/setup



[https://answers.launchpad.net/me-tv/+question/90538](https://answers.launchpad.net/me-tv/+question/90538)

---

### Post by goatgonads on 2010-02-24
I got it working finally.

[http://ubuntuforums.org/showthread.php?t=1392684](http://ubuntuforums.org/showthread.php?t=1392684)

---

