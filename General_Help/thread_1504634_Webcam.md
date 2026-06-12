---
title: "Webcam"
date: 2010-06-08
forum: General Help
---

### Post by Xavierdri on 2010-06-08
Hi

Is it possible to have a Logitech web-cam to work on Ubuntu 9.10 and if so where would I get the driver?

Regards Xavier

---

### Post by wolf_3d on 2010-06-08
Hi,

You didn't say which model exactly but my Logitech Quickcam 3000 used to work with 9.10. They are normally well supported and should run out of the box.

---

### Post by quacked on 2010-06-08
What are you trying to get the webcam to work with ? 

Have you installed  " Cheese " or some other webcam app,,, ??? 

Kopete, will work  as yahoo messenger,,,, empathy works with,,, live,,,,  Kopete also needs Jasper ,,,, to work with the IM,,,

---

### Post by Xavierdri on 2010-06-08
Cheese :confused: no I don't have any thing yet as I don't have the flintiest idea of what to do or what to use Ho yes I want to get this Logitech to work with Skype on the Lagitech doc it says QuickCam Express and on the installation CD  QuickCam 5.4.4. So I take it that I must install Cheese?  I must say that I did have a good laugh with that Cheese thing I guess that the guys that make the software for linux Have one heck of a good sense of humour I'm loving it more and more

Regards Xavier

---

### Post by radddi on 2010-06-08
I have a Logitech QuickCam Messenger and it only works when you use:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```

However, to start it up on boot or through the GUI you need to make a script and paste it into your /usr/bin directory in order to start it up with the command "skype". Open a preferred text editor and save the following as: skype

The Script:
```
#!/bin/bash
#
#~/bin/skype_mod.sh
#
# Ensure that the LD_PRELOAD is clear
unset LD_PRELOAD

# Export LD_PRELOAD
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

# Execute Skype
exec /usr/bin/skype 

exit 0

### End of File ###
```

Then to copy it into the foulder, open a terminal and:
```
cd /usr/bin
sudo mv skype skype.backup
sudo rm skype
sudo cp /path/to/your/script/skype /usr/bin
```

Then restart Skype and check in its options whether video works.

---

### Post by Xavierdri on 2010-06-08
Thanks a lot for your help I saved it in word now I will print it and try it. I installed Cheese (it still makes me laugh) and the cam works with it so I guess that it a good sign. Man how will I ever get to know all this stuff :confused:

regards Xavier

---

### Post by radddi on 2010-06-08
Oops, I seemed to have expressed myself somewhat badly. The script has to be saved by a plain text editor such as gedit (Applications >> Accessories >> gedit Text editor). Office suites aren't good for writing scripts because they add all sorts of formatting information to the file. Open gedit and save under the name: skype - no extentions. In this way Ubuntu can read it as a script file and execute it.

> Man how will I ever get to know all this stuff

Don't worry about it. Ubuntu kind of sticks by itself. I've been an (almost) completely migrated Ubuntu user since version 8.04 - April 2008. By doing many searches on problems (especially while upgrading the OS) you will start to know your way around much better.

.:CheerS:.

---

### Post by Xavierdri on 2010-06-08
OK will do that Thanks

---

### Post by Xavierdri on 2010-06-08
Ho yes I see the text went blue and brown Now That's something else

---

### Post by Xavierdri on 2010-06-08
OK did all that BUT here is what it tells me

xavier@xavier-desktop:/usr/bin$ mv .skype.skype.backup
mv: missing destination file operand after `.skype.skype.backup'
Try `mv --help' for more information.
xavier@xavier-desktop:/usr/bin$ 

is this bad doctor

Xavier

---

### Post by radddi on 2010-06-08
You seem to have a typo. Copy the commands EXACTLY as they are written. This particular one should be:
```
sudo mv skype skype.backup
```
with spaces after 'mv' and 'skype'. This command backs up your old skype launch script in case of a future error.

.:CheerS:.

---

### Post by Xavierdri on 2010-06-08
Ok will do ok well this is what I get

xavier@xavier-desktop:/usr/bin$ sudo mv skype skype.backup
mv: cannot stat `skype': No such file or directory

Found that Skype is not in bin but I did find it here
[email]xavier@xavier-desktop:~/.Skype[/email]$

---

### Post by radddi on 2010-06-10
This is no problem. Continue with the script. :popcorn:

---

