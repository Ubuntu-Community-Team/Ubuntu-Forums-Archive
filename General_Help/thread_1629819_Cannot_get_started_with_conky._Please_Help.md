---
title: "Cannot get started with conky. Please Help"
date: 2010-11-24
forum: General Help
---

### Post by shazzy007 on 2010-11-24
I am a **NEWBIE** at all this. So please bear with me. I hope you will. :)


I recently installed Ubuntu and I came across Conky.I was fascinated with this software and installed it using terminal codes. At first it rand with the default config file loaded. then i PC shutdown due to a power failure. now conky does not start and after searching over the net i found out that my conky config file is missing. I pasted the conky config fiel yet to no avail.

**It gives me this error while running it in Terminal**


```
Conky: /home/shazzy/.conkyrc: 30: no such configuration: 'on_bottom'
Conky: /home/shazzy/.conkyrc: 63: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: /home/shazzy/.conkyrc: 94: no such configuration: 'xmms_player'
Conky: got an endif without matching if
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

Also I found out a configuration which i'm interested in.

Here's the link to the site. I'm not sure how do i set this up as my conky config.

[Link to ConkyConfig]("http://gnome-look.org/content/show.php/Conky_Ken?content=134705&PHPSESSID=fc54ce6a265de351224348573ff56ff5")

Can you please help me.. :)

---

### Post by mikewhatever on 2010-11-24
Well concky sees the new config file alright, but it complains about errors in it. You should either fix the errors or post the contents of the file .conkyrc here.

---

### Post by shazzy007 on 2010-12-01
I solved it... thank you very much for trying to help me. :)
Seems i was not following the process told by the author properly.

Anyways thanks for your time. :)

---

