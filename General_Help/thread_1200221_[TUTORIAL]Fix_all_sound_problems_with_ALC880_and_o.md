---
title: "[TUTORIAL]Fix all sound problems with ALC880 and other HDA cards *Jaunty*[TUTORIAL]"
date: 2009-06-29
forum: General Help
---

### Post by NikolaiKalashnikov on 2009-06-29
Hey dudes,
I don't know if this is in the wrong section (if a mod wants to move it they can),but I've made this tutorial explaining in detail how to fix sound problems with the popular Intel ACL880 HDA soundcard and other Intel HDA soundcards.
I've come across other tutorials but they are either over-elaborate,not detailed enough,or include things that are totally unnecessary.So I've written this clear and concise tutorial to help those who are new to Ubuntu.



First of all let's open up the file browser.

Navigate to /etc/modprobe.d/

Open up the file alsa-base.conf in text editor



Now we must insert this line at the bottom of the text file
> options snd-hda-intel model=*insert your computer's brand here*For instance,I'm using a Fujitsu Siemens Amilo M1450g,so I insert "fujitsu" like so:

> options snd-hda-intel model=fujitsuThe same goes for other brands e.g. if you're using an acer,insert "acer" (minus the quotations),or "sony" and so on and so forth.

Save the modified file to your desktop,if you try to save it straight into /etc/modprobe.d/,it will deny you permission.



Now you must open up the file browser but with root rights with this command:

> gksudo nautilusNavigate to /etc/modprobe.d/

Cut and paste the modified alsa-base.conf that you saved onto your desktop into /etc/modprobe.d/,
because you are using root rights,it will not deny you permission this time,when it asks you if you want to replace the file,click "replace".


Restart your PC and Hey Presto!You've got sound!



Hope I've helped somehow,Iand hope my English wasn't too crap,I'll be translating it into Russian and French soon.
Regards,
Nikolai.

---

