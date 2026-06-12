---
title: "Adobe Reader in Google Chrome."
date: 2010-11-19
forum: General Help
---

### Post by bhishan on 2010-11-19
I use Ubuntu 10.10 and Windows Vista in my laptop. In both OS's I use Google Chrome. In Vista if I open a pdf file link Adobe reader opens the file within Google Chrome in a new tab, whereas in Ubuntu it just downloads the file and I have to open it outside the browser for it to work. How can I make Ubuntu do the same?

---

### Post by pytheas22 on 2010-11-19
It looks like [this]("https://chrome.google.com/extensions/detail/nnbmlagghjjcbdhgmkedmbmedengocbn") would be one solution, although it may not be exactly what you want.  It would open all of your PDFs in Google Docs.

If you want to open the PDF inside Chrome using external PDF reader that displays inside the Chrome window like you do in Windows, you'd need to install a Chrome plugin for that.  The PDF reader that comes installed by default in Ubuntu is Evince (which Ubuntu sometimes also refers to as "Document Viewer") and it has a browser plugin that works fine in Firefox, but apparently not so with Chrome.  If you search for something like "pdf plugin chrome ubuntu" there are a lot of people with this problem, but I couldn't find anyone who's found a better solution that using the Google Docs plugin.  I also didn't search extensively, however.

You could try installing the Linux version of Acrobat Reader from Adobe's site, which should also provide a browser plugin that might work better than the Evince one.  Personally I much prefer Evince over Reader, however, as it provides all the same features while being about 1000% lighter and faster, and never phones home to update itself.

---

### Post by bhishan on 2010-11-24
What is the path for chrome browser for ubuntu? In one of the options in Adobe reader it asks to specify the browser used and asks for the absolute path.

---

### Post by pytheas22 on 2010-11-25
Try:
```

/usr/bin/chromium-browser
```

---

### Post by bhishan on 2010-11-25
> **pytheas22 said:**
> Try:
```

/usr/bin/chromium-browser
```

I am using google chrome not chromium. Is it the same for both?

---

### Post by pytheas22 on 2010-11-26
I'm not sure if it's the same.  You can check which command is used to call the application by going to System>Preferences>Main Menu, finding the entry for Chrome and then selecting "Properties."  The "Command" field should tell you the path to the executable.  (If there's something like a %U in the command, ignore that part as it's not part of the path.)

---

### Post by kanishkdudeja on 2010-11-26
/usr/bin/google-chrome

---

### Post by bhishan on 2010-11-26
Still didn't work.

---

### Post by kanishkdudeja on 2010-11-26
Sorry. No idea.

---

### Post by pytheas22 on 2010-11-28
Did you use the menu-configuration tool to see which command is being used to launch Chrome?  If you type that command in a terminal, does Chrome start?  Are you sure there's not some possibly other problem with your configuration for the Adobe plugin?

---

### Post by bhishan on 2010-11-29
> **pytheas22 said:**
> Did you use the menu-configuration tool to see which command is being used to launch Chrome?  If you type that command in a terminal, does Chrome start?  Are you sure there's not some possibly other problem with your configuration for the Adobe plugin?

Yes i did it and it didnt work. I checked everything else many times and I dont seem to find any problems.

---

### Post by pytheas22 on 2010-11-30
> **bhishan said:**
> Yes i did it and it didnt work. I checked everything else many times and I dont seem to find any problems.

Sorry to hear that, although it's strange that typing the command that was given in the menu-configuration tool doesn't start Chrome.  It definitely should; otherwise Chrome wouldn't start from the menu either!

In any case, I'm afraid I'm out of ideas.  The best suggestions I can make are to try using the plugin that I linked to in my first post to open documents in Google Docs.  Using a different browser is also an option, obviously.

---

