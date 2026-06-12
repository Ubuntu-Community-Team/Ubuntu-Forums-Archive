---
title: "Just installed Ubuntu, got a few problems"
date: 2010-11-02
forum: General Help
---

### Post by neschn on 2010-11-02
So, I got sick of XP and got a virus on it and installed Ubuntu. I love it so far but I have a couple problems with it.

1. When I close my netbook (which is an Acer Aspire One 7051-h I believe), it goes into hibernate (or suspend) and when I open it back up its just a black screen and doesn't do anything.

2. I can't adjust my screen brightness, I hate having a really bright background and it kills my battery life.

3. Talking about battery, the battery life doesn't even show. So I have no clue what my battery life is at.


Also it seems to run kind of slow on my computer, but I'm thinking that might just be the processor or something. Is there anyway to overclock?

Thanks a ton,
neil

---

### Post by Quackers on 2010-11-02
Welcome to UF.
If you go to System > Preferences > Power Management you can set most of the options for power and suspend/hibernate/shutdown.
Please note that there are settings for using AC power and for using the battery. In the General tab there is an option to show the battery icon or not.

---

### Post by neschn on 2010-11-02
> **Quackers said:**
> Welcome to UF.
If you go to System > Preferences > Power Management you can set most of the options for power and suspend/hibernate/shutdown.
Please note that there are settings for using AC power and for using the battery. In the General tab there is an option to show the battery icon or not.

Yeah I found that but when I click the button for the battery it just shows a lightning bolt. Which I'm guessing means charging? but its not in the charger.

Also, with the screen brightness, I been trying everything I have found and I can't get my screen to dim :\

---

### Post by Rypervenche on 2010-11-02
> **neschn said:**
> Also, with the screen brightness, I been trying everything I have found and I can't get my screen to dim :\

I would try either updating your BIOS which very often fixes these problems (it did for me on my old Acer when the fan would not work at all and would cause the laptop to overheat), or you can try this...

Open a terminal and edit your Grub configuration file:

sudo gedit /etc/default/grub
And change the option row GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" as follow:

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash"
Then update Grub installation with the command:

sudo update-grub2
and restart your netbook


I hope one of those two options works for you.

---

### Post by Quackers on 2010-11-02
The screen brightness doesn't work on my laptop. It seems to be a common problem. There is an applet that gives some people the option to change the brightness but that doesn't work for mine. If you want to try that right-click on the top panel and select add to panel then in the box that opens up highlight the brightness applet and click add.

My battery icon doesn't show the lightning bolt unless the AC adaptor is plugged in. If yours isn't like that something is different. Maybe an ACPI setting or problem?

---

### Post by yetiman64 on 2010-11-02
1. You will need a swap space as large as your RAM amount to successfully hibernate your machine. You can check your swap size you can use
```
top
```in a terminal. Compare the mem and swap values.The amounts are in the top block of information. Use q on the keyboard to quit top.
For more info on swap check here, [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

2. Check out this info and see if it is of any help [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
and
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Brightness%20hotkeys](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Brightness%20hotkeys)
both links are for the same page, the second specifies the brightness key issue. I don't know how much of this you will need to use.

3. Quackers mentions the General Tab. :)

Welcome to the forum.

---

### Post by neschn on 2010-11-02
Thank you for all your help, Im trying that grub thing and restarting my computer.


Also, when I load up my computer it greats me with in the beginning saying something like FATAL: and then has something about a module. Is this normal?

---

### Post by neschn on 2010-11-02
I don't know what that grub thing is supposed to do lolz, but I restarted my computer.

Also, I'm pretty computer smart kinda but what is ACPI?

EDIT:

It seems like that Grub thing got rid of my audio playback. I was playing audio completely fine and then I put in that code and restarted and now no audio will come out of my speakers.

---

### Post by Rypervenche on 2010-11-02
> **neschn said:**
> Also, I'm pretty computer smart kinda but what is ACPI?

Type "man acpi" in your terminal. It gives you information about your battery.

> It seems like that Grub thing got rid of my audio playback. I was playing audio completely fine and then I put in that code and restarted and now no audio will come out of my speakers.

But does the lighting work? If it works, try restarting your laptop again to make sure that that is what is causing the speaker problem and then we can continue from there.

---

### Post by neschn on 2010-11-02
> **Rypervenche said:**
> Type "man acpi" in your terminal. It gives you information about your battery.



But does the lighting work? If it works, try restarting your laptop again to make sure that that is what is causing the speaker problem and then we can continue from there.

Nahh my lighting didn't seem to be effected. And I took off the code, updated grub, and restarted my computer and my audio seems to be back

and thanks for the acpi code, I'll check it out. EDIT: I didn't work :\

---

### Post by Rypervenche on 2010-11-02
Did you try updating your BIOS? Make sure your BIOS is up to date. There is a good chance that that is your problem.

And I believe you have to sudo apt-get install acpi in order to use it and see the man page. I don't think it's in Ubuntu by default.

---

