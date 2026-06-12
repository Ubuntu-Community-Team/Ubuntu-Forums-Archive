---
title: "Root uses different theme?"
date: 2010-06-04
forum: General Help
---

### Post by X-Windows on 2010-06-04
Interesting issue here, after installing a new theme all programs run with root privileges use a different theme. Below is an example screenshot, everything root does is running with what I assume is the default theme. Any idea how to fix this? 

Ubuntu 10.4 Lucid

---

### Post by bodhi.zazen on 2010-06-04
Do not run X as root, it is a bad habit.

---

### Post by rhysforge on 2010-06-04
like he said,   but in general     

DON'T RUN AS ROOT.

---

### Post by Woody1987 on 2010-06-04
> **bodhi.zazen said:**
> Do not run X as root, it is a bad habit.

I dont think he is. Applications which require root privileges have a different theme for him. Personally I do not suffer from this, all my applications regardless of privilege has the same theme.

What you could do is log in as root, set the theme, then return to normal user. I think this will make root apps have the correct theme.

---

### Post by X-Windows on 2010-06-04
Yes, I am not running as root, but applications that I have to "sudo" all use the default theme. Could someone explain how to log in as root? I have avoided it in general as it could make more trouble than it's worth, but if it is as simple as logging in and using a different theme it shouldn't be too bad.

---

### Post by stinkeye on 2010-06-04
Make all your themes fonts and icons installed in your home folder
available to root
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

---

### Post by Woody1987 on 2010-06-04
> **X-Windows said:**
> Yes, I am not running as root, but applications that I have to "sudo" all use the default theme. Could someone explain how to log in as root? I have avoided it in general as it could make more trouble than it's worth, but if it is as simple as logging in and using a different theme it shouldn't be too bad.

Log out, and in the username field enter root, and the password is the sudo password. Then set the theme you want to use. Log out and back in as the normal user and may make sudo apps have the correct theme. Im not totally sure on this, it wouldnt hurt to try it. This method would need to be repeated for any theme changes you make.

---

### Post by Woody1987 on 2010-06-04
Or do as stinkeye suggested.

---

### Post by X-Windows on 2010-06-04
> **stinkeye said:**
> Make all your themes fonts and icons installed in your home folder
available to root
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```


Thanks, that fixed it. You are genius! :P

Edit: Thanks for how to log in as root. I thought it was some cryptic terminal entry. You learn something new every day here at the forums!

---

### Post by stinkeye on 2010-06-04
> **X-Windows said:**
> Thanks, that fixed it. You are genius! :P

Yes I am a copy and paste genius. :P

---

### Post by sdennie on 2010-06-04
Linking something from /root into your home directory is a very bad idea from a security standpoint.  You can get the same behavior but at less risk with:

```

sudo cp -R ~/.themes /root
sudo cp -R ~/.icons /root
sudo cp -R ~/.fonts /root

```

Even that is only slightly better.  I'd say, 1) Why are you using so many programs as root that you even notice the theme is different?  2) If you are using enough programs as root to notice it, having it be different is likely to save you a lot of heartache because you will think twice about doing things in the differently themed windows.  3) What bodhi.zazen said.

---

