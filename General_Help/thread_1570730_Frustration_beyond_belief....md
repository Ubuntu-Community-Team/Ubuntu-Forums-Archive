---
title: "Frustration beyond belief..."
date: 2010-09-08
forum: General Help
---

### Post by dougalkerr on 2010-09-08
Hi Folks

I am unable to capture a screenshot of what my Network connections menu looks like to show a problem that I have.

I have been trying to use a new USB wireless thingy and although the connection information looks correct (checked against another PC) and it looks like the computer wants to let me choose a Network, when I open the Network icon on the panel, the options to connect to are non-descript characters.
If I choose Auto etho or if I put the wrong connection name into the settings (which I had done to start with) then I see normal English.

The thing is that when I start the screen capture software and take a snapshot to show things nothing is captured to the Clipboard. If I try to press any of the options on the screen capture Window then the Network menu disappears, very frustrating... HELP. Please. It seems like I am almost there.

---

### Post by dougalkerr on 2010-09-08
And of course Linux can do a lot more than Windows in general but, we won't want to get into that here. There are other pages for this ongoing war...
My Ultimate Edition 2.6 that I am running on this laptop to write this post is a fantastic version of Linux based upon Ubuntu but, much more automated and set-up. I can't seem to find the correct phrase... ah, 'Brilliant' that's a good word for it.
It does everything for me but, unfortunately just like Windows... I can't get it to install on the old timer that I have Ubuntu jaunty on, it is just too much. UE needs a bit of power and RAM and I don't think the old DVD reader installed helps.

Hope this might persuade you to think again about the whole Windows versus Linux thing if you have a go with UE.

---

### Post by mirchichamu on 2010-09-08
> **dougalkerr said:**
> And of course Linux can do a lot more than Windows in general but, we won't want to get into that here. There are other pages for this ongoing war...
My Ultimate Edition 2.6 that I am running on this laptop to write this post is a fantastic version of Linux based upon Ubuntu but, much more automated and set-up. I can't seem to find the correct phrase... ah, 'Brilliant' that's a good word for it.
It does everything for me but, unfortunately just like Windows... I can't get it to install on the old timer that I have Ubuntu jaunty on, it is just too much. UE needs a bit of power and RAM and I don't think the old DVD reader installed helps.

Hope this might persuade you to think again about the whole Windows versus Linux thing if you have a go with UE.

I wished, I would have helped you but my knowledge of Linux is also limited.

Right now I am replying from my "brilliant" Ultimate Edition 2.7. I have tested almost all the Linux Distros BUT Ultimate Edition is the King of All. I am so happy with that I removed windows 7 from  my Laptop and Installed Ultimate Edition as solo.

---

### Post by Gunman1982 on 2010-09-08
Screen capture software? ... Just try to press the 'Print' button on your keyboard to take a screenshot. Should prompt you for a filename/directory to save it afterwards.

---

### Post by coffeecat on 2010-09-08
> **Gunman1982 said:**
> Screen capture software? ... Just try to press the 'Print' button on your keyboard to take a screenshot. Should prompt you for a filename/directory to save it afterwards.

I can confirm the OP's problem here. If you click on the network manager icon to drop its list of networks down, the PrtScr key no longer initiates a screengrab. Nothing happens. If you click the desktop to get rid of the network manager menu, then the Print key works again. As the OP points out - very frustrating.

> **dougalkerr said:**
> I open the Network icon on the panel, the options to connect to are non-descript characters.

Can you describe what you mean by nondescript? I know this isn't very satisfactory, but can you take a digital photo of the screen and post that?

---

### Post by tgalati4 on 2010-09-08
Look for an option to choose "Shared Key" vs "Open Key".  It looks like the wireless router is sending an encrypted key and your USB dongle is not decrypting it.  Try changing from "Open Key" to "Shared Key".

---

### Post by Gunman1982 on 2010-09-08
> **coffeecat said:**
> I can confirm the OP's problem here. If you click on the network manager icon to drop its list of networks down, the PrtScr key no longer initiates a screengrab. Nothing happens. If you click the desktop to get rid of the network manager menu, then the Print key works again. As the OP points out - very frustrating.


Ah ok, didn't test it, shame on me.

Just tested something and it worked, at least on a Debian since I don't have Ubuntu at hand atm.
Check your Application->Accessories?->Screen Capture 
(Dunno if its called accessories and screen capture so check yourself)
Gives you a dialogue Where you can choose if you want to capture whole screen, just a window and so on. The best thing is you can set a timer, like set it to 2 seconds, click on "capture screen" and click on the network-manager icon to get the list of available networks. Now wait  till it takes the picture. :-)

---

### Post by coffeecat on 2010-09-08
> **Gunman1982 said:**
> Just tested something and it worked, at least on a Debian since I don't have Ubuntu at hand atm.
Check your Application->Accessories?->Screen Capture 
(Dunno if its called accessories and screen capture so check yourself)

Sounds useful but it's not in an Ubuntu default install, and I haven't got Debian to hand. :p

I can't find anything in the Ubuntu repositories that seems to correspond with this. What is the command in Alacarte that launches it? That might give us a clue and be useful for the OP.

---

### Post by Gunman1982 on 2010-09-08
> **coffeecat said:**
> Sounds useful but it's not in an Ubuntu default install, and I haven't got Debian to hand. :p

I can't find anything in the Ubuntu repositories that seems to correspond with this. What is the command in Alacarte that launches it? That might give us a clue and be useful for the OP.

It's called 'gnome-screenshot --interactive'

---

### Post by coffeecat on 2010-09-08
> **Gunman1982 said:**
> It's called 'gnome-screenshot --interactive'

Aha! After some research I discovered the following. gnome-screenshot is part of gnome-utils and is included in a default install of Ubuntu (Lucid). But that menu entry with that command is not there and I guess that when you press the Print key that invokes gnome-screenshot with presets. Not as flexible as with the --interactive option though, so thanks for that. I've now put an entry in my menu.

@dougalkerr, if you've been following this, you can put the command 'gnome-screenshot --interactive' into a terminal or press alt-F2 and use that instead. You'll then be able to get a screenshot of the network manager menu.

I'm logging off now. Late here.

---

### Post by howefield on 2010-09-08
> **coffeecat said:**
> But that menu entry with that command is not there and I guess that when you press the Print key that invokes gnome-screenshot with presets. 

Should be in Applications > Accessories > Take Screenshot ?

---

### Post by coffeecat on 2010-09-09
> **howefield said:**
> Should be in Applications > Accessories > Take Screenshot ?

You are quite right. I must have been tired last night to have missed  that. It's staring me in the face together with the menu entry that I  added as well. My apologies to anyone I misled.

---

### Post by dougalkerr on 2010-09-19
Hi guys

I have been coming at things from a different angle and ended up installing Ubuntu 10.04 afresh.
After some searching and a lot of help from others I am at the stage where the wireless utility program 'RutilT' can detect the wireless USB but, throws an error message Cannot detect frequency/channel. Code: 22.
At least I was at that stage. I followed some other advice about installing backports and now the prog can't detect the device at all but, I don't blame anyone for this. People are only trying to help.

I will get to the bottom of this problem yet.

Thanks again for help on the screen capture. It'll be useful I'm sure.

---

