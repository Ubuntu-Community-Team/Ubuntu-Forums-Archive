---
title: "Print Screen for Remote Desktop"
date: 2010-07-07
forum: General Help
---

### Post by jack frost on 2010-07-07
I was going to put this under Networking; but went ahead and put here. I have an issue when I am on VPN and connected remotely to my work computer. At work we have xp and when I need to do a print screen within windows  using the print screen key it will completely freeze up the gnome remote desktop window session I am in. I do get the pop up to save to clipboard; but when I choose that option it completely freezes my RDP connection to my work and have to close out the browser window and re-connect.  

I have also tried choosing save; but it wants to save the image to my ubuntu host and the windows remote environment doesn't even seen to acknowledge that I hit the print screen key.  I go to paint right after; but there is no option to paste. It is like the ubuntu host takes over the print screen key even though I am doing it inside the remote windows session.

I want to be able to take a screen shot within the remote session at work (windows) for error screen shots etc. and paste them in paint in the remote session. Any help is appreciated. Thanks.

---

### Post by Shompol on 2010-07-07
I use rdesktop for VPN. It seems to be a much better virtual environment -- feels like you are sitting at the remote terminal. 

A much easier solution for you: don't use the Print Scrn key! There are much better options out there: download any freeware screen capture utility off tucows, like this one: [http://www.tucows.com/preview/515706](http://www.tucows.com/preview/515706)
and you can capture the exact area of the screen you need.

---

### Post by jack frost on 2010-07-07
> **Shompol said:**
> I use rdesktop for VPN. It seems to be a much better virtual environment -- feels like you are sitting at the remote terminal. 

A much easier solution for you: don't use the Print Scrn key! There are much better options out there: download any freeware screen capture utility off tucows, like this one: [http://www.tucows.com/preview/515706](http://www.tucows.com/preview/515706)
and you can capture the exact area of the screen you need.

thanks. I will try it out.

---

### Post by jack frost on 2010-07-10
> **jack frost said:**
> thanks. I will try it out.

thanks.. works like a charm.. install on my work machine yesterday and VPN today and tested it out.

---

