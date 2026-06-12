---
title: "hp netbook help"
date: 2012-05-19
forum: General Help
---

### Post by fabulouskilljoy on 2012-05-19
I have a hp mini 210-4100

I just installed ubuntu 12.04 
and the issue is with my brightness
there is no option im stuck at the default brightness
and the other issue is with my mouse flickering when I move it

any help would be appreciated :)

---

### Post by celldweller1591 on 2012-05-19
have you tried installing additional graphic drivers for your system ? Please give info about your system. For the time being try this - 
Method I
  
[LIST=1]
[*]Click the icon at the very right of the panel and select System Settings.
[*]In the Hardware section, click Power Management.
[*] Adjust the Set display brightness slider to a comfortable value.
 Many laptop keyboards have special keys on the keyboard to adjust the brightness.     These are usually located on the F8 and F9 keys. Hold     down the Fn key to use these keys.
[/LIST]
 Method II

First edit xorg.conf in terminal with the command:
> sudo gedit /etc/X11/xorg.conf  And then find the Section &#8220;Device&#8221; and add the bold line.
> 
[I]Section &#8220;Device&#8221;
Identifier    &#8220;Default Device&#8221;
Option     &#8220;NoLogo&#8221;     &#8220;True&#8221;
**Option &#8220;RegistryDwords&#8221;    &#8220;EnableBrightnessControl=1&#8243;**[/I] [I]
EndSection[/I]

  And now your brightness control is working in next login! And from next time please search the forum before posting your problems :)

---

### Post by fabulouskilljoy on 2012-05-19
[IMG]http://s3.kkloud.com/gett/4Jz5tuH/Screenshot%20from%202012-05-20%2004%3A43%3A50.png.0x675.fb1uhg1e4e2buik9e8w2xchl6ry66r.png[/IMG]

I don't have a brightness option

---

### Post by HermanAB on 2012-05-20
When all else fails, use xrandr to adjust the brightness.  Read the man page.

---

