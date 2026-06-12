---
title: "All link open in Chrome/ium but FF is default"
date: 2010-12-11
forum: General Help
---

### Post by drewsus on 2010-12-11
Hello all,

I have Ubuntu 10.10 with Firefox 3.6.13 and Chromium 8.0.552.215 (67652). 

Whenever I click on a link (like in Emesene or OpenOffice) it opens it in Chromium. Firefox is set as my default browser and html files are set to open with FF in nautilus. 

Anyone know how I can go about fixing this? 

Thanks, 
Drew

---

### Post by miegiel on 2010-12-11
> **drewsus said:**
> Hello all,

I have Ubuntu 10.10 with Firefox 3.6.13 and Chromium 8.0.552.215 (67652). 

Whenever I click on a link (like in Emesene or OpenOffice) it opens it in Chromium. Firefox is set as my default browser and html files are set to open with FF in nautilus. 

Anyone know how I can go about fixing this? 

Thanks, 
Drew

I get that too somtimes, but the other way around. It used to happen with every link. The way I solved it was by right clicking a *.htm* and a *.html* file in thunar (nautilus for you) choose *properties* and change the *open with* setting to chromium (firefox for you).

---

### Post by drewsus on 2010-12-11
> Firefox is set as my default browser and html files are set to open with FF in nautilus

Nah, I already have that. It was the first thing I checked, too. But thank you for your suggestion!

---

### Post by miegiel on 2010-12-11
> **drewsus said:**
> Nah, I already have that. It was the first thing I checked, too. But thank you for your suggestion!

Did you try *system -> preferences -> preferred applications* ?

---

### Post by drewsus on 2010-12-11
atta boy! 
It was set to **Custom** and then *sensible-browser*.

Thank you sir! You are a gentleman and a scholar. 

Now, how is it that the default browser is not considered the sensible choice for the system?

---

### Post by drewsus on 2010-12-11
Hmm. I ran:
```
sudo update-alternatives --config x-www-browser
```

and it turns out chromium was set to the default. Odd. Very odd as I know that on both of my computers that I chose not to have chromium as the default when asked, yet it set it as it anyway.

---

### Post by miegiel on 2010-12-11
> **drewsus said:**
> atta boy! 
It was set to **Custom** and then *sensible-browser*.

Thank you sir! You are a gentleman and a scholar. 

Now, how is it that the default browser is not considered the sensible choice for the system?

You're welcome :D

Don't know, but I've got a feeling not every program is using a central/unified (sensible?) default browser setting.

---

### Post by miegiel on 2010-12-11
> **drewsus said:**
> Hmm. I ran:
```
sudo update-alternatives --config x-www-browser
```

and it turns out chromium was set to the default. Odd. Very odd as I know that on both of my computers that I chose not to have chromium as the default when asked, yet it set it as it anyway.

Thanks, I just did that too. Maybe now, links will open chromium for me every time.

---

### Post by drewsus on 2010-12-11
I truly love when someone asks for help and both parties end up learning something.

---

### Post by AldenIsZen on 2011-01-05
> **drewsus said:**
> Hmm. I ran:
```
sudo update-alternatives --config x-www-browser
```and it turns out chromium was set to the default. Odd. Very odd as I know that on both of my computers that I chose not to have chromium as the default when asked, yet it set it as it anyway.
  What is even more odd is when I set it using that command, it still said custom in preferred applications, but the command was blank after that. I changed in via preferred apps to be sure. Why does one not reflect the other???

---

### Post by pwk on 2011-01-25
I fixed the Chrome as default problem in Xubuntu by installing Chromium instead.

I had already installed Opera which overwrote my /usr/bin/x-www-browser file with
```
#!/bin/sh
export OPERA_DIR=${OPERA_DIR:-/usr/share/opera}
exec /usr/lib/opera/opera "$@"
```

To get Firefox back as the default for Evolution I copied x-www-browser to x-www-browser.opera, commented out the Opera lines in x-www-browser and added ```
exec /usr/bin/firefox "$@"
```

I now launch Opera from an icon with the command```
/usr/bin/x-www-browser.opera
```

Why did I want Chromium? I couldn't get Opera 11 to work with Privoxy running on an IPv6 localhost address (::1) -- it just wouldn't accept it. But then I discover that to get Chromium to connect to a proxy it needs to be launched from the command line. Ugh. So I now run Chromium from an icon with ```
/usr/lib/chromium-browser/chromium-browser --proxy-server=::1:8118
```

---

