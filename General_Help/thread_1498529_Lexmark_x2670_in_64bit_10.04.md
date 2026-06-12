---
title: "Lexmark x2670 in 64bit 10.04"
date: 2010-05-31
forum: General Help
---

### Post by Merk42 on 2010-05-31
So as a gift I got the Lexmark x2670, but I have been unable to install it.

I went to download the drivers from the website, but I see they are 32bit only.  I figure I'll try them, so I had to run the .sh file in a  terminal since it wanted root access. The terminal reads:> /usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
  Then the installer comes up anyway.  I hit next a few times, then it just says installation failed, it does not specify why and the window cannot be resized or copied so I can't see the readout of how far it got.  

I try to do it manually with CUPS, but I do not see the specific make/model listed that the instructions mention.

I tried simply through System > Administrations > Printing > add printer, but again the same problem of it not listed.

The instructions mention a PDD file, but that is nowhere to be found and Google only results in a thread in these forums of someone else looking for the same thing.

---

### Post by Merk42 on 2010-06-01
Little bump and more information.

 I tried forcing the installation using [this tutorial](http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4), now it shows up but documents just stay in the queue as processing.   Eventually it just gives up and says there was an error.

---

### Post by vs8 on 2010-09-30
Same here dude. Have you tried bugging Lexmark about this? I did it and they answered me, take a look:

Here is your Service Request # 1-3016078301

Thank you for contacting Lexmark Technical Support. I really do apologize for the inconvenience you have in getting this printer to work on your 64 bit machine. I understand and appreciate your desire for 64 bit Linux driver but as of now we still don't have 64 bit Linux driver available. Thank you for notifying us of your concern. I will forward your request on to our development department, as it is only through input from you, our customers, that we can make these important business decisions.

If you have any more questions or concerns, please contact me at your convenience and I will be happy to assist you. (If I am not available, another representative may reply to your request.)

To respond, please select "Reply" in your e-mail software, and be sure that the past e-mail is included in this reply.

[AOL Users: In order to include the previous e-mail, you must highlight it with your mouse when you are replying.]

If your e-mail client automatically deletes prior e-mail thread information, it will cause a delay while we look up your support history. If this is the case you may want to save the old e-mails as attachments and attach them to the current e-mail.

Sincerely,
Efren
Lexmark eSupport Team
[http://support.lexmark.com](http://support.lexmark.com)

So if us, users bug them enough they might make a 64 bit driver :)

---

### Post by dzmijewski on 2011-02-19
My letter to Lexmark:

I am disappointed that a product that has been out nearly two years from what I see, still does not have acceptable Linux support. I purchased the x2670 all-in-one in good faith based on the fact it claims Linux support on the top of the carton. It is listed without caveats. It should be nothing if not a caveat.
 
 
To begin, the contents of the carton do not mention Linux _at all_. There isn't even a card pointing to a URL where the drivers can be downloaded. It of course contains 2 CDROMs with both Windows and Mac software. Thanks for the coasters, I guess.
 
 
There is barely basic printing support of which always has been and still is now a crap shoot. I got it to work once on 32 bit and I had nothing but issues with the printer being on and off line, extreme delays, and the config application that came with the driver only worked during install; it never could connect to the printer after that. Subsequently, I could never align the print heads and the very bottom edge of any doc was cut off.
 
 
There is ZERO OCR support. A scanner that won't scan--this is a 3-in-one printer and I can't even use a third of the advertised functions. And the final killer for me is ZERO 64 bit Linux support. The carton did not say 32bit Linux only just like Windows, yet there is 64bit Windows support.
 
 
I would sell it to someone who would use it except for two things: 1. The crappy black ink cartridge leaked out all over the printer, 2. I would never wish this piece of crap on another person.
 
 
I have been defrauded based on misleading and incomplete representation. Lexmark has now burned me on two printers now and I guarantee it will never happen again. Not to mention I'm going to share my story with anyone who cares.

---

### Post by Phoenix216 on 2011-04-16
I've had the same exact issue (even down to seeing 32 bit support on the box...). Is there a way to use WINE to get printing to work with this hunk-o-junk? I've been able to run the installer with WINE, but I still can't print afterwards...

---

### Post by DFNBunny on 2011-11-23
Did anyone ever resolve this?  The debian package will not work.  Step by step help plz

---

### Post by DFNBunny on 2011-12-01
Is there anyone out there that can resolve this?:(

---

### Post by DFNBunny on 2011-12-06
Forget it... probably going to go back to Windows.  At least I can get help quicker on a simple issue like adding a printer to the system.  If this Ubuntu thing could become more responsive then maybe I'll try again later.  Really wish someone could have helped with this.

---

