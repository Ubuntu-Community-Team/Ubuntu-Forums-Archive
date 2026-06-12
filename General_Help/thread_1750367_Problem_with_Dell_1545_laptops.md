---
title: "Problem with Dell 1545 laptops"
date: 2011-05-05
forum: General Help
---

### Post by Jeff_Mosawy on 2011-05-05
Hello,
There is a problem in Ubuntu with Dell laptops. Problem with wireless device!!

Look, if I want to connect to the internet at home, I should connect to the wireless router.
So, when I install Ubuntu on my laptop ( Dell 1545 ) device will not work on it. So I can not connect to the internet and get some drivers which can help me.

Do you have any solution to solve this problem?
Thank you.

---

### Post by brandonmcghee on 2011-05-05
I have a Dell Inspiron 15N, and the driver is Broadcom, if you have the ISO file for Ubuntu there should be a driver for broadcom on there.  I can't remember the exact directory but its in there.  I installed it from the ISO, if I find the directory l will post it for you.  For now just search the ISO file and find the driver, its in a .deb file.

---

### Post by Joe of loath on 2011-05-05
I've got a 1545.

Best thing I ever did? Buy an Intel wireless card. £7 ($10) from Hong Kong. Works without drivers, worth all the hassle of getting the broadcom to work.

---

### Post by Megaptera on 2011-05-05
I have sucessfully used this on my 1545 with 9.10, 10.04 and 10.10.

Don't worry that it says Dell Mini, and don't forget the reboot.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Jeff_Mosawy on 2011-05-05
Thank you for replying.
I'll do what you said and I will post what I got.
Thank you.

---

### Post by Jeff_Mosawy on 2011-05-05
Dear Megaptera:

I checked out the website which you posted for me.
There, they have said that I should connect to the internet in Ubuntu which I can't do that. And for some reasons I can't connect to the internet without wireless network ( I mean with wired network ).

Is there another solution for the problem which it doesn't need for connecting to the internet in Ubuntu?

Thank you once again.

---

### Post by colin.p on 2011-05-05
I can't remember where I got this from, either on this forum or Linux Questions but here it is. I haven't tried this as I was able to get the required driver using wired on my 1545.

I quote:


Re: dell inspiron 1545 wireless
Put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a terminal and do:

Code:
sudo apt-get update

Then:
Code:

sudo apt-get install bcmwl-kernel-source

Now reboot and select the Broadcom STA driver. in System, Administration, Hardware Drivers.

---

### Post by Jeff_Mosawy on 2011-05-06
Dear Colin.p:

I had installed this package. I mean "bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb"
But unfortunately it didn't work as well. 
All users of Dell 1545 laptops have the same problem with wireless device. You can see on Google.com. And also unfortunately it seems that no one could find a solution for it.

---

### Post by Megaptera on 2011-05-06
> **Jeff_Mosawy said:**
> Dear Colin.p:

I had installed this package. I mean "bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb"
But unfortunately it didn't work as well. 
All users of Dell 1545 laptops have the same problem with wireless device. You can see on Google.com. And also unfortunately it seems that no one could find a solution for it.

I posted my solution 
"Re: Problem with Dell 1545 laptops
I have **successfull**y used this on my 1545 with 9.10, 10.04 and 10.10.

Don't worry that it says Dell Mini, and don't forget the reboot.

[http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html) " and have highlighted an important word this time round. :D

---

### Post by Jeff_Mosawy on 2011-05-06
> **Megaptera said:**
> I posted my solution 
"Re: Problem with Dell 1545 laptops
I have **successfull**y used this on my 1545 with 9.10, 10.04 and 10.10.

Don't worry that it says Dell Mini, and don't forget the reboot.

[http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html) " and have highlighted an important word this time round. :D

Your link doesn't work. May you post it again? 
By the way, I've installed the latest version 11.04. And maybe the old solutions don't work for this version. And for your information, if your solution needs Internet in Ubuntu OS, it won't be useful for me cause I can't connect to the Internet only by wireless network ( UNFORTUNATELY )

And if my wireless device starts working or not, thank you guys for helping me.

---

### Post by Megaptera on 2011-05-06
> **Jeff_Mosawy said:**
> Your link doesn't work. May you post it again? 
By the way, I've installed the latest version 11.04. And maybe the old solutions don't work for this version. And for your information, if your solution needs Internet in Ubuntu OS, it won't be useful for me cause I can't connect to the Internet only by wireless network ( UNFORTUNATELY )

And if my wireless device start working or not, thank you guys for helping me.

Sorry my link doesn't work. Here it is again plus another. I'm posting them in case it helps others b t w. They both seem to be working now.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

If you had said earlier on that you have no ethernet connection that would have been most helpful!
Do any of your friends have ethernet that you could borrow for a few mins to get the drivers you need to download?

---

### Post by Scattered on 2011-05-06
Did you run the "Additional Drivers" application. This may list the Broadcom STA wireless driver which might work for you. If a wireless driver is detected, enable it and see if that works.

---

### Post by Jeff_Mosawy on 2011-05-07
Megaptera:
I saw your solution and I understood from it that I MUST install that kernel which I did. And also I went and took a look at Additional Drivers, but unfortunately there wasn't anything.
Perhaps your solution works only for the previous versions of Ubuntu, but for the latest one doesn't.

---

### Post by Megaptera on 2011-05-07
Just tried it in 11.04 with ethernet connection, my wireless is detected and a pop-up offering 'restricted drivers' shows on top right of screen. Click on that, allow install, reboot & there you are up and running.

But you need ethernet to start you off so once again I suggest going to a friend's and borrowing their ethernet connection for a few minutes.

---

### Post by Jeff_Mosawy on 2011-05-07
I'll do what you did suggest me. But I don't think I'll can find someone of my friends that uses ethernet. Because nearly all of my friends have wireless connection that I set it up for them or they use Dial-Up connection :D. However, I'll also look for someone who have ethernet.

Anyway, I want to tell you again that I did install the package which called " bcmwl-kernel-source " from the ISO file which I'd downloaded it from Ubuntu.com.

Having Ubuntu on my laptop or PC isn't very important for me. Because I work on Windows Mobile ROMs and I must using Windows OS and that's why the Windows is my default OS. I just wanted to have Ubuntu on my laptops and browsing the web with it as well as downloading program for it and test them.

Anyway, thanks to all you guys for helping me. By the way, sorry for my bad English and maybe I used some words or sentences wrong. :D
Jeff

---

### Post by Megaptera on 2011-05-07
You're welcome!

---

