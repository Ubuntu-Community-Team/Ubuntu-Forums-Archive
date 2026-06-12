---
title: "ADB setup with Samsung Captivate"
date: 2010-11-16
forum: General Help
---

### Post by smurfgod on 2010-11-16
I have tried everything to get this to work.

I've googled all day, ran every command, followed every guide and still can't get adb to be a recognized command.

I had it up and running in Windows for my G1 but now I need it in Ubuntu x64 for my Captivate. I'm slowly making a switch from M$ to Ubuntu and this is something holding me back.

I have my sdk folder and the Eclipse folder in my Applications folder in my Home folder, as well as my home folder(just to be safe)

I have started the Android in sdk/tools and gotten all my updates and have successfully ran the Eclipse IDE...I just can't get adb to run.

The file people have been saying to add to the file..this is what I added

export  PATH=${PATH}:$HOME/SDK/android-sdk-linux_86/
export  PATH=${PATH}:$HOME/SDK/android-sdk-linux_86/platforms/android-2.0.1/tools/
export  PATH=${PATH}:$HOME/SDK/android-sdk-linux_86/tools/

I can drag and drop the adb file from the tools folder into terminal and it will run, but once I start adb devices, it says it's not a command.

I'm trying to mainly use the adb install command and adb reboot recover/download commands


Any help?? I'm comfortable with Terminal, and am trying to learn, so termianl commands are a plus..lol

Thanks

---

