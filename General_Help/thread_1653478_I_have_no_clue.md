---
title: "I have no clue"
date: 2010-12-26
forum: General Help
---

### Post by ColourH3AR7 on 2010-12-26
I just installed Ubuntu 10.10, and I really have no idea how to login. When I first start it up, it is a black screen and a lot of codes and stuff pop up. It says to login, so I do, but I don't know how to get past that. How do I get to the desktop?

Edit: Please help. I have no one else to turn to...

---

### Post by amsterdamharu on 2010-12-26
I guess your video card is not supported properly and you have to do some tweaking for it to work.

Can you post the output of the following commands? (after you log in to the text only terminal)
```
sudo lshw -C video
```This should show what Ubuntu thinks is your video card, could you post that here?

Then try the following command:
```
sudo dpkg-reconfigure xorg
```Reboot and see if that helps.

If not then see if there is an xorg.conf file.
```
ls /etc/X11/xorg.conf 
```If that says:
```
ls: cannot access /etc/X11/xorg.conf: No such file or directory
```Then you cannot do the following steps but if it does try the following:
```
sudo nano /etc/X11/xorg.conf
```There are a couple of lines beginning with driver like Driver         "nvidia".
Leave the the mouse and kbd alone (if they are there because they are for the keyboard and mouse).
The driver line under "Section "Device"" should be the following:
```
Driver         "vesa"
```To save the file press control + o -> enter -> control + x
Now reboot again and see if you get a low resolution desktop. From there Ubuntu might detect your hardware so you can install it and restart with the correct drivers.

---

### Post by ColourH3AR7 on 2010-12-26
I have no idea what you are talking about.

---

### Post by amsterdamharu on 2010-12-26
You say you can log in and then have a black screen where you can type stuff right?

Then try typing the commands that I posted before, if there are any errors write them down and post them here please.

---

### Post by bodhi.zazen on 2010-12-26
> **ColourH3AR7 said:**
> I just installed Ubuntu 10.10, and I really have no idea how to login. When I first start it up, it is a black screen and a lot of codes and stuff pop up. It says to login, so I do, but I don't know how to get past that. How do I get to the desktop?

Edit: Please help. I have no one else to turn to...

Did you install the serer edition or desktop?

Either you did not install the desktop or your videocard was not recognized.

---

### Post by dcstar on 2010-12-28
> **ColourH3AR7 said:**
> I have no idea what you are talking about.

Type in the Username you created during the setup, and then the password.

Once you have logged into the text terminal you can run the commands listed previously and then post the results here.

---

### Post by supershin on 2010-12-28
Listen to dcstar. When you installed Ubuntu you had to create a username and password, use that to login.

Though it sure sounds like the server edition was installed.

---

