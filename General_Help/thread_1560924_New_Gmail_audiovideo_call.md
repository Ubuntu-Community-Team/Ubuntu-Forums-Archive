---
title: "New Gmail audio/video call"
date: 2010-08-25
forum: General Help
---

### Post by micheledm on 2010-08-25
Hi everybody. I just installed the brand new plugin for making calls from Gmail but neither from Chrome or Firefox I'm able to use it since it keeps me asking for the installation, as the installed package is not recognized by the browser.

Any suggestion?

---

### Post by inameiname on 2010-08-25
What browser are you using? I'm guessing you are using the right deb file, right? I know the version I got from here works fine in Firefox.

[http://www.webupd8.org/2010/08/google-voice-and-video-chat-comes-to.html](http://www.webupd8.org/2010/08/google-voice-and-video-chat-comes-to.html)

---

### Post by micheledm on 2010-08-25
> **inameiname said:**
> What browser are you using? I'm guessing you are using the right deb file, right? I know the version I got from here works fine in Firefox.

[http://www.webupd8.org/2010/08/google-voice-and-video-chat-comes-to.html](http://www.webupd8.org/2010/08/google-voice-and-video-chat-comes-to.html)

As i said, both firefox and chrome. The plugin i think is installed fine because in firefox i can see "Google talk plugin" and "Google talk plugin video accellerator".

---

### Post by sanderd17 on 2010-08-25
I used the official version, and it seems to work good. From here: [http://www.google.com/chat/video](http://www.google.com/chat/video)

---

### Post by inameiname on 2010-08-25
Yeah it's the same version as the one I linked to. It was just an article about it, which then refers to the official site.

---

### Post by micheledm on 2010-08-25
downloaded and installed from that page :(

---

### Post by superdug on 2010-08-25
> **micheledm said:**
> downloaded and installed from that page :(

64-bit 10.04 lts desktop here.

Are you amd64 or i386?

I know the package I installed was an *.amd64.deb

I also cannot seem to get it to work by simply installing the .deb from google.

Restarted both firefox, swiftfox, chrome, and chromium (I don't know why I have those all installed, but I do ...)

None seem to recognize the google talk plugin.

---

### Post by micheledm on 2010-08-25
I just tested it with chromium and it works, without installing the plugin again.

it's weird, both firefox and chrome are up to date.

---

### Post by inameiname on 2010-08-25
I'm sure you already know this, but if the person you are trying to audio/video call with doesn't have it working on theirs, it's not gonna work on yours. I tried running it from my Firefox to my Opera just to check, and it wouldn't work. Shows that it's installed and I can see the little camcorder icon by my other gmail account's name in my contact list, but when I try it merely sends an invite to my other one, which is on Opera, and it won't install in it.

Anyway, I'll be able to really check for sure now that you can actually phone for free from Gmail as of today. Should be available to all Gmail users in the next few days, and only requires this very thing.

---

### Post by superdug on 2010-08-25
> **inameiname said:**
> I'm sure you already know this, but if the person you are trying to audio/video call with doesn't have it working on theirs, it's not gonna work on yours. I tried running it from my Firefox to my Opera just to check, and it wouldn't work. Shows that it's installed and I can see the little camcorder icon by my other gmail account's name in my contact list, but when I try it merely sends an invite to my other one, which is on Opera, and it won't install in it.

I'm not even going that far, I'm just using this link

[https://mail.google.com/mail/?shva=1#settings/chat]("https://mail.google.com/mail/?shva=1#settings/chat")

To the left it says
```

Voice and video chat:
Learn more
Google Talk Plugin v1.4.1.0
Google Talk Plugin Video Accelerator v0.1.43.3
```

But when I expand Verify Settings, nothing shows up

---

### Post by Ichtyandr on 2010-08-26
I have an issue, not sure if it is related to this thread.
I installed the plugin and it works fine but my integrated microphone stops working several seconds after conversation starts. 
With Skype I installed pulse audio volume control app made adjustments and unticked the box 'allow Skype to automatically adjust my mixer levels'.
Apparently google plugin immediately adjusts mixer levels.
Is there any setting like with the new google voice chat plugin? 
I am eager to get rid of Skype at this point, so any tips are apreciated!

---

### Post by brettdunnam on 2010-08-26
Mine works just fine. The dialpad pops up in the bottom right corner. 

You could try uninstalling the package and reinstalling making sure that you have no browser processes running.

---

### Post by Zeitgeist6149 on 2010-08-26
I can't get the calling feature to work. I'm really excited about this so I'm disappointed it's not working on my Ubuntu system.

How do I uninstall and reinstall the package?

I obtained the package from google.com/call and I am running it in Chrome w/ Ubuntu 10.04 

Any suggestions???

---

### Post by micheledm on 2010-08-26
For uninstalling you just need to "sudo aptitude purge google-talkplugin" and install it back again.

Before doing that check if the puglin is recognized by your browser by typing about:plugins in your address bar

---

### Post by kamrul.islam on 2010-11-06
You need to restart the browser to get it running.

---

### Post by huangja123 on 2010-11-10
I am trying to use Google chat with a  A4Tech PK-7MA Flexicam ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam. The setting shows that the driver is gspca_main. Sound is OK both ways. But no video.
Initially, I couldn't get it to work with Skype either. But after adding in a script as suggested in the forum 'skype video issue', it works. But I don't know how to use the same trick on Google Chat because it is a plugin. Would like to know if anyone has Google Chat video working with my model of camera.

Thks.

---

