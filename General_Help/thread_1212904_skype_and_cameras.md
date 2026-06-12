---
title: "skype and cameras"
date: 2009-07-14
forum: General Help
---

### Post by unix1adm on 2009-07-14
What is a good camera to use with Ubuntu and Skype? 

I want to start using my Ubuntu LT to talk over Skype. 
I was thinking Logetech is a good camera just not sure what one is Linux compatible. 

I know they come with the windoz drivers but how do you get them to work with Linux?

---

### Post by schmidtbag on 2009-07-14
most logitech cameras are linux compatible.  the more popular a camera is, the more likely it is to work.  if you have v4l or v4l2 (video for linux) then the camera should automatically work right when you plug it in.  i'm pretty sure ubuntu comes with v4l 1 and 2 installed

---

### Post by unix1adm on 2009-07-15
I am looking at

Logitech 960-000048 QuickCam Pro 9000 Webcam - 2.0 Megapixel Sensor, Autofocus, Built-In Microphone

---

### Post by schmidtbag on 2009-07-15
look up the model name in google and add "linux support" in the search.  if people say it works, then get it

---

### Post by kyphi on 2009-07-15
The Logitech Quickcam Pro 9000 works perfectly in Ubuntu.  Just plug it in.

In my opinion it is the best webcam available.

No need for Windows drivers.  The drivers are already built into the kernel.

---

### Post by unix1adm on 2009-07-16
ok then im sold. now to find one at a good price. Costco online has it for 65$ but i am looking localy.

---

### Post by unix1adm on 2009-07-16
I tried a friends camera and I see the video fine in a test but I dont seem to have any audio when I try to make a test sound. 

my sound it not on mute and is maxed out. 
My startup sound plays when I first login and when I press the up and down volume controls it make a beep... so I know it works. 

Thoughts on why skype wont do sound?

I am running version 2.0.0.72

---

### Post by kyphi on 2009-07-17
Sound works fine with me using the inbuilt microphone.

Do you have microphone capture enabled in alsamixer?

What kind of soundcard do you have?

Do you want your answers here or in LinuxQuestions?

---

### Post by unix1adm on 2009-07-17
i tired this and i got problem with audio play back. 

I am using an IBM R51 laptop if that helps. I dont know what sound card I have. How can I tell?

---

### Post by ZeldeR on 2009-07-17
try this [Solution]("http://zeldor.biz/?p=42")

---

### Post by unix1adm on 2009-07-17
i was able to select intel 82801DB-ICH4(hw:I8201DBICH4,0) and have it work.

Ill try the video when i connect to somene and see if that works

---

### Post by unix1adm on 2009-07-17
i was installing sw to synce my cell phone an dnow i dont have any audio. not even my startup sound will play. 

any idea where to look to see what is broken and why...

i would nto think the syncce sw would touch the sound card drivers. Yes I rebooted 2 times

---

### Post by unix1adm on 2009-07-17
well i got the sound working but not really sure how i did it. see if it works next time i boot

---

