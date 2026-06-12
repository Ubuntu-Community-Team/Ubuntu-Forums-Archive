---
title: "Headphone jack not working"
date: 2010-07-13
forum: General Help
---

### Post by EllyBilateralCI on 2010-07-13
Hi,

I've searched to find a solution for my headphone jack that doesn't seem to be working.

I'm using Ubuntu 10.04 Lucid Lynx, the sound board I have when I put in the command:

cat /proc/asound/card0/codec#* | grep Codec

and the result is this: VIA VT1708S

I've got the latest alsa installed - can't remember how I installed it but it was by manually installing it terminal.   

From Applications -> Sound & Video -> GNOME Alsa Mixer

I can see the Headphone column and it is unmuted.

I'm baffled as my speakers works perfectly but it is the headphone jack.  Is there a way of detecting it that the jack can work?

I do have virtual box - windows xp and I can't get it to work there either....so I was wondering if it was best to find a way of working in the virtual box first and then in Ubuntu.

I would be very grateful for any help as I just don't understand why it won't work.  

Elaine

---

### Post by jsstn on 2010-07-13
try searching [http://www.linlap.com/](http://www.linlap.com/) for your computer. if it is listed, there's a chance somebody has found a solution and posted it there.
although this: [http://www.spinics.net/lists/alsa-devel/msg34961.html](http://www.spinics.net/lists/alsa-devel/msg34961.html) does make things look pretty bleak.

---

### Post by EllyBilateralCI on 2010-07-13
Thanks jsstn for your assistance.....it does look bleak doesn't it.....!

Ummmm I don't have a laptop just a pc - how do I know what type of it is?  is there a command that I can run?   I know it sounds daft but I got a homemade PC - it was a blank empty case with bits and bobs from different manufactures put together and hey presto a home made PC! (A Christmas present from my hubby and kids).

---

### Post by nano_tauluna on 2010-07-13
Same here ...

I Have Toshiba Laptop using ATI chipset...

Speaker on my laptop working just fine...

But when I plug Earphone into the Earphone Jack, speaker on my laptop still sounding but not my earphone....

Does any body know how to solve it ??

---

### Post by peyek on 2010-07-16
I also have the same problem with Acer 4745G on lucid, anybody know to solve the problem?

---

### Post by EllyBilateralCI on 2010-07-19
It works fine on LIVE CD....so does that mean I have to re-install Lucid Lynx?

---

### Post by rockneverdies on 2010-07-20
I have HP Pavilion PV4 - 2045dx... I got same problem too...

---

### Post by stoneage on 2010-07-20
> **EllyBilateralCI said:**
> It works fine on LIVE CD....so does that mean I have to re-install Lucid Lynx?

If it works on the Live disc it is probably a configuration or drivers issue.

I'm not sure in what form it is available on 10.04 (I'm still using 9.10), but try installing Pulseudio Device Chooser - I think it is called padevchooser - it has a range of options for managing and configuring sound.

---

### Post by rockneverdies on 2010-07-20
Actually I've just found this:

[http://ubuntuforums.org/showthread.php?t=1043568&highlight=hp+pavilion+dv4+headphone](http://ubuntuforums.org/showthread.php?t=1043568&highlight=hp+pavilion+dv4+headphone)

in the forum. 

My earphones are working just fine now... 

It could be solution for you too...

---

### Post by farish03 on 2010-07-22
i am very new to ubuntu.
I also have the same problem with Acer 4745G.
i have ubuntu 10.04 installed.
has anyone solved the headphone issue on an Acer 4745G?

---

### Post by EllyBilateralCI on 2010-07-22
> **farish03 said:**
> i am very new to ubuntu.
I also have the same problem with Acer 4745G.
i have ubuntu 10.04 installed.
has anyone solved the headphone issue on an Acer 4745G?

Hi Farish,

I have just re-installed Lucid Lynx (I originally had lucid before but it was of beta stage before lucid was officially released in May - it was all working find except sound) as have now got my sound back.

I couldn't find anywhere for my via vt1708s compatible sound check from hd audio text file which I'll explain in a minute.

But in [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) there is a brilliant step by step instruction to investigate and possibly (fingers crossed) fix your sound problem.  In this link I've provided you'll see a hd audio text list of possible compatible model codes you can use in relation to your acer model.  I have to warn you that it can take a few reboots for each model try out to see which would work.

As I say I've done a complete reinstall but this time I used Ubuntu Tweak to help tweak a few things here and there without interfering the ubuntu system too much.  I'm being extra careful what I install on my PC from now on but Ubuntu is fantastic - it beats windows, definitely.  

Hope this will help you Farish.

---

### Post by farish03 on 2010-07-30
thanks :)

---

