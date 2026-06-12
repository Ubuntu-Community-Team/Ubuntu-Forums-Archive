---
title: "Login in Classic mode from live USB stick?"
date: 2011-06-16
forum: General Help
---

### Post by Riverglen on 2011-06-16
I decided to put a copy of Ubuntu 11.04 on a USB stick.  Downloaded the image file and USB installer and built the stick with no problems.  I REALLY don't like the new interface, so I went to the login screen tool and changed the login to come up in Classic mode.  Trouble is, now when I try to bring the system up I'm presented with a log-in screen that asks for a user name and password.  Since I'm using a live image (akin to a live CD) I don't have any user name or password established.  Are there defaults that will allow me to log in?  Or do I have to recreate the installation and create a user account that will let me log in?

---

### Post by pqwoerituytrueiwoq on 2011-06-16
try making it with unetbootin there are boot options given
live usb boots to classic for me since it would need a nvidia driver to run unity

---

### Post by Riverglen on 2011-06-17
I'm not familiar with unetbootin.  Where can I find it?  Does it allow you to specify the Classic log-in option at the time you instal the image?

For what it's worth, I have two machine with dual boot set up for Win-XP and Ubuntu 11.04, with no problems, so if the utility you're recommending is available from on of the repositories, it won't be a problem to go get it.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
unetbootin is in the universe repository and is available for windows a quick google search of the app name is all it a takes
i have not tryed it on 11.04 so i dont know if it has that option but it can bypass the try/install prompt (was using 10.04 at that time)

---

### Post by Riverglen on 2011-06-17
Well, I found it with no problem, but haven't had time to try it yet.  It looks very similar to the Universal USB Installer that I found via the Ubuntu web site.  I'm guessing that it won't solve my fundamental problem though.

I can build a working USB stick with no problems.  The trouble is that the latest version of Ubuntu (11.04) the default GUI is a new "beautified" interface that I find to be repulsive and clumsy to work with.  I first made a few trial changes within that context which were saved on the stick with no difficulties, and which were still there when I booted it up again.

BUT, I then changed the default log-in to go directly to Classic mode, which is basically the old GUI prior to the latest version.  Didn't establish a user name or password, and in fact don't know whether you can do that with a live USB (obviously would have trouble creating a persistent log-in on a live CD).  Now, when I reboot the stick, I come up on a log-in screen that includes the legend Ubuntu, and a editable list box that shows Other... as the default (and only) choice.  If I continue with the log-in I get prompted for Username and Password, neither of which exist (unless there are some sort of defaults I don't know about).

I'm sure I can reburn the default image back on the stick, but I'd really like to get a stick that boots into classic mode working. So...?

---

### Post by LordNeo on 2011-06-17
To the OP:

The LiveCD user and password is:

user: ubuntu
password:

(Empty password)

---

### Post by Riverglen on 2011-06-17
Thank you very much.  Worked like a charm, once I remembered that user ID's are case sensitive.

As a follow-up, if I should need to do a sudo for something, will I need to have a password in that case?  Maybe I should look into establishing a different user account on the stick?

Probably not worth worrying about, since my only expected use of the stick installation is occasional troubleshooting and Ubuntu demos for the uninlightened.

---

### Post by C.S.Cameron on 2011-06-17
You should be able to go to Administration / Login Screen and set to automatic login.

---

### Post by Riverglen on 2011-06-17
Yeah, didn't think of that.  But now that I know what the live image expects for a log-in, I'm content to do it manually.

---

### Post by Riverglen on 2011-06-17
Yeah, didn't think of that.  But now that I know what the live image expects for the log-in, I'm content to do it manually.

---

### Post by C.S.Cameron on 2011-06-17
If you want your own user name and password in a persistent install you can add them in users and groups and user ubuntu will disappear.

---

