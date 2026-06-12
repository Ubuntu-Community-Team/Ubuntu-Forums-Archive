---
title: "Installing Ubuntu 10.04 LTS on a netbook"
date: 2011-11-04
forum: General Help
---

### Post by pauloz on 2011-11-04
Hi everybody

I have an ASUS 1005HA netbook that presently dual boots with Windows XP. I'm seriously thinking of ditching Windows XP because it will not be supported soon - when I don't know. Also, the existing setup i.e dual booting on my netbook makes it run slowly. I intend to install Ubuntu 10.04 LTS instead of 11.10, which is presently on my netbook. Whilst Ubuntu 11.10 is OK I do prefer 10.04 LTS because I have that version on my desktop computer and it works flawlessly and am comfortable with it.
Can anybody help me and advise how I should go about installing 10.04 LTS solely on my netbook? Quite honestly, whatever Windows XP can do, I find that Ubuntu 10.04 LTS can do it just as well, if not better.

Thanks.

---

### Post by drawkcab on 2011-11-04
1.  Download the 10.04.3 .iso to your desktop machine while running ubuntu.

2.  Use usb start up creator to create a bootable usb.

3.  Plug the usb into your eeepc.

4.  Reboot the eeepc and, as it starts up, hit esc a bunch of times--it will eventually bring you to boot menu.

5.  Select the usb, boot into and then install ubuntu from the usb.

FWIW, the netbook desktop for 10.04 is pretty nice on the eeepc.

[http://www.youtube.com/watch?v=xEUlczV2ggI](http://www.youtube.com/watch?v=xEUlczV2ggI)

---

### Post by M!K3_$ on 2011-11-04
I wonder how much you could pick a first gen netbook like that up for? hmm.

---

### Post by pauloz on 2011-11-04
> **drawkcab said:**
> 1.  Download the 10.04.3 .iso to your desktop machine while running ubuntu.

2.  Use usb start up creator to create a bootable usb.

3.  Plug the usb into your eeepc.

4.  Reboot the eeepc and, as it starts up, hit esc a bunch of times--it will eventually bring you to boot menu.

5.  Select the usb, boot into and then install ubuntu from the usb.

FWIW, the netbook desktop for 10.04 is pretty nice on the eeepc.

[http://www.youtube.com/watch?v=xEUlczV2ggI](http://www.youtube.com/watch?v=xEUlczV2ggI)
Thanks drawkcab - will this procedure wipe all existing contents from my netbook?

---

### Post by tartalo on 2011-11-04
> **pauloz said:**
> will this procedure wipe all existing contents from my netbook?

Only if you decide so during the installation process

---

### Post by snowpine on 2011-11-04
End-of-support for Windows XP is not 100% definite yet (it's been announced and then extended a couple of times) but end-of-support for Ubuntu 10.04 is definitely scheduled for April 2012. (edit: see below!) Keep that in mind when making your decision and good luck! Also I highly recommend extensively test-driving in "live" mode before you install, so there are no nasty surprises. :)

---

### Post by cottfcfan on 2011-11-04
Doesn't support for 10.04 end April 2013?
3 years for LTSs. Correct me if i,m wrong.
And from what I here the next LTS could have 5 years support.

---

### Post by Gatemaze on 2011-11-04
There are no nasty surprises. I have exactly the same model (1005HA) and 10.04 work just fine. Install eee-control also. I think it is in the repos otherwise websearch for it. The only thing you will need to fix is the mic. Download pavucontrol and mute the left or the right mic and then it will work.

During install do manual partition to keep your windows alongside. Ask a friend if you are not comfortable with partitioning tools.

---

### Post by Gatemaze on 2011-11-04
> **cottfcfan said:**
> Doesn't support for 10.04 end April 2013?
3 years for LTSs. Correct me if i,m wrong.
And from what I here the next LTS could have 5 years support.

Yup, 10.04 is until 4/13. [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.04_LTS_.28Lucid_Lynx.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.04_LTS_.28Lucid_Lynx.29)

---

### Post by laithbsoul on 2011-11-04
> **cottfcfan said:**
> Doesn't support for 10.04 end April 2013?
3 years for LTSs. Correct me if i,m wrong.
And from what I here the next LTS could have 5 years support.

Correct support for 10.04 (desktop) Doesn't end till 04/2013 12.04 (desktop) will have the same 3 year support where your probably getting the 5 years of support from is the server version all server versions have 5 years of support

---

### Post by cottfcfan on 2011-11-04
I think the support for 12.04 has been extended to 5 years.
See link.
[http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/](http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/)

---

### Post by laithbsoul on 2011-11-04
> **cottfcfan said:**
> I think the support for 12.04 has been extended to 5 years.
See link.
[http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/](http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/)

I had not seen that yet... Nice! Thats great news.

---

### Post by snowpine on 2011-11-04
Whoops, my bad... the next LTS does come out in April 2012 but of course support for 10.04 overlaps for a year until April 2013. :)

---

### Post by pauloz on 2011-11-05
> **Gatemaze said:**
> There are no nasty surprises. I have exactly the same model (1005HA) and 10.04 work just fine. Install eee-control also. I think it is in the repos otherwise websearch for it. The only thing you will need to fix is the mic. Download pavucontrol and mute the left or the right mic and then it will work.

During install do manual partition to keep your windows alongside. Ask a friend if you are not comfortable with partitioning tools.
Thanks for the tips Gatemaze. I don't intend to keep Windows XP on my 1005HA - I don't really need it anymore. I'm sure Ubuntu solely can do the job.

---

### Post by pauloz on 2011-11-06
Thanks to everybody who replied to this thread.

I've managed to get my netbook (ASUS 1005HA) up and running with Ubuntu 10.04.3 but I'm having problems with my wireless network connection. I'm finding I have to manually connect each time I boot up. Can I fix this so it will automatically connect when booting?

---

### Post by Gatemaze on 2011-11-07
> **pauloz said:**
> Thanks to everybody who replied to this thread.

I've managed to get my netbook (ASUS 1005HA) up and running with Ubuntu 10.04.3 but I'm having problems with my wireless network connection. I'm finding I have to manually connect each time I boot up. Can I fix this so it will automatically connect when booting?

Right click on network manager in the taskbar -> edit connections -> edit the wireless connection you want -> and if i recall well there is a tick box connect automatically.

However, in my machines, both netbook and laptop, it takes a min to connect to my hidden wifi after logging in. I think it connects quickly to non-hidden.

---

