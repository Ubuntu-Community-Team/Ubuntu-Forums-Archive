---
title: "Sudo still gives me permission denied"
date: 2011-11-05
forum: General Help
---

### Post by mendhak on 2011-11-05
Hello there, I am trying to create a file with some text in it inside rules.d

```
sudo echo SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666", OWNER="mendhak" > /etc/udev/rules.d/51-android.rules

```

So I want to write that string to the 51-android.rules file.  Whether or not I use sudo, the output is always


> 
bash: /etc/udev/rules.d/51-android.rules: Permission denied


If I gksu gedit a file there, it works just fine and I can create it.  


However, I'd like to be able to do this via a bash script.  What am I missing?

---

### Post by LowSky on 2011-11-05
try using sudo -i before issuing the command, it will place you into a root like setting so you no longer have write sudo with every command. it will last for a few minutes or until you close the terminal.
```
sudo -i

echo SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666", OWNER="mendhak" > /etc/udev/rules.d/51-android.rules
```

---

### Post by coffeecat on 2011-11-05
The problem is using a bash redirect with sudo. 

```
sudo echo *string* > /path/to/file
```

... will fail with the error you see. What you can do is:

```
echo *string* | sudo tee /path/to/file
```

I'll leave you to adapt that with your collection of strings. :wink:

Or - you can obtain a root terminal with sudo -i as LowSky suggests.

---

### Post by mendhak on 2011-11-05
Very nice, I didn't know about sudo -i.  I will add that to my script.

Both of your solutions worked, thanks very much!

---

