---
title: "Cannot Mount iPod, help please"
date: 2012-02-21
forum: General Help
---

### Post by GGGlenn on 2012-02-21
Hi all, I recently updated my iPod iOS to 5.0.1 and now when I plug it in I get 

Unable to mount Dzyan
Unhandled Lockdown error (-4)

I have tried installing iFuse and libimobile, but cannot get it to run. I had no problems on my old iOS 4.3 something.

I'm reasonably new to anything other than windows, so please speak stupid at me

Thanks

---

### Post by bluexrider on 2012-02-22
Found this which may prove itself to work for you 


[LIST=1]
[*]Open terminal, write it: [FONT=Monaco]```
sudo add-apt-repository ppa:mcenery/ppa
```[/FONT]
[*]And that, write it: [FONT=Monaco]```
sudo apt-get update
```[/FONT]
[*]After that, write it: [FONT=Monaco]```
sudo apt-get upgrade
```[/FONT]
[*]Now, you need to install ifuse. Write it:  ```
sudo apt-get install ifuse
```
[*]First tool, write it: [FONT=Courier 10 Pitch]```
sudo apt-get install libimobiledevice2
```[/FONT]
[*]Second tool, write it: [FONT=Courier 10 Pitch]```
sudo apt-get install libimobiledevice-utils
```[/FONT]
[*]The final step, write it: [FONT=Courier 10 Pitch]```
idevicepair unpair && idevicepair pair
```[/FONT]
[/LIST]




[http://fuelledbykrawu.wordpress.com/2011/10/29/how-to-fix-unhandled-error-lockdown-in-ubuntu-while-attempting-to-mount-an-ios5-device/](http://fuelledbykrawu.wordpress.com/2011/10/29/how-to-fix-unhandled-error-lockdown-in-ubuntu-while-attempting-to-mount-an-ios5-device/)

unplug and replug your iDevice

---

### Post by GGGlenn on 2012-02-22
Thats got it mate, 

thanks very much

---

