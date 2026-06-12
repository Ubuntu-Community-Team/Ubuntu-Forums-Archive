---
title: "Spotify in wine"
date: 2010-08-18
forum: General Help
---

### Post by Snapdragon19 on 2010-08-18
I'd like to note that i'm very new to Ubuntu so this is probably a stupid question. I have set up and configured wine according to [_these instructions_]("http://www.spotify.com/int/help/faq/wine/#install-and-configure-wine") but when i try to open Spotify i get this error message: The file '/home/daniel/Desktop/Spotify Installer.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit. How do i mark it as executable i.e. make it work?

---

### Post by realzippy on 2010-08-18
run

```
chmod +x /home/daniel/Desktop/Spotify Installer.exe
```

to make it executeable;check the path if it is correct

---

### Post by Smart Viking on 2010-08-18
The above command will fail, run this instead:
```
chmod +x "/home/daniel/Desktop/Spotify Installer.exe"
```

When you have launched that command, you can try to install again.:)

---

### Post by emra2emra on 2010-08-18
[http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/)

---

### Post by Snapdragon19 on 2010-08-18
> **realzippy said:**
> run

```
chmod +x /home/daniel/Desktop/Spotify Installer.exe
```

to make it executeable;check the path if it is correct

chmod: cannot access `Installer.exe': No such file or directory :(

---

### Post by Snapdragon19 on 2010-08-18
> **emra2emra said:**
> [http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/)

Unfortunately that version is only available to Spotify premium subscribers and i am not among them.

---

### Post by howefield on 2010-08-18
Right click the exe file, and select properties. Go into the permissions tab and mark Allow executing as program.

PS.
In the command above, you would need to escape the space in the filename.

---

### Post by realzippy on 2010-08-18
> **Snapdragon19 said:**
> chmod: cannot access `Installer.exe': No such file or directory :(

 **Sorry**,thought Smart Viking corrected my missing "  "
The correct one:

```
chmod +x "/home/daniel/Desktop/Spotify Installer.exe"
```

---

### Post by Snapdragon19 on 2010-08-18
> **howefield said:**
> Right click the exe file, and select properties. Go into the permissions tab and mark Allow executing as program.

PS.
In the command above, you would need to escape the space in the filename.

OK i managed to start the program and log in no problem but when i tried to play some music i got this: There is a problem with your sound card. Spotify can't play music. Edit: I checked and wine is configured right and there are no drivers to download.

---

### Post by realzippy on 2010-08-18
Now it is a "wine" sound topic and you have to make a new thread in the wine section  ;-)

---

### Post by howefield on 2010-08-18
> **Snapdragon19 said:**
> OK i managed to start the program and log in no problem but when i tried to play some music i got this: There is a problem with your sound card. Spotify can't play music. Edit: I checked and wine is configured right and there are no drivers to download.

Try going into wine configuration and selecting a different sound driver. Mine works with Alsa but the Spotify help pages suggest the OSS driver.

---

### Post by Snapdragon19 on 2010-08-18
> **howefield said:**
> Try going into wine configuration and selecting a different sound driver. Mine works with Alsa but the Spotify help pages suggest the OSS driver.

It is set to the OSS driver but i tried Alsa and it didn't work either.

---

### Post by howefield on 2010-08-18
Might be worth updating your version of Wine, the current stable version is 1.2 whereas the version you have sounds like 1.1.42, given the instructions that you followed.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Snapdragon19 on 2010-08-18
> **howefield said:**
> Might be worth updating your version of Wine, the current stable version is 1.2 whereas the version you have sounds like 1.1.42, given the instructions that you followed.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I'm pretty sure it's up to date seeing as i downloaded it yesterday. I think it's far more likely that my instructions are out of date.

---

### Post by howefield on 2010-08-18
> **Snapdragon19 said:**
> I'm pretty sure it's up to date seeing as i downloaded it yesterday. I think it's far more likely that my instructions are out of date.

The instructions you followed installed the version of Wine from the Ubuntu repository, which at the latest will be 1.1.42, assuming that you are running Ubuntu 10.04. If you are running an earlier version of Ubuntu, your Wine version will be even further back along the evolutionary scale. 

As I said,  the current stable version of Wine is 1.2, available by adding the Wine repository to your sources.list.

Have fun.

---

### Post by Snapdragon19 on 2010-08-18
> **howefield said:**
> The instructions you followed installed the version of Wine from the Ubuntu repository, which at the latest will be 1.1.42, assuming that you are running Ubuntu 10.04. If you are running an earlier version of Ubuntu, your Wine version will be even further back along the evolutionary scale. 

As I said,  the current stable version of Wine is 1.2, available by adding the Wine repository to your sources.list.

Have fun.

Did that, tried to play a song, got the same error. :sad:

Update: i restarted Spotify and now it works! I feel so silly. Thanks for all your help.

---

