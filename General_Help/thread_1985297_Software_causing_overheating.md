---
title: "Software causing overheating?"
date: 2012-05-23
forum: General Help
---

### Post by katya_sehgal on 2012-05-23
Hello,
I am using Sound Converter to change music files from flac to mp3. I could use ffmpeg but there are several folders involved and I don't know the command line yet.

My problem is this. To successfully convert using this software, I have to plug out power source so that temperature falls from 80-90 degrees to an average 60. Then, after a few seconds, the temperature rises to the nineties again. So I plug in the power cord and quickly remove it. The temperature goes down to the sixties again.

The cycle continues till the software finishes the conversion. If I don't do this, the laptop shuts down.

This is how it looks:

[IMG]http://i50.tinypic.com/dllqw7.jpg[/IMG]
Where does the problem lie? If at it is a power saving issue, is there a solution?

Thank you.

---

### Post by Tony Flury on 2012-05-23
Sounds to me that your fan/temp sensors are doing something screwy.

---

### Post by katya_sehgal on 2012-05-23
> **Tony Flury said:**
> Sounds to me that your fan/temp sensors are doing something screwy.

That is sad.
Like in Windows, from which I have emerged, is there a software that controls the fans? For instance, if it crosses 65 degrees, it takes care of the fan speed and temperature?

Or do you suggest, as I have learned from these forums, the 'cooling pad'. Would working exclusively in an Air Conditioned environment help?

---

### Post by Redblade20XX on 2012-05-23
Look into process activity and see which one is over driving your cpu(s). It could be a software related issue if it only happens when converting the music file.

-Red

---

### Post by mcduck on 2012-05-23
Software may cause high CPU load, which is of course perfectly normal (when there's lots of work to do, you *want* the CPU to work hard).

...on the other hand, any actual *overheating* is _always_ a hardware problem. Either the cooling of the system is dirty, some component of the cooling system is broken or loose, or (rarely, but sometimes seen on cheaper pre-built systems) it's a faulty design in the first place and isn't up to the task of getting rid of the thermal power the hardware outputs.

The first thing to do would be making sure the system is clean of any dust, all fans are working properly and there's nothing restricting the air flow to the coolers.

After at it all depends on your actual hardware, is it a laptop or a desktop, does it have integrated or separate graphics card, or perhaps both, and so on.

Edit: Fans are not controlled by operating system or software, they are under direct control of the computer's BIOS. (Any fan control software you might see will only *request* the BIOS to adjust the fan speed, which it will only do if it decides that's OK and temperatures are within reasonable limits.)

---

### Post by katya_sehgal on 2012-05-23
Redblade20XX and mcduck,

the laptop shutdown recently while I was playing Warzone 2100.
About a month and a half back, I cleaned the fans and threw out the dust that accumulated from where the air flow is supposed to be constant.

Suppose software is causing high load, is it possible that the reading is faulty and hence the laptop shuts down, for I am not sure that the laptop ever actually reaches 80 to 90 degrees. 

You would say this is a hardware fault, but could it have something at all to do with the software. Your answer may help me decide on future course of action.

Thanks to both of you.

---

