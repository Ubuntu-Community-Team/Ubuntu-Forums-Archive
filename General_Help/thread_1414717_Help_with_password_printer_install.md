---
title: "Help with password printer install?"
date: 2010-02-23
forum: General Help
---

### Post by kuchi36 on 2010-02-23
I am trying to get my Lexmark Pro705 printer up and running. My wife bought it, opened it, and it is up to me to get it running. It has been opened therefore Office Despot will not take it back.
I found some .deb drivers for it on the Lexmark site for 8.10, when I tried running the set up it asked for Authentication.
"This operation requires root (administrative) privileges. Please enter the administrative password below."
No problem, I an the admin so I type in my password and I get:
"Incorrect password give, please retype."

I am using the same password I always use when the machine asks for one *during updates etc.

So, where do I go from here?

I have typed it about 20 times making sure I spelled everything correctly.

HELP.

If I can't get this up and running, I will have to consider going back to Windows.
Tim

---

### Post by mikewhatever on 2010-02-24
I very much doubt the problem has anything to do with the printer. Check Caps Lock, other then that, not sure I can be of any help.

---

### Post by drdanielfc on 2010-02-24
> **kuchi36 said:**
> I am trying to get my Lexmark Pro705 printer up and running. My wife bought it, opened it, and it is up to me to get it running. It has been opened therefore Office Despot will not take it back.
I found some .deb drivers for it on the Lexmark site for 8.10, when I tried running the set up it asked for Authentication.
"This operation requires root (administrative) privileges. Please enter the administrative password below."
No problem, I an the admin so I type in my password and I get:
"Incorrect password give, please retype."

I am using the same password I always use when the machine asks for one *during updates etc.

So, where do I go from here?

I have typed it about 20 times making sure I spelled everything correctly.

HELP.

If I can't get this up and running, I will have to consider going back to Windows.
Tim

what does running setup as root from the begining do?

---

### Post by kuchi36 on 2010-02-24
what does running set up from the root mean? I am fairly computer stupid when it comes to directories etc.

Thanks,
Tim

---

### Post by drdanielfc on 2010-02-25
> **kuchi36 said:**
> what does running set up from the root mean? I am fairly computer stupid when it comes to directories etc.

Thanks,
Tim

what set up program are you running? is it loaded when you try to install the printer from the .deb file?

---

### Post by kuchi36 on 2010-02-26
This is the file that I am trying to install the drivers with:

lexmark-inkjet-09-driver-1.0-1.i386.deb.sh

I got it off of the Lexmark website and it should be what I need if I was running 8.10 Ubuntu, but I have 9.10. Should that make any difference in the set up accessing my admin passord?

Thank you,

Tim

---

### Post by drdanielfc on 2010-02-27
> **kuchi36 said:**
> This is the file that I am trying to install the drivers with:

lexmark-inkjet-09-driver-1.0-1.i386.deb.sh

I got it off of the Lexmark website and it should be what I need if I was running 8.10 Ubuntu, but I have 9.10. Should that make any difference in the set up accessing my admin passord?

Thank you,

Tim

Googled around a bit - [http://www.mydellmini.com/forum/ubuntu-netbook-remix/7520-lexmark-z2320-printer-mini-9-a.html](http://www.mydellmini.com/forum/ubuntu-netbook-remix/7520-lexmark-z2320-printer-mini-9-a.html)

The second post may be of assistance

---

### Post by kuchi36 on 2010-03-03
Well, 
Ubuntu has been fun, and a great alternative to the other OS but since I can't resolve this issue, and can't return the printer, it is off to 7 I go.

Cheers and 
Thanks for all the fish.

Tim

---

### Post by Spellinator on 2010-03-07
I know this is an old thread, but right now, I'm having the same problem. Although I'm not trying to install printer. I'm just trying to change the IP address assigned to a printer I had setup.

Last week I upgraded to Karmic Koala. I don't know if that created a problem, but now when I try to make a change via the GUI, it prompts for the root password, I enter it and it comes back with authentication failed.

Now mind you, if I open up a terminal window and do su for root, I switch users with no problem using the password I just tried with the printer configuration change.

So what's the dealio?


Thanks,
Danny

P.S. I've tried searching the forums, but no luck in finding anything, but this thread so far. Still searching...

---

### Post by Spellinator on 2010-03-07
Never mind. I just got it.

From terminal, I did:
sudo system-config-printer

Then it prompted for password and launched the window.

Funny thing is, I did get two messages. See...
libnotify-Message: GetServerInformation call failed: Launch helper exited with unknown return code 1
libnotify-Message: Error getting spec version

Not sure what that means, but I was able to make my change and move on. Glory be to God.
:-)

---

### Post by Spellinator on 2010-03-07
OOPS! Posted to soon, I think. Why I was posting that I got it working, I had the printer generating a test page. Well, I just looked at the test page and it shows this:
ERROR: undefined
OFFENDING COMMAND; bp$$SubUD$$

STACK:

{cachestatus 7 1 roll pop pop pop pop pop pop 0 setcachelimit currentdict /XUID undef }
/dct1
-dictionary-
false
-dictionary-
false
true
false

Okay, that's a bit too cryptic for me. What's up with this?


Thanks,
Danny

---

### Post by jessier101 on 2010-03-23
I had the same problem trying to install this Lexmark driver.. I installed it using the terminal: sudo /home/name/Downloads/lexmark-08z-series-driver-1.0-1.i386.deb.sh
and it installed without asking for the administrative password.. sad to say the driver still didnt work tho..

---

### Post by Buntudabblin on 2010-09-23
> **kuchi36 said:**
> I am trying to get my Lexmark Pro705 printer up and running. My wife bought it, opened it, and it is up to me to get it running. It has been opened therefore Office Despot will not take it back.
I found some .deb drivers for it on the Lexmark site for 8.10, when I tried running the set up it asked for Authentication.
"This operation requires root (administrative) privileges. Please enter the administrative password below."
No problem, I an the admin so I type in my password and I get:
"Incorrect password give, please retype."

I am using the same password I always use when the machine asks for one *during updates etc.

So, where do I go from here?

I have typed it about 20 times making sure I spelled everything correctly.

HELP.

If I can't get this up and running, I will have to consider going back to Windows.
Tim

"Newbie" Here. 

1.  Download the driver [here.]("http://support.lexmark.com/index?page=recommendedDownloads&locale=EN&productCode=LEXMARK_X5650&segment=DOWNLOAD&userlocale=EN_US#2")
2. Invoke Terminal. Enter following command:
> 
sudo /home/name/Downloads/lexmark-08z-series-driver-1.0-1.i386.deb.sh
3. Now administrative password is not asked for. ( Make sure you change NAME to your login name and that Downloads is where you saved the driver or else replace Downloads with the name of the folder.
4.  Plug-in USB to the front of the printer.  **BACK USBs do not connect.**
5. Follow instructions and close.
Enjoy

P.s Do not get discouraged.  Ubuntu solves more problems with free software than Microsoft does with paid.  Solutions are out there mostly and no problems are unique in either Windows or Ubuntu.  Please search google and the forums for help.

---

### Post by cloyd on 2010-09-23
I had similar problems, but solved it by creating a seperate root (and not merely adminstrative) password. Later, I heard that it was against forum policy to post instruction on how to create a true root account. 

However, I've also read that if one opens nautilus from the terminal with gksudo and install the driver that way in nautilus. It can be done, but for some reason it will not accept the usuall sudo password in the normal manner. 

I got my lexmark to work, but the next printer I bought was an HP.

---

