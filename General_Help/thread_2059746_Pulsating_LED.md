---
title: "Pulsating LED"
date: 2012-09-18
forum: General Help
---

### Post by Shadius on 2012-09-18
Hey everybody! :)

I just built my first computer and I have this idea to have a pulsating light that pulsates to sound. Say I'm playing music from my computer, I want a light to pulsate to the beat. Is there anything like that? Maybe a fan with an LED light that pulsates? Thanks.

---

### Post by f8l_0e on 2012-09-18
There are a couple of ways you could go about this.  There are circuits with a microphone that can detect a frequency range and trigger leds.  There are circuits that could be plugged into a Y adapter for the speaker output, if you are using analog stereo out. Instead of having to find existing ones or building your own you could probably find a tutorial on doing either method with an arduino.  
The more complicated way would be to use a pulseaudio plugin to drive a circuit, which now that I look, someone has already done:

[http://www.youtube.com/watch?v=F0Nq_V9VGqc]("http://www.youtube.com/watch?v=F0Nq_V9VGqc")

---

### Post by HermanAB on 2012-09-19
The simplest way is to hook a LED to the analogue audio output.  Since the bass has most energy, it will flash with the beat without any fancy tricks.

---

### Post by f8l_0e on 2012-09-19
I'm no engineer, but line out voltage is supposed to be around 2V peak to peak which means that is an AC current.  The LED would have to tolerate at least 2V reverse breakdown voltage so it wouldn't blow up.  

If the LED has a significant amount of voltage drop, isn't it going to muddy the sound going to the speakers?  

If the connected LED has too high of a voltage drop couldn't that effect the current draw on the audio chipset?  Would it be possible to damage the soundcard?

---

### Post by Shadius on 2012-09-19
> **f8l_0e said:**
> There are a couple of ways you could go about this.  There are circuits with a microphone that can detect a frequency range and trigger leds.  There are circuits that could be plugged into a Y adapter for the speaker output, if you are using analog stereo out. Instead of having to find existing ones or building your own you could probably find a tutorial on doing either method with an arduino.  
The more complicated way would be to use a pulseaudio plugin to drive a circuit, which now that I look, someone has already done:

[http://www.youtube.com/watch?v=F0Nq_V9VGqc]("http://www.youtube.com/watch?v=F0Nq_V9VGqc")

Thanks for that link. It led me to a whole bunch of other links which helped me. I came across this [link]("http://www.instructables.com/id/Led-Cube-8x8x8/?ALLSTEPS"). Looks very interesting! Looks like you can do tons with Arduino!

---

### Post by zero2xiii on 2012-09-19
> **Shadius said:**
> Thanks for that link. It led me to a whole bunch of other links which helped me. I came across this [link]("http://www.instructables.com/id/Led-Cube-8x8x8/?ALLSTEPS"). Looks very interesting! Looks like you can do tons with Arduino!

Hay.

Arduino's are basicly very small computers! haha.. You can run complete factories from them. Not worth the money if you just want to blink an LED :o

You get specialy designed IC's that does exactly that, will look up a product code just now.

Cherz

EDIT:
Hmmm seems the IC I used to use is no longer made (I bough a few hundred of them a few years back).

However, look at either one of theses:
LM2907N
LM2917N

The datasheet [here]("http://www.futurlec.com/Linear/LM2907N.shtml") has a lot of example (application circuits which include a few options to do what you wish to do.

Cherz :)

---

