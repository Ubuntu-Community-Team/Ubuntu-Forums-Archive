---
title: "login screen"
date: 2011-03-06
forum: General Help
---

### Post by mmsmc on 2011-03-06
how do o change what my login screen looks like?

---

### Post by capn.hector on 2011-03-06
system -> administration -> login screen  but it depends on what you want to do with it

---

### Post by mmsmc on 2011-03-06
im looking to change the background of the login screen

---

### Post by mmsmc on 2011-03-06
*bump*

---

### Post by vivek.pandey on 2011-03-06
Method 1:
1. Go to console by pressing Ctrl+Alt+F1, then you have to login with your sudoer username
2. Then after logging in, type: “export DISPLAY=:0.0” (without quotes) then press enter.
3. After that, type : “sudo -u gdm gnome-control-center” (without quotes) and press enter, it will show a pop-up window, choose Appearance>Backgrounds –then simply  choose your image file.

Method 2:
1. Move your favorite login wallpaper to your Home folder. Make sure that it is of .JPG format.
2. Move the wallpaper to the system wallpaper directory. In the terminal:&#65279;
sudo mv ~/your-wallpaper-name.jpg /usr/share/backgrounds
3. Activate the Appearance window upon login
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

4. Close the terminal. Log out of  your current session. At the login screen, the Appearance window will show up. Go to the background tab and select your favorite wallpaper as the background. (If you can’t find your favorite wallpaper, click Add. You should be able to find your wallpaper in the /usr/share/backgrounds directory).

5. Your login background will instantly change to the wallpaper you have selected. Now login to your account.
6.  Open terminal. Type the following command to deactivate the Appearance window upon login.
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

Method 3: 
1. This is the most simple method. First you should install Ubuntu Tweak. Open the terminal and type
sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update
sudo apt-get install ubuntu-tweak&#65279;
2. Then access it through Applications &#8594; System Tools &#8594; Ubuntu Tweak
3. When Ubuntu tweak opens go to login settings and click unlock and enter your password when prompted


4. Click the button to change the login background

---

### Post by mmsmc on 2011-03-06
thanks man, very informative

---

