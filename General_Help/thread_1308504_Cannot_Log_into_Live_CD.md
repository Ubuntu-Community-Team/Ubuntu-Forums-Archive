---
title: "Cannot Log into Live CD"
date: 2009-10-31
forum: General Help
---

### Post by BushyIII on 2009-10-31
Downloaded and burned the Live CD.  It boots fine but it asks for a login.  I don't know if it is creating a new account or if there is a default.  Anyhow, no matter what I try it won't log me in.

Any suggestion.  Again this is the LIVE CD

---

### Post by Egi_Power on 2009-10-31
Hi!

I guess you speak about the 9.10 LiveCD.

I tried it yesterday, and it logged in automatically for me.

The username in the top right corner on the panel was ***ubuntu***.

Take it easy.

Egi_Power

---

### Post by lisati on 2009-10-31
Although by no means normal, I have seen the Live CD of previous releases ask for a user name and password. Usually doing nothing is the answer, as auto-login should kick in.

---

### Post by P4man on 2009-10-31
I guess you have a non graphical login? White text on a black screen?
Try waiting a few more seconds.

If it really stalls there then something is wrong. You could log in with username ```
ubuntu
``` and no password tho, but its not what it should be. check the cd for errors perhaps

---

### Post by BushyIII on 2009-10-31
None of the suggestions have worked.  It just sits at the login screen.  I tried entering ubunto for the username w/o a password and tried entering passed the logon w/o a username as well.  Every time it replies with an Authentican failure.

---

### Post by P4man on 2009-10-31
> **BushyIII said:**
> None of the suggestions have worked.  It just sits at the login screen.  I tried entering ubunto for the username w/o a password and tried entering passed the logon w/o a username as well.  Every time it replies with an Authentican failure.

can you confirm if you are getting a graphical login or a text based?

---

### Post by BushyIII on 2009-10-31
It is a graphic logon

---

### Post by BushyIII on 2009-10-31
I'll try re-burning the CD.  Does anyone know the checksum?

---

### Post by BushyIII on 2009-10-31
Burned another one at 4x and exactly the same experience, no difference.  Maybe the download was bad.  I'll try downloading it again.  Otherwise I don't know what else to do.

---

### Post by BushyIII on 2009-11-01
Downloaded again, burned another Live CD and the same thing.  It wants a username and password.

Anyone have any other ideas how to try the Live CD?

---

### Post by pixegen on 2009-11-18
I'm having the same problem, using the Live CD for PPC and the Graphic option.

It won't automatically login, and selecting Automatica Login produces an "Authentication Failure" error. I've tried logging in as user "ubuntu" with no password, and with "ubuntu" and "live" as the password to no avail.

Bummer.

---

### Post by Thaddeus Morgan on 2009-11-19
I can confirm this problem using Ubuntu 9.10 PPC on an iBook G4 laptop.  I'm using the default boot options, which means I'm booting into the standard graphical mode from the live CD.  Clicking "Automatic Login" results in "Authentication failure."  Clicking "Other..." and brings up a username and password dialog which results in the same failure for no username or password, username=ubuntu and no password, username=ubuntu and password=ubuntu.  I know Ubuntu is better than this, but this is a horrible first impression.  Any suggestions on how to fix this?

---

### Post by ajmctaggart on 2009-11-23
Hey everyone,

I *believe it may have to do with UTC and the Time/Date of Openfirmware on PPC Macs...

Using this thread
[http://www.macosxhints.com/article.php?story=20060814075952448]("http://www.macosxhints.com/article.php?story=20060814075952448")\

I cannot say whether this will actually allow you to get into a system that has already told you authentication failure, (because the install thinks it was done in 1904, now you wanna boot the thing in 2009!).  It does get a LiveCD working and will hopefully make this install successful, I will report back!

Hope this helps!
-ajmctaggart

---

### Post by Cheesemill on 2009-11-23
The few times I've seen this problem it has always been because of a bad burn.
Did you check the md5sum of your downloaded iso and run the disc check on the CD?

---

### Post by ajmctaggart on 2009-11-23
It is absolutely not a bad burn (in this instance)...

This is spread between alternate and desktop images, and has nothing to do with the actual login and password...

Still installing, I'll report if it was a bad timeset in the Open Firmware...

-ajmctaggart

---

### Post by ajmctaggart on 2009-11-23
Got it!

It's the time & date settings on the machine!

If you can dual boot, then boot into OS X and change the time to the correct time and date.

If not, see my earlier post in this thread for the tip on how to fix the issue through OpenFirmware (that's how I did it).

Again, not sure if this will allow you into an installed system (like if you installed from alternate disk).

But this allowed me to get into the LiveCd and install without a hiccup!

I believe all the other times I chose to install with UTC enabled, and that's probably why the alternate CD install wouldn't work for me either.

Hope this helps!
-ajmctaggart

---

### Post by gadolinio on 2009-11-23
I had that exact same symptoms, but with a remastered CD I did with remastersysbackup. It asked for a username and password, but anything worked.

---

### Post by Leggie on 2009-12-13
> **ajmctaggart said:**
> Got it!

It's the time & date settings on the machine!

If you can dual boot, then boot into OS X and change the time to the correct time and date.

If not, see my earlier post in this thread for the tip on how to fix the issue through OpenFirmware (that's how I did it).

Again, not sure if this will allow you into an installed system (like if you installed from alternate disk).

But this allowed me to get into the LiveCd and install without a hiccup!

I believe all the other times I chose to install with UTC enabled, and that's probably why the alternate CD install wouldn't work for me either.

Hope this helps!
-ajmctaggart

Thanks. I had exactly the same problem and the Open Firmware editing you suggested solved it for me. Cheers!

---

### Post by rjhakkesteegt on 2010-02-13
I have the same problem with the Xubuntu . I have two laptops. An old IBM Thinkpad T30 and a not-so old Thinkpad T60 and both boot up to the graphical screen and show the login prompt. Entering ubuntu without password does not let me in.
 
Live CD of Xubuntu 9.10 (Karmic Koala) x86 32 bit
 
Burned two different Cd-s.
 
Let it set at the graphical logon screen for a minute, but it did not continue.
 
I then downloaded the 9.04 version and that one works fine. It also shows the graphical logon screen but this time also a timer that counts down from 10 to 0 and then continues

---

