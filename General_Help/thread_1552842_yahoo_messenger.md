---
title: "yahoo messenger"
date: 2010-08-14
forum: General Help
---

### Post by red eagle on 2010-08-14
please help me in downloading yahoo messenger i need it please help
i saw the lesson but i couldn't apply it good [COLOR=Red]so can anyone make the lesson in pictures[/COLOR] please help me from the beginning, and thank you.

---

### Post by viralmeme on 2010-08-14
> **red eagle said:**
> please help me in downloading yahoo messenger

[http://www.technixupdate.com/download-yahoo-messenger-for-ubuntu-linux-with-webcam-voice-chat-photo-sharing-support/](http://www.technixupdate.com/download-yahoo-messenger-for-ubuntu-linux-with-webcam-voice-chat-photo-sharing-support/)

---

### Post by red eagle on 2010-08-14
thank you, but i have a problem with the bath can you type for me the command with the bath
it is downloaded in the downloads folder please help me

---

### Post by Smart Viking on 2010-08-14
> **red eagle said:**
> thank you, but i have a problem with the bath can you type for me the command with the bath
it is downloaded in the downloads folder please help me

Did you get stuck with this command "sudo dpkg -i /path/ymessenger_1.0.4_1_i386.deb"? If it is on the download folder, do this:

```
sudo dpkg -i ~/Downloads/ymessenger_1.0.4_1_i386.deb
```

If you have another language on your system, replace "Downloads" with what the folder is called on your language. :)

---

### Post by red eagle on 2010-08-14
thank you but it gave me an error see the terminal
> Selecting previously deselected package ymessenger.
(Reading database ... 
dpkg: warning: files list file for package `blender' missing, assuming package has no files currently installed.
(Reading database ... 164630 files and directories currently installed.)
Unpacking ymessenger (from .../ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

please help me

---

### Post by Smart Viking on 2010-08-14
I am using fedora right now, so i don't know if those packages is in the default ubuntu repos, you could try to launch the following command to see if they are. If they are all in the repos, install them and then launch the other command again. (Theres a good chance they are not in the repos)

```
sudo apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 libssl0.9.6 xlibs
```

---

### Post by red eagle on 2010-08-14
thank u but it didn't work :(

---

### Post by pbrane on 2010-08-14
The instructions at that link are pretty straight forward.
What OS are you using? Intrepid, Jaunty? 32-bit or 64-bit? There are no *official* versions for ubuntu. Are you trying to use the Gyachi versions?

---

