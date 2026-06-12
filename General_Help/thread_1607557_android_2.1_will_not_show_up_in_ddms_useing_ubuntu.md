---
title: "android 2.1 will not show up in ddms useing ubuntu 9.10"
date: 2010-10-27
forum: General Help
---

### Post by darksourcetech on 2010-10-27
i have a samsung acclaim with android 2.1 eclair on it 

im trying to link it to my computer for dev purposes and screenshots
everytime i link it to the computer and load ddms it doesnt show up....i dont know if i did something wrong 

the computer im useing is a Dell Latitude D500 Ubuntu 9.10

any help is great

---

### Post by Steve2009 on 2010-10-27
Open the terminal and try cd'ing into the tools directory of your Android SDK folder. Plug your phone in, make sure you enter debug mode, then do 
```
sudo ./adb kill-server
sudo ./adb start-server

```in your Ubuntu terminal. 

Then
```
./adb devices
```If all goes well, your phone will show up in the devices list after that command. You should then be able to use ddms.

---

### Post by darksourcetech on 2010-10-27
i did as you said and got 


```
burningrage@burningrage-laptop:~/android-sdk-linux_x86$ 
burningrage@burningrage-laptop:~/android-sdk-linux_x86$ adb kill-server
burningrage@burningrage-laptop:~/android-sdk-linux_x86$ adb start-server
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
burningrage@burningrage-laptop:~/android-sdk-linux_x86$ adb devices
List of devices attached 
????????????	no permissions
```

---

### Post by Steve2009 on 2010-10-27
Don't forget the "sudo" before ./adb start-server and ./adb kill-server. You'll have to enter your password after the first one.

```
sudo ./adb start-server
sudo ./adb kill-server
```

---

### Post by darksourcetech on 2010-10-27
i tried that but cannot get it to do anything forgive my lack of know-how im still new to linux

cd'ing a directory is
cd /<pathway>

but when i put in 
sudo ./adb kill-server   i get

```
burningrage@burningrage-laptop:~/android-sdk-linux_x86$ sudo ./adb kill-server
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sudo: command not found
```

---

### Post by darksourcetech on 2010-10-27
well now there is a new problem everytime i enter any form of command i get the same message as above nomatter what it is i enter 

anyone know how to fix

---

### Post by Steve2009 on 2010-10-27
I have no idea why sudo isn't working like it should (I'm fairly new to Linux myself). Simply restarting the terminal might do it, but I'm not sure. Hopefully someone will see this and help out with that. For now, entering
```

cd ~/android-sdk-linux_x86/tools
/usr/bin/sudo ./adb kill-server
/usr/bin/sudo ./adb start-server 

```should at least get ddms to work.

---

### Post by darksourcetech on 2010-10-27
IT WORKED!!!!!!!

thank you for your help

one last ? 
will i have to do that everytime i connect it to the computer

---

### Post by Steve2009 on 2010-10-27
No problem. Unfortunately, yes, it does have to be done whenever you want to connect your phone.

---

### Post by gnorsilva on 2010-10-30
Hi,

This shows how to have it done automatically every time you connect your device:

[https://help.ubuntu.com/community/AndroidScreenshots](https://help.ubuntu.com/community/AndroidScreenshots)

---

