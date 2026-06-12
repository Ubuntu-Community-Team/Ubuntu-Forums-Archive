---
title: "Help with Ipod touch support  in 10.4"
date: 2010-04-29
forum: General Help
---

### Post by luisico on 2010-04-29
I've just installed 10.4 and it works like a charm.
The only problem I have is that I've plugged my ipod touch 3g in and nothing happens.
It seems like the system doesn't detect it. Opening rhythmbox nothing happens either.

Do i need to do any extra thing in order to have my ipod working?

The only thing I can see in the syslog is this message:

 usb 2-3: new high speed USB device using ehci_hcd and address 8
 usb 2-3: configuration #1 chosen from 3 choices

Thanks in advance

---

### Post by luisico on 2010-04-30
It's solved.
Was my fault. Doing some debugging with libimobiledevice-utils I saw that the problem was my ipod is protected with password, so the mobiledevice libraries can't access the device information. I disabled the password protection and it worked.

Thanks

---

### Post by nakamuraxxx on 2010-09-15
Hi i noticed you had the same problem as i do right now. and i just bought the ipod touch 3g and i had the same problem. can you explain to me how did you get it to work? im new to using ubuntu 10.4. my ipod screen has a picture of a plug with an arrow pointing to the itunes Cd. thank you very much.

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> Hi i noticed you had the same problem as i do right now. and i just bought the ipod touch 3g and i had the same problem. can you explain to me how did you get it to work? im new to using ubuntu 10.4. my ipod screen has a picture of a plug with an arrow pointing to the itunes Cd. thank you very much.

You mention that you have just purchased an iPod Touch, have you initialised it on a Windows machine?  If not then what you need to do is go to a PC that has Windows on and download the latest version of iTunes and register the device on the iTunes account, you will only need to do this once.  Once you have done that, then connect your iPod Touch to your Ubuntu PC and Rhythmbox Music Player will start up and your iPod Touch will be detected immediately.

I had to do the very same thing when I bought one, I know it's a bit of a fuss but once you've initialised it via Windows pc/iTunes then it's basically plain sailing after that.

---

### Post by nakamuraxxx on 2010-09-15
oh i see. well i'll try that and see if it works. i was so happy to use it then seeing it didnt work just shot my hopes down lol thank you very much.

---

### Post by scouser73 on 2010-09-15
Post back if you have any problems please.

---

### Post by nakamuraxxx on 2010-09-15
yes for some reason rhythm box didn't open when i plugged in my ipod. i first had to install the new version of itunes on to my desktop then plugged it in and it recognized it. so i created an account on itunes. now that i plug back to my ubuntu 10.4 it still doesn't recognize it. what did i do wrong?

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> yes for some reason rhythm box didn't open when i plugged in my ipod. i first had to install the new version of itunes on to my desktop then plugged it in and it recognized it. so i created an account on itunes. now that i plug back to my ubuntu 10.4 it still doesn't recognize it. what did i do wrong?

Is the iPod Touch locked at all?, if so unlock it and it should then recognise it.

---

### Post by nakamuraxxx on 2010-09-15
no theres no lock, passcode or anything. i see the screen after i plugged it in on my desktop. now there it recognized.

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> no theres no lock, passcode or anything. i see the screen after i plugged it in on my desktop. now there it recognized.

Unplug your iPod Touch, restart the Ubuntu PC, then re-attach your iPod Touch making sure that it's not locked and see if it's connected to it this time.

---

### Post by nakamuraxxx on 2010-09-15
alright i'll do that now.

---

### Post by nakamuraxxx on 2010-09-15
ok so it now shows an icon and it recognizes as ipod but with a camera as the icon. i believe it has that because i took a picture. but i think if i add a few songs using my desktop that i will open up rhythm box. i think i should try that.

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> ok so it now shows an icon and it recognizes as ipod but with a camera as the icon. i believe it has that because i took a picture. but i think if i add a few songs using my desktop that i will open up rhythm box. i think i should try that.

Yes, add music by dragging and dropping from Rhythmbox to your iPod Touch and once you've done that it will start synchronising the music to the device.

---

### Post by nakamuraxxx on 2010-09-15
well i added a song and now nothing shows up. ugh

---

### Post by nakamuraxxx on 2010-09-15
no no i didn't use my ubuntu pc. i had to use the desktop to add a song and i wanted to see if rhythm box would recognize it but it didn't.

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> no no i didn't use my ubuntu pc. i had to use the desktop to add a song and i wanted to see if rhythm box would recognize it but it didn't.

What format is the song in?

iPod Touch Music File Formats.

[B]- AAC (M4A, M4B, M4P, up to 320 Kbps)
- Apple Lossless (a high-quality compressed format)
- MP3 (up to 320 Kbps)
- MP3 Variable Bit Rate (VBR)
- WAV
- AA (audible.com spoken word, formats 2, 3, and 4) 
- AAX (audible.com spoken word, AudibleEnhanced format)
- AIF[/B]

---

### Post by nakamuraxxx on 2010-09-15
i added a song from the itunes library on my desktop. they should all be mp3. but i'll add more in case that's the issue

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> i added a song from the itunes library on my desktop. they should all be mp3. but i'll add more in case that's the issue

Have you tried adding music to your iPod under Ubuntu yet? If not, please try.

---

### Post by nakamuraxxx on 2010-09-15
i can't thats the problem. nothing is showing up. rhythm box isn't opening so i have no idea what's the issue.

---

### Post by scouser73 on 2010-09-15
> **nakamuraxxx said:**
> i can't thats the problem. nothing is showing up. rhythm box isn't opening so i have no idea what's the issue.

Go to Terminal, copy and paste the following command. > sudo rhythmbox

Enter your password when asked, Rhythmbox will now start.

---

### Post by nakamuraxxx on 2010-09-15
ok so now the ipod is still not showing up. thats the issue.

---

### Post by mr_luksom on 2010-09-15
Do you have the iOS version for the iPod?

---

### Post by lenco12 on 2010-09-16
> **scouser73 said:**
> You mention that you have just purchased an iPod Touch, have you initialised it on a Windows machine?  If not then what you need to do is go to a PC that has Windows on and download the latest version of iTunes and register the device on the iTunes account, you will only need to do this once.  Once you have done that, then connect your iPod Touch to your Ubuntu PC and Rhythmbox Music Player will start up and your iPod Touch will be detected immediately.

I had to do the very same thing when I bought one, I know it's a bit of a fuss but once you've initialised it via Windows pc/iTunes then it's basically plain sailing after that.
oh i see. well i'll try that and see if it works. i was so happy to use  it then seeing it didnt work just shot my hopes down lol thank you very  much.

---

### Post by nakamuraxxx on 2010-09-16
ok just to let everyone know i have a 32G. 4th generation ipod touch.

---

