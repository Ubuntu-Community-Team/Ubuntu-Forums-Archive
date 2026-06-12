---
title: "unable to send fax using efax-gtk"
date: 2009-09-22
forum: General Help
---

### Post by mardybear on 2009-09-22
Hello...

I have what seems to be a great external hardware modem: US Robotics Sportster. It consistently receives faxes no problem. 

I am, however, unable to successfully send faxes and receive numerous error messages:

Error: wrong response to command to receive a frame
Error: no answer from remote fax
finished - invalid modem response

Please let me know if you require more info. Tried searching the forums, google, efax man pages, played around with the settings and DIP switches, etc. I use this computer and modem for business, so it's not just a nice to have. I love Linux and Ubuntu, so it's sad to say but my Windows XP system sends faxes no problem. I'm hoping to eventually get all of these types of barriers fixed so I can switch to Linux only.

Thanks in advance,

Marty - Linux newbie going on 3+ years !

---

### Post by mardybear on 2009-09-22
Sorry.. Some info I should have included:

I am attempting to fax a .pdf file (read somewhere efax-gtk only supports sending ps files or something similar - ? true).

The modem dials out fine, attempts to connect with receiving modem, then error messages.

I have minimal experience with AT type modem commands, played around and nothing helped. I was hoping the 'fix' is something this simple...just add xxx to your modem initialization and automagically all my fax problems are solved :)

Thanks again,

Marty

---

### Post by duf on 2009-09-23
efax, and by extension efax-gtk can only send postcript files.
Change your pdf file to postcript by using the program pdftops, it is part of the poppler-utils (it is in the repositories).
You can also print the pdf file to a postcript file using your printer.

---

### Post by mardybear on 2009-09-24
Thanks for the feedback duf.

Used pdftops to convert a .pdf file to .ps...
still error messages. Some of my efax-gtk output below.

duf or anyone else got some suggestions?

Any assistance appreciated.

Thanks,

Marty


efax-0.9a: 17:07:38 connected
efax-0.9a: 17:07:41 Error: timed out reading frame data
efax-0.9a: 17:07:41 Error: wrong response to command to receive a frame
efax-0.9a: 17:08:12 Warning: timed out after waiting
efax-0.9a: 17:08:12 Error: no answer from remote fax
efax-0.9a: 17:07:41 received UNKNOWN
efax-0.9a: 17:07:41 received UNKNOWN
efax-0.9a: 17:08:12 received UNKNOWN
efax-0.9a: 17:08:12 failed page /home/skeletal/Documents/test ps file.ps.001
efax-0.9a: 17:08:12 failed page /home/skeletal/Documents/test ps file.ps.002
efax-0.9a: 17:08:13 finished - invalid modem response

---

### Post by mardybear on 2009-09-26
Just replying to myself...hopefully someone out there can help.

Updated troubleshooting info as follows. Still can't send faxes (error messages in previous post). Rock solid receiving faxes, never a problem with my us robotics sportster and Ubuntu. Attempted to fax out both .ps and .pdf files without success. Was previously able to send faxes no problem when I first hooked up this external fax modem about two months ago. Was finally able to successfully send a fax today, but only when I booted to an old Ubuntu kernel (works in 2.6.15-54-386, no work in 2.6.24-24-386)...must have stopped working after the last kernel update.

Questions:
Is it safe to boot/run with the old kernel? I would imagine there are security concerns and/or I won't be able to take advantage of other kernel improvements. Also got some type of hal error when booting to the old kernel.

Do I just patiently wait for the next kernel release, hoping it will be fixed?

What's the procedure for a general user to submit an error or bug report re: efax and this latest kernel?

Thanks,

Marty

---

