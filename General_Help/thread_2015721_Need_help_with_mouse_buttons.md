---
title: "Need help with mouse buttons"
date: 2012-07-03
forum: General Help
---

### Post by GradeZero on 2012-07-03
After some searching and reading up on my problem, I decided to post on the forums.

My mouse (Microsoft Explorer Touch Mouse) has two buttons on it that on my windows partition, have been set to backward and forward. Normally on this mouse, it is not by default the back and forth commands, I had to set it to do so.

The problem is that these two buttons are not working in Ubuntu. I have tested with xev and I have determined that the buttons are not even detected within Ubuntu (I could be wrong).

Basically I am asking if anyone would know how to fix this issue. Thanks in advance.

---

### Post by msammels on 2012-07-03
Hey Grade,

I'm not too strong on the hardware side of things, so excuse me if I fail here. Have you looked on Microsoft's website to see if there are either drivers and/or software available?

---

### Post by GradeZero on 2012-07-03
> **msammels said:**
> Hey Grade,

I'm not too strong on the hardware side of things, so excuse me if I fail here. Have you looked on Microsoft's website to see if there are either drivers and/or software available?

The drivers they currently have listed are only for Mac and Windows.

---

### Post by msammels on 2012-07-03
Right, OK. Give me some time to look into this for you, I'll see what I can dig up - and maybe someone else will be able to help as well.

---

### Post by GradeZero on 2012-07-03
> **msammels said:**
> Right, OK. Give me some time to look into this for you, I'll see what I can dig up - and maybe someone else will be able to help as well.

Alright thanks.

---

### Post by msammels on 2012-07-03
Grade,

Can I ask you to take a look at [this link](https://help.ubuntu.com/community/ManyButtonsMouseHowto) please? It may help your situation.

---

### Post by GradeZero on 2012-07-03
On the remapping section. It asks for a device name like so, > xinput set-button-map <device name> 1 2 3 6 7

I am having trouble with putting the device name down as it has spaces (shell newbie).  That and I am not sure I am even putting the right device name on it.

---

### Post by msammels on 2012-07-03
Grade,

In order to use spaces simply put it inside "quotation marks", however to be on the safe side... post here what you're using please?

---

### Post by GradeZero on 2012-07-03
> van@VanUbuntu-VPCEH12FX:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=15	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer         	id=10	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
van@VanUbuntu-VPCEH12FX:~$ xinput set-button-map "Virtual core pointer" 1 2 3 6 7
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  17
  Current serial number in output stream:  17
van@VanUbuntu-VPCEH12FX:~$ 


To clarify, I used Virtual core pointer in the above attempt.

---

### Post by msammels on 2012-07-03
> **GradeZero said:**
> I am having trouble with putting the device name down as it has spaces

Yes, but I was referring to this, as in what device name are you putting down? :)

---

### Post by GradeZero on 2012-07-03
Sorry, my mistake. I used "Microsoft Microsoft® Nano Transceiver v1.0" this time(the mouse is wireless and uses a nano transceiver) and it said I have to use the device ID as there is two of them.

> van@VanUbuntu-VPCEH12FX:~$ xinput set-button-map "Microsoft Microsoft® Nano Transceiver v1.0" 1 2 3 6 7
Warning: There are multiple devices named "Microsoft Microsoft® Nano Transceiver v1.0".
To ensure the correct one is selected, please use the device ID instead.

unable to find device Microsoft Microsoft® Nano Transceiver v1.0


---

### Post by msammels on 2012-07-03
It is at this point I would ask for the help of a hardware specialist... sorry, I'm more of a software solutions. :(

---

### Post by GradeZero on 2012-07-03
> **msammels said:**
> It is at this point I would ask for the help of a hardware specialist... sorry, I'm more of a software solutions. :(

Aw, thanks for your help though.

---

### Post by msammels on 2012-07-03
Not a problem... hopefully you'll get the other half fixed later today.

---

### Post by GradeZero on 2012-07-03
So I tried to do, > xinput set-button-map "12" 1 2 3 6 7 and > xinput set-button-map "13" 1 2 3 6 7

And then I lost my scrolling ability. So then I changed it to > xinput set-button-map "12" 1 2 3 4 5 And for 13 as well and I got my scrolling back. I think the only issue is that it does not detect the buttons as I also tried > xinput set-button-map "12" 1 2 3 4 5 6 7 and for 13 as well and nothing happened.

---

### Post by msammels on 2012-07-03
Well, they always did say that 13 was unlucky for some. May I ask where you pulled them numbers from? It might help shed some light...

---

### Post by GradeZero on 2012-07-03
> **msammels said:**
> Well, they always did say that 13 was unlucky for some. May I ask where you pulled them numbers from? It might help shed some light...

Using xinput list,

[HTML]van@VanUbuntu-VPCEH12FX:~$ xinput list
&#9121; Virtual core pointer id=2	[master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4	[slave pointer (2)]
&#9116; &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=12	[slave pointer (2)]
&#9116; &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=13	[slave pointer (2)]
&#9116; &#8627; AlpsPS/2 ALPS DualPoint TouchPad id=15	[slave pointer (2)]
&#9116; &#8627; DualPoint Stick id=16	[slave pointer (2)]
&#9123; Virtual core keyboard id=3	[master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5	[slave keyboard (3)]
&#8627; Power Button id=6	[slave keyboard (3)]
&#8627; Video Bus id=7	[slave keyboard (3)]
&#8627; Sony Vaio Keys id=8	[slave keyboard (3)]
&#8627; Power Button id=9	[slave keyboard (3)]
&#8627; Sony Visual Communication Camer id=10	[slave keyboard (3)]
&#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=11	[slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=14	[slave keyboard (3)][/HTML]

And in the code it says the id=12 and id=13 beside both items being listed as nano transceiver. Since it asked for a device id, I just used the device id and put it into the quotations. It worked I guess.

---

### Post by msammels on 2012-07-03
Makes sense. From what I can gather, one id is for scrollwheel, the other is for the actual buttons, but like I say... this is hardware :P

---

### Post by GradeZero on 2012-07-03
Going to search around for more info, will update if there is anything new then.

---

