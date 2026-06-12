---
title: "Internet works only with root permission to browser!"
date: 2010-10-01
forum: General Help
---

### Post by mayankbhagya on 2010-10-01
I connect to internet using a USB stick.

After the connection is established, I can access internet only when I run the browser with root permissions ('sudo').

I enabled:
'Use modems'
'Connect to internet using a modem'
in the 'User privileges' tab for my user.

Any suggestions?

---

### Post by wojox on 2010-10-01
Check out the [First Symptom]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html") here.

---

### Post by mayankbhagya on 2010-10-02
Thanks for the response.

But it isn't a browser issue.
Because when I connect to internet using my ethernet adapter, it works fine. (I don't need to add sudo to firefox or chrome!)

But in case of dial up usb stick modem, it just doesn't work!
I tried adding myself to dialout and dip groups too..

Nothing seems to work!

---

### Post by Rubi1200 on 2010-10-02
Perhaps consider reinstalling Firefox? Clearly, running a browser with root privileges is not advisable. Something with permissions must have got changed?

---

### Post by mayankbhagya on 2010-10-02
Restarting a browser shouldn't help because this happens with both Firefox and Chrome.

Moreover, the browsers do not bother me when I'm connected using ethernet card rather than the modem!

As far as I think, it's something to do with the usb stick modem permisisons.

Anyone?

---

### Post by garvinrick4 on 2010-10-02
What does permissions say in .mozilla

---

### Post by gandaran on 2010-10-02
> **mayankbhagya said:**
> I connect to internet using a USB stick.

After the connection is established, I can access internet only when I run the browser with root permissions ('sudo').

I enabled:
'Use modems'
'Connect to internet using a modem'
in the 'User privileges' tab for my user.

Any suggestions?
is this USB stick wlan wireless internet or mobile broadband internet?
and how did you do the connection setup, wouldn't the setup work without adding it to the user privileges?

---

### Post by mayankbhagya on 2010-10-02
@garvinrick4
All files in .mozilla are under my ownership with full permissions.

@gandaran
The USB stick is a mobile broadband.
The stick had a bash script which took care of the installation and has installed a GUI which can now be used to connect/disconnect.

The GUI has quick links to a few websites which, when clicked, open the browser with root permissions. Internet works in that browser but doesn't work in any other browser window I open (without sudo).

Also, I had run the setup script with sudo.

---

