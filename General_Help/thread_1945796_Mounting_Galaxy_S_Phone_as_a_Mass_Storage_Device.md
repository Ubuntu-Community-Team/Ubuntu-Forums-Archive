---
title: "Mounting Galaxy S Phone as a Mass Storage Device"
date: 2012-03-23
forum: General Help
---

### Post by ddjolley on 2012-03-23
I had a Galaxy S phone from T-Mobile (3g).  I never had a problem mounting that phone as a mass storage device on my desktop computer running Ubuntu 11.10.  I just connected it to the computer via a USB cable, acknowledged a dialog popup, and viola!  I recently upgraded my phone to a later version of the Galaxy S from T-Mobile (4g).  I can't get the upgraded phone to mount as a mass storage device on my desktop computer no matter what I do.  Anyone have any thoughts?  FWIW, I have tried both with USB Debugging enabled and disabled.  Thanks for any input.

     ... doug

---

### Post by gandaran on 2012-03-23
> **ddjolley said:**
> I had a Galaxy S phone from T-Mobile (3g).  I never had a problem mounting that phone as a mass storage device on my desktop computer running Ubuntu 11.10.  I just connected it to the computer via a USB cable, acknowledged a dialog popup, and viola!  I recently upgraded my phone to a later version of the Galaxy S from T-Mobile (4g).  I can't get the upgraded phone to mount as a mass storage device on my desktop computer no matter what I do.  Anyone have any thoughts?  FWIW, I have tried both with USB Debugging enabled and disabled.  Thanks for any input.

     ... doug
I'm not sure but I think the new Galaxy use MTP protocol now
you will need to install MTP tools from software center.

---

### Post by imachavel on 2012-03-23
with my dads ipad2, I used an app called file drive for his ipad, I don't remember if I had to pay for it or not. It was very simple, you configure it on your device(remember that tablets and smart phones usually use an identical OS), then you find the directory from your computer. On my pc with ubuntu I chose the wireless option to use the i.p. address, the i.p. is routed through the router giving internet, or I should say routing your i.s.p. d.n.s. gateway and giving subnet mask, anyway it's simple enough then you drag and drop files into a directory folder that pops up on your smart phone device through the network.

Now this method is not the only way, as you said, you connect through usb to make the device mountable right? Ok but I'm not sure of an app that works for galaxy. However, try this app:

