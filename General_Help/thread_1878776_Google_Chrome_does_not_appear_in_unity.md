---
title: "Google Chrome does not appear in unity"
date: 2011-11-10
forum: General Help
---

### Post by merry_meerkat on 2011-11-10
Hello,
I've installed google-chrome (not chromium), but it doesn't seem to work with unity.

(1) When I search for it in the unity dash (i.e. menu), it does not appear.
(2) When it is running (by starting it via Alt-F2 and typing "google-chrome"), it does not appear in the taskpanel.

Please see the attached screenshots to see what I mean.
Any suggestions on how to fix this would be very welcome.

(I'm on Ubuntu 11.10 Oneiric 64-bit)

Thanks!!

---

### Post by ProntoAnthony on 2011-11-10
how was Chrome installed? Look in your System Settings > Software Sources. Is there an entry in the Other Software tab like "http://dl.google.com/linux/chrome/deb/ stable main"?

---

### Post by merry_meerkat on 2011-11-10
> **ProntoAnthony said:**
> how was Chrome installed? Look in your System Settings > Software Sources. Is there an entry in the Other Software tab like "http://dl.google.com/linux/chrome/deb/ stable main"?

This is how I installed it:
[LIST=1]
[*]downloaded 64-bit.deb file from [http://www.google.com/chrome/](http://www.google.com/chrome/)
[*][FONT="Courier New"][SIZE="2"]sudo dpkg -i google-chrome-stable_current_amd64.deb
[*]sudo apt-get -f install[/SIZE][/FONT] 
[/LIST]

Yes, I have [FONT="Courier New"][SIZE="2"]http://dl.google.com/linux/chrome/deb/ stable main[/SIZE][/FONT] in the Other Software tab.

Thanks for any suggestions!

---

### Post by ProntoAnthony on 2011-11-10
Everything you did sounds good. The only thing you have that is different than mine is you are using the 64-bit version. Are you also using the 64-bit version of 11.10?

I've read that the 32-bit version of Ubuntu is recommended even for those with 64-bit machines. And even though I have a AMD-64 chip in my desktop I'm using the 32-bit version on both machines so I can have the same software on both the laptop and desktop.

---

### Post by merry_meerkat on 2011-11-10
This is getting more complicated. In addition to the symptoms I mention above, I also have the following behaviour:

(1) While searching in the **dash/home** (when the "home" icon is selected at the bottom of the dash), I do not find Google Chrome. But when I select **dash/applications** (the ruler, pencil and brush icon), it does appear (see screenshot). Yet, clicking on it in the dash results in nothing. The dash stays open and nothing happens.

(2) Starting Google Chrome like so: [FONT="Courier New"][SIZE="2"]Alt-F2 > google-chrome[/SIZE][/FONT] starts the browser just fine, including adding its icon to the taskpanel (launcher) as it should. However, when I now right-click on it in the taskpanel and select "Keep in launcher" it'll do the following...
[LIST]
[*]the icon does stay in the launcher and clicking it launches Chrome, but it does not indicate on the launcher that chrome is open, i.e. **no little white triangles** (see screenshot).
[*]minimising chrome and clicking the launcher icon again brings up a new chrome window and the **minimised one is nowhere to be found** (not sure if it's still open or not).
[/LIST]

---

### Post by merry_meerkat on 2011-11-10
> **ProntoAnthony said:**
> Everything you did sounds good. The only thing you have that is different than mine is you are using the 64-bit version. Are you also using the 64-bit version of 11.10?

I've read that the 32-bit version of Ubuntu is recommended even for those with 64-bit machines. And even though I have a AMD-64 chip in my desktop I'm using the 32-bit version on both machines so I can have the same software on both the laptop and desktop.

Thanks, it is true that I'm using 64-bit. My machine is 64-bit, and I'm using Ubuntu 64-bit. If someone confirms that this is the problem, then I'll probably stop using chrome.

---

### Post by ProntoAnthony on 2011-11-10
You might want to try this:

[http://www.upubuntu.com/2011/11/how-to-add-applications-manually-to.html](http://www.upubuntu.com/2011/11/how-to-add-applications-manually-to.html)

I have not tested the solution.

---

### Post by merry_meerkat on 2011-11-12
Well, for whatever reason the most annoying part of this problem has simply gone away. I'm not aware of having changed anything, but now the icon in the launcher/taskpanel behaves as it should (i.e. launching chrome, indicating with white triangle when its open, minimising and restoring it).

The problems with the dash are still there, but that has little impact on everyday use.

I tried the suggestion you linked to, but for some reason "main menu" does not let me add any entry.

---

### Post by roy913 on 2012-01-08
i have everything 32bit, still i have exactly the same problem.

---

### Post by vasa1 on 2012-01-08
> **roy913 said:**
> i have everything 32bit, still i have exactly the same problem.

What is your OS? Is it 10.04? Or is it 11.10? If it's 10.04, it can't be "exactly the same problem".

In any case, it maybe a nice idea to process the deb file using the Ubuntu Software Center rather than via terminal commands.

---

