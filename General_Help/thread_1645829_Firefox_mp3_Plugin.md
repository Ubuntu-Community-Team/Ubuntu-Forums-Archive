---
title: "Firefox mp3 Plugin"
date: 2010-12-15
forum: General Help
---

### Post by eamonnfpc on 2010-12-15
Hi. Running 10.10 with gde.
In Firefox, if I go Edit>Preferences>Applications there is no entry for mp3. I understand there should be and I'd like to change how Firefox plays mp3's. At the minute it uses Totem and the visual effects (which I can't disable in the browser) drive me bonkers and deactivate the screensaver to boot. I'd like to change it to have Firefox use VLC or RealPlayer for mp3's instead but don't have that option.
Any ideas anyone?
Cheers, Eamonn

---

### Post by sikander3786 on 2010-12-15
Welcome to the forums?

Is VLC installed and is it able to play mp3 files?

---

### Post by eamonnfpc on 2010-12-15
btw, I searched the Firefox forums to no avail.
I did find this in their support section....
**Download actions**
When you click a link to download a file, the [MIME type]("https://developer.mozilla.org/en/Properly_Configuring_Server_MIME_Types#What_are_MIME_types.3F")  determines what action Firefox will take.  You may already have a  plugin installed that will automatically handle the download, such as [Windows Media Player]("http://support.mozilla.com/en-US/kb/Using%20the%20Windows%20Media%20Player%20plugin%20with%20Firefox") or [QuickTime]("http://support.mozilla.com/en-US/kb/Using%20the%20QuickTime%20plugin%20with%20Firefox").   Other times, you may see a dialog asking whether you want to save the  file or open it with a specific application.  When you tell Firefox to  open or save the file and also check the option to "Do this  automatically for files like this from now on", an entry appears for  that type of file in the Firefox [Applications panel]("http://support.mozilla.com/en-US/kb/Options%20window%20-%20Applications%20panel"), shown below. 

Only problem - re the last line - I tried doing the above and an entry DID NOT appear!!!

E

---

### Post by eamonnfpc on 2010-12-15
> **sikander3786 said:**
> Welcome to the forums?

Is VLC installed and is it able to play mp3 files?

Sir yes Sir! ;)

---

### Post by sikander3786 on 2010-12-15
Type this in your Web Browser's address bar.

```
about:plugins
```

Is VLC listed there?

There is a package in Software Center named mozilla-plugin-vlc. You can try installing that. However that is not installed on my system and yet I have VLC plugin in my Firefox.

The only thing I installed was ubuntu-restricted-extras to get all the codecs for audio/video.

---

### Post by eamonnfpc on 2010-12-15
Yes it is...
application/x-vlc-plugin VLC Multimedia Plugin Yes   
application/vlc VLC Multimedia Plugin Yes   
video/x-google-vlc-plugin VLC Multimedia Plugin Yes
I also ran the same command you did for restricted. Tell a lie, I added it to the sources.list as per a suggestion in another forum.
Thanks, E

btw, I installed the vlc browser plugin too. Didn't work. Thanks for the suggestion though.

---

