---
title: "24/96 HD sound on Music Streamer II in Ubuntu"
date: 2011-10-17
forum: General Help
---

### Post by bo.vestergaard on 2011-10-17
Hello guys,

I recently bought a Music Streamer II USB sound card (or DAC as it is also called). It sounds phenomenal. The Music Streamer is a high definition DAC which can play 24 bit FLAC files at the following sample rates, 32K, 44K (CD quality), 48K, 88K and 96K.

However, Ubuntu plays all files at 16 bit 44KHz no matter how the FLAC file is encoded. I can find nowhere to configure the sample rate. In Windows XP I can click properties on the sound card and select the desired sample rate. Obviously, that is of no use as I have no intention of running Windows but I mention it because it shows that the hardware does work.

The Music Streamer II has LED's which indicates the sample rate so I can easily tell when it goes 24/96.

I have looked around on the net and a lot of people are talking about this but I haven't been able to find a solution. 24/96 is becoming more and more popular in the music world and Ubuntu is the perfect OS for a music streamer so it seems a shame the 24/96 format is not supported.

So my questions are:

Does Ubuntu actually support HD sample rates such as 24/96?

If so, what do I need to do to enable it?

Obviously, I can provide further information. Please let me know what config files you need and I will provide them.

Regards,

Bo

---

### Post by bo.vestergaard on 2011-11-03
I think I have partly solved this. In /etc/pulse/daemon.conf I added the following:

default-sample-format = s24le
default-sample-rate = 96000

I had to reboot for it to take effect. The Music Streamer now indicates that it is running 96K sample rate. The problem is, now it runs 96K all the time, regardless of the source. Also, if I change it I have to reboot the computer every time I do so. There must be a better way of doing this. Any suggestions anyone?

Bo

---

