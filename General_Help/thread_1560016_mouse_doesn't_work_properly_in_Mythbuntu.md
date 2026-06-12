---
title: "mouse doesn't work properly in Mythbuntu"
date: 2010-08-24
forum: General Help
---

### Post by Phil Binner on 2010-08-24
I've just loaded Mythbuntu as a dual boot with my Ubuntu machine. I am beginning to wish I hadn't. There seem to be people out there with it working, so presumably it's possible. I have a number of problems.

1. My mouse doesn't work properly in Mythbuntu. There are areas of the screen in which it does show, but they are exceptions. Some drop down boxes don't recognise the mouse, so I can't complete the set-up.

2. The back end set-up is gobbledy-gook. I when it asks me to say what kind of capture cards I'm using it uses terms I have no idea about. I tried searching them on the internet, but no joy. Is there a manual anywhere.

3. There seems to be no way to turn it off once it's on. I've had to just shut down the machine at the box.

4. This is the first time I've seen a dual boot, but it isn't what i expected. There is a list of possibilities, including recovery mode, rather than a simple Ubuntu or Mythbuntu. If i don't respond immediately it goes into Mythbuntu, and then I have to shut down at teh box again to sort it out. Is this right.

All help appreciated.

---

### Post by warfacegod on 2010-08-24
```
sudo apt-get install startupmanager
```

This will give you some GRUB options. Including changing the order that the OS's appear in GRUB and changing the time out.

---

### Post by WJason on 2010-08-24
I had the same problems with Mythbuntu so I ended up uninstalling it. :-(
Mouse pointer only appeared when it was in a field (the box into which you'd type an answer.
Setup asked endless questions to which I did not know the answers.
Although my Hauppage TV card was in the hardware compatibility list, I saw nothing that looked like it in the Myth setup list.
I did finally figure out how to get to the "home" screen and do a normal shutdown; but I don't remember how I did it.  I even got to the point in Mythbuntu where I could edit the grub file and change the boot order.
But, being unable to complete the setup questionaire, Mythbuntu was pretty much useless.

---

### Post by Phil Binner on 2010-08-24
Thanks for those. Since the previous answer is pretty well exactly my experience of today, can I please ask the Mythbuntu development team how anyone is expected to set this up. This is not a retorical question,as it seems that lots of people do. Are there any kind of instructions available in ordinary English. Even knowing what my objectives are would help.

For the record, I have a Pinnacle Systems Digger 51013524-5.1A sat card, and a Hauppauge WinTV Nova-T DVB-T 90003 LF broadcast signal card. The setup seems to recognise that the Pinnacle card is there, but there's no mention of the Hauppauge card.

---

