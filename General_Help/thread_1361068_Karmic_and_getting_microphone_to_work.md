---
title: "Karmic and getting microphone to work"
date: 2009-12-21
forum: General Help
---

### Post by fragos on 2009-12-21
The microphone wouldn't work with any application under Karmic. For test purposes I chose the "Sound Recording" application. Without going through all the failed attempts I'll cut to the chase and just say what works. Right click the Speaker applet-> select "Sound Preferences"-> Input Tab. Next boost the "Input volume:". In the choose device area I saw two selections, both labeled "Internal Audio Analog Stereo" with the 1st already selected. Select the 2nd and the "Connector:" will change to "Analog Microphone / Input 1 / Microphone 1". Assuming you have a microphone plugged in you'll the "Input level:" when you speak or make noise. Go back to "Sound Recording" and you can further confirm operation.

Despite getting the microphone to work I still can't get Skype to make a test call but that's likely a different problem.

---

### Post by eaidoido on 2009-12-26
thanks. that fixed my mic issues. I also still cant get skype audio to work. i hope someone there is reading this. here my output when running skype from the terminal. 

```
RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

---

