---
title: "Windows Vista has stopped booting"
date: 2009-12-30
forum: General Help
---

### Post by fizz126 on 2009-12-30
Hello. I am completely new to all this Linux stuff. I am not very technical, as you'll probably tell from my description of my problem below, So I appologise in advance for the long explanation. 

I have a work Laptop, and i thought i would try to be clever and do personal computing stuff (like looking at porn on the internet) on an Installation of Ubuntu on a USB Hard Drive. Leaving the work Laptop with a Windows vista home basic intalled on it for work stuff.

For personal, Ubuntu computing i would plug in my USB drive, swtich the computer on, press the F12 button and select "boot from usb" and a selection screen will come up and i can choose to boot either Ubuntu, Windows and some other options i have never paid attention too

At work, i would ensure the usb drive was removed, switch the computer on and windows would load as normal - this has stopped working.

I can still boot Ubuntu and Windows from the options i get from having the usb Drive plugged in, but windows has stopped booting on its own accord. Please somebody help me fix this because my boss will go ape if he thinks i've killed my new laptop.

I have tried usuing system restore and the start-up repair thing on the windows Vista cd without any success.

---

### Post by nerdtron on 2009-12-30
Do you get any error message when you boot vista? Or have you changed any other settings in your BIOS lately? Sometimes, windows won't boot successfully if it detects new hardware, specially if you enabled or disabled some settings in the BIOS.

---

### Post by kevinatkins on 2009-12-30
Oops..

OK, all is probably not lost - it sounds like when you installed Ubuntu, you killed the master boot record on the primary hard drive (ie, the one with Vista on...)

Given that you mention you've got a Vista CD, check this out -

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

.. and leave the USB drive disconnected!

Good luck - in the event that things don't work out, just tell your boss that Vista has inexplicably f*cked up (and that's not such an improbable scenario really) and you haven't got a clue what happened.. ;-)

---

### Post by fizz126 on 2009-12-31
Thank you Kevin, i went through each thin microsoft suggested on the link you gave me and it´s working again now. 
 
I assume the thing i`m doing, booting my computer into Ubuntu from my USB drive, should work in theory without any problems?
 
Thanks again

---

### Post by kevinatkins on 2009-12-31
Great - glad you're up and running again.

Booting into Ubuntu from your USB drive should still work without further modification and it shouldn't mess with your newly restored MBR on the primary hard disk.

---

### Post by ddarsow on 2009-12-31
Congratulations ;)
Oops, I meant about Vista not booting but I see the trouble has returned!

---

