---
title: "screen resolution too low"
date: 2009-12-16
forum: General Help
---

### Post by mikejaron on 2009-12-16
im using the newest version of ubuntu and have a new sony vaio. the maximum screen resolution i can select is 1280x768 but when i type in sudo xrandr in the terminal it says my maximum is 2176 x 768, also my computer is full HD 1080p. (sometimes when i open certain things like preference boxes or save to boxes i cant even see the bottom of the box, it is just to big for my screen and i cant resize it to make it smaller) i am new to ubuntu and def a newb at computing so if you could explain it in lamens terms that would be great.

---

### Post by coffeecat on 2009-12-17
Are you sure about those figures? Are you sure you don't have to have an external monitor fitted to get full HD? My understanding of full HD is that you need a native pixel resolution of 1920x1080 on the monitor. Anything less would need some sort of interlacing and wouldn't be true full HD. From the figures you give it looks as though your laptop screen has a pixel resolution of 1280x768, which doesn't sound right either because that's an older widescreen resolution, not even 16x10. If your machine is new and supports HD it should have a 16x9 screen.

What's the actual model of your Vaio? Then we can look up the manufacturer's specifications. Also - what graphics card? If you're not sure about that, open a terminal (Applications > Accessories > Terminal) and post the output of:

```
lspci | grep "VGA"
```That business of preference and save to boxes is a curse of limited vertical resolution. Can you not just scroll down with the mouse/touchpad? Perhaps you could explain which apps you are getting with this problem, so we can be sure we are talking about the same thing.

---

### Post by mikejaron on 2009-12-17
> **coffeecat said:**
> Are you sure about those figures? Are you sure you don't have to have an external monitor fitted to get full HD? My understanding of full HD is that you need a native pixel resolution of 1920x1080 on the monitor. Anything less would need some sort of interlacing and wouldn't be true full HD. From the figures you give it looks as though your laptop screen has a pixel resolution of 1280x768, which doesn't sound right either because that's an older widescreen resolution, not even 16x10. If your machine is new and supports HD it should have a 16x9 screen.

What's the actual model of your Vaio? Then we can look up the manufacturer's specifications. Also - what graphics card? If you're not sure about that, open a terminal (Applications > Accessories > Terminal) and post the output of:

```
lspci | grep "VGA"
```That business of preference and save to boxes is a curse of limited vertical resolution. Can you not just scroll down with the mouse/touchpad? Perhaps you could explain which apps you are getting with this problem, so we can be sure we are talking about the same thing.


i double checked and it still says those figures, and i am not running an external display. although i have ran an external display but its not HD (its an old tv, i used a scan converter, to go from VGA to RCA, is it possible my comp still thinks its running on a external display?) my comp is a Sony VIAO FW series with Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

no it wont let me scroll down as the window is outside of the screen. Some specific examples are in open office when i open file>properties, or tools>options (and the options box is vertically and horizontally to big). those are just some examples if you need more please let me know.

---

### Post by coffeecat on 2009-12-17
> **mikejaron said:**
> and i am not running an external display. although i have ran an external display but its not HD (its an old tv, i used a scan converter, to go from VGA to RCA, is it possible my comp still thinks its running on a external display?)

I didn't suggest you were running an external display. I was suggesting that it could be possible that the machine needs an external monitor to display true HD. But to be sure we need to look at the full manufacturer's specs....

> **mikejaron said:**
>  my comp is a Sony VIAO FW

Please quote the **full model number**. On the Sony UK website there are 7 different FW series listed. Five have 1920x1080 screens, but two have 1600x900 screens. Also, none of them have the.....

> **mikejaron said:**
> Mobility Radeon HD 3650

So - what country are you in and where did you buy the Sony? The specs for Sony Vaios can be different in different countries even with the same model number.

Last point - you have an ATI graphics card, probably running the open-source video driver. This may be a problem, but let's confirm the machine spec first. Full model number and country of purchase please.

**Edit:** you say you are running the newest version of Ubuntu. Please confirm that you mean Karmic (9.10) and not a development version of Lucid (10.04).

---

