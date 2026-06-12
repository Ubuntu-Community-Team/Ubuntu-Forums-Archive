---
title: "ubuntu 9.10 3 usb dongle trouble"
date: 2010-04-20
forum: General Help
---

### Post by mul01 on 2010-04-20
hello all,
i am a newbie to ubuntu.
I have ubuntu 9.10 and ubuntu reconises my 3 usb dongle which is model HUAWEI E122 HSPA STICK now it asks me for a password i have tried all the usual ones three,password,three.co.uk not sure what it could be.i have set up the connection right but keeps asking me for password for the actual stick now as far as i know i dont have 1.

any help would be very greatful.

thanks :)

---

### Post by P4man on 2010-04-20
No idea, but have you tried blank password?
also what is the prompt exactly? You sure its not asking for the keyring password which is something entirely different (and by default is the same your ubuntu account password, unless you changed either).

---

### Post by mul01 on 2010-04-20
i have tried blank password,no luck.
the prompt is exactly that it needs the password for the HUAWEI E122 HSPA STICK to connect to the mobile broadband.
as it does try and connect at the top of screen but it needs the password to do so,which i dont know
any ideas?

thanks

---

### Post by P4man on 2010-04-20
Contact your provider?

---

### Post by klemes on 2010-04-20
Maybe it asks for the PIN number of the SIM card ....
Just guessing.....:)

---

### Post by mul01 on 2010-04-21
thanks guys i try that

---

### Post by David Batty on 2010-04-21
I suspect it is requesting the password you use to connect with your provider, (the one you type in to see your e-mails) It only needs to be entered once, from then on the USB will remember it and connect you every time you plug in.

---

### Post by mul01 on 2010-04-21
klemes thanks but i tried the pin and that never worked.



P4man i may have to contact 3 to get these password problem is just have to ask for password cos if i tell them i use linux there just we dont support linux even tho the stick reconises linux straght away.

David Batty thanks i previously have windows vista on laptop and u did not need a password to connect to the stick then but my harddrive broke and i thought i replace it with ubuntu linux now it asks me for a password,i have three,guest all the ones can find on the net.I have tried my log in passwords for my3 but no luck as of yet.

thankyou guys for all help:)
(i am on my partners computer at the mo on vista thats how on the web now)

---

### Post by P4man on 2010-04-21
I think we're missing something obvious here somehow. All of my googling suggests you dont need a password.

Do this; right click on network manager, edit connection, mobile broadband, add. Follow the wizard. (If you are in the UK, ubuntu calls that Britain in that list, just so you know).  At the end, make sure you mark the "available to all users"

If/when you should get a prompt for a password, kindly make and post a screenshot. Im guessing it will only ask you ubuntu account password, possibly gnome keyring password, but nothing else.

---

### Post by mul01 on 2010-04-21
thanks i just try that now i was not clicking avalible to all users,wont be long:)

---

### Post by mul01 on 2010-04-21
thanks,it dont ask me for a password anymore,i didnt have it set to connect to all users thing.

how long does it take to connect roughly?as i get a round spinning thing at the top?is that it trying to connect?

---

### Post by mul01 on 2010-04-21
The spining thing goes on forever but when i click on the connections it says its connected but when i load firefox says i am offline

---

### Post by P4man on 2010-04-22
Im sorry to hear that, I cant help you beyond this point. i have no handson experience with 3g dongles, much less those of your provider.

Maybe nudge GeorgeVita on this forum, ive seen him help out a few times specifically on 3g issues and unlike me, I think he knows what he is talking about ;)

---

### Post by mul01 on 2010-04-22
thanks p4man you have been great in helping me.i will let u know if i get it sorted,i have messaged GeorgeVita hopefully he can help.

many thanks

---

### Post by GeorgeVita on 2010-04-22
Hi **mul01**,
an idea is to try everything from the 1st step!

Remove modem, right click network manager icon, edit connections, mobile broadband, click on every connection and delete it.

Use any other connection to update your Ubuntu 9.10 to the latest kernel as initial version had [bug#446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") that affects most 3g modems.

Remove SIM PIN check (for simplicity) using a cell phone (insert SIM to the phone, use menu to de-activate this check).

Reboot your updated Ubuntu 9.10, attach modem, wait 20 seconds, right click network manager icon to see the 'new mobile broadband connection...' and use menus to set it up.

If a window appear saying 'passwords keyring etc.' leave password blank, continue, **use unsafe area**, continue. On every next window with a message 'enter password', leave it blank and proceed.

Post back your comments to follow up!

Regards,
George

---

### Post by mul01 on 2010-04-22
thanks GeorgeVita i take my computer to my dads he has wifi broadband once updated i try and get back to.

many thanks :)

---

### Post by mul01 on 2010-04-24
thanks GeorgeVita that worked i fully updated the system and now  the 3g dongle is working perfect many thanks for your help

:)

---

### Post by cuddy2977 on 2010-04-24
> **GeorgeVita said:**
> Hi **mul01**,
an idea is to try everything from the 1st step!

Remove modem, right click network manager icon, edit connections, mobile broadband, click on every connection and delete it.

Use any other connection to update your Ubuntu 9.10 to the latest kernel as initial version had [bug#446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") that affects most 3g modems.

Remove SIM PIN check (for simplicity) using a cell phone (insert SIM to the phone, use menu to de-activate this check).

Reboot your updated Ubuntu 9.10, attach modem, wait 20 seconds, right click network manager icon to see the 'new mobile broadband connection...' and use menus to set it up.

If a window appear saying 'passwords keyring etc.' leave password blank, continue, **use unsafe area**, continue. On every next window with a message 'enter password', leave it blank and proceed.

Post back your comments to follow up!

Regards,
George


Does anyone know if this procedure will work on a Dell GX260 desktop, running Xubuntu 9.10?

---

### Post by GeorgeVita on 2010-04-24
> **cuddy2977 said:**
> Does anyone know if this procedure will work on a Dell GX260 desktop, running Xubuntu 9.10?

Hi **cuddy2977**,
any 'initial' (liveCD) version of Ubuntu 9.10 has this bug that affects many (not all) 3g modems. This was into kernel 2.6.31-12... Now an updated Ubuntu 9.10 uses kernel 2.6.31-**21**-generic #59

You can check kernel version from terminal: **uname -a**

SIM PIN check removed, is always better assuming that you do not need this lock.

>>> Other dial-up modems have some problems with modem-manager which [solved after removing it]("http://ubuntuforums.org/showthread.php?t=1456850")!

If you have any problem be specific, post more data (and type of modem looking at the sticker on it).

Regards,
George

---

