---
title: "&quot;Create&quot; a microphone device for Flash?"
date: 2012-02-20
forum: General Help
---

### Post by Timendus on 2012-02-20
Hello forums,

I was wondering if anyone knows a way or a tool to "create" a microphone device in Ubuntu that Adobe Flash recognizes. I want to use Bambuser or YouTube Live to create a live webcam stream with audio and these websites rely on a Flash applet that records your webcam and your microphone. Same goes for chat roulette and pretty much all other websites that work with recording input devices. Flash nicely recognizes both my internal and my USB microphone. But I don't want to record my microphone but instead I want to stream audio from a pre-existing (icecast) audio stream to the flash applet.

The best way I've discovered so far is to set my analog line-in as input connector in the sound preferences dialogue and connect my line-out to the line-in. Anything I play on the PC will then be recorded and streamed. However, I'd like to do this in a more elegant (software) way. I don't need to record anything I play, I just need to record the audio stream.

I guess what I want is a piece of software that does for microphones what all those "fake webcam" programs do for webcams: allow you to stream anything and pretend it's a hardware device.

If you have any ideas on how to achieve this, please let me know. Thanks in advance.

Cheers,
Timendus

---

### Post by puchrojo on 2012-07-04
Hi,
sudo apt-get install pavucontrol
work for me on ubuntu 12.04

Source: [http://www.nikolakis.net/2010/01/make-webcam-mic-work-with-flash-in-ubuntu/](http://www.nikolakis.net/2010/01/make-webcam-mic-work-with-flash-in-ubuntu/)

---

