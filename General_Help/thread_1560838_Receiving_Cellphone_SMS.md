---
title: "Receiving Cellphone SMS"
date: 2010-08-25
forum: General Help
---

### Post by MikeVaughanG on 2010-08-25
First Off, I wasn't quite sure where to post this, but here it is. 


I want to be able to see the text messages that are sent to MY phone on my machine. (I have Ubuntu 10.04, and Window$), And be able to reply to them on my machine. 

Does anyone know of any software for this?

I have found all kinds of software, or services online that allow you to send text messages to phones, and receive and reply, but never through my existing phone. 

Basically, I need a way to intercept texts from my phone. 


Any help would be much appreciated. 

Sincerely Signed,
Mike Vaughan

---

### Post by inameiname on 2010-08-25
I'm not sure how that would be possible. The only way I can think of is for your service itself would send the same message to both your phone and your computer, and accept replies back from both sources. Not sure they do that, I'm afraid.

Technically though, you might be able to forward all incoming messages to your phone to whatever number (or email) you designate. Pocket PC phone can certainly do that, and I think it's possible on many types of other phones to forward all SMS messages. That's an option to receive duplicates on your computer, but I doubt it'd be possible to send messages as your phone from your computer. Of course, you could email phone numbers, which is an easy thing, such as [EMAIL="10digitnumber@vtext.com"]10digitnumber@vtext.com[/EMAIL] or something, and then have the folks reply not to your email, but to your phone, which would also get forwarded to your email or computer using the above method. Only thing I can think of.

---

### Post by MikeVaughanG on 2010-08-25
Thanks for the input. I've considered this, and I'm pretty sure my phone is capable, but its not quite what I'm looking for. 

I have the ability to link my phone to my machine with USB or bluetooth. 
Maybe this info could help someone.

---

### Post by inameiname on 2010-08-25
Oh, well if you have it linked to your computer, I think BitPim does that sort of thing while connected to your phone. Doesn't work for all phones, but is the Mecca for this sort of thing.

sudo apt-get bitpim

Also, there is a newer bitpim from their website.

---

### Post by sisco311 on 2010-08-25
gnome-phone-manager, gnokii and gammu (wammu for a GUI) are in the repositories too.

---

### Post by drewbub on 2010-08-25
Do you have a smartphone?

I once wrote an android app for this purpose..

---

### Post by MikeVaughanG on 2010-08-25
> **drewbub said:**
> Do you have a smartphone?

I once wrote an android app for this purpose..

No, I don't

And wammu seemed promising, But I'm having trouble getting my Samsung Solstice to connect. 

Busy or no permissions. 
"Error code: 2"

---

### Post by micheledm on 2010-08-25
I used gnome-phone-manager for this purpose for quite a long time but with a Nokia 6680. You should check if your model is supported.

---

### Post by MikeVaughanG on 2010-08-25
> **micheledm said:**
> I used gnome-phone-manager for this purpose for quite a long time but with a Nokia 6680. You should check if your model is supported.

I dont understand how to use gnome-phone-manager. 
Is there GUI for it?
Or a guide somewhere?

---

### Post by sisco311 on 2010-08-25
> **MikeVaughanG said:**
> I dont understand how to use gnome-phone-manager. 
Is there GUI for it?
Or a guide somewhere?

Yes, gnome-phone-manager is a GUI application. Start it from Applications -> System Tools -> Phone Manager. 

A little phone icon will show up in the *Notification Area*, right click on it and select *Preferences*, configure it (in the *Connection* tab select the connection mode), then close the *Preferences* window. 

Click the icon to open the *Send Message* box. Enter the phone number in the *Recipient* text field and type the SMS in the *Message* box, then click the *Send* button. :)

For screenshots and more details check out:
[http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager)

---

### Post by MikeVaughanG on 2010-08-25
> **sisco311 said:**
> Yes, gnome-phone-manager is a GUI application. Start it from Applications -> System Tools -> Phone Manager. 

A little phone icon will show up in the *Notification Area*, right click on it and select *Preferences*, configure it (in the *Connection* tab select the connection mode), then close the *Preferences* window. 

Click the icon to open the *Send Message* box. Enter the phone number in the *Recipient* text field and type the SMS in the *Message* box, then click the *Send* button. :)

For screenshots and more details check out:
[http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager)


Haha, Now i feel silly. I was running it from command, and just not noticing the icon at the top. 

Now, it will send texts, but doesn't show new ones. But my phone also isn't on the compatibility list. (its also not on the incompatibility list)

---

### Post by sisco311 on 2010-08-25
> **MikeVaughanG said:**
> No, I don't

And wammu seemed promising, But I'm having trouble getting my Samsung Solstice to connect. 

Busy or no permissions. 
"Error code: 2"

How do you connect the phone to the computer? Via USB or bluetooth?

Also check out the phone settings, somewhere in the bluetooth menu you should be able to set the computer as authorized or something...

> **MikeVaughanG said:**
> 
Now, it will send texts, but doesn't show new ones. But my phone also isn't on the compatibility list. (its also not on the incompatibility list)

Make sure that the *Pop-up window for new messages* box is selected under Properties -> Interface tab.

---

### Post by MikeVaughanG on 2010-08-25
Im connecting via bluetooth. 

I couldn't find anything in the settings, that's the first thing I thought of. 

And I have the display pop up on new message box checked.

---

### Post by MikeVaughanG on 2010-08-26
gnome=phone-manager seems to be the way to go. 

I have it sending messages, but it doesn't receive messages. 

Could this because I'm using bluetooth instead of USB?

(Yes. I have the "Show message box" box checked)

Thanks again, I'm halfway there. :D

---

### Post by mamdez on 2010-12-11
I just found an easy app with a GUI that requires no command line tweeking.  It should work on all linux x86 distros.  Just extract the program file from the archive and click on it.  Here's the link [http://www.sw4me.com/wiki/CellMessenger](http://www.sw4me.com/wiki/CellMessenger)
The only change that may be needed is for those using USB modem sticks (the app website only mentions cell phones but it works with USB modems too and their Help guide explains this).  In the Setup you will select connection type: serial port.  Then type in the serial port instead of using the options in the drop-down box.  For example I typed, /dev/ttyUSB1 to connect to my USB modem (Huawei E1552), and I am using a prepaid service on a GSM/HSDPA network.  Then select fast or full sync and hit "apply".  That's it.  I typed a message and synced and was able to both send and retrieve all the messages that I have not been able to read on my USB stick over the past few months.  If you are a novice and don't know which port your USB is on, the easiest thing to do is to type dmesg at the command line prompt while your USB modem is plugged in.  While watching your screen plug then unplug your modem to see which "tty" disappears and reappears then use that as your port.

On a side note, I was able to send sms text messages using UMTSMON but could not receive anything.  Also I would get an error message saying the message was "not sent OK" after sending; however, the messages where actually sent.  I confirmed this by sending a message to my cell phone and from the messages I was just able to retrieve using the Cell Messenger program.  UMTSMON sends the messages after registering on the network without being actually connected to network. I have tried a ton of other programs.  None of the native apps worked for me (gnome phone manager, gammu, kphone etc.) and I tried Vodafone (Betavine project), Mobile Partner, etc.  I am so happy I found Cell Messenger, that I had to share.

---