[http://www.downloadaresgalaxy.com/](http://www.downloadaresgalaxy.com/)

see if you can find it in the galaxy app store, I assume it works backwards. Otherwise how are you trying to mount the device?

---

### Post by ddjolley on 2012-03-23
> I'm not sure but I think the new Galaxy use MTP protocol now
> you will need to install MTP tools from software center.

It looks like I already had the MTP runtime tools installed.  I installed the MTP library tools.  It's still not working even though I now have both packages installed.  It was a good thought though.  Thanks.

       ... doug

---

### Post by imachavel on 2012-03-23
> **gandaran said:**
> I'm not sure but I think the new Galaxy use MTP protocol now
you will need to install MTP tools from software center.

btw works for me. Just in case the OP wants to see what it installed after installing from software sources will look like

---

### Post by ddjolley on 2012-03-23
> try this app:

> [http://www.downloadaresgalaxy.com/](http://www.downloadaresgalaxy.com/)

To me this looks more like a network file sharing utility.  It may be an alternative to mounting the phone as a mass storage device for some purposes.  However, my objective is to mount the phone as a mass storage device (like I was able to do with my old 3g phone).

Thanks for the input.

      ... doug

---

### Post by The Cog on 2012-03-24
I don't know if this is the same as a Galaxy S, but for my Galaxy S2 I use this procedure:
**On the phone:**
Open Settings -> Wireless and network -> USB utilities
Press "Connect storage to PC"
Connect the cable
Press "Connect USB storage"
Press "OK"
**On the computer:**
Open the USB drive in the file manager

---

### Post by cortman on 2012-03-24
> **The Cog said:**
> I don't know if this is the same as a Galaxy S, but for my Galaxy S2 I use this procedure:
**On the phone:**
Open Settings -> Wireless and network -> USB utilities
Press "Connect storage to PC"
Connect the cable
Press "Connect USB storage"
Press "OK"
**On the computer:**
Open the USB drive in the file manager

Same here, for my Galaxy s2.

---

### Post by ddjolley on 2012-03-24
**> On the phone:**
> Open Settings -> Wireless and network -> USB utilities
> Press "Connect storage to PC"
> Connect the cable
> Press "Connect USB storage"
> Press "OK"

I think that we're onto something here.  It sure sounds like that should work.  Here is what happens for me:  I am able to get down to the step which you have described as, "Connect USB storage".  Just FYI, for me the button says, "Connect storage to PC".  When I tap on that button I get a dialog box  that says "Connect USB cable to mass storage" and there is a "Cancel" button just below that.  I'm assuming that the phrase, "Connect USB cable to mass storage" means to connect the phone to the computer via a USB cable.  When I do that not much happens.  I get an audible notification that I am connected to power and a lightening bolt is added to the battery at the top indicating that the phone is being charged.  So, I know that the phone is connected to the computer via the USB cable.  There is no "OK" button for me to press.  The above results are the same whether or not I have USB Debugging Disabled in Settings -> Location and Security.  Thoughts?

I consider this a major step forward in resolving this problem.  Thanks.

          ... doug

---

### Post by cortman on 2012-03-24
> **ddjolley said:**
> **> On the phone:**
> Open Settings -> Wireless and network -> USB utilities
> Press "Connect storage to PC"
> Connect the cable
> Press "Connect USB storage"
> Press "OK"

I think that we're onto something here.  It sure sounds like that should work.  Here is what happens for me:  I am able to get down to the step which you have described as, "Connect USB storage".  Just FYI, for me the button says, "Connect storage to PC".  When I tap on that button I get a dialog box  that says "Connect USB cable to mass storage" and there is a "Cancel" button just below that.  I'm assuming that the phrase, "Connect USB cable to mass storage" means to connect the phone to the computer via a USB cable.  When I do that not much happens.  I get an audible notification that I am connected to power and a lightening bolt is added to the battery at the top indicating that the phone is being charged.  So, I know that the phone is connected to the computer via the USB cable.  There is no "OK" button for me to press.  The above results are the same whether or not I have USB Debugging Disabled in Settings -> Location and Security.  Thoughts?

I consider this a major step forward in resolving this problem.  Thanks.

          ... doug


Here's how I do it: (and you MUST have USB debugging enabled)

Plug phone into computer.
Swipe down from the top to open the notifications or whatever menu.
Select "USB Connected"
Click "Connect USB Storage" button at bottom.
SDCard and Interal both automount in Ubuntu.

---

### Post by The Cog on 2012-03-24
> **ddjolley said:**
> **> On the phone:**
> Open Settings -> Wireless and network -> USB utilities
> Press "Connect storage to PC"
> Connect the cable
> Press "Connect USB storage"
> Press "OK"

I think that we're onto something here.  It sure sounds like that should work.  Here is what happens for me:  I am able to get down to the step which you have described as, "Connect USB storage".  Just FYI, for me the button says, "Connect storage to PC".  When I tap on that button I get a dialog box  that says "Connect USB cable to mass storage" and there is a "Cancel" button just below that.  I'm assuming that the phrase, "Connect USB cable to mass storage" means to connect the phone to the computer via a USB cable.  When I do that not much happens.  I get an audible notification that I am connected to power and a lightening bolt is added to the battery at the top indicating that the phone is being charged. So, I know that the phone is connected to the computer via the USB cable.  There is no "OK" button for me to press.  The above results are the same whether or not I have USB Debugging Disabled in Settings -> Location and Security.  Thoughts?

I consider this a major step forward in resolving this problem.  Thanks.

          ... doug
We are identical up to the point where you connect the cable. As soon as I do this, I get a new dialog screen that shows a green android-man holding a USB connector up and text beneath that says > USB connected
Phone connected to computer by USB. Tab the button below to copy files between computer and Android's USB storage
And below this is a button marked "Connect USB storage".

This is beginning to look like a compatibility issue or a cable fault. You might try a different cable, different USB ports on the computer, or even a different computer. Beyond that, I'm out of ideas.

---

### Post by ddjolley on 2012-03-24
> This is beginning to look like ... a cable fault.

Yikes!!  It was a faulty cable!  (The cable has been placed in the trash.)   I'm good to go.  Thanks so much to all who contributed!

        ... doug

---

### Post by cortman on 2012-03-24
> **ddjolley said:**
> > This is beginning to look like ... a cable fault.

Yikes!!  It was a faulty cable!  (The cable has been placed in the trash.)   I'm good to go.  Thanks so much to all who contributed!

        ... doug

Great, glad it's solved. Please mark this thread [SOLVED] using the thread tools in the upper right. Thanks!

---

### Post by ddjolley on 2012-03-24
As an epilog to this whole discussion, I was surprised to learn that once I got it working, it would work without regard for whether "USB Debugging" was disabled.  Should I be surprised at that result?  Thanks.

         ... doug

---

### Post by The Cog on 2012-03-25
Oo-Yah! I wasn't really expecting it to be a cable fault. Result!

I think that turning USB debugging on might shorten the steps needed in the above procedure. But I also found that USB debugging turns itself off - I haven't worked out when or why. I just stopped worrying about the debugging setting.

---

### Post by ddjolley on 2012-03-25
> I just stopped worrying about the debugging setting.

That sounds like really good advice to me in any case where it will work. Unfortunately, I think there are cases where the debug setting is critical.  My Android pad is an example.

In any event, I think that we've pretty well flogged this horse to death.  Again, I thank all who contributed.

      ... doug

---

