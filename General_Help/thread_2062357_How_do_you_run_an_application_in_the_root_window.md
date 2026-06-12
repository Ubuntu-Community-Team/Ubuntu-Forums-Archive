---
title: "How do you run an application in the root window?"
date: 2012-09-24
forum: General Help
---

### Post by Cavaticus on 2012-09-24
I had no idea where to post this question, so I put it in "General Help"

I am trying to create a kiosk of sorts using Ubuntu as a base OS and Openbox as the window manager. I was wondering how to set Firefox to start in the root window when startx is run from command line after logging in.

I have tried modifying
/etc/xdg/openbox/autostart
by adding
/usr/bin/firefox -root &
to the script, but I am getting nowhere with this endeavor.

I have tried scouring Google and multiple forums for the past few hours and have only turned up dead links and unhelpful information.

Can someone please clarify what I am doing wrong?

---

### Post by wojox on 2012-09-24
Why do you feel it's necessary to run Firefox as root? Just run it as a normal user.

---

### Post by MG&amp;TL on 2012-09-24
> **wojox said:**
> Why do you feel it's necessary to run Firefox as root? Just run it as a normal user.

He means the root window, which is X.org terminology for the desktop, or fullscreen.

---

### Post by jerrrys on 2012-09-24
> **MG&TL said:**
> He means the root window, which is X.org terminology for the desktop, or fullscreen.

So is this whats up here?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=open+run+firefox+in+root&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=open+run+firefox+in+root&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by wojox on 2012-09-24
> **MG&TL said:**
> He means the root window, which is X.org terminology for the desktop, or fullscreen.

:lolflag: not root user, I see know.

What about an addon [R-kiosk]("https://addons.mozilla.org/en-US/firefox/addon/r-kiosk/")

---

### Post by Cavaticus on 2012-09-24
> **jerrrys said:**
> So is this whats up here?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=open+run+firefox+in+root&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=open+run+firefox+in+root&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Not running "as" root, just in the "root window" like as the desktop background.

I have seen tutorials showing how to run feh, xscreensaver, and a few others, but the process doesn't seem to work with firefox, or maybe I am missing something.

---

### Post by Cavaticus on 2012-09-24
I'll take a look at R-kiosk. Thanks!

---

### Post by Cavaticus on 2012-09-24
Wojox, it would almost work except  the only problem with r-kiosk that I can see is that I will be needing to launch a separate instance of firefox while the kiosk is running and the addon will affect that one as well.

Thanks for trying tho! :)

---

### Post by newb85 on 2012-09-24
I'm not sure what you mean by a kiosk "of sorts", but you may want to check out [http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/]("http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/").
It's more involved and more comprehensive.

---

### Post by Cavaticus on 2012-09-24
> **newb85 said:**
> I'm not sure what you mean by a kiosk "of sorts", but you may want to check out [http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/).
It's more involved and more comprehensive.

@newb85: That article had good info in it. I think I'm gonna abandon the whole run in "root window" idea and combine what you and wojox have posted to this thread.

Thanks a bunch! :)

---

