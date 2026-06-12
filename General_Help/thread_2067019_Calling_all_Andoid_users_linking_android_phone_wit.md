---
title: "Calling all Andoid users: linking android phone with ubuntu 12.04"
date: 2012-10-05
forum: General Help
---

### Post by Advait on 2012-10-05
Hi All,

I'm an Android newbie and soon plan to purchase my first Android phone (probably with Android 4 ICS). I'm using 12.04.

What are the best practices for connecting an Android phone with Ubuntu? I did some googling and thread searching on this and didn't find much details.

My plan is to move all my Outlook contacts and tasks into Android. I don't need to sync them. I plan to do a daily backup of my Android phone and save that file into Ubuntu. I plan to only manage contacts and tasks on the Android, not in Ubuntu. I don't need or plan to sync my gmail contacts with Android.

Thanks!

Advait

---

### Post by Mark Phelps on 2012-10-06
I'm not aware that you can use Outlook on an Android OS.  So, moving your contacts and tasks is not a good idea if that is the case.

As to connecting the phone, Google decided to REMOVE the capability to connect an Android phone as a USB Mass Storage device with the new OS version -- ICS.  So, the previous way of simply connecting with a USB cable doesn't work well anymore.

There are threads about using MTP, but I've not been able to get that to work well, as have others reported as well.

---

### Post by MoebusNet on 2012-10-06
> **Mark Phelps said:**
> (Snip)As to connecting the phone, Google decided to REMOVE the capability to connect an Android phone as a USB Mass Storage device with the new OS version -- ICS.  So, the previous way of simply connecting with a USB cable doesn't work well anymore.(/Snip)

I'm not sure where you got the idea that ICS is unable to "connect an Android phone as a USB Mass Storage device" but I am doing precisely that as I type, looking at the photos taken by my HTC Rezound running ICS version 4.0.3 and Sense version 3.6 which is what Verizon sent me as an OTA update from Gingerbread. Unless you have a link to an upcoming change?...

---

### Post by thatguruguy on 2012-10-06
There's a great program available on the Google Play store called "Airdroid." It makes moving packages back and forth between your computer and android device pretty painless.

---

### Post by MoebusNet on 2012-10-06
@Advait > (Snip)What are the best practices for connecting an Android phone with Ubuntu?(/Snip)

Ubuntu sees an Android phone as a USB storage device in my experience. Although it varies from Android version to version, on my HTC Rezound the procedure is fairly straightforward:

1) Plug your phone into a running Ubuntu's USB port.
2) If your phone is asleep, unlock the phone (mine uses an upward swipe)
3) A menu automatically appears _on your phone_ that offers a selection of "Charge only" or "Connnect as USB Mass Storage Device". Select "Connnect as USB Mass Storage Device", then click "OK".
4) Phone internal storage and SD storage appear as 2 separate USB drives.

NOTE: Step #3 can be modified in Menu>Settings so that it changes the default selection ("Charge Only"). If you aren't getting this menu, check Menu>Settings>Connect to PC>Default connection type. If you wait too long to unlock your phone, the PC connection menu will time out. This is an Android thing, not Ubuntu.

---

### Post by Advait on 2012-10-06
> **Mark Phelps said:**
> I'm not aware that you can use Outlook on an Android OS.  So, moving your contacts and tasks is not a good idea if that is the case.

Once I transfer all my contacts and tasks to Android, I will no longer need Outlook. I plan to manage contacts and tasks on the phone, not on a PC.

> **Mark Phelps said:**
> As to connecting the phone, Google decided to REMOVE the capability to  connect an Android phone as a USB Mass Storage device with the new OS  version -- ICS.  So, the previous way of simply connecting with a USB  cable doesn't work well anymore. There are threads about using MTP, but I've not been able to get that to work well, as have others reported as well.

May not be a problem in my case. I presume I can create a full Android backup file with Titanium, then copy that backup file onto the SDHC chip. and then remove the SDHC chip and insert it into my PC using a USB adapter , and then copy the backup file to my Ubuntu PC.

Any flaws in that plan? Thanks for responding to my newbie questions! Cheers,

Advait

---

### Post by Advait on 2012-10-06
Thank you *MoebusNet.* I plan to get an ICS phone and if it shows up in Ubuntu as attached drives that's great! Easier then yanking out the SDHC and connecting it to the PC. 

Due to expensive 3G bandwidth here in India, I do not plan to do any OTA syncing. Too expensive. 

Only when all my Outlook data is safely transferred to the Android (and after I've got it backed up six ways to Sunday), only then will I nuke Windows and Outlook and devote my whole drive to the embrace of Ubuntu. Thanks,

Advait

---

### Post by Advait on 2012-10-06
> **thatguruguy said:**
> There's a great program available on the Google Play store called "Airdroid." It makes moving packages back and forth between your computer and android device pretty painless.

Sounds like AirDroid is an OTA syncing solution...? That true? Due to expensive 3G here in India, I don't plan on doing any OTA syncing. Actually, I don't plan on doing any syncing at all. Just a daily transfer of the Titanium backup file to my Ubuntu PC.

I do plan to explore syncing with Thunderbird. I was told there's some Tbird extension that can sync contacts with Android.

Is there some extension that allows Tbird to sync tasks/todos with Android? I don't use Outlook Calendar, only contacts and tasks.

Thanks!

Advait

---

### Post by GBGamer117 on 2012-10-07
I'm not sure about calendar/todo, but if you want to sync contacts, check this extension out.
[https://addons.mozilla.org/en-US/thunderbird/addon/google-contacts/](https://addons.mozilla.org/en-US/thunderbird/addon/google-contacts/)

---

### Post by Advait on 2012-10-07
> **GBGamer117 said:**
> I'm not sure about calendar/todo, but if you want to sync contacts, check this extension out.
[https://addons.mozilla.org/en-US/thunderbird/addon/google-contacts/](https://addons.mozilla.org/en-US/thunderbird/addon/google-contacts/)

Thanks for the info. However, I don't plan on using Google contacts because that would require OTA syncing which would require a data plan (too expensive here). I plan to just dump all my Outlook contacts into the Android phone and only manage them on the phone. I'm now researching ways to sync contacts between Android and Ubuntu Thunderbird; looks like there's some add-ons for that. I need to do more research.

For the most part, I'll be using my soon to be purchased Android phone *without* a data plan (only voice and sms). Thanks!

Kind Regards,

Advait

---

### Post by GBGamer117 on 2012-10-07
I understand. Hopefully they make data plans more cheap before I go there :). I'm sorry I couldn't have helped you more.

---

### Post by MoebusNet on 2012-10-09
> **MoebusNet said:**
> I'm not sure where you got the idea that ICS is unable to "connect an Android phone as a USB Mass Storage device" but I am doing precisely that as I type, looking at the photos taken by my HTC Rezound running ICS version 4.0.3 and Sense version 3.6 which is what Verizon sent me as an OTA update from Gingerbread. Unless you have a link to an upcoming change?...

@Mark Phelps

Thank you for educating me! I had not heard about this issue, since my phone connected by USB as it always had. I guess  for some newer phone models, this would be necessary.

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

---