### Post by mikejaron on 2009-12-17
ok sorry for the inconvenience as i am new to ubuntu and i really appreciate the help. ok so my full model number is a sony vaio VGN-FW390 and i bought it online in the united states. Also i am running Karm.ic (9.10).

---

### Post by coffeecat on 2009-12-17
I found the US Sony site unhelpful for trying to get specifications (your model is not listed on the UK Sony site), but Google came to the rescue. According to this:

[http://docs.google.com/viewer?a=v&q=cache:i9CB4n9bMIcJ:www.sonystyle.com/wcsstore/SonyStyleStorefrontAssetStore/pdf/VGN-FW390CTO_Spec_Sheet_FINAL.pdf+vaio+vgn-fw390+specifications&hl=en&gl=uk&pid=bl&srcid=ADGEESg8DctU2mQy4CvAB85LgFaD6hF8DGxrgREele6VtpevLSOOuRmcLhvxmXI8MYqSw1ohPLj6NqjXagukkoK16XcR03Vv09zqygEZZBP-y6s8GciDlketQBi7W8JK12PlTQhIaZta&sig=AHIEtbQTHLV5QtcLLJrm7T5NDIlTX8INcw](http://docs.google.com/viewer?a=v&q=cache:i9CB4n9bMIcJ:www.sonystyle.com/wcsstore/SonyStyleStorefrontAssetStore/pdf/VGN-FW390CTO_Spec_Sheet_FINAL.pdf+vaio+vgn-fw390+specifications&hl=en&gl=uk&pid=bl&srcid=ADGEESg8DctU2mQy4CvAB85LgFaD6hF8DGxrgREele6VtpevLSOOuRmcLhvxmXI8MYqSw1ohPLj6NqjXagukkoK16XcR03Vv09zqygEZZBP-y6s8GciDlketQBi7W8JK12PlTQhIaZta&sig=AHIEtbQTHLV5QtcLLJrm7T5NDIlTX8INcw)

.... the VGN-FW390 is customer-configurable and the screen comes with a choice of two configurations: 1600x900 or 1920x1080. :lol: So you'll have to tell me what the screen resolution is. :wink: Perhaps the quickest way would be to boot into Vista and check there.

But whichever it is, something is clearly not right if the maximum resolution you can get is 1280x768 - and xrandr is obviously being less than useless.

Let's check a few basic things. It sounds as though you might have done this but, if not, go to System > Preferences > Display and see if you can change the resolution there.

Next thing - let's look at the driver. if you haven't already installed the proprietary driver, you are probably using the open-source radeon driver. I'm posting from a 1600x900 resolution laptop with the ATI Radeon HD 4200 graphics chipset and I can get 1600x900 just fine. But if you can't, go to System > Administration > Hardware Drivers and see if it's prompting you to activate the proprietary fglrx driver. That might help. Or it might not. Things were actually worse on my machine with the fglrx driver. I'm afraid ATI graphics can be a challenge in Linux.

---

### Post by kopus on 2010-04-17
I'm having a similar problem. I also have a sony vaio (VGN-FW11M) that comes with the Mobility Radeon HD 3400 Series. The maximum resolution for this model is 1600x900.

I'm using the ati opensource driver.

When I only use the ati opensource driver with no external monitor connected to my laptop, everything is fine and the resolution is automatically detected and set to 1600x900.
The problem is when I connect my external LCD monitor that does (1280x1024 maximum) the max resolution allowed for the laptop display is 1440x900, 1600x900 disappears.

If I use the fglrx driver I can set the laptop display with 1600x900 and the external monitor with 1280x1024. It must be a bug, I can help figure out what it is if you guys (developers) need my help.

---

### Post by kopus on 2010-04-17
I forgot to say, to anyone else having this problem, my solution was to use amdcccle to generate the xorg.conf and then I changed the driver from fglrx to ati.

---

### Post by mikejaron on 2010-05-06
> **kopus said:**
> I forgot to say, to anyone else having this problem, my solution was to use amdcccle to generate the xorg.conf and then I changed the driver from fglrx to ati.

i am sorry as i am new to computers and ubuntu. how do i do this in lamens terms?

---

