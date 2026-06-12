---
title: "No new interface after upgrading to Natty"
date: 2011-04-28
forum: General Help
---

### Post by wojcianiu on 2011-04-28
Hello,
I've upgraded from beta to stable release of Ubuntu 11.04, but I can't see this interface:
[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty-consumer-pages/whatsnew-launcher.jpg[/IMG]
I still have this:
[IMG]https://picasaweb.google.com/lh/photo/EkihmUTUDumGpulhWfGWKukoa2eyYbV95JojKKRnal8?feat=directlink[/IMG][IMG]https://lh4.googleusercontent.com/_oixuPyzXhmk/TbmbKaGdgWI/AAAAAAAAADo/-Gi7tKqwC4w/s800/zrzut_ekranu.png[/IMG]
Why? How to "upgrade" it?:) Please help me.

---

### Post by grahammechanical on 2011-04-28
At the log in screen look at the bottom panel and you will see an option to choose your desired interface. There is a list. You can only do this at log in.

Regards.

---

### Post by Rascal74 on 2011-04-28
Hello,
Same problem here.
It looks like my video card is not recognized.
I have Geforce 8400GS (MSI).
Running from persistent live usb.

@[grahammechanical]("http://ubuntuforums.org/member.php?u=1087323") : I don't get this login screen, and when I try to switch user ubuntu I don't get the option to choose the desired interface.

---

### Post by Peter09 on 2011-04-28
Have you installed the nvidea driver?

---

### Post by wojcianiu on 2011-04-28
> **grahammechanical said:**
> At the log in screen look at the bottom panel and you will see an option to choose your desired interface. There is a list. You can only do this at log in.

Regards.
So, I'm the only one user of this computer and I've ticked to not display the login screen. And, if I want to unlock the settings of this screen, if I press "Unlock" nothing's doing. Is there other method to turn it on? In Update manager if I click "Install updates" nothing's doing too. What's that?!

---

### Post by Peter09 on 2011-04-28
On the power button (shutdown) in the top right there is an option to logout, this will get you to the login screen and the options you need.

---

### Post by wojcianiu on 2011-04-28
> **Peter09 said:**
> On the power button (shutdown) in the top right there is an option to logout, this will get you to the login screen and the options you need.
There are only 3 options:
* Next power button
* Date
* Magnifier etc.
This is shown if I don't click my username. If I do it, I go to my account because I've setted to not ask for a password. And, once again, I can't change that option:mad:.

---

### Post by Peter09 on 2011-04-28
Try Cntrl-Alt-Delete and select logout from there

---

### Post by Rascal74 on 2011-04-28
It doesn't work.

---

### Post by wojcianiu on 2011-04-28
> **Peter09 said:**
> Try Cntrl-Alt-Delete and select logout from there
There isn't an option to log out. I can't reinstall Ubuntu because it works only installed through Wubi and Windows doesn't work and I don't have Windows install CD.

---

### Post by Peter09 on 2011-04-28
You should click the powerbutton to start the shutdown, it should give you an option to logout/shutdown.

---

### Post by wojcianiu on 2011-04-28
> **Peter09 said:**
> You should click the powerbutton to start the shutdown, it should give you an option to logout/shutdown.
No, it shuts down the computer automatically, any window appeared (except the first with power down, reboot etc. :)).

---

### Post by Rascal74 on 2011-04-28
Same for me. The only option to log out is located in the system menu.
But in the login screen there is no option/list to choose the interface. Ok ?

---

### Post by Rascal74 on 2011-04-28
I wanted to test the new unity interface, but unity doesn't want me to test it.
I guess this new ubuntu is not for me...

---

### Post by Natpjohnson on 2011-04-28
I'm getting this problem as well and I have installed the recommended nvidia graphics driver for my system. At the log in screen I see no option for choosing which design I want. After the first log in though, I got an alert telling me me hardware was not up to the requirements, but I looked through the requirements and I totally meet them. After installing the driver I never got that alert again.

---

### Post by wojcianiu on 2011-04-29
I think GDM is a problem so I try to install the beta of it, but I can't compile the package because it needs "X Development Libraries". What package should I install? (Is GDM a problem?:))

---

### Post by sikander3786 on 2011-04-29
Press Ctrl + Alt + F1 at the desktop. Login to tty1 using your credentials then

```
sudo service gdm stop
sudo service gdm start
```

Click your username. Don't type the password yet. Sessions menu will appear in the bottom. Can you please post which options have you got there?

For Unity, you need to choose 'Ubuntu' and login.

---

### Post by wojcianiu on 2011-04-29
> **sikander3786 said:**
> Press Ctrl + Alt + F1 at the desktop. Login to tty1 using your credentials then

```
sudo service gdm stop
sudo service gdm start
```Click your username. Don't type the password yet. Sessions menu will appear in the bottom. Can you please post which options have you got there?

For Unity, you need to choose 'Ubuntu' and login.
It logged me in automatically after "sudo service gdm start". What are X development libraries?

---

### Post by wojcianiu on 2011-04-29
I know why I can't see the new interface. Ubuntu (Safe mode) is choosed to load at every start, but I can't unlock these settings in log in setup menu to change this setting.

---

### Post by sikander3786 on 2011-04-29
What happens when you try to unlock the login screen preferences window?

---

### Post by wojcianiu on 2011-04-29
> **sikander3786 said:**
> What happens when you try to unlock the login screen preferences window?
Nothing

---

### Post by wojcianiu on 2011-04-29
**I have found the solution (!),...**
My own method:
Log out from your account and choose Other in a window with users. Write "kluser" and press OK. Now, at the bottom of the screen, you can see the options. Choose "Ubuntu" and in a window press "Cancel". Log in using your username. You should see Unity now.
**...but**
After doing what's above, new window appeared:
```
Your hardware doesn't support Unity. Choose Classic Ubuntu at log in screen.
```:mad::mad::mad::mad::mad::mad::mad::mad:
And thousands of windows appeared with message: "Could not acquire name on session bus"

---

